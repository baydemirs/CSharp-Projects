# CSharp-Projects

## About

A collection of C# desktop applications, games, API examples, and programming exercises. Each folder has its own source, project configuration, and dependencies.

The catalog covers **17 top-level project folders**, containing **26 `.csproj` files** and **16 `.sln` files**. These are separate counts: some applications have multiple projects, and the exercise folder contains five standalone console projects.

Descriptions and technologies below are based on the tracked source and project files. They describe implemented examples and declared dependencies; they do not establish build success, runtime reliability, or production readiness.

## Project Catalog

### Games

| Project | Description | Verified technologies | Start here |
| --- | --- | --- | --- |
| [Hangman](Adam_Asmaca1/) | Word-guessing game with letter and full-word guesses, drawn hangman stages, and earned hints. | C#, .NET Framework 4.8, Windows Forms, System.Drawing | [Solution](Adam_Asmaca1/AdamAsmacaOyunu/AdamAsmacaOyunu.sln) |
| [Flappy Bird](FlappyBird2/) | Keyboard-controlled bird game with a timer loop, moving pipes, collision checks, and scoring. | C#, .NET Framework 4.8, Windows Forms | [Solution](FlappyBird2/FlappyBird-main/FlappyBird/FlappyBirdGame/FlappyBirdGame.sln) |
| [Minesweeper](MayinTarlasi/) | Button-grid game with configurable mine count, random placement, and adjacent-cell reveal logic. | C#, .NET Framework 4.8, Windows Forms | [Solution](MayinTarlasi/MayinTarlasi/MayinTarlasi.sln) |
| [Top-Down Car Racing](top-down-car-speed/) | Lane-based racing game with steering, scrolling traffic, collision checks, and score-based speed changes. | C#, .NET Framework 4.8, Windows Forms, System.Media | [Solution](top-down-car-speed/top-down-car-speed/Car%20Racing%20Game%20MOO%20ICT.sln) |
| [Tic-Tac-Toe](xoxgame/) | Local two-player board game with alternating turns and win/draw checks. | C#, .NET Framework 4.8, Windows Forms | [Solution](xoxgame/xoxgame.sln) |

### Desktop Utilities and Productivity

| Project | Description | Verified technologies | Start here |
| --- | --- | --- | --- |
| [Keyboard Utilities](KeyLogger/) | Hotkey management, typing practice/statistics, key-display overlay, and text-snippet expansion; stored in the historical `KeyLogger` folder. | C#, .NET 8, Windows Forms, Win32 P/Invoke, System.Text.Json | [Solution](KeyLogger/KeyboardUtils.sln) / [README](KeyLogger/README.md) |
| [Notebook](NotebookApp-master/) | Desktop note listing, addition, editing, and deletion with a demonstration login and an in-memory data store. | C#, .NET 6, Windows Forms, `List<T>` | [Solution](NotebookApp-master/NotebookApp-master/NotebookApp.sln) |

### Speech and Language

| Project | Description | Verified technologies | Start here |
| --- | --- | --- | --- |
| [SpeechToText](SpeechToText/) | Microphone-to-text example with recognizer/device selection. Turkish input requires a compatible installed recognizer; build and microphone validation remain incomplete. | C#, .NET Framework 4.8, Windows Forms, System.Speech.Recognition, NAudio 2.2.1 | [README](SpeechToText/README.md) / [Solution](SpeechToText/Spech%20to%20text/Spech%20to%20text.sln) |
| [Text to Speech](TextToSpeechApplication-master/) | Speaks entered text asynchronously and exposes pause/resume controls through the installed speech-synthesis engine. | C#, .NET Framework 4.7.2, Windows Forms, System.Speech.Synthesis | [Solution](TextToSpeechApplication-master/TextToSpeechApplication-master/TextToSpeechApplication.sln) |
| [Multi-Language Translator](%C3%87oklu%20dil%20%C3%A7evirisi/) | Translation UI with Turkish/English interface switching and a local dictionary-based mock translation engine. | C#, .NET 8, Windows Forms, dictionaries | [Project](%C3%87oklu%20dil%20%C3%A7evirisi/MultiLanguageTranslator/MultiLanguageTranslator.csproj) / [README](%C3%87oklu%20dil%20%C3%A7evirisi/MultiLanguageTranslator/README.md) |

