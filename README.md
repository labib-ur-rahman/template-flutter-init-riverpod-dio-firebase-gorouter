# Flutter Init

Production-ready Flutter starter built with a feature-first structure, Riverpod, Dio, Firebase, GoRouter, and Easy Localization.

This template is designed to give teams a clean starting point for authentication flows, scalable feature modules, shared UI primitives, and app-level infrastructure without forcing a heavy architecture rewrite later.

## Highlights

- Feature-first folder structure under `lib/src/features`
- Riverpod and Hooks Riverpod for app state
- GoRouter-based navigation
- Firebase bootstrap with auth-ready foundation
- Dio client configured through centralized app config
- Easy Localization with English and Spanish translations
- Shared UI kit, wrappers, hooks, helpers, and services
- Material 3 light and dark themes
- Native splash integration via `flutter_native_splash`

## Tech Stack

| Layer | Package / Approach |
| --- | --- |
| State management | `flutter_riverpod`, `hooks_riverpod`, `flutter_hooks` |
| Navigation | `go_router` |
| Networking | `dio` |
| Backend | `firebase_core`, `firebase_auth`, `cloud_firestore`, `firebase_database`, `firebase_storage` |
| Localization | `easy_localization` |
| Persistence | `shared_preferences`, `flutter_secure_storage` |
| UI utilities | `flutter_screenutil`, `skeletonizer`, `flutter_svg`, `cached_network_image` |
| Device utilities | `permission_handler`, `device_info_plus`, `url_launcher`, `share_plus`, `image_picker` |

## Project Structure

```text
lib/
  main.dart
  src/
    app.dart
    config/
    core/
    extensions/
    features/
      auth/
        data/
        domain/
        presentation/
      home/
      onboarding/
    imports/
    routing/
    services/
    shared/
      enums/
      helpers/
      hooks/
      widgets/
      wrappers/
    theme/
    utils/
```

## Included Starter Flow

The current scaffold already includes:

- Onboarding screen
- Login screen
- Signup screen
- Forgot password screen
- Home screen
- Session listener that redirects based on Firebase auth state

Initial routing starts at `/onboarding`, and session changes are handled centrally through `SessionListenerWrapper`.

## Getting Started

### 1. Install dependencies

```bash
flutter pub get
```

### 2. Create your environment file

Create a root `.env` file:

```env
API_BASE_URL=https://api.example.com
```

`AppConfig` reads `API_BASE_URL` during startup and falls back to `https://api.example.com` if it is missing.

### 3. Configure Firebase

Firebase is initialized in [`lib/src/config/app_config.dart`](/Users/bdcalling/Labib's Workspace/template-flutter-init-riverpod-dio-firebase-gorouter/lib/src/config/app_config.dart:1), so native Firebase setup is required before running the app.

Typical setup:

```bash
dart pub global activate flutterfire_cli
flutterfire configure
```

Make sure the generated Firebase configuration files are added for each target platform you plan to support.

### 4. Run the app

```bash
flutter run
```

## Localization

Translations live in:

- [`assets/translations/en.json`](/Users/bdcalling/Labib's Workspace/template-flutter-init-riverpod-dio-firebase-gorouter/assets/translations/en.json:1)
- [`assets/translations/es.json`](/Users/bdcalling/Labib's Workspace/template-flutter-init-riverpod-dio-firebase-gorouter/assets/translations/es.json:1)

Generated locale keys are stored in:

- [`lib/src/core/i18n/locale_keys.g.dart`](/Users/bdcalling/Labib's Workspace/template-flutter-init-riverpod-dio-firebase-gorouter/lib/src/core/i18n/locale_keys.g.dart:1)

When translation files change, regenerate the keys:

```bash
flutter pub run easy_localization:generate -S assets/translations -O lib/src/core/i18n -o locale_keys.g.dart
```

## Splash Screen

Native splash configuration is defined in [`flutter_native_splash.yaml`](/Users/bdcalling/Labib's Workspace/template-flutter-init-riverpod-dio-firebase-gorouter/flutter_native_splash.yaml:1).

After updating splash assets or colors, regenerate it with:

```bash
dart run flutter_native_splash:create --path=flutter_native_splash.yaml
```

## Authentication Notes

The scaffold currently ships with Firebase Auth service methods for:

- Login
- Signup
- Password reset
- Logout
- Current session lookup

Relevant files:

- [`lib/src/services/auth_service.dart`](/Users/bdcalling/Labib's Workspace/template-flutter-init-riverpod-dio-firebase-gorouter/lib/src/services/auth_service.dart:1)
- [`lib/src/features/auth/data/repositories/auth_repository_impl.dart`](/Users/bdcalling/Labib's Workspace/template-flutter-init-riverpod-dio-firebase-gorouter/lib/src/features/auth/data/repositories/auth_repository_impl.dart:1)
- [`lib/src/features/auth/presentation/providers/session_provider.dart`](/Users/bdcalling/Labib's Workspace/template-flutter-init-riverpod-dio-firebase-gorouter/lib/src/features/auth/presentation/providers/session_provider.dart:1)

## Architecture Notes

- Features own their `data`, `domain`, and `presentation` layers.
- Shared cross-cutting pieces live under `lib/src/shared`.
- App-wide infrastructure lives under `config`, `routing`, `services`, `theme`, and `utils`.
- `AppConfig.init()` initializes Firebase and the shared Dio client before `runApp`.

For a brief architectural note, see [`architecture.md`](/Users/bdcalling/Labib's Workspace/template-flutter-init-riverpod-dio-firebase-gorouter/architecture.md:1).

## Next Steps After Scaffolding

- Replace placeholder API base URLs in `.env`
- Complete native Firebase setup for your target platforms
- Add platform permissions for features like camera, gallery, and sharing
- Expand feature modules under `lib/src/features`
- Add tests beyond the default widget smoke test

## Additional Documentation

- [`SETUP.md`](/Users/bdcalling/Labib's Workspace/template-flutter-init-riverpod-dio-firebase-gorouter/SETUP.md:1)
- [`architecture.md`](/Users/bdcalling/Labib's Workspace/template-flutter-init-riverpod-dio-firebase-gorouter/architecture.md:1)

## License

Use this template according to your team or product requirements.
