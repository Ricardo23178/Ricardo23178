# 朱思兴 / Zhu Sixing

2027 届软件工程本科生（湖南信息学院），求职方向 **开发工程师**。

主线是移动客户端：HarmonyOS（ArkTS / ArkUI）、Android（Kotlin / MVVM）；服务端能独立写 Spring Boot，习惯顺手给自己的接口补一套自动化测试。

2096704694@qq.com

---

## 一条能跑通的完整链路

不是一个 demo 拆成三个仓，而是同一个系统（家属协同用药提醒）的两个客户端、一个服务端、一套接口测试，每块都能单独跑起来验证：

| 层 | 仓库 | 做了什么 |
|---|---|---|
| 客户端 · 鸿蒙 | [medication-harmony](https://github.com/Ricardo23178/medication-harmony) | HarmonyOS ArkTS 客户端，16 个页面 / 31 个 .ets / 3846 行，含适老化交互与家属协同 |
| 客户端 · Android | [medication-android](https://github.com/Ricardo23178/medication-android) | Kotlin + Compose 重做同一套业务，37 个文件 / 约 4100 行 / 32 个用例，验证规则确实只在服务端有 |
| 服务端 | [medication-backend](https://github.com/Ricardo23178/medication-backend) | Spring Boot 3.5 + MyBatis-Plus + MySQL + JWT，用药计划状态机、定时提醒、家属绑定 |
| 测试 | [medication-api-tests](https://github.com/Ricardo23178/medication-api-tests) | pytest 接口测试，141 条用例 / 2244 行，覆盖鉴权、越权隔离、状态机、确认幂等 |

写测试时挖出一个真实缺陷：用户点「稍后提醒」后，确认窗口被重算成 `now + 延迟 + 120s`，若原提醒时间仍在未来，新窗口反而比原来更短。已用 `xfail` 标记并保留复现路径，修法是取两者较大值。

> 这条链路是我最想让人看的部分：从界面到接口再到用例，能自己把三段接起来，也知道接口契约在两端不一致时该先怀疑谁。

## 独立模块

- **[stilltick](https://github.com/Ricardo23178/stilltick)** — 静刻，纯本地专注计时器（Kotlin / Compose）。状态里不存剩余秒数、只存结束时间戳，界面每帧现算；到点的三个入口统一收敛，进程被杀也不丢时间。14 个源文件 / 1533 行 / 22 个用例。
- **[video-analysis-module](https://github.com/Ricardo23178/video-analysis-module)** — 把视频转成模型可读的证据材料：FFprobe 元信息 + 均匀抽帧 + 字幕/Whisper 转写，输出带 schema 版本的 `analysis.json`，配契约测试保证字段不漂移。
- **[scrap-return](https://github.com/Ricardo23178/scrap-return)** — Unity 2D 点击解谜原型，三关连续可玩（缺肢装配 / 伪装通行 / 气压联锁），3747 行 C#，场景由 Editor 脚本代码生成而非手工拖拽。

## 技术栈

| 分类 | 内容 |
|---|---|
| 语言 | Kotlin · Java · ArkTS / TypeScript · Python · SQL |
| 移动端 | ArkUI 声明式开发 · Stage 模型生命周期 · 页面路由与状态管理 · MVVM · Compose 与 XML 两套 UI · Retrofit / OkHttp |
| 服务端 | Spring Boot · MyBatis-Plus · MySQL · JWT · RESTful 接口设计 |
| 测试与工具 | pytest · Git · DevEco Studio · Android Studio · IntelliJ IDEA |

## 当前在做

- 安卓端已接上毕设后端，同一份接口契约在 HarmonyOS、Android、pytest 三处行为一致，登录与今日提醒两条主链路都跑通。
- 补 Kotlin 协程与 ViewModel 的底层理解——目标不是会调 API，而是能讲清为什么这样用。

---

<sub>简历里写的项目都在这里，代码公开可读。</sub>