### AI and Computer Vision

| Project | Description | Verified technologies | Start here |
| --- | --- | --- | --- |
| [LLM Chatbot](LLMChatbot.WinForms/) | Conversation UI with an HTTP client for the OpenAI Responses API; reads its API key from `OPENAI_API_KEY`. | C#, .NET 8, Windows Forms, HttpClient, System.Text.Json | [Project](LLMChatbot.WinForms/LLMChatbot.WinForms.csproj) / [README](LLMChatbot.WinForms/README.md) |
| [YOLO Image Detection](ML%20Math%20Image%20Prossess/) | Loads images, runs YOLOv8-style ONNX inference, draws detection boxes, and saves annotated images; requires an external `yolov8n.onnx` model. | C#, .NET 8, Windows Forms, ONNX Runtime 1.16.3, ImageSharp 3.1.7, ImageSharp.Drawing 2.1.5 | [Solution](ML%20Math%20Image%20Prossess/YoloWinForms.sln) / [README](ML%20Math%20Image%20Prossess/README.md) |
| [FaceApp](open%20cv/) | Camera face capture, training, and recognition example using Haar detection and LBPH; source also includes EigenFace support. | C#, .NET 8, Windows Forms, Emgu CV 4.9.0.5092, OpenCV | [Project](open%20cv/open%20cv/FaceApp/FaceApp.csproj) / [README](open%20cv/open%20cv/FaceApp/README.md) |

### Web APIs and Networking

| Project | Description | Verified technologies | Start here |
| --- | --- | --- | --- |
| [BookVerse API Example](BookVerse.AntiSolidApi/) | ASP.NET Core template with order-processing example classes. The current startup maps the weather endpoint; order controllers are not registered or mapped, and payment/email steps are console placeholders. | C#, .NET 9, ASP.NET Core, Microsoft.AspNetCore.OpenApi 9.0.9 | [Project](BookVerse.AntiSolidApi/BookVerse.AntiSolidApi/BookVerse.AntiSolidApi.csproj) / [README](BookVerse.AntiSolidApi/README.md) |
| [TCP Desktop Chat Example](Chat-Desktop1/) | Separate client and server UIs for TCP messaging. The server logs incoming lines; message broadcasting is not implemented. | C#, .NET Framework 4.7.2, Windows Forms, System.Net.Sockets, DevExpress 21.2 (server) | [Client](Chat-Desktop1/ChatClient/ChatClient.csproj) / [Server](Chat-Desktop1/ChatServer/Chat-Desktop1.csproj) / [README](Chat-Desktop1/README.md) |

### Security Learning

| Project | Description | Verified technologies | Start here |
| --- | --- | --- | --- |
| [VirusAntivirus](VirusAntivirus/) | Educational file/folder scanner with SHA-256 signature matching, heuristic scoring, JSON reports, and manual quarantine. | C#, .NET 8, Windows Forms, System.Security.Cryptography, System.Text.Json | [Solution](VirusAntivirus/VirusAntivirus.sln) / [README](VirusAntivirus/README.md) |

### Programming Exercises

[Exercise collection](%C3%87al%C4%B1%C5%9Fma%20Sorular%C4%B1/) contains five independent console projects. The scenarios below are simulations demonstrating C# concepts.

