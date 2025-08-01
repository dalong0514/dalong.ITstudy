### 文档

[Getting Started with Gazebo? — Gazebo ionic documentation](https://gazebosim.org/docs/all/getstarted/)

### 安装

2025-07-23

最终的解决方案还是通过 parallels 安装了 Ubuntu 24.04 (with Rosetta) 操作系统，在该操作系统上安装的。




如果你希望避免任何架构问题，则可在 Apple Silicon Mac 上安装 x86 Ubuntu VM（推荐 VMware Fusion 免费版或 UTM），然后在 VM 里安装 ROS 2 + Gazebo。Reddit 用户指出：

“使用 VMware Fusion 的 3D 加速在 Apple Silicon 上 Gazebo 表现良好” 
Reddit
。

这种方式虽然需要额外配置虚拟机，但兼容性最高，开发体验也稳定。

[Alternatives to Gazebo : r/ROS](https://www.reddit.com/r/ROS/comments/1id12qn/alternatives_to_gazebo/?utm_source=chatgpt.com)




01 先安装 RoboStack（没走通，虽然 RoboStack 可以用但跑步起来 gazebo）

[Getting Started - RoboStack](https://robostack.github.io/GettingStarted.html#__tabbed_1_2)

用 conda 安装失败了，换用 micromamba 安装成功的。

brew install micromamba

初始化 shell 环境，以便正确激活和管理虚拟环境：

$HOMEBREW_PREFIX/opt/micromamba/bin/mamba shell init --shell <your-shell> --root-prefix ~/mamba

$HOMEBREW_PREFIX/opt/micromamba/bin/mamba shell init --shell zsh --root-prefix ~/mamba

例如 bash 或 zsh 。

micromamba --version


Installing ros

\# Create a ros-humble desktop environment
micromamba create -n ros_env -c conda-forge -c robostack-humble ros-humble-desktop

\# Activate the environment
micromamba activate ros_env


```
micromamba activate ros_env

'micromamba' is running as a subprocess and can't modify the parent shell.
Thus you must initialize your shell before using activate and deactivate.

To initialize the current zsh shell, run:
    $ eval "$(micromamba shell hook --shell zsh)"
and then activate or deactivate with:
    $ micromamba activate
To automatically initialize all future (zsh) shells, run:
    $ micromamba shell init --shell zsh --root-prefix=~/.local/share/mamba
If your shell was already initialized, reinitialize your shell with:
    $ micromamba shell reinit --shell zsh
Otherwise, this may be an issue. In the meantime you can run commands. See:
    $ micromamba run --help

先用 eval "$(micromamba shell hook --shell zsh)" 初始化然后再激活虚拟环境。

```



Installing tools for local development

micromamba install -c conda-forge compilers cmake pkg-config make ninja colcon-common-extensions catkin_tools rosdep




mkdir -p /Users/Daglas/dalong.eai/gazebo_ros_ws/src
cd /Users/Daglas/dalong.eai/gazebo_ros_ws

pip install -U vcstool






换用 pixi 安装，但最后没走通，虽然 RoboStack 可以用但跑步起来 gazebo。

1、先安装 pixi。

curl -fsSL https://pixi.sh/install.sh | bash

2、安装 RoboStack。

pixi init robostack
cd robostack

修改文件 pixi.toml 后的内容，然后安装：

pixi install

3、启动环境。

You can now start an environment with your desired robostack distribution using one of the below commands (either executed from within the project directory or by appending `--manifest-path` and pointing to your project directory):

\# ROS noetic
pixi shell -e noetic

\# ROS humble
pixi shell -e humble

\# ROS jazzy
pixi shell -e jazzy

\# ROS kilted
pixi shell -e kilted

安装后返回的信息：
```
WARN Skipped running the post-link scripts because `run-post-link-scripts` = `false`
	- bin/.librsvg-pre-unlink.sh

To enable them, run:
	pixi config set --local run-post-link-scripts insecure

More info:
	https://pixi.sh/latest/reference/pixi_configuration/#run-post-link-scripts

 WARN Could not find activation scripts: /Users/Daglas/dalong.eai/robostack/install/setup.bash
```

4、测试安装是否成功。

After installation, you should test if you are able to run rviz/rviz2 and other ROS tools.

以测试 ROS2 为例。

cd robostack
pixi run -e humble rviz2 # OR jazzy, kilted

Updating all packages in your environment is as easy as:

cd robostack
pixi update

You can just exit the current shell to deactivate the current environment.

exit  # or press Ctrl+D


### 问题记录

2025-07-22

1、卡在最后一步安装不上 ogre1.9。







### 其他


SDF is used to specify the contents of simulation. Take a look at the available SDF tutorials to get started.

SDF 用于定义模拟环境的具体内容。想要入门，你可以先查阅一下现有的 SDF 教程。

Modifying an existing SDF world is also a good way to get started. Gazebo Sim ships with a number of example SDF worlds that you can freely copy and modify. These example SDF files are installed. Many of the SDF files also have instructions located at the top of the SDF file. The instructions typically contain information about how to run Sim with the SDF file in order to experience a particular feature.

修改一个已有的 SDF 世界也是一个不错的入门方法。Gazebo Sim 提供了许多示例 SDF 世界文件，你可以随意复制和修改它们。这些示例 SDF 文件是预装好的。许多 SDF 文件开头通常也附有说明。这些说明通常会告诉你如何使用该 SDF 文件来运行 Sim，从而体验某项特定功能。

There are a wide variety of simulation resources at your disposal on https://app.gazebosim.org/fuel. If you find a model you’d like to use, then click on the <> icon in the model description page, highlighted in the image below, to copy an SDF snippet into your clipboard. This snippet can be pasted directly into your custom SDF file.

在 https://app.gazebosim.org/fuel 网站上，您可以使用各种各样的模拟资源。如果您找到了一个想使用的模型，只需点击模型描述页面中那个类似「<>」的图标（如下图所示），就能将相应的 SDF 片段复制到您的剪贴板。这个片段可以直接粘贴到您自定义的 SDF 文件中。
