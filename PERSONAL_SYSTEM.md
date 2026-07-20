# 个人系统深度规划:时间 × 输入 × AI × 学业

> 这四件事不是四个独立项目,而是一套系统的四层。自下而上:
>
> ```
> 第4层 目标层   学业/成长规划(一切下层为它服务)
> 第3层 处理层   Obsidian 笔记 + Anki(已在 LEARNING_PLAN.md 建立)
> 第2层 输入层   信息饮食(读什么、从哪读)
> 第1层 数据层   时间测量与复盘(知道时间去哪了)
>        AI 不是单独一层,是贯穿四层的放大器
> ```
>
> 总原则:**先跑最小闭环,再加插件。** 系统维护时间超过学习时间的 10%,就是在用"搭系统"逃避"用系统"。

---

## 一、时间管理与可视化

### 先讲清现实约束

苹果的"屏幕使用时间"**没有公开导出 API**,iPhone 数据基本封闭,别在这上面死磕。正确策略是:**电脑端全自动记录,手机端粗粒度人工摘抄**。

### 电脑端:ActivityWatch(核心)

- 开源免费,数据全部存本地,自动记录每个应用/窗口/网页标题的停留时长。
- 有社区插件 **aw-watcher-obsidian**,连你在 vault 里每个笔记文件花了多久都能记录。
- 付费替代:RescueTime、Rize;Mac 上的 Timing 也有对应的 obsidian-timing-plugin。

### 手机端:接受粗粒度

- 周复盘时打开"屏幕使用时间"周报,手抄 3 个数字进周记:总时长、Top 3 App、拿起次数。两分钟,够用。
- 想"限制"而非"记录":one sec、Opal 这类 App 在打开社交软件前加一道摩擦。

### Obsidian 时间管理插件栈(最小集)

| 插件 | 用途 |
|------|------|
| Periodic Notes + Templater | 日/周/月笔记自动按模板生成 |
| Day Planner | 当天时间块 |
| Tasks | 任务(截止日期/重复任务) |
| Dataview | 从每日笔记的 frontmatter 自动聚合周报 |
| Heatmap Calendar | 习惯热力图(Anki 是否清零、深度工作) |
| Super Simple Time Tracker | 手动番茄计时(可选) |

### 关键设计:复盘 > 仪表盘

- 每日笔记 frontmatter 只记 **3 个指标**:`deep_work_hours`、`anki_done`、`sleep_hours`。超过 3 个必然弃坑。
- **周日 30 分钟复盘仪式**(整个系统的心跳):看 ActivityWatch 周报 + 手机周报,回答三个问题——本周最大时间黑洞是什么?下周砍掉什么?下周唯一重点是什么?
- 量化系统的经典失败模式:记录很全,行为不变。**数据不改变行为,复盘时做的决定才改变。**

---

## 二、输入渠道优化:从"推送流"到"订阅流"

### 诊断

公众号/B站/小红书的问题不在中文,在于它们是**算法推送流**——平台决定你看什么,且无限下滑没有"读完"状态。改造方向:换成**订阅流**(你决定看什么,收件箱有限、可清零)。英文高质量内容恰好 90% 活在 RSS / newsletter / 独立博客里,天然适合订阅流。

### 四段式管道

1. **聚合(RSS 中枢)**:Readwise Reader(推荐,和后面标注/同步一体化)或免费的 Folo、NetNewsWire。
   - 中文源桥接进来:**WeWe RSS**(公众号 → RSS,基于微信读书,可自部署)、**RSSHub**(B站 UP 主、播客等 → RSS)。
   - 效果:把"刷"变成"收件箱",读完就是读完。
2. **稍后读 + 标注**:Reader 统一处理网页/newsletter/PDF/YouTube 字幕并划线;学术论文单独走 Zotero。
3. **同步进 Obsidian**:Readwise 官方插件自动把所有划线同步进 vault → 每周提炼成自己的话 → 接回 LEARNING_PLAN.md 里的 Anki 流程。
4. **视频降维**:B站/YouTube 长视频先把字幕丢给 AI(NotebookLM / Claude)出摘要,再决定值不值得看全片。视频是信息密度最低的媒介,默认 2 倍速 + 只看值得的。

