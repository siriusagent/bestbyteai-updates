<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius 0.1.8.8 · Build 215

## GPT prompt caching

GPT-6.2 Sol and Astra can now reuse the instructions Sirius sends on each step of a conversation. This fixes a prompt-format issue that made repeated instructions count as fresh input, including during tool use. The fix applies to ChatGPT sign-in and the OpenAI API. Background reflection also reuses the cache for the conversation it is reviewing.

## Background memory and profile nudges

- **Keep chatting while Sirius reviews what to remember.** After a completed turn, a nudge queues a review on your configured background provider. Memory reviews look for facts worth remembering. Profile reviews look for stable preferences you’ve shared. Both get priority over pending chat recaps and can finish without saving anything. Switching chats, closing a session, or quitting Sirius leaves queued work for the background worker.
- **Sirius can still remember something on the spot.** Ask in your own words, or let Sirius save a detail when it comes up. The background reviews also work across remote conversations, including SiriusMsg.
- **A profile question stays in the conversation where it came up.** For example, if you ask for a recurring Monday briefing and haven’t given a time zone, the reviewer can suggest a question. On your next message in that private chat, Sirius can ask it in its reply or skip it if a placeholder will do. A suggestion alone never becomes a saved preference.
- **Choose how often reviews run.** In **Settings → Context & Memory**, turn memory and profile nudges on or off independently and set their intervals. Memory can come due after chat turns or tool iterations. Profile follows chat turns. The chat quick menu can mute both. Ask mode and Temporary Chat skip periodic reviews.
