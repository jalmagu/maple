# LinkMap Aggregate

LinkMap Aggregate 是一个面向技术研究者、内容策展人和信息架构师的高密度外链归集与导航系统。该项目不生产原始内容，而是通过对特定域名下结构化文章资源的批量收录与分类呈现，为垂直领域的信息检索提供一条高效、可复用的中间层路径。目标用户包括需要快速获取特定站点公开资料的分析人员、维护个人知识库的开发者，以及希望从大量分散链接中提炼主题脉络的信息整理者。

项目核心解决三个问题：第一，将大量无规律的 URL 转化为可浏览、可筛选的资源清单；第二，通过目录树与文档导航表格建立链接与上下文之间的映射关系，降低认知负载；第三，提供标准化的快速启动流程，使用户能在五分钟内获得一个可离线运行或二次开发的外链索引框架。LinkMap Aggregate 不依赖任何外部数据库，所有收录资源均以静态清单形式存在，便于版本控制与协作编辑。

## 功能概览

批量链接收录：支持从文本源直接导入大量 URL，自动去重并按原始顺序排列，保留完整协议与路径结构。

域名级归类：以域名 map.blog.zdvgjr.cn 为根节点，将所有链接按文章编号自然排序，形成可预测的浏览序列。

裸协议保留：严格保持每个 URL 的原始协议前缀（http 或 https），不自动升级或降级，确保访问路径与源站设计一致。

只读索引模式：项目本身不存储任何文章副本，仅提供外链引用，避免版权与存储冗余问题。

静态文档生成：基于 Markdown 构建全部页面，无需动态服务端支持，可直接托管于任意静态文件服务或本地浏览器打开。

多维度导航表格：内置文档导航与安装要求两张表格，分别从用户视角和运维视角提供结构化信息入口。

ASCII 目录树可视化：通过文本图形展示项目文件夹层次，每个目录附带职责说明，降低新贡献者的理解成本。

贡献者友好流程：明确定义了从克隆到提交的完整协作步骤，支持外部人员通过 Pull Request 增删或修正链接记录。

## 应用场景

技术文献回溯分析：研究人员可利用该项目的链接清单，批量访问 map.blog.zdvgjr.cn 下的历史文章，进行主题分布、发布时间或引用关系的粗略统计，无需手动收集入口地址。

个人知识库的素材索引：知识管理爱好者可将本项目的 URL 列表作为外部源，导入到 Obsidian、Notion 或 Logseq 等工具中，结合标签系统构建自己的专题阅读队列。

静态网站的外链展示页：个人博客或小型团队站点可以直接 fork 本项目，将资源列表章节嵌入到自己的导航页面中，作为“推荐阅读”或“参考来源”的公开记录。

数据迁移前的链接盘点：当源站进行架构调整或域名迁移时，运维人员可借助本项目提供的完整 URL 清单，快速校验哪些路径需要配置重定向或更新内部引用。

## 快速开始

以下命令序列适用于 Linux、macOS 及 Windows WSL 环境，确保系统已安装 Git 和 Node.js（建议 LTS 版本）。

```bash
# 克隆仓库到本地
git clone https://github.com/your-org/linkmap-aggregate.git
cd linkmap-aggregate

# 安装依赖（用于本地预览和链接格式校验）
npm install

# 运行构建脚本，生成最终的资源索引页面
npm run build
```

执行完成后，在 `dist/` 目录下会生成一个静态 HTML 文件和一个纯文本格式的链接清单。用户可以直接双击 HTML 文件在浏览器中打开，或通过 `npm run serve` 启动一个本地开发服务器进行预览。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Node.js | >=16.0.0 | 用于运行构建脚本和格式校验工具 |
| npm | >=8.0.0 | 包管理器，用于安装项目依赖 |
| Git | >=2.25.0 | 用于克隆仓库和版本控制操作 |
| 现代浏览器 | 最新两个主要版本 | 用于预览生成的静态页面（Chrome/Edge/Firefox） |
| 磁盘空间 | >=50MB | 用于存放源代码、依赖及构建产物 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户入门 | `docs/quick-start.md` | 如何最快速度看到链接列表？如何本地预览？ |
| 维护指南 | `docs/maintenance.md` | 如何新增或删除链接？如何更新资源列表章节？ |
| 设计说明 | `docs/architecture.md` | 为什么采用纯静态方案？目录结构的设计依据是什么？ |
| 校验规则 | `docs/validation.md` | URL 格式的硬性检查规则有哪些？违反后如何修复？ |

## 资源列表

