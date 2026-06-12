## Editor Note

All credit to [github.com.](https://github.com/lrusso). I only changed the controls and added a speed up button (TAB).

# Super Nintendo

A Super Nintendo emulator with mobile compatibility designed for running in pure JavaScript pre-ECMAScript 2015 (no WebAssembly). Simply open the link below, click the red icon, and select a ROM file in `SFC` or `SMC` format from your computer; it will be loaded and booted automatically.

## Links:

- [Super Nintendo emulator](https://lrusso.github.io/SuperNintendo/SuperNintendo.htm)
- [Demo booting a sample game](https://lrusso.github.io/SuperNintendo/SuperNintendo.htm?demo)

## Screenshots:

![alt screenshot1](https://lrusso.github.io/SuperNintendo/SCREENSHOT1.jpg)

![alt screenshot2](https://lrusso.github.io/SuperNintendo/SCREENSHOT2.jpg)

![alt screenshot3](https://lrusso.github.io/SuperNintendo/SCREENSHOT3.jpg)

![alt screenshot4](https://lrusso.github.io/SuperNintendo/SCREENSHOT4.jpg)

## How to use it:

Examples of loading local and online files can be found [here](https://github.com/lrusso/SuperNintendo/blob/main/SuperNintendo.htm#L141-L193) and [here](https://github.com/lrusso/SuperNintendo/blob/main/SuperNintendo.htm#L221-L268).

```js
embedSuperNintendo({
  container: "game",
  name: gameURL,
  rom: xhr.response,
  soundEnabled: true,
  showMobileControls: isMobileDevice(),
  backText: "BACK",
  soundText: "SOUND",
  loadText: "LOAD",
  saveText: "SAVE",
  player1: {
    up: "KeyW",
    down: "KeyS",
    left: "KeyA",
    right: "KeyD",
    a: "KeyK",
    b: "KeyJ",
    x: "KeyL",
    y: "KeyU",
    l: "KeyI",
    r: "KeyO",
    start: "Space",
    select: "ShiftLeft",
  },
  player2: {
    up: "ArrowUp",
    down: "ArrowDown",
    left: "ArrowLeft",
    right: "ArrowRight",
    a: "KeyG",
    b: "KeyF",
    x: "KeyH",
    y: "KeyR",
    l: "KeyT",
    r: "KeyY",
    start: "Enter",
    select: "ShiftRight",
  },
  cbStarted: function cbStarted() {
    pleaseWait.style.display = "none"
  },
  })
```

| Parameter          |    Type     | Required | Default value | Description                |
| :----------------- | :---------: | :------: | :-----------: | :------------------------- |
| container          |   string    |   yes    |       –       | Target element ID.         |
| name               |   string    |   yes    |       –       | Game name.                 |
| rom                | ArrayBuffer |   yes    |       –       | ROM file.                  |
| soundEnabled       |   boolean   |    no    |     true      | Initial sound state.       |
| showMobileControls |   boolean   |    no    |     false     | Show mobile controls.      |
| backText           |   string    |    no    |     BACK      | Text for the Back button.  |
| soundText          |   string    |    no    |     SOUND     | Text for the Sound button. |
| loadText           |   string    |    no    |     LOAD      | Text for the Load button.  |
| saveText           |   string    |    no    |     SAVE      | Text for the Save button.  |
| player1            |   object    |    no    |       –       | Player 1 keys.             |
| player2            |   object    |    no    |       –       | Player 2 keys.             |
| cbStarted          |  function   |    no    |       -       | Called on emulator start.  |

## Special keys:

| Action          | macOS Shortcut | Windows Shortcut | Safari Shortcut |
| :-------------- | :------------: | :--------------: | :-------------: |
| Save state      |  Command + S   |     Ctrl + S     |    Ctrl + S     |
| Load state      |  Command + Q   |     Ctrl + Q     |    Ctrl + 2Q    |
| Toggle sound    |  Command + P   |     Ctrl + p     |    Ctrl + P
|
| Fullscreen mode |  Command + F   |     Ctrl + F     |    Ctrl + F     |
| Reset game      |  Command + R   |     Ctrl + R     |    Ctrl + R     |

## Author's note:

This emulator is compatible with both Android and iOS devices. However, WebKit on iOS has historically lagged behind; for instance, it took nearly a decade for Apple to allow developers to set a custom download filename for an `a` tag. This feature was implemented recently on iOS, so you can now download the game state. Another three iOS quirks: 1) if a slow connection causes the script to take several seconds to load, WebKit may fail to initialize the AudioContext; 2) if you send Safari to the background and return to it, there will be no audio; 3) if you click on the file selector and it takes you several seconds to choose a ROM file, there will be no audio. In any case, a manual tap on the screen is required to enable or re-enable the audio.

## Main differences with the original project:

- Transpiled JS to pre-ES2015 via `node ConverterES5.js SuperNintendo.js`.

## This is a modified version of snes9x2005-wasm:

https://github.com/lrusso/snes9x2005-wasm

**NOTE:** Emscripten 4.0.23 was used to build the emulator.

## Virtual joystick code:

https://github.com/lrusso/VirtualJoystick
