# Fit Hunter Releases

**Latest Version:** 1.0.26-beta (beta)
**Date:** 2026-06-03

[⬇️ Download APK](https://github.com/walisoncm/fit_hunter-releases/raw/main/beta/fit_hunter_1.0.26-beta.apk)

## Release Notes

# Release Notes - v1.0.26-beta

## 🌟 Major Features

### 📬 Message Delivery Status
- **Sent Indicator (✓):** A single grey checkmark appears when your message is successfully sent to the server.
- **Delivered Indicator (✓✓):** A double grey checkmark appears when the recipient's device receives the message (via push notification or app resume).
- **Read Indicator (✓✓):** A double blue checkmark appears when the recipient opens the conversation and views the message.
- **Real-Time Updates:** Status changes are pushed instantly via Supabase Realtime — no need to refresh.
- **Smart Timestamp Grouping:** Messages now show individual timestamps when their delivery status differs, even if sent in the same minute. Edited messages also always display their own timestamp.
- **Retry Queue:** Failed status updates are automatically retried up to 3 times when connectivity restores.
- **Reconnection Resilience:** After a network disconnection, message statuses are refreshed from the server within 5 seconds of reconnection. Last known status is preserved during offline periods.

### 🔐 End-to-End Encryption (E2EE) for Private Messages
- **Zero-Config Security:** Encryption keys are automatically generated and exchanged when you first log in — no setup required.
- **X25519 + AES-256-GCM:** Industry-standard cryptography ensures only you and the recipient can read messages.
- **Lock Indicator:** A small lock icon (🔒) appears next to encrypted message timestamps for visual confirmation.
- **Backward Compatible:** Existing messages remain readable; only new messages are encrypted.
- **Secure Key Storage:** Private keys never leave your device — stored via platform-secure storage (Keychain/Keystore).
- **Graceful Fallback:** If a friend hasn't updated yet, messages send as plain text. If decryption fails, a lock icon placeholder is shown.

### 🛡️ Group End-to-End Encryption (Sender Keys)
- **Parties & Guilds Security:** Group messages are now fully encrypted using the "Sender Keys" protocol.
- **Auto-Rotation:** Encryption keys are automatically rotated when a member leaves a party or guild to ensure forward secrecy.
- **Zero-Touch Key Distribution:** Your device securely shares group keys with teammates automatically when you join or they join.
- **Offline Key Recovery:** Missed encryption keys sent while you were offline are automatically fetched and processed when you resume.

### ⌨️ Real-time Typing Status
- **Live Typing Indicator:** See when the person you're chatting with is composing a message — a subtle "typing..." appears in the chat header.
- **Chat List Preview:** Typing status also shown in the conversations list as "typing..." subtitle.
- **Group Chat Support:** In Guild and Party chats, see multiple names when people are typing (e.g., "Alice and Bob are typing..." or "Several people are typing...").
- **Smart Debounce:** Typing status is broadcast efficiently with a 3-second inactivity timeout to avoid unnecessary network traffic.
- **Privacy-First Cleanup:** Your typing status is automatically cleared when you send a message, navigate away, or background the app — no ghost indicators.
- **Full i18n Support:** Typing indicator labels fully translated to Portuguese and English.

### 🏰 Custom Guild Avatar Photos
- **Guild Photo Upload:** Guild leaders can now set a custom photo as the guild avatar, replacing the old emblem system.
- **Legacy Emblem Removal:** The procedurally generated guild emblems have been removed in favor of photo-based avatars.
- **Seamless Migration:** Existing guilds display a default avatar until a photo is uploaded.

### 💾 Message Retention & Local Backup
- **Local Message Backup:** Messages are now synced to a local encrypted backup for offline access and faster loading.
- **Decrypt-on-Receive:** Group messages are decrypted immediately upon receipt and stored locally in plaintext for performance.
- **Party & Guild Sync:** Both party and guild messages sync to local backup with full E2EE support.
- **Orphan Cleanup:** Automatic detection and cleanup of orphaned group messages when re-syncing.
- **Local-First Merge:** When loading conversations, local backup data takes priority with server data merged as supplement.

### 📊 App Stats Standardization
- **Unified StatDisplay Component:** All HUD statistics (Daily Missions, Party Challenges, Dungeons) now use a consistent visual component.
- **Centralized HUDService:** A single service manages all active metrics, ensuring reactive updates and visual consistency.

## 🎨 UI/UX Improvements

### 📱 Social HUD Scroll Redesign
- **Unified Scroll:** Stories, search bar, and chat list now scroll together as one cohesive view instead of being separated.
- **Pinned Search Bar:** The search input scrolls up with the content but pins at the top of the screen when reached.
- **Snap-Back on Reverse Scroll:** When scrolling back down at any point, the view smoothly animates back to reveal stories and search bar.
- **Single Refresh Indicator:** Pull-to-refresh now shows only one loading spinner for the entire view.

### 🔄 Story Feed Improvements
- **Viewed Indicator:** Story rings now show a gradient ring for unviewed stories and a gray ring for viewed ones with optimistic updates.
- **Own Story Ring Unification:** Own story avatar uses the same StoryRing widget as friends, with numeric badge removed.
- **"You" Label:** Own story avatar now shows a localized "You" label instead of the player name.
- **Persist Own Views:** Own story views are persisted correctly and marked as viewed optimistically.

### 🔑 Login Page
- **App Icon:** Replaced the bolt icon with the app icon on the login page for brand consistency.

## 🛠️ Technical Improvements

### 🏥 Health Connect
- **Background Permission Prompt:** Users are now prompted to grant Health Connect background data access for automatic syncing.
- **Settings Shortcut:** Direct link to Health Connect settings page for managing background read permissions.

### 🔧 Architecture & Refactoring
- **Chat Controller Extraction:** Chat logic extracted into dedicated controllers, simplifying chat page widgets.
- **E2EE Key Recovery Fix:** Improved key recovery flow for decrypt-on-receive and local-first message merge scenarios.
- **Delivery Status Fix:** Fixed delivery status updates on message receipt and encrypted push notification decryption.

### 🗄️ Database & Migrations
- **Delivery Status Schema:** New `status`, `delivered_at`, and `read_at` columns on `private_messages` with forward-only transition enforcement via trigger.
- **Row Level Security:** Receiver can only update status columns; sender cannot modify delivery status fields.

### 🧪 Testing
- **Property-Based Tests:** Comprehensive test coverage using Glados for enum parsing, transitions, widget rendering, message filtering, and accessibility.
- **Message Merge Tests:** Updated to match local-first priority logic.

---
*This repository is automatically updated by CI/CD.*