### 规则(比工具重要)

1. 纯推送流(小红书/抖音式信息流)卸载,或限制为每天一次、固定时段。
2. 英文输入从**你已懂的领域**切入(Go、ML)——内容熟悉度抵消语言成本,这是最平滑的过渡。
3. 收藏与精读比例不超过 3:1,否则"稍后读"就是"永不读"。
4. 每两周审查订阅源:两周没点开的,退订。

### 英文起步源(结合你的方向)

- Newsletter:Golang Weekly、The Batch(Andrew Ng)、Import AI(Jack Clark);阮一峰周刊虽是中文,但链接大量英文源,当跳板用。
- 博客:Simon Willison、Lil'Log(Lilian Weng)、Dave Cheney。
- 视频:3Blue1Brown、Karpathy、StatQuest。
- 社区:Hacker News,每天只看首页 10 分钟。

---

## 三、AI Agent 长期规划

### 分层使用模型

| 层 | 工具 | 用途 |
|----|------|------|
| L1 对话层(每天) | Claude / ChatGPT | 苏格拉底 tutor:解释、出题、批改、费曼陪练 |
| L2 检索层 | NotebookLM、Perplexity | 把课程材料/书喂进去做问答和音频概览;带引用的检索 |
| L3 Agent 层(干活) | Claude Code / Cowork | 代码、文件批处理、批量整理——本仓库的计划文档就是这么生成的 |
| L4 集成层(关键一步) | Obsidian Local REST API 插件 + Obsidian MCP server | 让 Claude 直接读写你的 vault:自动生成周报草稿、把 AI 对话产出写进笔记、基于你全部笔记回答问题 |
| L5 本地层(可选) | Ollama + 本地模型 | 隐私内容(日记、个人数据)不出本机 |

Obsidian 站内插件:Smart Connections(vault 语义搜索)、Copilot for Obsidian(笔记内对话)。

### 季度路线图

- **Q1 习惯层**:每天用 AI 当 tutor(读完出题、费曼复述让它挑毛病);打通 Readwise → Obsidian。
- **Q2 集成层**:配置 Obsidian MCP;每周日让 AI 基于本周日记自动草拟周报,你只做修订。
- **Q3 自动化层**:RSS 文章自动摘要;Anki 卡片半自动生成(AI 从周笔记提候选卡,你人工筛——**不要全自动**,筛选本身就是学习)。
- **Q4 裁剪**:砍掉所有说不出"每周省了几小时"的环节。

### 铁律

- 每个新工具试用两周,量化省时,留不下证据就删。
- 折腾 agent 本身是最大的时间黑洞。判断标准永远是:**真实节省的小时数**,不是玩过多少工具。

---

## 四、学业规划:斯坦福大一 + 40 AP 学分

### AP 学分的现实(2025–26 政策,最终以 Registrar 为准)

- 外部学分(AP/IB/转学分合计)**上限 45 quarter units**,单科考试最多 10 units,一般要求 4–5 分。
- AP 的真实价值不是"抵课",而是:① **Placement**——跳过入门直接进正课(Calc BC → 直接 Math 51;AP 物理 → PHYSICS 61 系列);② **日程弹性**——某学季轻载、提前修研究生课、给双学位/辅修留空间。
- 注意:多数专业的核心课**不能**用 AP 抵。你这 40 units 买到的是自由度,不是毕业进度条。

### 专业选择:大一不用决定

- 候选集:CS(默认强选项)、Mathematical & Computational Science、Symbolic Systems(CS+认知科学,适合 AI 方向)、EE、Data Science。
- 策略:前三个学季修**所有候选专业的公共前缀**——CS106B、Math 51/53、CS103、CS109。修完这四门,你对自己喜欢什么的判断会比任何测评准。
- 选课情报:用 **Carta**(校内平台)看每门课的真实周时长、评价、成绩分布;配合公开的 ExploreCourses 目录和各系 handbook。

