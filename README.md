# Fit Hunter Releases

**Latest Version:** 1.0.27-beta (beta)
**Date:** 2026-06-17

[⬇️ Download APK](https://github.com/walisoncm/fit_hunter-releases/releases/download/v1.0.27-beta/fit_hunter_1.0.27-beta.apk)

## Release Notes

# Release Notes - v1.0.27-beta

## 🌟 Major Features

### 🔔 Real-Time Update Notifications
- **In-App Popup on New Version:** When a new version is published, the update popup now appears immediately inside the app — no need to close and reopen.
- **Background Fallback:** If the app is in the background when a new version is published, a system notification is sent with the same message as the in-app popup.

### 📥 Reliable APK Download
- **Screen Stays Awake During Download:** The screen now remains active while downloading an update APK, preventing the OS from terminating the process when the device locks.

### 🔐 Signal Protocol Encryption (Double Ratchet + X3DH)

We upgraded the private message encryption engine from static ECDH to the Signal Protocol — the same standard used by WhatsApp and Signal.

- **Perfect Forward Secrecy:** Every message uses unique keys that rotate automatically with each exchange. Even if a current key were compromised, past conversations remain protected.
- **Automatic Session Setup (X3DH):** The very first message to a contact transparently establishes a secure encrypted channel — no configuration needed.
- **One-Time Prekeys (OTKs):** Secure sessions can be initiated even when the recipient is offline.
- **Security Code Notification:** When a contact reinstalls the app or regenerates their keys, a clear in-chat notification appears (similar to WhatsApp/Signal). Key exchange and re-delivery of held messages happen automatically in the background.
- **Offline Resilience:** Messages held during a key exchange are automatically delivered when you reopen the app.
- **72-Hour Message Expiration:** Messages that cannot be delivered within 72 hours are expired with a notification, preventing infinite accumulation.
- **Decrypted Previews:** The conversations list now shows the readable message content instead of the lock icon 🔒.
- **Automatic Migration:** Existing messages were migrated to the new schema transparently — no action required.

### 💬 Ephemeral Global Chat
- **Real-Time Messages with Zero Persistence:** The global chat now operates in a fully ephemeral mode via Supabase Realtime Broadcast. Messages arrive instantly and exist only in memory while the app is in the foreground. When you minimize the app, the history is automatically discarded. No messages are stored in any local or remote database.

### 🏰 Party & Guild Chat — Full Feature Parity
- **Parity with Private Chat:** Party and guild chats now offer the same experience as private chats: message editing, bulk deletion, replies, reactions, and polls.
- **Per-Member Delivery & Read Tracking:** 3-state delivery indicators (sent ✓, delivered ✓✓, read ✓✓ blue) now work in group chats with individual per-member tracking, just like private chat.
- **WhatsApp-Style Group Push Notifications:** Push notifications for party and guild messages now display the group name, sender avatar and name, and message content — including full E2EE support with background decryption.

## 🎨 UI/UX Improvements

### ✉️ Invitation Cancellation from Chat Bubble
- **Cancel Party and Guild Invites:** Senders of party or guild invitations can now cancel them directly from the chat bubble by tapping the new "CANCEL INVITATION" button. This automatically retracts the pending invite and deletes the invitation message.

### 💬 Chat Background Wallpaper
- **WhatsApp-Inspired Fit Hunter Wallpaper:** Created a premium, subtle chat background wallpaper featuring vector fitness doodles (dumbbells, kettlebells, stopwatches, hearts, targets, swords, shields, trophies, crowns, water bottles, flames, chat bubbles, and stars) glowing faintly in neon cyan.
- **Extended Background Coverage:** The wallpaper now covers the entire chat page body, including the bottom input bar/footer, which now has a transparent background.
- **Enhanced Pattern Density & Size Variance:** Increased doodle density and added size, scale, and stroke-width variance alongside geometric filler shapes (pluses, rings, wavy lines, sparkles, double stars) to achieve a richer, more organic WhatsApp-style look.
- **Standardized System Message Bubble Background:** Updated all system messages (such as team join/leave events and security code changes) to use a unified, fully opaque bubble background (`AppTheme.cardGrey` with no transparency) for maximum readability against the chat wallpaper.

### 📱 Stories Scroll Behavior Fix
- **Floating Stories on Scroll Up:** The stories section now reappears when scrolling up at any position in the chat list — not just at the top.
- **No More Jump to Top:** Only the stories header floats back, without affecting the chat list position.
- **Opaque Background:** The stories section now has a solid background, preventing chat items from showing through.

### 🏥 Background Permission Flow (Health Connect)
- **Direct Settings Access:** After granting Health Connect permissions, the app now opens the Health Connect settings page directly — no intermediate confirmation dialog.
- **One-Time Prompt:** The background permission redirect only happens once and never repeats.

## 🛠️ Technical Improvements

### 🔒 Database Security
- **RLS Hardening:** Enabled RLS on pending tables, set a static `search_path` on all `SECURITY DEFINER` functions to prevent privilege hijacking, and optimized Row Level Security policies for better performance at scale.
- **Foreign Key Indexes:** Added 44 B-tree indexes on FK columns across 19 tables, reducing join query latency.
- **Cascading Deletes:** Added foreign keys referencing message tables (`messages`, `private_messages`, `guild_messages`, `party_messages`, `scheduled_messages`) to the `live_locations` table with `ON DELETE CASCADE` and trigger-based backlinking, ensuring live location cleanup when messages are deleted. Added cascade deletion triggers for polymorphic relations (`message_reactions` and `message_poll_votes`) and explicitly configured `ON DELETE CASCADE` for the `party_checkins.party_id` reference.
- **Stories Auto-Pruning & Storage Cleanup:** Implemented minutely automatic database pruning of expired stories via `pg_cron`. Added a database trigger `trigger_cleanup_story_storage` on the `stories` table that automatically deletes corresponding media files from the Supabase storage bucket (`storage.objects`) whenever a story is deleted.
- **Avatar Storage Cleanup:** Implemented automatic database triggers (`trigger_cleanup_avatar_hunter_profiles`, `trigger_cleanup_avatar_guilds`, `trigger_cleanup_avatar_parties`) that listen for updates or deletions of profiles, guilds, and parties, automatically removing any unused/orphaned avatar files from the `avatars` storage bucket.
- **Chat Media Storage Cleanup & Retention Policy:** Implemented automatic database triggers (`trigger_cleanup_message_media`, `trigger_cleanup_private_message_media`, `trigger_cleanup_guild_message_media`, `trigger_cleanup_party_message_media`, `trigger_cleanup_scheduled_message_media`) that listen for deletions on message tables, automatically removing their associated files from the `chat-media` storage bucket. Designed a native PostgreSQL procedure `public.enforce_message_retention_policy` scheduled daily via `pg_cron` that cleans up expired media files older than 3 days (setting message reference to `NULL`) and deletes messages older than 7 days in performance-efficient batches, replacing legacy Edge Function crons.

---
*This repository is automatically updated by CI/CD.*