- http://map.blog.zdvgjr.cn/Article/426346.shtml
- http://map.blog.zdvgjr.cn/Article/2174.shtml
- http://map.blog.zdvgjr.cn/Article/6059785.shtml
- http://map.blog.zdvgjr.cn/Article/8700482.shtml
- http://map.blog.zdvgjr.cn/Article/4767844.shtml
- http://map.blog.zdvgjr.cn/Article/7133337.shtml
- http://map.blog.zdvgjr.cn/Article/76918.shtml
- http://map.blog.zdvgjr.cn/Article/425282.shtml
- http://map.blog.zdvgjr.cn/Article/120104.shtml
- http://map.blog.zdvgjr.cn/Article/2864.shtml
- http://map.blog.zdvgjr.cn/Article/82259.shtml
- http://map.blog.zdvgjr.cn/Article/960852.shtml
- http://map.blog.zdvgjr.cn/Article/265335.shtml
- http://map.blog.zdvgjr.cn/Article/3165039.shtml
- http://map.blog.zdvgjr.cn/Article/8574.shtml
- http://map.blog.zdvgjr.cn/Article/609409.shtml
- http://map.blog.zdvgjr.cn/Article/912353.shtml
- http://map.blog.zdvgjr.cn/Article/625740.shtml
- http://map.blog.zdvgjr.cn/Article/485885.shtml
- http://map.blog.zdvgjr.cn/Article/353770.shtml
- http://map.blog.zdvgjr.cn/Article/5025418.shtml
- http://map.blog.zdvgjr.cn/Article/95163.shtml
- http://map.blog.zdvgjr.cn/Article/434104.shtml
- http://map.blog.zdvgjr.cn/Article/433710.shtml
- http://map.blog.zdvgjr.cn/Article/664920.shtml
- http://map.blog.zdvgjr.cn/Article/2415.shtml
- http://map.blog.zdvgjr.cn/Article/66920.shtml
- http://map.blog.zdvgjr.cn/Article/0422.shtml
- http://map.blog.zdvgjr.cn/Article/4797.shtml
- http://map.blog.zdvgjr.cn/Article/890112.shtml
- http://map.blog.zdvgjr.cn/Article/7741991.shtml
- http://map.blog.zdvgjr.cn/Article/296682.shtml
- http://map.blog.zdvgjr.cn/Article/746142.shtml
- http://map.blog.zdvgjr.cn/Article/950397.shtml
- http://map.blog.zdvgjr.cn/Article/68361.shtml
- http://map.blog.zdvgjr.cn/Article/67421.shtml
- http://map.blog.zdvgjr.cn/Article/331066.shtml
- http://map.blog.zdvgjr.cn/Article/6569035.shtml
- http://map.blog.zdvgjr.cn/Article/2294080.shtml
- http://map.blog.zdvgjr.cn/Article/1133264.shtml
- http://map.blog.zdvgjr.cn/Article/149789.shtml
- http://map.blog.zdvgjr.cn/Article/87341.shtml
- http://map.blog.zdvgjr.cn/Article/489876.shtml
- http://map.blog.zdvgjr.cn/Article/2220.shtml
- http://map.blog.zdvgjr.cn/Article/93924.shtml
- http://map.blog.zdvgjr.cn/Article/11510.shtml
- http://map.blog.zdvgjr.cn/Article/2643699.shtml
- http://map.blog.zdvgjr.cn/Article/1586.shtml
- http://map.blog.zdvgjr.cn/Article/57306.shtml
- http://map.blog.zdvgjr.cn/Article/06289.shtml
- http://map.blog.zdvgjr.cn/Article/0113.shtml
- http://map.blog.zdvgjr.cn/Article/6970947.shtml
- http://map.blog.zdvgjr.cn/Article/0160.shtml
- http://map.blog.zdvgjr.cn/Article/1371755.shtml
- http://map.blog.zdvgjr.cn/Article/74661.shtml
- http://map.blog.zdvgjr.cn/Article/848566.shtml
- http://map.blog.zdvgjr.cn/Article/744671.shtml
- http://map.blog.zdvgjr.cn/Article/57123.shtml
- http://map.blog.zdvgjr.cn/Article/1979502.shtml
- http://map.blog.zdvgjr.cn/Article/9593599.shtml
- http://map.blog.zdvgjr.cn/Article/1553496.shtml
- http://map.blog.zdvgjr.cn/Article/6974114.shtml
- http://map.blog.zdvgjr.cn/Article/56551.shtml
- http://map.blog.zdvgjr.cn/Article/706140.shtml
- http://map.blog.zdvgjr.cn/Article/068586.shtml
- http://map.blog.zdvgjr.cn/Article/1957.shtml
- http://map.blog.zdvgjr.cn/Article/0406.shtml
- http://map.blog.zdvgjr.cn/Article/0397.shtml
- http://map.blog.zdvgjr.cn/Article/804438.shtml
- http://map.blog.zdvgjr.cn/Article/95858.shtml
- http://map.blog.zdvgjr.cn/Article/69841.shtml
- http://map.blog.zdvgjr.cn/Article/6958.shtml
- http://map.blog.zdvgjr.cn/Article/2043787.shtml
- http://map.blog.zdvgjr.cn/Article/98324.shtml
- http://map.blog.zdvgjr.cn/Article/19998.shtml
- http://map.blog.zdvgjr.cn/Article/2388319.shtml
- http://map.blog.zdvgjr.cn/Article/8748424.shtml
- http://map.blog.zdvgjr.cn/Article/6596316.shtml
- http://map.blog.zdvgjr.cn/Article/150874.shtml
- http://map.blog.zdvgjr.cn/Article/8871405.shtml
- http://map.blog.zdvgjr.cn/Article/834854.shtml
- http://map.blog.zdvgjr.cn/Article/15655.shtml
- http://map.blog.zdvgjr.cn/Article/014603.shtml
- http://map.blog.zdvgjr.cn/Article/0304.shtml
- http://map.blog.zdvgjr.cn/Article/751040.shtml
- http://map.blog.zdvgjr.cn/Article/3917762.shtml
- http://map.blog.zdvgjr.cn/Article/59801.shtml
- http://map.blog.zdvgjr.cn/Article/1542.shtml
- http://map.blog.zdvgjr.cn/Article/9231.shtml
- http://map.blog.zdvgjr.cn/Article/72337.shtml
- http://map.blog.zdvgjr.cn/Article/2257.shtml
- http://map.blog.zdvgjr.cn/Article/699994.shtml
- http://map.blog.zdvgjr.cn/Article/54403.shtml
- http://map.blog.zdvgjr.cn/Article/455684.shtml
- http://map.blog.zdvgjr.cn/Article/606940.shtml
- http://map.blog.zdvgjr.cn/Article/26241.shtml
- http://map.blog.zdvgjr.cn/Article/2129931.shtml
- http://map.blog.zdvgjr.cn/Article/8174350.shtml
- http://map.blog.zdvgjr.cn/Article/7802.shtml
- http://map.blog.zdvgjr.cn/Article/108705.shtml
- http://map.blog.zdvgjr.cn/Article/25051.shtml
- http://map.blog.zdvgjr.cn/Article/2055.shtml
- http://map.blog.zdvgjr.cn/Article/679378.shtml
- http://map.blog.zdvgjr.cn/Article/84715.shtml
- http://map.blog.zdvgjr.cn/Article/4745.shtml
- http://map.blog.zdvgjr.cn/Article/30624.shtml
- http://map.blog.zdvgjr.cn/Article/4933.shtml
- http://map.blog.zdvgjr.cn/Article/179370.shtml
- http://map.blog.zdvgjr.cn/Article/35203.shtml
- http://map.blog.zdvgjr.cn/Article/066691.shtml
- http://map.blog.zdvgjr.cn/Article/12031.shtml
- http://map.blog.zdvgjr.cn/Article/340224.shtml
- http://map.blog.zdvgjr.cn/Article/311238.shtml
- http://map.blog.zdvgjr.cn/Article/17446.shtml
- http://map.blog.zdvgjr.cn/Article/61526.shtml
- http://map.blog.zdvgjr.cn/Article/250870.shtml
- http://map.blog.zdvgjr.cn/Article/021365.shtml
- http://map.blog.zdvgjr.cn/Article/022578.shtml
- http://map.blog.zdvgjr.cn/Article/07402.shtml
- http://map.blog.zdvgjr.cn/Article/2788889.shtml
- http://map.blog.zdvgjr.cn/Article/2089.shtml
- http://map.blog.zdvgjr.cn/Article/5821458.shtml
- http://map.blog.zdvgjr.cn/Article/736471.shtml
- http://map.blog.zdvgjr.cn/Article/318531.shtml
- http://map.blog.zdvgjr.cn/Article/8132.shtml
- http://map.blog.zdvgjr.cn/Article/9508873.shtml
- http://map.blog.zdvgjr.cn/Article/08675.shtml
- http://map.blog.zdvgjr.cn/Article/6612917.shtml
- http://map.blog.zdvgjr.cn/Article/86964.shtml
- http://map.blog.zdvgjr.cn/Article/79980.shtml
- http://map.blog.zdvgjr.cn/Article/25994.shtml
- http://map.blog.zdvgjr.cn/Article/863042.shtml
- http://map.blog.zdvgjr.cn/Article/1206720.shtml
- http://map.blog.zdvgjr.cn/Article/1321100.shtml
- http://map.blog.zdvgjr.cn/Article/750521.shtml
- http://map.blog.zdvgjr.cn/Article/4681603.shtml
- http://map.blog.zdvgjr.cn/Article/60169.shtml
- http://map.blog.zdvgjr.cn/Article/15202.shtml
- http://map.blog.zdvgjr.cn/Article/9629.shtml
- http://map.blog.zdvgjr.cn/Article/6461065.shtml
- http://map.blog.zdvgjr.cn/Article/9178421.shtml
- http://map.blog.zdvgjr.cn/Article/4831269.shtml
- http://map.blog.zdvgjr.cn/Article/481436.shtml
- http://map.blog.zdvgjr.cn/Article/8142933.shtml
- http://map.blog.zdvgjr.cn/Article/94033.shtml
- http://map.blog.zdvgjr.cn/Article/6526.shtml
- http://map.blog.zdvgjr.cn/Article/34520.shtml
- http://map.blog.zdvgjr.cn/Article/7262190.shtml
- http://map.blog.zdvgjr.cn/Article/4057.shtml
- http://map.blog.zdvgjr.cn/Article/349191.shtml

