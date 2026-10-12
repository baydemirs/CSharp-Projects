# SpeechToText

![C#](https://img.shields.io/badge/language-C%23-512BD4)
![.NET Framework 4.8](https://img.shields.io/badge/.NET_Framework-4.8-512BD4?logo=dotnet&logoColor=white)
![Windows Forms](https://img.shields.io/badge/UI-Windows_Forms-0078D4)
![NAudio 2.2.1](https://img.shields.io/badge/NAudio-2.2.1-008080)
[![MIT License](https://img.shields.io/badge/license-MIT-green)](LICENSE)

## Project Overview

SpeechToText is a Windows Forms desktop application written in C# and targeting .NET Framework 4.8. It uses `System.Speech.Recognition` for speech recognition and NAudio for capturing audio from a selected microphone.

The application lists the speech recognizers installed on the computer, lets the user select a microphone, and displays recognized phrases in a read-only text area. Turkish (`tr-TR`) recognition depends on a compatible Turkish recognizer being installed and visible to `SpeechRecognitionEngine.InstalledRecognizers()`. The project does not include a Turkish recognition model or installer.

Originally maintained as a standalone repository, the project was imported into this collection with its original Git history preserved.

> **Validation status:** This is an educational desktop project with known dependency and audio lifecycle limitations. A successful clean build and end-to-end recognition with a real microphone have not yet been verified. It should not be treated as production-ready.

## Features

The following behaviors are implemented in the source; their presence does not imply successful end-to-end validation:

- Enumerate installed speech recognizers and display their language and name.
- Prefer a Turkish recognizer in the UI, then English (`en-GB`), then the first available recognizer.
- Enumerate microphone input devices through NAudio and allow device selection.
- Start and stop continuous recognition using `RecognizeMode.Multiple` and `DictationGrammar`.
- Capture selected-microphone input as 16 kHz, 16-bit, mono PCM audio.
- Append recognized phrases with a confidence score of at least `0.5` to a scrollable text area.
- Display listening status and error dialogs.

The UI uses Turkish labels. Transcripts remain in the application's text area; file export and persistence are not implemented.

## Technologies Used

| Technology | Role |
| --- | --- |
| C# | Application language |
| .NET Framework 4.8 | Target runtime and framework |
| Windows Forms | Desktop interface |
| `System.Speech.Recognition` | Installed SAPI recognizer discovery, dictation grammar, and recognition events |
| NAudio 2.2.1 | Microphone enumeration and audio capture |
| `BufferedAudioStream` | Custom producer-consumer stream between NAudio and the recognition engine |
| Visual Studio solution / MSBuild | Project loading and compilation |
| NuGet `packages.config` | Existing package declaration format |

The project currently references `packages/NAudio.2.2.1/lib/net472/NAudio.dll`. NAudio 2.2.1 also depends on component packages, including `NAudio.Core` and `NAudio.WinMM`; the current project declares only the main package and assembly. See [Known Limitations](#known-limitations).

## Project Structure

Paths below are relative to this `SpeechToText/` directory. The existing `Spech to text` spelling is intentional in these paths.

```text
SpeechToText/
|-- README.md
|-- LICENSE
|-- .gitattributes
|-- .gitignore
`-- Spech to text/
    |-- Spech to text.sln
    |-- SpeechToText.csproj
    |-- packages.config
    |-- Program.cs
    |-- MainForm.cs
    |-- SpeechRecognizerService.cs
    |-- Streaming/
    |   `-- BufferedAudioStream.cs
    |-- packages/
    |-- bin/
    `-- obj/
```

| File | Responsibility |
| --- | --- |
| [Program.cs](Spech%20to%20text/Program.cs) | Application entry point and top-level exception dialogs |
| [MainForm.cs](Spech%20to%20text/MainForm.cs) | Controls, device lists, listening status, and transcript display |
| [SpeechRecognizerService.cs](Spech%20to%20text/SpeechRecognizerService.cs) | Recognizer initialization, audio input, recognition events, and disposal |
| [BufferedAudioStream.cs](Spech%20to%20text/Streaming/BufferedAudioStream.cs) | Buffered audio stream consumed by the recognition engine |
| [SpeechToText.csproj](Spech%20to%20text/SpeechToText.csproj) | .NET Framework target, compilation items, and assembly references |
| [packages.config](Spech%20to%20text/packages.config) | NAudio package declaration |

`bin/`, `obj/`, and package files are currently tracked. Existing binaries are historical artifacts and are not evidence of a successful build from the current source.

## Requirements

- Windows with a working microphone and permission for desktop applications to access it.
- Visual Studio with the **.NET desktop development** workload, or corresponding MSBuild tools for .NET Framework projects.
- The [.NET Framework 4.8 Developer Pack](https://dotnet.microsoft.com/en-us/download/dotnet-framework/net48) to compile the project. Installing only the runtime is insufficient for compilation.
- A compatible SAPI speech recognizer supporting dictation, installed for the application's process architecture.
- For Turkish input, an installed recognizer whose culture is `tr-TR`. A Turkish display language, keyboard layout, or text-to-speech voice alone does not establish compatibility.
- Complete, correctly referenced NAudio 2.2.1 dependencies. The repository's current package configuration may require correction before compilation succeeds.
- Git and NuGet package restore access when obtaining the repository and dependencies.

## Installation & Setup

1. Clone the collection into a reasonably short Windows path. The long-path option also helps with other folders in the collection:

   ```powershell
   git -c core.longpaths=true clone https://github.com/baydemirs/CSharp-Projects.git
   Set-Location CSharp-Projects
   git config core.longpaths true
   ```

2. Install the development prerequisites listed above.
3. Open [Spech to text.sln](Spech%20to%20text/Spech%20to%20text.sln) in Visual Studio.
4. Use **Restore NuGet Packages** from the solution's context menu, then inspect the project's references and build errors.
5. Check the NAudio dependency configuration before expecting a successful build. Restoring the existing `packages.config` alone is not a verified repair for its missing component declarations or assembly references. Any package repair is a separate development task.
6. Confirm that the intended recognizer appears in the recognizer list and that Windows allows microphone access.

These steps describe the setup process; they do not guarantee that the current checkout will build without dependency corrections.

## How to Run

Proceed after the dependency issues have been resolved and a fresh build succeeds.

### Visual Studio

1. Set `SpeechToText` as the startup project.
2. Select **Debug** or **Release** with the solution's **Any CPU** platform.
3. Build the solution and resolve errors before launching it.
4. Start the application with **F5** or **Ctrl+F5**.
5. Select the intended recognizer and microphone before the first listening session.
6. Use the start button to begin recognition, speak in the selected recognizer's language, and inspect the text area.
7. Use the stop button to end the session. Restart the application before changing devices or testing another session because of the lifecycle limitations below.

### MSBuild

From a Visual Studio Developer PowerShell with MSBuild available, starting at the collection root:

```powershell
Set-Location "SpeechToText\Spech to text"
msbuild ".\SpeechToText.csproj" /t:Build /p:Configuration=Release /p:Platform=AnyCPU
```

Only after that build completes successfully, launch the newly generated executable from the same directory:

```powershell
Start-Process ".\bin\Release\SpeechToText.exe"
```

Do not use the committed Debug executable to validate the current source. During review, its assembly references did not include NAudio, whereas the current source directly uses NAudio types.

## Known Limitations

- **Build validation remains incomplete.** The reviewed clean-build attempt stopped with `MSB3644` because the environment lacked .NET Framework 4.8 reference assemblies. No successful clean build or real-microphone recognition test has been established.
- **NAudio dependencies are incomplete or incorrectly configured.** The checkout contains the main package, while required component packages and references are missing. An isolated compilation check using the current NAudio reference failed to resolve `WaveInEvent` and `WaveFormat` with `CS0234`.
- **Turkish recognition is conditional.** The service uses the selected installed recognizer, otherwise prefers `tr-TR`, and otherwise falls back to the first installed recognizer. The window title does not guarantee a Turkish engine. Initialization fails when no speech recognizer is installed.
- **Device changes are not reapplied after initialization.** Preference setters update fields, but the initialized engine and microphone are reused. Restart the application before changing the selected devices.
- **Repeated start/stop is unreliable.** Stopping NAudio marks the custom stream as completed, and a subsequent start reuses it without resetting its completion state.
- **Audio shutdown can block.** A full-buffer writer does not observe completion or cancellation while waiting. An isolated stream test showed that completion did not unblock the writer. A zero-length `Read` also waited instead of returning immediately.
- **Failure cleanup is incomplete.** If recognition startup fails after microphone recording begins, recording is not explicitly rolled back. Unexpected recognition completion also does not guarantee that capture stops. Close the application after such a failure and check microphone activity.
- **Long sessions may slow the UI.** Each phrase rebuilds the complete transcript string; output has no explicit retention limit. The project has no automated test suite or structured diagnostic logging.

No recognition accuracy, latency, or reliability benchmark is available.

## Troubleshooting

| Symptom | What to check |
| --- | --- |
| `MSB3644` or missing .NET Framework 4.8 reference assemblies | Install the 4.8 Developer Pack / targeting pack; the runtime alone does not supply compilation references. |
| `CS0234` for `WaveInEvent` or `WaveFormat`, or a missing NAudio assembly | Inspect the component packages and project references, particularly `NAudio.Core` and `NAudio.WinMM`. The single existing `NAudio.dll` reference is insufficient. |
| No recognizer is listed | Verify installed, dictation-capable SAPI recognizers and process architecture. See Microsoft's [InstalledRecognizers documentation](https://learn.microsoft.com/en-us/dotnet/api/system.speech.recognition.speechrecognitionengine.installedrecognizers?view=netframework-4.8.1). |
| Turkish input is not recognized | Confirm that an actual `tr-TR` recognizer appears and is selected. A language fallback may be running. |
| No microphone is listed, or capture fails | Check the device connection, Windows desktop-app microphone permissions, the selected device, and support for 16 kHz mono capture. |
| Recognition runs but no phrases appear | Check the selected language and microphone, input level, and noise. Results below confidence `0.5` are filtered out. |
| A second session fails, or a device change has no effect | Restart the application; the current service reuses initialized devices and the completed stream. |
| Stop or close hangs, or microphone activity persists after an error | The buffering and cleanup limitations may be involved. End the application process if necessary and confirm microphone activity has stopped. |
| Git reports a filename-too-long error while cloning the collection | Use a shorter checkout path and enable Git's `core.longpaths` option as shown above. |

Consult the [NAudio 2.2.1 package dependency list](https://www.nuget.org/packages/NAudio/2.2.1) when reviewing package configuration. Avoid treating an existing executable as proof that dependency or runtime issues have been resolved.

## License

This project is licensed under the [MIT License](LICENSE).

Copyright (c) 2025 Emirhan Aydemir. Retain the copyright and license notice when copying or redistributing the project. NAudio has its own license, included with the bundled package.
