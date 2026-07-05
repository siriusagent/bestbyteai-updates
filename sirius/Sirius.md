<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.109

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

This release fixes a packaged-app crash introduced in earlier alphas and
restores native LaTeX math glyphs in signed builds.

## What's new

- **Fixed a packaged-app crash on `Bundle.module`.** A computer-use
  `observe` call against a bundled app (Safari, TextEdit, Music, Terminal,
  Finder, System Settings, …) trapped with `EXC_BREAKPOINT` inside
  SwiftPM's generated `Bundle.module` accessor
  (`fatalError("unable to find bundle named SiriusUI_SiriusUI")`) because
  the SiriusUI resource bundle ships without an `Info.plist`, so
  `Bundle(url:)` returns nil. `ComputerAppAdapter.guidance(for:)` now
  resolves guidance markdown through `SiriusUIResourceLookup` (a
  filesystem probe that returns nil on miss) like every other resource
  site, and the guard test now scans all of `Sources/SiriusUI` for
  `Bundle.module` usage so a new site cannot slip past. This is the
  alpha.108 crash `F8DBD5E5`.
- **Native LaTeX math glyphs render again in signed builds.** Picking up
  SiriusMarkdown 0.6.3, which vendors SwiftMath as an inline target and
  patches `MTFont.fontBundle` to search
  `Bundle.main.url(forResource:)` / `Bundle(for:).url(forResource:)`
  (which find the resource bundle under `Contents/Resources`) before the
  `.app` root and the SwiftPM build-time fallback. Native math now
  renders without breaking the signed versioned-bundle layout. The SPM
  resource bundle renamed from `SwiftMath_SwiftMath.bundle` to
  `SiriusMarkdown_SwiftMath.bundle` (`<Package>_<Target>` convention);
  `build.sh` copies every `*.bundle` generically so no special-case copy
  was needed. The external `mgriebling/SwiftMath.git` dependency is gone.

## Notes

- **Sparkle build version** is `109` (`CFBundleVersion`), the primary
  comparison key for auto-update. Apps on `108` or earlier will offer
  this build.
- **Signed-product layout verified:** `.app` root contains only
  `Contents/`, `SiriusMarkdown_SwiftMath.bundle` lands at
  `Contents/Resources/`, and `codesign --verify --deep --strict` passes.
- **Known follow-up:** the SiriusUI resource bundle still ships without
  an `Info.plist` (a SwiftPM build-hygiene issue); runtime resource
  sites avoid `Bundle.module` for that reason, but the bundle is not
  individually codesign-verifiable as a standalone bundle. Not a
  runtime blocker.