| Exercise | Description | Verified technologies | Start here |
| --- | --- | --- | --- |
| [Station Data Filtering](%C3%87al%C4%B1%C5%9Fma%20Sorular%C4%B1/1.%20%20%20%20Kuzey%20G%C3%B6zlem%20%C4%B0stasyonu%20%E2%80%93%20Buzun%20ve%20Belle%C4%9Fin%20%C4%B0nce%20%C3%87izgisi/) | Filtering invalid floating-point values and cold readings with extension methods and LINQ. | C#, .NET Framework 4.7.2, LINQ | [Solution](%C3%87al%C4%B1%C5%9Fma%20Sorular%C4%B1/1.%20%20%20%20Kuzey%20G%C3%B6zlem%20%C4%B0stasyonu%20%E2%80%93%20Buzun%20ve%20Belle%C4%9Fin%20%C4%B0nce%20%C3%87izgisi/1.%20Kuzey%20G%C3%B6zlem%20%C4%B0stasyonu%20%E2%80%93%20Buzun%20ve%20Belle%C4%9Fin%20%C4%B0nce%20%C3%87izgisi.sln) |
| [Generic Grid Buffer](%C3%87al%C4%B1%C5%9Fma%20Sorular%C4%B1/2%E2%80%83%20Deprem%20Erken-Uyar%C4%B1%20A%C4%9F%C4%B1%20%E2%80%93%20Dinamik%20%C3%87ok-Boyutlu%20Haf%C4%B1za%20Tetrisi/) | Resize a two-dimensional generic grid while preserving overlapping data, then apply rectangular patches. | C#, .NET Framework 4.7.2, generics, multidimensional arrays | [Solution](%C3%87al%C4%B1%C5%9Fma%20Sorular%C4%B1/2%E2%80%83%20Deprem%20Erken-Uyar%C4%B1%20A%C4%9F%C4%B1%20%E2%80%93%20Dinamik%20%C3%87ok-Boyutlu%20Haf%C4%B1za%20Tetrisi/2%E2%80%83Deprem%20Erken-Uyar%C4%B1%20A%C4%9F%C4%B1%20%E2%80%93%20Dinamik%20%C3%87ok-Boyutlu%20Haf%C4%B1za%20Tetrisi.sln) |
| [Big-Endian Sensor Packets](%C3%87al%C4%B1%C5%9Fma%20Sorular%C4%B1/3.%E2%80%83Byte-%C5%9Eelalesi%20Sens%C3%B6r%C3%BC%20%E2%80%93%20Endian%20Sava%C5%9Flar%C4%B1%20ve%20Ani%20Sel/) | Decode 16-bit big-endian values and demonstrate packet creation and parsing with simulated sensor readings. | C#, .NET 8, BitConverter | [Solution](%C3%87al%C4%B1%C5%9Fma%20Sorular%C4%B1/3.%E2%80%83Byte-%C5%9Eelalesi%20Sens%C3%B6r%C3%BC%20%E2%80%93%20Endian%20Sava%C5%9Flar%C4%B1%20ve%20Ani%20Sel/3.%E2%80%83Byte-%C5%9Eelalesi%20Sens%C3%B6r%C3%BC%20%E2%80%93%20Endian%20Sava%C5%9Flar%C4%B1%20ve%20Ani%20Sel.sln) |
| [Async Order Processing](%C3%87al%C4%B1%C5%9Fma%20Sorular%C4%B1/4.%E2%80%83G%C3%B6rev%20Kuyru%C4%9Fu%20Sunucusu%20%E2%80%93%20%E2%80%9CAsync%20void%E2%80%9Din%20Sessiz%20%C3%87%C4%B1%C4%9Fl%C4%B1%C4%9F%C4%B1/) | Simulate concurrent order handling with linked cancellation, timeouts, exception logging, and an atomic counter. | C#, .NET 8, Task, CancellationTokenSource, Interlocked | [Solution](%C3%87al%C4%B1%C5%9Fma%20Sorular%C4%B1/4.%E2%80%83G%C3%B6rev%20Kuyru%C4%9Fu%20Sunucusu%20%E2%80%93%20%E2%80%9CAsync%20void%E2%80%9Din%20Sessiz%20%C3%87%C4%B1%C4%9Fl%C4%B1%C4%9F%C4%B1/4.%E2%80%83G%C3%B6rev%20Kuyru%C4%9Fu%20Sunucusu%20%E2%80%93%20%E2%80%9CAsync%20void%E2%80%9Din%20Sessiz%20%C3%87%C4%B1%C4%9Fl%C4%B1%C4%9F%C4%B1.sln) |
| [Turkish Cart Calculations](%C3%87al%C4%B1%C5%9Fma%20Sorular%C4%B1/5.%E2%80%83%C3%87evrim-%C4%B0%C3%A7i%20Sepet%20%E2%80%93%20T%C3%BCrk%C3%A7e%20Y%C3%BCzdeler%2C%20Canl%C4%B1%20Koleksiyon%20ve%20%E2%80%9C%C3%9Ccretsiz%20Kargo%E2%80%9D/) | Recalculate cart totals on collection changes, parse Turkish percentages, and emit shipping-status events. | C#, .NET 8, ObservableCollection, CultureInfo, LINQ | [Solution](%C3%87al%C4%B1%C5%9Fma%20Sorular%C4%B1/5.%E2%80%83%C3%87evrim-%C4%B0%C3%A7i%20Sepet%20%E2%80%93%20T%C3%BCrk%C3%A7e%20Y%C3%BCzdeler%2C%20Canl%C4%B1%20Koleksiyon%20ve%20%E2%80%9C%C3%9Ccretsiz%20Kargo%E2%80%9D/5.%E2%80%83%C3%87evrim-%C4%B0%C3%A7i%20Sepet%20%E2%80%93%20T%C3%BCrk%C3%A7e%20Y%C3%BCzdeler%2C%20Canl%C4%B1%20Koleksiyon%20ve%20%E2%80%9C%C3%9Ccretsiz%20Kargo%E2%80%9D.sln) |