## 项目结构

```
linkmap-aggregate/
├── src/                         # 源代码主目录
│   ├── index.js                 # 入口脚本，协调构建流程
│   ├── collector.js             # 链接收集与去重模块
│   ├── validator.js             # URL 格式校验器（协议/大小写/尾部斜杠）
│   ├── formatter.js             # 输出格式化（表格、列表、目录树）
│   └── templates/               # 模板引擎目录
│       ├── html.template        # 静态 HTML 骨架模板
│       └── markdown.template    # 纯文本输出模板
├── data/                        # 数据存储目录
│   └── raw-links.txt            # 原始链接导入文件（用户可替换）
├── docs/                        # 项目文档
│   ├── quick-start.md           # 快速入门指南
│   ├── maintenance.md           # 日常维护流程
│   ├── architecture.md          # 架构设计决策记录
│   └── validation.md            # 校验规则详细说明
├── dist/                        # 构建输出目录（自动生成，不纳入版本控制）
│   ├── index.html               # 可浏览的静态页面
│   └── links.txt                # 纯文本链接清单
├── tests/                       # 单元测试目录
│   ├── validator.test.js        # 校验器测试用例
│   └── formatter.test.js        # 格式化器测试用例
├── .github/                     # GitHub 协作配置
│   └── PULL_REQUEST_TEMPLATE.md # PR 模板，引导贡献者填写变更说明
├── package.json                 # npm 项目配置文件
├── README.md                    # 本文件，项目入口文档
└── LICENSE                      # MIT 许可证文本
```

