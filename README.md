# UniPlan

UniPlan turns a timetable image into calendar entries. Pick an image or take a photo, send it for extraction, and view the resulting schedule.

It is built with Flutter, OpenRouter and local Hive storage.

## How it works

The scanner sends the image to OpenRouter using `openai/gpt-4o-mini`. The response becomes schedule events saved locally. Although the service file is named `claude_service.dart`, the configured model is GPT-4o mini.

The app also supports adding and editing events manually.

## Run locally

Install Flutter and get your own OpenRouter API key. Replace the placeholder in `lib/services/claude_service.dart` for local development, then run:

```sh
flutter pub get
flutter run
```

Extraction requires internet access and may incur OpenRouter charges. Keep your key out of commits. A distributed version should route requests through a backend rather than bundle a private key.

On Windows, use the gallery option; camera capture is not supported by the scanner there.

## Current limitations

Extraction can misread a timetable. Results are saved immediately, so check the calendar after scanning. Scanning the same timetable again can create duplicates.

Schedule records stay in local Hive storage. There is no account-based sync between devices.
