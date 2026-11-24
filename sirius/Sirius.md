<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius 0.1.8.17

Sirius chats can now work together, and SiriusBrowser can use a connected Robinhood Agent Card at supported checkouts. You can also retry a stalled Goal from its saved progress and share the latest version of an edited PDF with your chat.

## Wallets & Payments

- **Connect a Robinhood Agent Card.** In **Settings → Wallets & Payments → Connections**, sign in through SiriusBrowser, verify the card, and optionally make it your default for agent checkout. The connection can be paused or disconnected from Settings. Coinbase CDP and Robinhood have independent connection and approval settings.
- **Set spending rules for each payment method.** The Spending tab brings together the **Allow agent purchases** switch, per-order and monthly limits, allowed merchants, and confirmed spending. Choose **Ask every time** or allow eligible USD card purchases **Within rules**. Strict mode and matching ask rules still require approval. Pending checkouts count against the available card limit across app restarts and concurrent checkouts.
- **Use the approved card at checkout.** Sirius keeps the selected card attached to the review and checks the current merchant, currency, and total before filling supported checkout forms, including supported Stripe card fields. The card details stay in the native checkout flow. Filling the card and submitting the order are separate actions.
- **See what happened to a payment.** Wallet Activity shows paid, pending, declined, blocked, denied, canceled, and failed attempts, with details for each. Opening Activity or choosing **Refresh** checks recent unresolved card checkouts against available issuer history. A matching authorization awaiting settlement stays **Pending** and can move to **Paid** when it posts. Sirius can also confirm a supported itch.io purchase using the merchant receipt and matching issuer authorization.
- **Save a personal card for your own checkout.** Turn on **Offer saved cards at checkout** to use a card stored in macOS Keychain. Touch ID or your Mac password unlocks the fill on supported HTTPS forms. You enter any required security code and submit the form yourself.
- **Review x402 payments from the page.** On supported payment pages, choose **Review payment** to see the amount, network, and recipient. **Review in Composer** brings that offer to chat without replacing your draft. The payment stays tied to the offer you reviewed and always requires your approval. Coinbase CDP and x402 payments use the **Wallet payments** component in Settings.

## Chats can work together

- **Send messages and files between saved chats on the same Mac.** Ask one chat to send another a note, link, or file, check delivery, or watch for updates. The receiving transcript identifies the source chat, and clicking its label opens that conversation.
- **Reach a chat even when it’s closed.** With Sirius running and the main window available, a saved desktop chat can reopen in the background to receive and answer a message without taking focus. A saved conversation on a configured messaging channel can also receive and reply through that channel.
- **Check a Goal by name.** A chat can find a saved Goal by its objective, chat title, or project and check its status. A request to control a Goal goes to the chat that owns the verified Goal.

## Approvals and activity

- Wallet, credential, tool, and computer-use requests use a consistent layout above the composer, with the action and scope up front and additional information under **Details**. Strict-mode requests for authenticated HTTP calls show the credential, destination, and method together.
- When a permission or connection change withdraws a pending request, Sirius explains what happened in the transcript. Unrelated requests stay open. **Permissions & Security → Activity** shows the decision, scope, and source in plain language, with a direct link to Wallet Activity.

## Goals and notifications

- **Retry a stalled Goal.** If a Goal stopped because it made no progress, press **Play** to continue from its saved progress. Sirius resets the no-progress counter and keeps the Goal’s existing usage and limits. Expand the Goal tab to see its objective.
- Goal views and Notification Center refresh when saved changes arrive. Sirius processes those updates off the main thread to keep the sidebar and notification drawer responsive during active work.

## Browser and passkeys

- Closing the selected site-opened popup returns you to its opener when that tab is still open. Browser Use can target visible controls in embedded frames from the current viewport and recognize when a sequence of actions keeps returning to the same page or form state.
- When signing in with a passkey on your phone, choose which passkey to use in Sirius if the phone returns several for the site.

## Reader and workspace Start

- **Share the latest version of an edited PDF.** When you send a message with an edited PDF attachment open in Reader, Sirius finishes saving and gives the chat a read-only copy for that turn, with the pages containing Reader signature marks identified.
- Reader keeps a failed file open in its tab and offers **Retry**, **Locate File**, and **Show Parent Folder** so you can recover it.
- The workspace Start page shows compact previews for recent files and can display **Favorites** and **Frequently Visited** together.
- Text search preserves file and line details for paths such as `release-255-draft`.

## Updated license terms

The Sirius license now covers agent-assisted purchases and payments. Existing users will see the updated agreement on launch. If the core runtime is already ready, choose **Accept & Continue** after reviewing the terms.