## Technologies

| Area | Technologies present in source or project configuration |
| --- | --- |
| Language and runtimes | C#; .NET Framework 4.7.2 and 4.8; .NET 6, 8, and 9 |
| Desktop UI | Windows Forms, System.Drawing; DevExpress 21.2 references in the TCP server |
| Web and networking | ASP.NET Core, OpenAPI, HttpClient, TCP sockets; OpenAI Responses API integration in the chatbot |
| Speech | System.Speech recognition/synthesis; NAudio 2.2.1 |
| Computer vision | Emgu CV / OpenCV, ONNX Runtime, ImageSharp and ImageSharp.Drawing |
| Data and platform APIs | System.Text.Json, LINQ, collections, async/await, cancellation, cryptographic hashing, Win32 P/Invoke |
| Build tooling | Visual Studio solutions, MSBuild, SDK-style and legacy `.csproj` formats, NuGet |

There is no shared runtime version or repository-wide startup project. Follow the target framework and dependencies of the project you select.

## Getting Started

1. Clone into a reasonably short Windows path. Enable Git long-path support because some tracked folders have long names:

   ```powershell
   git -c core.longpaths=true clone https://github.com/baydemirs/CSharp-Projects.git
   Set-Location CSharp-Projects
   git config core.longpaths true
   ```

2. Choose a project from the catalog and read its own README when available.
3. Use Windows and the .NET desktop development tools for Windows Forms applications. Match the selected project's declared target: legacy projects require the appropriate .NET Framework Developer/Targeting Pack; SDK-style projects require an SDK that supports their target framework.
4. Open the linked `.sln` in Visual Studio. Where a solution is absent, open the linked `.csproj` directly. Multi-project applications should be opened through their solution where one is provided.
5. Restore dependencies, inspect build errors, and build the selected project before launching it. DevExpress references, camera/microphone access, installed speech engines, and external model files require project-specific setup.

For SDK-style examples, `dotnet build` and `dotnet run --project` can be used with the selected `.csproj` path and suitable tooling. Legacy .NET Framework projects should use Visual Studio/MSBuild. These instructions describe the development workflow; successful builds across the collection have not been established.

## Notes

- This repository contains independent learning projects and prototypes. Catalog entries summarize source behavior; no repository-wide build, automated-test, hardware-test, or performance success is claimed.
- The five exercise scenarios use local simulations. Their storylines do not represent deployed sensor networks, queue services, or commerce integrations.
- The translator uses a mock dictionary engine. The BookVerse order example uses console placeholders and is not wired into the current HTTP startup. The TCP server does not broadcast received messages.
- SpeechToText has documented dependency and audio lifecycle limitations. Its [project README](SpeechToText/README.md) remains the detailed setup and validation reference.
- YOLO Image Detection expects an external `yolov8n.onnx` file, which is not tracked. FaceApp has separate cascade, face-data, and model requirements described in its own README.
- Keyboard Utilities uses global keyboard hooks and hotkeys. VirusAntivirus is a learning scanner; its quarantine implementation moves files, so use disposable test copies when exploring that function.
- Some folders contain committed `bin/`, `obj/`, `.vs/`, package files, or historical executables. Their presence does not prove that the current source builds or runs correctly.
- Existing folder names and nested paths are retained. Check each project's license and bundled dependency licenses before reuse or redistribution.
