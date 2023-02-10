# win-timer

![t-shirt-design-template-inspired-by-minecraft-with-an-8-bit-style-illustrated-tomato-4523e (3)](https://user-images.githubusercontent.com/28788001/217974780-26214d69-e438-4e9a-8945-921c7dda27d8.png)

A "pomodoro" designed timer to keep track of productivity. Stay focused by breaking apart your useful time.

I use Windows 10. This is designed around Windows because it uses the
winapi to pull out the Beeps. It may compile for macos and linux. I
added the #[cfg(target_os = "macos")] to only compile on certain build.
The beeps currently don't work on MacOS from my test.

```
use winapi::um:utilapiset::Beep;
// ...

unsafe {
  Beep(440, 500);
  Beep(400, 800);
  Beep(440, 500);
}
```

That's pretty much all that's dependant on windows. I think...

![image](https://user-images.githubusercontent.com/28788001/217939719-1e502ad3-d93c-41b9-adf4-1206ec96e9e7.png)

**Table of Contents**

- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
  - [Simple Mode](#simple-mode)

## Features

- Set a timer
- Simple use `win-timer 1h30m40s`, `win-timer 30m`, `win-timer 30s`, `win-timer 1h`, `win-timer 5h39m`
- q: quit early
- Bar visual lowers until 00h:00m:00s

## Installation

For now win-timer needs to be built from source.

- install [rustup.rs](https://rustup.rs)
- `git clone https://github.com/Benderjrk/win-timer.git`
- `cd win-timer`
- `cargo install --path .`

> If you decide to make code changes to customize it to your needs you'll have to re-run `cargo install --path .`

## Usage

```
win-timer 27m
```

![image](https://user-images.githubusercontent.com/28788001/217941210-eaca6e0b-9e1f-4db7-96f7-a9668e12fa92.png)

### Simple Mode

It's simple to use. It beeps 3 times at the end of the timer. It should quit if you click on `q`. At least the code is there for it.

`win-timer 50m10s`

![image](https://user-images.githubusercontent.com/28788001/217941887-95102dba-7d70-448b-a60d-4021a3cdc3c3.png)

`win-timer 2h20m`

![image](https://user-images.githubusercontent.com/28788001/217942075-98eaecf0-9fa9-4e21-b08e-aa83e06cb560.png)


### Cargo.toml

```
[package]
name = "win-timer"
version = "0.1.0"
edition = "2021"

[target.'cfg(windows)'.dependencies]
winapi = { version = "0.3", features = ["utilapiset"] }

[dependencies]
tui = "0.19.0"
crossterm = "0.25"
```
