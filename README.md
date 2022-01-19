# vosk_flutter_plugin

Flutter plugin for Vosk speech recognition.

## How to use

### Configurations
Add this pro guard rules in ...android/app/proguard-rules.pro
If file not exist, create it.
```proguard
-keep class com.sun.jna.* { *; }
-keepclassmembers class * extends com.sun.jna.* { public *; }
```

Add this plugin to pubspec.yaml
```dart
vosk_flutter_plugin:
```

### Load and init model
```dart
ByteData modelZip = await rootBundle.load('assets/models/vosk-model-small-en-us-0.15.zip');
await VoskFlutterPlugin.initModel(modelZip);
```

### Start recognition
```dart
VoskFlutterPlugin.start();
```

### Stop recognition
```dart
VoskFlutterPlugin.stop();
```

### Listen to results
```dart
StreamBuilder(
  stream: VoskFlutterPlugin.onPartial(),
  builder: (context, snapshot) => Text(snapshot.data.toString()),
),
```

