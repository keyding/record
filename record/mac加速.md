## Mac 加速

**加速dock栏上打开应用闪两下**

- 关闭：`defaults write com.apple.dock launchanim -boolean false; killall Dock`
- 还原：`defaults write com.apple.dock launchanim -boolean true; killall Dock`

**禁用dock自动隐藏和显示动画**

- 关闭：`efaults write com.apple.dock autohide-time-modifier -float 0; killall Dock`
- 还原：`efaults write com.apple.dock autohide-time-modifier -float 0.7; killall Dock`

**关闭dock显示时的延时时间**

- 关闭：`defaults write com.apple.Dock autohide-delay -float 0; killall Dock`
- 还原：`defaults write com.apple.Dock autohide-delay; killall Dock`