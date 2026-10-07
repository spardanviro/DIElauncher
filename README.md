# DIE Reborn Launcher

Launcher for the **DIE Reborn** community server of *Dead Island: Epidemic*.
*Dead Island: Epidemic* 的 **DIE Reborn** 私服登陆器。

> Unofficial fan project. Not affiliated with Deep Silver, Stunlock Studios, or any rights holder.
> 非官方爱好者项目，与 Deep Silver、Stunlock Studios 及任何权利方无关。

## How to use

1. Install *Dead Island: Epidemic* in Steam.
2. Download `DIE-Launcher.exe` from the [latest release](https://github.com/spardanviro/DIElauncher/releases/latest).
3. Run it. It finds the game folder, installs or updates the client patch, shows whether the server is up and how many players are online, and starts the game through Steam.

The launcher switches between English and Chinese (bottom right). Windows 10 / 11, no extra runtime needed.

## 使用方法

1. 在 Steam 里安装 *Dead Island: Epidemic*。
2. 在[最新发布](https://github.com/spardanviro/DIElauncher/releases/latest)里下载 `DIE-Launcher.exe`。
3. 运行它。它会自己找到游戏目录，安装或更新客户端补丁，显示服务器是否开服和在线人数，并通过 Steam 启动游戏。

登陆器右下角可以切换中文 / English。支持 Windows 10 / 11，不需要另装运行库。

## What the patch changes / 补丁改了什么

`DIE-ClientPatch.zip` is unpacked into the game folder: the BepInEx loader, one plugin, and an `ip.cfg` that points the game at the community server. The original `ip.cfg` is kept as `ip.cfg.orig`. **Uninstall patch** in the launcher removes exactly these files and restores the original.

`DIE-ClientPatch.zip` 解压到游戏目录：BepInEx 加载器、一个插件，以及指向私服的 `ip.cfg`。原版 `ip.cfg` 备份为 `ip.cfg.orig`。登陆器里的**卸载补丁**只删这些文件并还原原版。
