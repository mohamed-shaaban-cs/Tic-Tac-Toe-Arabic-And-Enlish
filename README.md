# Tic-Tac-Toe Arabic & English

**A bilingual Windows Forms Tic-Tac-Toe game for Arabic and English players.**

[![C#](https://img.shields.io/badge/C%23-100%25-239120?logo=csharp&logoColor=white)](https://learn.microsoft.com/dotnet/csharp/)
[![.NET Framework](https://img.shields.io/badge/.NET%20Framework-4.8-512BD4?logo=dotnet&logoColor=white)](https://dotnet.microsoft.com/download/dotnet-framework/net48)
[![Windows Forms](https://img.shields.io/badge/UI-Windows%20Forms-0078D4)](https://learn.microsoft.com/dotnet/desktop/winforms/)
[![Platform](https://img.shields.io/badge/Platform-Windows-0078D4?logo=windows&logoColor=white)](https://www.microsoft.com/windows)
<a href="#license"><img src="https://img.shields.io/badge/License-MIT-yellow.svg" alt="License: MIT"></a>

## 📋 Overview

**Tic-Tac-Toe Arabic & English** is a two-player desktop implementation of the classic Tic-Tac-Toe game. It provides a Windows Forms interface, visual `X` and `O` player pieces, win and draw detection, game restart functionality, and a runtime interface-language switcher.

The application supports Arabic and English through localized .NET resources and persists the selected language in application settings. It does not include network play, database storage, or a computer opponent.

## 🏗️ Architecture & System Components

This repository uses a compact, single-tier Windows Forms architecture.

```text
┌──────────────────────────────┐
│      Windows Forms UI        │
│  Form1, Designer, .resx      │
└──────────────┬───────────────┘
               │ Event handlers
┌──────────────▼───────────────┐
│       Application Logic      │
│  Turns, board state, wins    │
│  draws, restarting, locale   │
└──────────────┬───────────────┘
               │ Resources/settings
┌──────────────▼───────────────┐
│  Images & User Settings      │
│  X/O images, strings, culture│
└──────────────────────────────┘
```

### Application Entry Point

- `Program.cs` enables Windows visual styles and launches `Form1`.
- It loads the saved language from `Properties.Settings`.
- It assigns both `CurrentUICulture` and `CurrentCulture` before opening the application.

### Presentation Layer

- `Form1.cs` contains the game events and orchestration logic.
- `Form1.Designer.cs` declares and initializes the Windows Forms controls.
- `Form1.resx`, `Form1.ar.resx`, and `Form1.en.resx` provide UI localization resources.
- `Form1_Paint` draws the horizontal and vertical board grid directly with `System.Drawing`.

### Game Logic

- `PlayerTurn` identifies whether Player 1 or Player 2 is active.
- Each board button stores `X`, `O`, or `?` in its `Tag` property.
- `CheckWinner()` tests all rows, columns, and diagonals.
- `CheckValues()` highlights matching winning cells in green-yellow.
- `PlayCount` detects a draw after nine moves.
- `RestartGame()` clears all board buttons and resets turn and result state.

### Localization & Persistence

- `Properties.Settings.Default.Language` stores `ar` or `en`.
- Changing the language updates the setting, saves it, applies the culture, and refreshes form resources.
- Arabic is the default language configured in `App.config`.

## 🛠️ Tech Stack

### Language

- C#

### Framework

- .NET Framework 4.8
- Windows Forms
- Microsoft .NET resource and settings infrastructure

### Platform Libraries

- `System.Windows.Forms`
- `System.Drawing`
- `System.Globalization`
- `System.Threading`
- `System.ComponentModel`

### Development Tools

- Visual Studio
- MSBuild
- Visual Studio Solution (`.sln`) format
- Windows desktop deployment

### Assets

- PNG images for `X`, `O`, question marks, title art, and resources
- ICO and PNG application images
- `.resx` files for localized text and UI resources

## ✨ Key Features

- 🎮 Two-player, local Tic-Tac-Toe gameplay
- ❌ Player 1 uses `X`
- ⭕ Player 2 uses `O`
- ✅ Automatic detection of all rows, columns, and diagonals
- 🟩 Green-yellow highlighting for winning cells
- 🤝 Draw detection after nine moves
- 🔄 Complete board reset and turn reset
- 🚫 Rejection of moves made on occupied cells
- 🌐 Arabic and English interface localization
- 💾 Persistence of the selected language
- 🖼️ Image-based player markers and interface artwork
- 🖥️ Native Windows Forms presentation
- 🎨 Directly drawn board grid using `System.Drawing`

## 🚀 Getting Started

### Prerequisites

- Windows
- Visual Studio 2017 or newer
- **.NET Framework 4.8 Developer Pack**
- MSBuild
- A C#/.NET desktop development workload

### Clone the Repository

```bash
git clone https://github.com/mohamed-shaaban-cs/Tic-Tac-Toe-Arabic-And-Enlish.git
cd Tic-Tac-Toe-Arabic-And-Enlish
```

### Open the Solution

Open:

```text
XO-Game-Final.sln
```

in Visual Studio.

### Build and Run

#### Visual Studio

1. Open `XO-Game-Final.sln`.
2. Select **Debug** and **Any CPU**.
3. Press **F5**, or select **Start**.
4. Visual Studio builds the solution and launches `XO-Game-Final.exe`.

#### Command Line

Run from the repository root:

```powershell
msbuild XO-Game-Final.sln /t:Build /p:Configuration=Release /p:Platform="Any CPU"
```

The executable is generated under:

```text
bin\Release\XO-Game-Final.exe
```

### Configuration

No database or external service configuration is required.

The application stores the selected language under:

```text
Properties.Settings.Default.Language
```

The default configured value is Arabic:

```xml
<setting name="Language" serializeAs="String">
    <value>ar</value>
</setting>
```

Language values used by the application are:

- `ar` — Arabic
- `en` — English

## 🎮 Usage

1. Start the application.
2. Player 1 begins the match and places an `X`.
3. Player 2 places an `O`.
4. Players alternate until a player completes three matching marks or all board positions are filled.
5. Select **Restart** to begin a new round.
6. Select **Change Language** to switch between Arabic and English.
7. Confirm or cancel the language-change prompt.
8. The new language is saved for the next application startup.

### Screenshots

#### English — Player 2 Win

![English Player 2 Win](Screenshots/en-Player2Win.png)

#### English — Draw

![English Draw](Screenshots/en-Draw.png)

#### Arabic — Player 1 Win

![Arabic Player 1 Win](Screenshots/ar-Player1Win.png)

## 👤 Author

**Mohamed Shaaban**

- GitHub: [@mohamed-shaaban-cs](https://github.com/mohamed-shaaban-cs)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
