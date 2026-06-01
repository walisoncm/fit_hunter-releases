# Fit Hunter Releases

**Latest Version:** 1.0.25-beta (beta)
**Date:** 2026-06-01

[⬇️ Download APK](https://github.com/walisoncm/fit_hunter-releases/raw/main/beta/fit_hunter_1.0.25-beta.apk)

## Release Notes

# Release Notes - v1.0.25-beta

## 🌟 Major Features

### � Ephemeral Stories (24h)
- **Story Creation:** Hunters can share photos and short videos (up to 30s) as stories visible only to accepted friends, with automatic expiration after 24 hours.
- **Story Feed:** Horizontal carousel at the top of the Social Hub with circular avatars and colored rings (gradient for unviewed, grey for viewed).
- **Full-Screen Viewer:** Immersive experience with segmented progress bar, tap navigation (right/left), swipe between friends, long-press to pause, and auto-advance (5s for photos, video completion for videos).
- **My Stories Management:** WhatsApp-style page listing all active stories with thumbnail, view count, timestamp, and individual delete option.
- **View Count:** Display of unique view count on own stories, with viewer list (swipe-up).
- **Story Deletion:** Delete button with confirmation, optimistic feed removal, and auto-advance to next story.
- **External Share to Stories:** When receiving media from external apps, a "My Stories" option appears in the share picker to post directly as a story.
- **Media Preloading:** Background preloading of the next story for a smooth viewing experience.
- **Smart Caching:** Integration with MediaCacheService with eviction priority for expired stories.
- **Automatic Cleanup:** Scheduled Edge Function (pg_cron) to remove expired stories every hour.
- **Privacy via RLS:** Story visibility restricted to accepted friends via Row Level Security at the database level.

### 🔘 Redesigned Social Hub
- **Floating Action Button (FAB):** Action menu (Create Party) moved to a floating button in the bottom-right corner with popup menu above the button.
- **Collapsible Stories:** Scrolling the chat list up hides the stories carousel with a smooth animation to give more space. Scrolling back down reveals it again.
- **Bottom Padding:** Spacing at the end of the chat list so the FAB doesn't cover the last item.

### 🌐 i18n Fixes
- **Media Labels:** Fixed bug where media type labels (Photo/Video/Audio) always appeared in English regardless of device language.

### �📸 Redefined Media Experience
- **Multi-Selection:** You can now select and send up to 10 photos or videos at once directly from the quick attachment panel.
- **Smart Media Groups:** Batch-sent messages are automatically grouped into an elegant grid, saving chat space.
- **Advanced Viewer:** New full-screen viewing interface that supports navigation between group items, as well as individual or batch selection and deletion.
- **Video Thumbnails:** Fixed thumbnail resizing to avoid distortion, now using smart aspect ratios.

### 🗑️ Global Sync and Batch Deletion
- **Real-time Global Delete:** Implemented a monitoring system that ensures deleted messages disappear instantly from all participating devices.
- **Group Deletion:** New functionality to delete entire media groups with a single command, including a confirmation dialog for "Delete for me" or "Delete for everyone".

### 📍 Live Location and Social
- **Live Location Sharing:** Hunters can now share their real-time location with guild or party members.
- **Enhanced Chat Bubbles:** Major refactor of chat bubbles for better performance, tight wrapping, and rich reply previews.
- **Unified Media Reactions:** Reactions on media groups are now aggregated for a cleaner view.

### 😃 Expressions and Emojis
- **Categorized Emoji Picker:** Full organization by categories (Faces, Animals, Food, Activities, etc.) with quick navigation.
- **Continuous Scrolling:** Much smoother and more performant emoji experience.
- **GIPHY Stickers & GIFs:** Improved support and rendering for animated stickers and GIFs.

## 🛠️ Refactoring & Performance

### 🛡️ Health & Biometrics
- **Health Connect Unified Permissions:** Fixed permission issues (SecurityException) by unifying Step, Workout, and Nutrition requests.
- **Improved Nutrition Tracking:** Added generic nutrition support and a dynamic "Metabolic Fuel" card that only appears when data is present.
- **Precision Biometrics:** Fine-tuned calorie and distance factors for pinpoint accuracy (3398 steps = 177 kcal / 2.42 km for 85kg hunter).
- **Workout Routes:** Integrated map visualization for workout routes with a native bridge for Health Connect data.
- **Sleep Efficiency:** Added advanced sleep stage analysis and a new history navigator.

### 🎥 Video Processing
- **Trim Stabilization:** Fixed trim service failures when processing multiple videos.
- **Media Preview:** Optimized pre-send preview flow.

## 🚀 Improvements & Fixes
- **HUD Reorganization:** The Status Window (HUD) now prioritizes System Advice and Daily Missions at the top, with an intelligent side-by-side layout for Nutrition and Sleep.
- **System Calibration:** New dialog for biometric calibration and Hunter awakening process.
- **Authentication:** Critical fix for Google Login reauthentication token failures.
- **Interface & Layout:** 
    - Fixed RenderFlex overflows in the HUD during loading.
    - Standardized card designs for a more harmonic cyberpunk aesthetic.
    - Improved touch detection and contextual menu behavior.
- **System:**
    - Comprehensive bilingual audit and fix for missing translations (PT/EN).
    - Stabilization of unit and integration tests.
    - Improved migration idempotency for database schema.

---
*This repository is automatically updated by CI/CD.*