### 哪些课在校修、哪些自学(核心判断框架)

**学费买的是反馈、同伴和门槛,不是信息。信息免费,反馈昂贵。**

在校修(反馈密集型):
- 证明类:CS103、数学深课——证明需要人批改,自学最容易学出幻觉。
- 大 project 课:CS107、CS111、CS161、CS229——deadline、队友、curve 是自学复制不了的强制力。
- 带稀缺资源的:实验室、教授 office hours、高质量同伴。

自学/零散时间(信息传递型,用 LEARNING_PLAN.md 的方法论):
- 工具类:Git、shell、Docker——你书架上那批书,不值得花学分。
- 公开材料完整的:CS229 notes(你已收藏)、CS224N 视频、fast.ai——先自学,之后选课就是"第二遍",效果翻倍。
- 兴趣试水:任何"好像有意思"的方向,先自学两周再决定是否投一个 quarter。

### 用 AI 深化学习(模拟教授对答)

- 把 syllabus + lecture notes + 你自己的笔记喂给 Claude,让它扮演 office hours:苏格拉底式追问、批改你的证明、模拟期中口试。
- NotebookLM:把整门课的材料变成可问答知识库 + 音频概览(通勤听)。
- 考前:让 AI 基于历年公开题出限时模拟卷。
- **红线**:每门课有自己的 AI 使用政策。AI 用于理解,不用于生成提交物——这既是诚信问题,也是你交学费的意义所在。

### 时间规划按什么维度?——分层,不同层不同粒度

| 层级 | 粒度 | 内容 |
|------|------|------|
| 年 | 1–2 个主题 | 方向层:"今年搞清楚我是否走 CS+AI" |
| 学季 | 10 周(斯坦福天然节奏) | 承诺层:选哪几门课 + 一个 side project |
| 周 | 周日 30 分钟复盘 | 调度层:排下周,砍上周的坑 |
| 天 | 时间块 + 3 个优先级 | 执行层:Day Planner |

**小时级计划只存在于"今天"。** 计划粒度越细,存活时间越短——长期按目标规划,短期才按时间规划。

### 大一年样例(示意,以实际 placement 为准)

- 秋:CS106B + Math 51 + 写作/通识 + 新生研讨课
- 冬:CS107 + CS103 + 通识
- 春:CS109(或 CS111)+ 探索课(SymSys/EE 试水)
- 业余:本仓库的 Go/项目线降为周末 side project;数学与 Python 保持为主线(见 LEARNING_PLAN.md 第九节)

---

## 五、落地路径:六周跑通最小闭环

- **W1–2 地基**:Obsidian 装最小插件集(Periodic Notes、Templater、Dataview、Tasks)+ 日/周模板;电脑装 ActivityWatch。
- **W3–4 输入**:配 Reader/RSS + WeWe RSS/RSSHub;卸载或限时推送流 App;订阅英文起步源。
- **W5–6 AI**:打通 Claude ↔ Obsidian(MCP);建立每日 AI tutor 习惯(读完出题 + 费曼复述)。
- 之后:**周日 30 分钟复盘是整个系统的心跳**;任何插件两周不用就删。

### 反模式自查(出现即整改)

- 搭系统的时间 > 用系统的时间
- 追踪指标超过 3 个
- 工具清单在变长,而笔记/卡片/代码量没变多
- 为了"完美的系统"推迟真正的学习——系统永远为学习让路

---

## 参考来源

- [Stanford Bulletin: Undergraduate Test Credit](https://bulletin.stanford.edu/academic-polices/transfer-test-credit/undergraduate-test)(45 单位上限、单科 10 单位)
- [Stanford AP Credit Chart](https://studentservices.stanford.edu/advanced-placement-ap-credit-chart)
- [aw-watcher-obsidian(GitHub)](https://github.com/LordGrimmauld/aw-watcher-obsidian)
- [WeWe RSS(GitHub)](https://github.com/cooderl/wewe-rss)
- [Readwise 官方 Obsidian 插件文档](https://docs.readwise.io/readwise/docs/exporting-highlights/obsidian)
