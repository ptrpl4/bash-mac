# 💻 comfy macOS

## Custom settings

docs - [https://macos-defaults.com/](https://macos-defaults.com/)

#### Fast dock

```bash
# make fast
defaults write com.apple.dock "autohide-delay" -float "0" && killall Dock
# bring back
defaults delete com.apple.dock "autohide-delay" && killall Dock
```

### gping

for debugging multiple hosts at once

```bash
brew install gping
gping 1.1.1.1 8.8.8.8 192.168.100.1 192.168.100.38
```

source - [https://t.me/zhovner\_hub/1991](https://t.me/zhovner\_hub/1991)
