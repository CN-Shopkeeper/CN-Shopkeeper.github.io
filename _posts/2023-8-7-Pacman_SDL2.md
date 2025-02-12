---
layout: post
author: shopkeeper
categories: projects
---

### 基于 SDL2 的吃豆人游戏

> :warning: ~~**本游戏的全部售卖收入将用于充值原神！**~~

[项目主页](https://github.com/CN-Shopkeeper/pacman-SDL2)，如果你喜欢[这个项目](https://github.com/CN-Shopkeeper/pacman-SDL2)，请给一个 star。

在线试玩请[点击跳转](https://cn-shopkeeper.github.io/Projects/Pacman-SDL2/Pacman.html)，注意，这个游戏需要键盘输入，目前只支持桌面端。

如果上述链接无法访问或加载，可以尝试[这个链接](http://146.56.248.15/games/pacman/)。注意，这个链接可能会失效。

## 关于服务器

排行榜后端服务器可能会随时失效(取决于何时被发现 🙏🙏🙏)，[后端项目地址](https://github.com/CN-Shopkeeper/games-server)。

如果不通过 Emscripten 编译，只是在本地运行，则不会受到影响。本地文件是 Stand Alone 的。

## 游戏规则

你说的对，但是《pacman-SDL2》是由 Shopkeeper 复刻 Atari 经典产品吃豆人的一款全新封闭世界冒险游戏。游戏发生在一个被称作「Maze」的幻想世界，在这里，被神选中的人将被授予「迈达斯之手」，导引无尽的暴食之力。你将扮演一位名为「Pacman」的神秘角色，在紧张的探索中邂逅性格各异、能力独特的怪物们，与他们斗智斗勇、相互追逐，吃掉豆子获取分数，逐步发掘「先贤遗迹」的真相。

1. 角色控制： 玩家控制的角色是一个呈现为一个圆形的 "吃豆人"（Pac-Man）。玩家可以使用键盘上的 WSAD 键来控制吃豆人的移动方向：上、下、左、右。

2. 迷宫： 游戏迷宫由一个迷宫地图组成，其中包含许多小豆子和其他特殊物体。

3. 小豆子和能量豆子： 迷宫中布满了小豆子，吃掉它们会增加玩家的分数。迷宫的四个特定位置各有一个大豆子（或 "能量豆子"），吃掉它们会使鬼魂变为蓝色，玩家此时可以吃掉蓝色的鬼魂来获取更高的分数。

4. 鬼魂： 迷宫中有四只鬼魂，它们分别有不同的名字：Blinky（红色）、Pinky（粉色）、Inky（青色）和 Clyde（橙色）。鬼魂会追逐吃豆人，如果吃豆人被鬼魂碰到，吃豆人会失去一条生命。然而，当吃掉能量豆子后，鬼魂会变为蓝色，此时吃豆人可以吃掉它们。

5. 吃掉鬼魂： 当鬼魂变为蓝色时，吃豆人可以吃掉它们，吃掉蓝色鬼魂会增加额外的分数。蓝色鬼魂会在一段时间后恢复成正常状态并重新追逐吃豆人。

6. 生命和得分： 玩家开始游戏时有多条生命。玩家通过吃豆子、吃掉鬼魂和完成特定任务（速通或保留更多生命）来获得分数。游戏的目标是获取尽可能高的分数。

## 游戏截图

<div style="text-align:center">
  <img src="/assets/images/2023-8-23-ranking_list_2023-8-22.png" alt="排行榜(截至2023年8月22日)">
  <figcaption>排行榜(截至2023年8月22日)</figcaption>
</div>

<div style="text-align:center">
  <img src="/assets/images/2023-8-23-gaming.png" alt="运行时">
  <figcaption>运行时</figcaption>
</div>

## 特别鸣谢

特别感谢`单身剑法传人`（[B 站](https://space.bilibili.com/256768793/) & [GitHub](https://github.com/VisualGMQ)）对我的帮助。

感谢以下内测人员的参与与反馈：

```
colin_008
satori
shear
shear's Queen
Crystal
M-thor
TX7
Lynn00
```

## 算法依据

[地图生成](https://shaunlebron.github.io/pacman-mazegen/) (简化了的)

[游戏机制](https://gameinternals.com/understanding-pac-man-ghost-behavior)

## 更新日志

- 2023 年 8 月 21 日

  - v1.3。对游戏机制进行了升级
  - 现在玩家有三条生命
  - 游戏得分方式更新：
    ```
    <!-- 获胜时 -->
    总分 = 吃掉的豆子 * 10 + 吃掉的鬼怪 * 对应的连杀奖励 + 时间奖励 + 剩余生命奖励
    <!-- 失败时 -->
    总分 = 吃掉的豆子 * 10 + 吃掉的鬼怪 * 对应的连杀奖励
    ```
  - 玩家在死亡时回到出生点，并拥有 3 秒的无敌时间。无敌时间内速度翻倍。
  - 修改了彩蛋的效果，使之更加符合描述。

- 2023 年 8 月 20 日

  - v1.2。感谢诸多内测人员的反馈与建议，该项目才能有了更多改进之处！
  - 增加了排行榜。当获胜时会通过消息框引导录入成绩。输入的用户 ID 最多为 10 个 ASCII 字符(因为 shopkeeper 就是 10 个字符)。
  - 排行榜存储在服务器本地文件，不具备 ACID 特性。如有错误产生，请见谅！
  - Ghost 的难度调整：speed 3 -> 5

- 2023 年 8 月 18 日

  - 增加了彩蛋：
    > > 在神秘的迷宫中，有四处遥远的角落，正午的太阳啊，能消灭世间一切邪魅，却为何不能将你的光芒挥洒到这些阴暗的角落，让其成为了邪魅躲避阳光猛烈的避难之所。
    > >
    > > 勇士啊，若你被困于那狭小的角落，当你半边的视野被阻隔，不要放弃希望，拼尽全力挣脱牢笼，伟大的先贤将会显现，为你降下保护结界，助你冲出重围！

- 2023 年 8 月 18 日

  - v1.1，极有可能是最终版本
  - 增加了连杀奖励
  - Pacman 现在不可以去 Ghost house 刷分

- 2023 年 8 月 17 日

  - 地图中有能量豆，吃了之后 Ghost 会进入 Frightened 模式
  - Frightened 模式下 Ghost 会变成蓝色，移动速度减慢
  - Frightened 模式下 Ghost 可以被吃掉（一个两百分）
  - 能量豆持续时间为 15 秒，最后三秒时 Ghost 会闪烁
  - 增加了 Debug 模式下的文字输出
  - 现在可以在 Frightened 模式时进鬼屋刷分。。。。。

- 2023 年 8 月 16 日
  - 完成了 v1.0 版本，有了正常的胜利、失败判定
  - 增加了计时器，根据时间改变 ghost 的行为模式
  - 增加了 inky 和 clyde 的出动条件（默认开局是不出鬼屋的）
  - 为 pacman 添加了动画

## TODO

- 随着游戏进程出现的加分水果
- ~~Pacman 不应该可以进入鬼屋~~
- ~~Frightened 模式下对 Ghost 应该有连杀奖励~~
- 触发彩蛋后无敌三秒
- ~~排行榜~~
- ~~Ghost 速度调整~~
- ~~剩余时间奖励~~
- ~~三条命~~

#### WASM

```shell
emcmake cmake -S . -B wasm-build
```

```shell
cmake --build wasm-build
```
