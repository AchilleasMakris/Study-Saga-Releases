<div align="center">
  <a href="https://www.study-saga.com/">
    <img src="screenshots/icon.png" width="120" alt="Study Saga" />
  </a>
  <h1 align="center">
    <img src="https://readme-typing-svg.herokuapp.com/?font=Righteous&pause=2000&size=35&color=F76B92&center=true&vCenter=true&width=500&height=70&duration=2000&lines=Study+Saga;" />
</h1>
  <p><strong>Lofi Pomodoro timer with focus music and a bit of an RPG to it.</strong></p>
  <p>
    <a href="https://github.com/AchilleasMakris/Study-Saga-Releases/releases/latest"><img src="https://img.shields.io/github/v/release/AchilleasMakris/Study-Saga-Releases?style=flat-square&color=1a1a2e" alt="Latest release" /></a>
    <a href="https://github.com/AchilleasMakris/Study-Saga-Releases/releases"><img src="https://img.shields.io/github/downloads/AchilleasMakris/Study-Saga-Releases/total?style=flat-square&color=1a1a2e&label=downloads" alt="Downloads" /></a>
    <a href="https://github.com/AchilleasMakris/Study-Saga-Releases/blob/main/LICENSE"><img src="https://img.shields.io/github/license/AchilleasMakris/Study-Saga-Releases?style=flat-square&color=1a1a2e" alt="MIT License" /></a>
    <a href="https://www.study-saga.com/"><img src="https://img.shields.io/badge/web%20app-study--saga.com-1a1a2e?style=flat-square&logo=googlechrome&logoColor=white" alt="Open the web app" /></a>
    <br/>
    <img src="https://img.shields.io/badge/macOS-1a1a2e?style=flat-square&logo=apple&logoColor=white" alt="macOS" />
    <img src="https://img.shields.io/badge/Windows-1a1a2e?style=flat-square&logo=windows&logoColor=white" alt="Windows" />
    <img src="https://img.shields.io/badge/Linux-1a1a2e?style=flat-square&logo=linux&logoColor=white" alt="Linux" />
  </p>
</div>

Study Saga is a free lofi Pomodoro timer with synthwave music, ambient sounds, and a bit of RPG-style gamification to keep you coming back. This repo holds the desktop builds for macOS, Windows, and Linux. They run the same thing as the website, just in their own window so it isn't buried in a browser tab, and they're built with [Pake](https://github.com/tw93/Pake) (a small Tauri/Rust wrapper).

Don't want to install anything? The [web app](https://www.study-saga.com/) is always there and always up to date.

<!-- PLACEHOLDER: replace with a wide hero screenshot of the app (recommended ~1280x720). Save it as screenshots/hero.png and swap the src below. -->
<p align="center">
  <img src="/screenshots/demo.webp" width="720" alt="Study Saga" />
</p>

## Download

**[Get the latest release →](https://github.com/AchilleasMakris/Study-Saga-Releases/releases/latest)**

Pick the file that matches your system from the release assets:

| Platform | File | Notes |
|----------|------|-------|
| macOS | `.dmg` | Universal — runs on Apple Silicon and Intel |
| Windows | `.msi` | x64 |
| Linux | `.AppImage` | Portable, runs without installing |
| Linux | `.deb` | For Debian / Ubuntu |

On macOS grab the `.dmg`, on Windows the `.msi`. On Linux, the `.AppImage` runs without installing anything; use the `.deb` if you'd rather install it properly on Debian or Ubuntu. Filenames include the version, so just take whichever matches your platform from the [releases page](https://github.com/AchilleasMakris/Study-Saga-Releases/releases).

## Installing

### macOS

Open the `.dmg` and drag Study Saga into your Applications folder. The build is signed, so it opens normally. Needs macOS 10.15 (Catalina) or later.

### Windows

Run the `.msi` and follow the installer, then launch Study Saga from the Start menu. SmartScreen may warn you the first time — see [First launch](#first-launch). Needs Windows 10 or later. The app uses Microsoft Edge WebView2, which ships with current Windows; if it's missing, the installer pulls it in.

To remove it: **Settings → Apps → Installed apps → Study Saga → Uninstall**.

### Linux

**AppImage** (portable, no root):

```bash
chmod +x ./study-saga_*_amd64.AppImage #(Replace with version name)
./study-saga_*_amd64.AppImage
```

**Debian / Ubuntu** (`.deb`) — installs dependencies for you:

```bash
sudo apt install ./study-saga_*_amd64.deb #(Replace with version name)
```

Or with `dpkg`, then pull in anything missing:

```bash
sudo dpkg -i ./study-saga_*_amd64.deb #(Replace with version name)
sudo apt-get install -f
```

Built for x86_64. The app needs WebKitGTK 4.1 and GTK3 at runtime; installing the `.deb` with `apt` pulls those in. On other distros, see the Linux notes under [First launch](#first-launch).

## First launch

The macOS build is code-signed, so it just opens. The Windows and Linux builds aren't signed yet, so those systems may warn you the first time — it's the same code that runs at [study-saga.com](https://www.study-saga.com/). Here's how to get past each warning.

<details>
<summary><b>Windows — "Windows protected your PC"</b></summary>

Click **More info**, then **Run anyway**. SmartScreen shows this for any app it hasn't seen before.

If there's no **Run anyway** button (some managed machines hide it), right-click the `.msi` → **Properties**, tick **Unblock** at the bottom, click **OK**, then run it.

</details>

<details>
<summary><b>Linux — AppImage won't start</b></summary>

Usually a missing FUSE 2 library:

```bash
# Debian / Ubuntu
sudo apt install libfuse2        # or libfuse2t64 on Ubuntu 24.04+
# Fedora
sudo dnf install fuse fuse-libs
# Arch
sudo pacman -S fuse2
```

If you'd rather not install FUSE, run it extracted:

```bash
./study-saga_*_amd64.AppImage --appimage-extract-and-run
```

</details>

<details>
<summary><b>Linux — blank window or instant exit</b></summary>

That's a missing WebKitGTK 4.1 runtime:

```bash
# Debian / Ubuntu
sudo apt install libwebkit2gtk-4.1-0 libgtk-3-0
# Fedora
sudo dnf install webkit2gtk4.1
# Arch
sudo pacman -S webkit2gtk-4.1
```

If your distro only ships WebKitGTK 4.0, use the AppImage, which targets the Ubuntu 22.04 / Debian 12 baseline.

</details>

## What's in it

- Pomodoro timer with adjustable focus and break lengths
- Lofi and synthwave stations plus ambient sounds (rain, wind, and more)
- Tomatoes, XP, levels, and a character that grows as you study
- Study rooms and chat to focus alongside other people
- Stats and streaks to see your focus time over the weeks

## Worth knowing

- Windows and Linux builds aren't signed yet (see [First launch](#first-launch)); the macOS build is signed.
- There's no auto-update — when a new version lands, come back here and download it. The web app updates itself.
- You'll need an internet connection; the app loads the live site.

## Links

- Web app: https://www.study-saga.com/
- Releases: https://github.com/AchilleasMakris/Study-Saga-Releases/releases
- Report a bug or request a feature: [open an issue](https://github.com/AchilleasMakris/Study-Saga-Releases/issues)
- Built with [Pake](https://github.com/tw93/Pake)
- License: [MIT](LICENSE)

<div align="center">
  <sub>Made by Achilleas Makris · <a href="https://www.study-saga.com/">https://study-saga.com</a></sub>
</div>
