# Refactor（重构）简介
（因 “想和朋友在大学计算机课前来一场紧张刺激的PVP” 而一时兴起的项目）

所有玩家均可一击毙命，每击碎一个敌方玩家 **+1** 分，在游戏时间结束时得分最高的玩家胜出...

> 游戏支持自定义游戏规则，默认规则为：3分钟游戏时长、无限重生次数

## 按键控制：
- 攻击：鼠标左/右键（攻击方式与武器有关...）；
- 左右移动：AD（单击）；
- 下落：S（长按）；
- 冲刺：shift（单击，长按增加冲刺距离）；
- 跳跃：space（单击，长按增加跳跃高度）；
- 切换武器：tap（单击，这是一个测试性的功能在未来更新可能会删除）。

## 游戏内容
  当前游戏内容有
- **3种武器**
  - **裂隙（初始近战武器）**
    - **左键单击/长按** 快速劈砍（目前有三段攻击，单击-第一段，短时间内再次单击-第二段，触发第二段时按键不放-第三段）；
    - **右键长按** 进入蓄力状态后 **按下左键** 朝鼠标指针将武器丢出（若 **未松开左键** 可在命中墙壁时将自身拉向目标位置）。
  - **光轮（BOSS级远程武器）**
    - 该武器会 缓缓跟随玩家 位移，所有 发射物 均从光轮射出；
    - **左键长按** 发射 <ins>可穿墙 可被摧毁</ins> 的飞弹；
    - **右键长按** 进入蓄力状态（当蓄力完毕时光轮将吸附在玩家身上），**松开按键** 朝鼠标指针发射 <ins>可穿墙</ins> 的激光。
  - **突击盾（初始近战武器-开发中）**
    - 该武器 **“显型”** 期间  <ins>可阻挡大多数来自正面</ins> 的攻击
    - **左键单击** 向鼠标指针方向挥舞盾牌；
    - **左键长按** 向鼠标指针方向举盾（期间会大幅降低玩家的移动速度与跳跃高度）；
    - ...
> 各武器仍有些许 “特殊机制” 未在此处列出...

  ---

- **1只完整BOSS**
  - **米迦勒**
    - 基础拥有7个技能...（暂不一一列举）；
    - 二阶段（50%生命）修改世界重力大小为0，额外追加1个技能，并稍微减小技能前后摇与增加技能强度。

## 游戏演示:
  ### 经典PVP:
  联机房间 -> 开始游戏
  <img width="960" height="540" alt="pvp_demo_GameStart" src="https://github.com/user-attachments/assets/60e2db83-83af-4500-8fd6-b5a458c082b3" />
  
  近战 **裂隙** 连击...
  <img width="960" height="540" alt="pvp_demo_Melee" src="https://github.com/user-attachments/assets/6f3f850c-6453-4863-a402-8e935cac6843" />
  
  近战 **裂隙** 击碎...
  <img width="1920" height="1080" alt="pvp_kill_Melee" src="https://github.com/user-attachments/assets/1ac6b6f2-8352-4f62-a1b6-5a2f44bc553b" />

  远程 **光轮** 击碎...
  <img width="1920" height="1080" alt="pvp_kill_LongRange1" src="https://github.com/user-attachments/assets/ad8d25a9-1e94-474d-a517-100fa5f5dab1" />

  近战 **裂隙** 被击碎...
  <img width="960" height="540" alt="pvp_killed_Melee" src="https://github.com/user-attachments/assets/3bce2271-36a9-49a6-9320-fe90c785d486" />

  远程 **光轮** 被击碎...
  <img width="1920" height="1080" alt="pvp_killed_LongRange" src="https://github.com/user-attachments/assets/d3ecafc6-3f14-4d15-8d85-75b7e87df33b" />

  时间耗尽...
  <img width="1920" height="1080" alt="pvp_Time&#39;sUp" src="https://github.com/user-attachments/assets/05f11026-4de0-432c-8b57-51e92dd77a2b" />

  
  ### BOSS战-“米迦勒”部分技能展示:
  短暂瞄准 **最近的玩家** 后释放大型飞弹...
  <img width="1280" height="720" alt="boss_skill_0" src="https://github.com/user-attachments/assets/b95fbfe7-5e52-4e8c-a5f9-472de5f70741" />

  预警数秒后以 **自身为中心** 释放数道激光...
  <img width="1280" height="720" alt="boss_skill_1" src="https://github.com/user-attachments/assets/4e49219d-e14c-4435-b7b6-bb1669c362cb" />

  改变画面颜色后释放 **交织于全场** 的激光...
  <img width="1280" height="720" alt="boss_skill_2" src="https://github.com/user-attachments/assets/50638e36-6083-4e82-b440-0e74d9263238" />

  释放小型飞弹后接大型飞弹，大型飞弹飞出后 **重定向** 小型飞弹的飞行轨迹...
  <img width="1280" height="720" alt="boss_skill_3" src="https://github.com/user-attachments/assets/ea4f516d-c04f-47b3-951f-5facbf3cf8f6" />

  释放 **力场（吸引/推开玩家并扭曲屏幕）** 后接大型飞弹索敌...
  <img width="1280" height="720" alt="boss_skill_4" src="https://github.com/user-attachments/assets/a21c95da-a73a-43b2-abf7-bba7cf34dc1d" />

  血量跌至50%时锁血并进入 **二阶段（“米迦勒”二阶段会使全场失重）**，进行一段演出后释放加强的小型+大型飞弹...
  <img width="640" height="360" alt="boss_nextState" src="https://github.com/user-attachments/assets/7f70ab41-c30a-473a-889f-ea6fcb98dd53" />

  二阶段下许多技能都有加强，以 **自身为中心** 释放的激光数量增加、前后摇缩短...
  <img width="1280" height="720" alt="boss_nextState_skill_0" src="https://github.com/user-attachments/assets/ab0323ad-d3b3-47b0-ac8d-f4616342071d" />
  
  加强后的 **吸引力场+小型飞弹+大型飞弹** ... 
  <img width="1000" height="562" alt="boss_nextState_skill_2" src="https://github.com/user-attachments/assets/fd322d2d-651d-4ce2-919a-2afb2f2fde8e" />

  甚至会有不同的技能变体...
  <img width="1200" height="675" alt="boss_nextState_skill_1" src="https://github.com/user-attachments/assets/a8ad7663-1a0c-422a-9982-279a7a958616" />

  以及全新的技能类型，比如 **三道横扫全场的激光（方向是随机的）** ...
  <img width="640" height="360" alt="boss_nextState_skill_3" src="https://github.com/user-attachments/assets/db4ece72-e012-4815-ad51-94574b443045" />

  **连发小型飞弹！**
  <img width="1000" height="562" alt="boss_nextState_skill_4" src="https://github.com/user-attachments/assets/86429b6c-3574-4d8d-82b0-1458cd570098" />

  大致如此...
