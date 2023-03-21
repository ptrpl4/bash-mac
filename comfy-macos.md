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
