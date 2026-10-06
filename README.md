# Fit Hunter Releases

**Latest Version:** 1.5.1 (stable)
**Date:** 2026-10-06

[⬇️ Download APK](https://github.com/walisoncm/fit_hunter-releases/releases/download/v1.5.1/fit_hunter_1.5.1.apk)

## Release Notes

# ✨ Fit Hunter v1.5.1 — AI Camera Pose Validator

## 🆕 What's New

- **AI Camera Pose Validator (System Daily Quests)**: Experience the authentic Hunter daily quest routine powered by on-device computer vision. Using Google ML Kit Pose Detection, Fit Hunter tracks your biomechanics in real-time across all three classic daily quest exercises:
  - **Squats**: Validates parallel knee depth ($\le 95^\circ$), upright posture, and includes walking step rejection.
  - **Push-ups**: Tracks elbow flexion ($\le 90^\circ$ descent, $\ge 160^\circ$ lockout) with full-body plank alignment verification ($\ge 145^\circ$ shoulder-hip-ankle line) to prevent sagging hip cheat reps.
  - **Sit-ups**: Tracks torso flexion ($\le 65^\circ$ peak contraction, $\ge 130^\circ$ floor extension) with knee-bent posture validation.
- **Fixed Quest Locked to Play**: Motion capture is 100% focused and locked to the selected quest (Push-up, Sit-up, or Squat) without in-exercise switchers, directly logging verified reps to that specific quest upon completion.
- **Animated Exercise Silhouette Guide (Picture-in-Picture)**: A floating HUD picture-in-picture (PIP) guide running in a smooth loop on the camera validation screen to demonstrate proper exercise execution in real time:
  - Vector silhouette animations for **Bodyweight Squats**, **Push-ups**, and **Floor Crunches** (all free / bodyweight movements without weights or benches).
  - Natural ping-pong frame cycle (`Start -> Movement -> Peak -> Movement -> Start`) demonstrating the ideal range of motion and joint positioning.
  - Floating PIP card can be minimized or expanded at any moment during the workout.
- **Active Hunter Mode Workouts Recorded to Google Health & Today's Exercises**: In Hunter Mode, all daily mission exercises are active physical challenges (push-ups, sit-ups, squats, and the 10KM run). Upon completing a camera-validated exercise or running session:
  - Exercises are automatically mapped to standardized activity types supported by Google Health Connect and Apple HealthKit (`CALISTHENICS` / Calisthenics with descriptive title, reps, duration, and burned calories).
  - The completed workouts immediately appear in **"Today's exercises"** (`WorkoutsList`) with their dedicated title, repetition count, and duration.
  - Active running workouts contribute directly and fully to the daily mission distance goal in Hunter Mode.
  - Automatically checks and requests workout write permissions before starting the camera pose validator if needed.
- **System HUD & Audio Feedback**: Cybernetic System HUD overlay featuring real-time joint angles, depth/peak confirmation badges, haptic response, audio clicks, and a post-workout quest completion summary with hunter XP rewards.
- **Zero-Latency & On-Device Privacy**: All skeletal pose estimation runs 100% locally on your device without transmitting video frames to the cloud or incurring external API latencies.

## 🛠️ Improvements & Fixes

- **Daily Quest Mode Selection (Casual Mode vs Hunter Mode)**: Choose the daily quest style that best fits your lifestyle and fitness routine:
  - **Casual Mode**: Track daily Steps, active Calories, and Distance passively via background sync with smartwatches and Health Connect, perfect for everyday users.
  - **Hunter Mode**: Undertake the System physical training routine with Push-ups, Sit-ups, Squats, and Running, powered by AI Camera form validation and quick-play buttons.
  - Easily toggle between modes anytime via the goal settings icon (⚙️) on the daily card, with customized goal validation rules for each mode.
- **Dedicated Circular Play Action on Each Daily Quest**: Each of the daily quest items features a compact circular icon-only action button (styled after the Fasting action button) to start the respective exercise. Tapping Play on Push-ups, Sit-ups, or Squats directly launches the AI Camera Pose Validator pre-selected for that exercise, automatically counting completed reps into today's daily mission upon finishing. Tapping Play on Running/Distance launches active GPS tracking. Once completed, the button shifts to a green checkmark icon.
- **Biomechanical walking filter**: integrated vertical hip-drop and bilateral leg symmetry checks to prevent walking steps towards the phone from being falsely registered as squats.
- **Clean visual with green edge glow**: removed invasive skeletal overlay lines in favor of a sleek emerald green edge pulse when valid exercise form is achieved.
- **Exclusive Double Reward Bonus for Hunter Mode**: The Hidden Quest and double reward bonus (+5 status points) are strictly reserved for Hunter Mode upon achieving double canonical goals. Casual Mode focuses on sustainable daily habit tracking.
- **Casual Mode XP Reward Floor**: Casual Mode Daily Quest XP reward is now guaranteed to be at least half of Hunter Mode canonical XP ($\ge 1000$ XP), ensuring fair progression even with lower step and calorie targets.
- **Hunter Mode Penalty Evaluation & Reversal**: Server-side daily penalty job and penalty reversal now support Hunter Mode canonical exercises (push-ups, sit-ups, squats, distance) alongside Casual Mode steps/calories, ensuring accurate penalty calculation and late-sync restoration across both modes.
- **Auto-Dismiss Goal Settings Dialog on Save in Hunter Mode**: Fixed an issue where the Daily Quest Settings dialog remained open after tapping "SAVE" in Hunter Mode. Added robust error handling, saving state indicators, support for comma-formatted decimals, local storage caching fallback, and guaranteed dialog dismissal.
- **Refined Floor Crunch Silhouette Biomechanics**: Updated the floor abdominal silhouette animation to accurately depict a conventional floor crunch: feet and legs remain stationary on the ground while the torso curls smoothly upward, completely eliminating any canvas angular jitter or tilt.
- **Deduplication of Multi-Part Camera Exercises & Health Connect Workouts**: Fixed an issue where completing daily mission exercises in multiple parts could cause earlier exercises to appear duplicated on Android devices when Health Connect synced the session. Enhanced the activity type matching to handle platform-specific mappings (e.g., `OTHER`, `CALISTHENICS`), prevented rapid double-submissions, and implemented an intelligent session deduplication pass that ensures each distinct exercise is displayed exactly once in "Today's exercises" while retaining accurate titles and burned calories.
- **Premium Subscription Now Available**: Fixed the Premium subscription not loading on the paywall. The app now connects to the subscription service in release builds and offers the monthly Premium plan, which removes all ads.
- **More Reliable Sit-up Counting**: Recalibrated the sit-up resting angle using live camera measurements so lying reps are recognized correctly, and the camera validator no longer freezes when pose detection stalls on a frame.

---
*This repository is automatically updated by CI/CD.*
