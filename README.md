# StomMinigameTemplate

A simple template for creating new minigames using the **StomArcade** minigame framework.
This project provides a minimal implementation that can be duplicated and modified to quickly build new minigames.

---

## Overview

The template includes:

* A base minigame implementation (`MyMinigame`)
* Default game state pipeline (Lobby → In-Game → Ending)
* Minimal configuration for automatic minigame loading
* Gradle project setup ready for development

---

## Getting Started

### 1. Clone or Copy the Template

Duplicate this template repository and rename the project to match your minigame.

Update:

* `rootProject.name` in `settings.gradle`
* Package names (recommended)
* Minigame ID inside the constructor

```
public MyMinigame() {
    super("myminigame", GameState.DEFAULTS);
}
```

---

### 2. Configure the Loader File

Ensure your loader JSON points to your main class:

```
{
  "main": "net.bitbylogic.stomarcade.minigame.template.MyMinigame"
}
```

---

### 3. Implement Game Logic

Override lifecycle methods inside your minigame:

```
@Override
public void onLoad() {
    // Called when the minigame is loaded
}

@Override
public void onStart() {
    // Called when the match begins
}

@Override
public void onEnd() {
    // Called when the match ends
}
```

---

## Default Game States

The template uses the built-in default state sequence:

* **LobbyState** – 30 seconds
* **InGameState** – 20 minutes
* **EndingState** – 5 seconds

Defined via:

```
GameState.DEFAULTS
```

You may provide your own state list if your minigame requires a custom flow.

---

## Project Structure

```
StomMinigameTemplate
├─ src/main/java
│  └─ net/bitbylogic/stomarcade/minigame/template
│     └─ MyMinigame.java
├─ src/main/resources
│  └─ minigame.json
└─ settings.gradle
```

---

## Creating a New Minigame (Recommended Workflow)

1. Copy the template
2. Rename `MyMinigame` to your game name
3. Change the minigame ID
4. Implement gameplay logic in lifecycle methods
5. Add event nodes, tasks, and utilities as needed

---

## Notes

* The minigame ID must be **unique** within the arcade environment.
* Avoid heavy initialization inside constructors — use `onLoad()` instead.
* State transitions and ticking are handled automatically by the framework.