## 贡献指南

我们欢迎外部贡献者以审慎且规范的方式参与本项目的维护。所有贡献需遵循以下步骤：

1.  Fork 本仓库到个人账户下，并克隆到本地开发环境。确保本地 Git 配置了正确的用户名和邮箱。

2.  在 `data/raw-links.txt` 文件中追加或删除 URL 条目。每次修改必须保持每行一个 URL 的格式，且不允许出现空行或多余空格。修改完成后，运行 `npm run validate` 执行格式校验。

3.  针对本次变更编写清晰的提交信息。提交信息的格式建议为 `类型: 简短描述`，其中类型可以是 `add`（新增链接）、`remove`（删除链接）或 `fix`（修正格式错误）。例如：`add: 收录 15 篇 map.blog 技术文章`。

4.  将本地提交推送到你的远程仓库，然后通过 GitHub 界面发起 Pull Request。PR 标题应概括变更内容，正文需引用本次操作涉及的文章编号范围或具体 URL 条目数。

5.  等待维护者审核。审核过程中可能要求补充说明或调整链接顺序。合并后，你的贡献将出现在下一版的资源列表中。

## 常见问题

问：为什么不能将 http 自动升级为 https？
答：本项目的核心原则是“原样呈现”。源站 map.blog.zdvgjr.cn 的部分资源可能仅在 http 协议下可访问，强制升级为 https 会导致访问失败。我们尊重源站的设计选择，由用户浏览器或网络环境决定最终使用的协议。

问：链接数量太多，如何快速查找某个特定编号的文章？
答：你可以使用浏览器的页面内查找功能（Ctrl+F 或 Command+F）搜索数字编号。另外，项目构建时会生成一个按编号排序的索引文件，位于 `dist/links.txt`，该文件支持系统自带的文本搜索工具进行快速过滤。

问：如果源站删除了某篇文章，本项目会同步删除吗？
答：本项目是静态外链清单，不会自动同步源站内容状态。如果发现某个链接已失效，欢迎通过贡献指南中的流程提交 Pull Request，将该条目从列表中移除，并在提交信息中注明“失效链接删除”。

## 许可证

MIT

> 外链数量: 150 | 生成时间: 2026-07-10 17:52:39
