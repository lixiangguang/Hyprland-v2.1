# 帮助文档和常见问题

* [hyprland 官方wiki](https://wiki.hyprland.org/)
* [该安装脚本原作者仓库](https://github.com/JaKooLit/Hyprland-v2.1)
* [gtk主题下载](https://www.xfce-look.org/browse/)
* [可以在wayland原生渲染的软件](https://arewewaylandyet.com/)

## 预设快捷键

* Super + shift + ? : 弹窗, 你可以选择后快速查看快捷键等设置文件
* Super + enter : foot 终端
* Super + d : wofi 应用选择
* Super + t : Thunar 文件管理器
* Prtsc : 区域截图, 需要点下载图标才会保存在`~/Pictures/Screenshots/`
* Super + Prtsc : 窗口截图
* Super + alt + Prtsc : 全屏截图
* Super + v : 剪切板管理器
* Super + shift + q : 杀死当前进程
* Super + b : 关闭状态栏
* Super + space : 平铺/浮动模式切换
* Super + shift + space : 窗口对调
* Super + F : 全屏
* Super + L : 锁屏
* Super + N : 上一个窗口
* Super + shift + N : 下一个窗口
------
* Super + h/j/k/l : 在窗口中移动焦点
* Super + shift + h/j/k/l : 移动窗口位置
* Super + ctrl + h/j/k/l : 调整窗口大小
------
* Super + 1/2/3 : 切换工作区
* Super + shift + 1/2/3 : 发送到工作区
* Super + ctrl + 1/2/3 : 发送到工作区并聚焦
------
* Super + shift + u : 发送到特殊工作区
* Super + u : 打开特殊工作区

## 状态栏快捷操作

*  : 鼠标左键 状态栏样式切换；右键 透明度调整；中键 布局模式切换
*  : 演讲模式(不锁屏不变暗)(实际生效不生效不清楚)
*  : 左键 检查更新, 鼠标 右键清理垃圾
*  : 左键 静态壁纸切换；右键 动态壁纸切换；中键 静态壁纸选择；
* 󰐾 : 黑暗/白天 主题切换
*  : 锁屏
*  : 电源选项


## 其他

* `hyprland` 设置目录在`~/.config/hypr/

## 没有声音

```sh
# 查看声卡信息
aplay -l
# 设置默认声卡
# 用户级别
vim ~/.asoundrc
===
defaults.pcm.card 1
defaults.pcm.device 0
defaults.ctl.card 1
===
# `pcm`选项决定用来播放音频的设备，而`ctl`选项决定哪个声卡能够由控制工具

# 系统级别
vim /etc/asound.conf

# 默认情况下，ALSA 将所有通道静音，所有这些都需要手动取消静音
alsamixer
# 显示mm是被静音的, 选中后使用按键m取消
# 还可以使用 amixer 来完成
amixer set Master unmute

# 可能还需要重启
```