# WebLink Archive Gateway

WebLink Archive Gateway 是一个面向技术研究与知识管理场景的轻量级外链归档与导航系统。该项目定位于帮助开发者、技术博主、数据分析师以及信息整理人员，对分散在各类内容平台上的优质外部链接进行统一采集、分类存储与快速检索。与通用的书签管理工具不同，WebLink Archive Gateway 专注于处理来自移动端内容源的结构化链接数据，提供基于元数据的过滤、去重与批量导出能力，适用于构建私有化知识库的底层链接管道。

该项目不提供全文爬取或内容解析功能，而是作为链接的可靠存储与索引层，保留原始来源信息、采集时间、内容摘要标签等关键字段。用户可以通过命令行接口或简单的 HTTP API 对链接进行增删改查操作，并支持将链接列表导出为 Markdown、JSON 或 CSV 格式，便于集成到静态站点生成器、文档系统或数据分析流水线中。WebLink Archive Gateway 适用于需要长期维护外部资源清单的团队或个人，尤其适合处理批次量大、来源域名集中的链接集合。

## 功能概览

批量链接导入：支持从纯文本文件、CSV 或标准输入流中一次性导入大量 URL，自动解析并提取域名、路径、查询参数等结构化信息。

元数据自动补全：对导入的链接进行基础元数据提取，包括来源域名、文件扩展名类型、路径层级深度，并支持通过正则表达式规则自动打标。

去重与冲突检测：基于 URL 完整路径与域名组合进行去重，当导入重复链接时输出冲突报告，允许用户选择覆盖或跳过。

灵活检索过滤：提供按域名前缀、路径关键词、导入批次号、时间范围等多维度过滤查询，支持组合条件与正则匹配。

多格式导出：内置导出模板引擎，支持将链接列表渲染为 Markdown 列表、JSON 数组、CSV 表格以及 HTML 无序列表，适配不同下游工具。

批次管理：每个导入批次自动生成唯一批次编号，记录导入时间与链接数量，支持按批次整体删除或导出，方便分批处理大规模链接集合。

状态标记与备注：每条链接支持自定义状态标记（如未读、已读、待整理、已归档）和文本备注字段，便于工作流状态跟踪。

命令行交互与脚本集成：提供完整的命令行界面，所有操作均支持非交互模式，可通过 Shell 脚本或 CI/CD 工具链调用。

## 应用场景

技术博客外链整理：技术博主在撰写文章时，需要引用大量外部参考资料。WebLink Archive Gateway 可用于临时收集散落在浏览器书签、移动端阅读列表中的链接，通过统一导入后按主题筛选，快速生成文章末尾的参考链接列表。

数据分析素材归档：数据分析师在开展行业研究时，经常从各类资讯平台采集报道链接。本项目支持按批次导入并添加分析主题标签，后续可基于标签快速导出特定主题的链接清单，用于构建数据集说明文档。

团队知识库链接底座：技术团队在维护内部 Wiki 或文档中心时，需要定期汇总团队成员推荐的外部学习资源。WebLink Archive Gateway 可作为链接收集中台，提供统一的去重与审核入口，审核通过后的链接可直接导出为 Markdown 格式嵌入文档页面。

个人阅读清单管理：开发者日常通过移动设备浏览技术文章，积累大量待读链接。利用本项目的命令行工具，可定期将移动端导出的链接批量导入，并按阅读状态筛选，优先处理高优先级未读内容。

## 快速开始

以下命令演示了从克隆代码到运行服务的完整流程，默认使用 SQLite 作为存储后端，无需额外配置即可启动。

```bash
git clone https://github.com/weblink-archive/gateway.git
cd gateway
pip install -r requirements.txt
cp .env.example .env
python scripts/init_db.py
python cli.py serve --host 127.0.0.1 --port 8080
```

启动成功后，可通过命令行导入链接文件：

```bash
python cli.py import --batch batch_20260710 --file ./links.txt
```

导出指定批次为 Markdown 列表：

```bash
python cli.py export --batch batch_20260710 --format markdown --output ./export.md
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
| :--- | :--- | :--- |
| Python | 3.9 及以上 | 核心运行环境，类型注解依赖 3.9+ 特性 |
| SQLite | 3.35 及以上 | 默认内置数据库，支持 JSON 扩展函数 |
| pip | 21.0 及以上 | Python 包依赖管理工具 |
| virtualenv 或 venv | 任意版本 | 推荐使用虚拟环境隔离项目依赖 |
| readline | 系统自带 | 命令行交互历史记录支持，Linux/macOS 通常预装 |
| tzdata | 2022.0 及以上 | 时区解析库，用于准确记录导入时间戳 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
| :--- | :--- | :--- |
| 用户手册 | docs/user/import.md | 如何导入第一批链接，支持哪些文件格式，批次号如何生成。 |
| 用户手册 | docs/user/query.md | 如何进行多条件过滤，正则表达式如何使用，查询结果如何排序。 |
| 用户手册 | docs/user/export.md | 导出模板如何配置，不同格式的区别，如何自定义 Markdown 渲染风格。 |
| 运维指南 | docs/ops/deployment.md | 如何部署到生产环境，SQLite 并发调优，日志配置与轮转策略。 |
| 开发者文档 | docs/dev/api.md | HTTP API 的端点列表，请求响应格式，认证与限流机制。 |
| 开发者文档 | docs/dev/plugin.md | 如何编写自定义元数据提取插件，插件加载顺序与优先级规则。 |

## 资源列表

- http://m.blog.zdvgjr.cn/Article/232260.shtml
- http://m.blog.zdvgjr.cn/Article/298123.shtml
- http://m.blog.zdvgjr.cn/Article/5906485.shtml
- http://m.blog.zdvgjr.cn/Article/586439.shtml
- http://m.blog.zdvgjr.cn/Article/125605.shtml
- http://m.blog.zdvgjr.cn/Article/04361.shtml
- http://m.blog.zdvgjr.cn/Article/8343.shtml
- http://m.blog.zdvgjr.cn/Article/9651690.shtml
- http://m.blog.zdvgjr.cn/Article/112236.shtml
- http://m.blog.zdvgjr.cn/Article/8382.shtml
- http://m.blog.zdvgjr.cn/Article/2826805.shtml
- http://m.blog.zdvgjr.cn/Article/9491121.shtml
- http://m.blog.zdvgjr.cn/Article/9966117.shtml
- http://m.blog.zdvgjr.cn/Article/7901.shtml
- http://m.blog.zdvgjr.cn/Article/2457709.shtml
- http://m.blog.zdvgjr.cn/Article/1048951.shtml
- http://m.blog.zdvgjr.cn/Article/277967.shtml
- http://m.blog.zdvgjr.cn/Article/95006.shtml
- http://m.blog.zdvgjr.cn/Article/566967.shtml
- http://m.blog.zdvgjr.cn/Article/78651.shtml
- http://m.blog.zdvgjr.cn/Article/3492330.shtml
- http://m.blog.zdvgjr.cn/Article/1675639.shtml
- http://m.blog.zdvgjr.cn/Article/547089.shtml
- http://m.blog.zdvgjr.cn/Article/3534701.shtml
- http://m.blog.zdvgjr.cn/Article/34278.shtml
- http://m.blog.zdvgjr.cn/Article/8265.shtml
- http://m.blog.zdvgjr.cn/Article/459470.shtml
- http://m.blog.zdvgjr.cn/Article/3590627.shtml
- http://m.blog.zdvgjr.cn/Article/927106.shtml
- http://m.blog.zdvgjr.cn/Article/1966167.shtml
- http://m.blog.zdvgjr.cn/Article/726386.shtml
- http://m.blog.zdvgjr.cn/Article/86617.shtml
- http://m.blog.zdvgjr.cn/Article/390318.shtml
- http://m.blog.zdvgjr.cn/Article/749865.shtml
- http://m.blog.zdvgjr.cn/Article/972251.shtml
- http://m.blog.zdvgjr.cn/Article/720448.shtml
- http://m.blog.zdvgjr.cn/Article/901305.shtml
- http://m.blog.zdvgjr.cn/Article/7848.shtml
- http://m.blog.zdvgjr.cn/Article/788865.shtml
- http://m.blog.zdvgjr.cn/Article/983822.shtml
- http://m.blog.zdvgjr.cn/Article/6431475.shtml
- http://m.blog.zdvgjr.cn/Article/9816.shtml
- http://m.blog.zdvgjr.cn/Article/6480596.shtml
- http://m.blog.zdvgjr.cn/Article/1625219.shtml
- http://m.blog.zdvgjr.cn/Article/289049.shtml
- http://m.blog.zdvgjr.cn/Article/99909.shtml
- http://m.blog.zdvgjr.cn/Article/232762.shtml
- http://m.blog.zdvgjr.cn/Article/1262.shtml
- http://m.blog.zdvgjr.cn/Article/5096.shtml
- http://m.blog.zdvgjr.cn/Article/4573679.shtml
- http://m.blog.zdvgjr.cn/Article/25329.shtml
- http://m.blog.zdvgjr.cn/Article/645031.shtml
- http://m.blog.zdvgjr.cn/Article/4802.shtml
- http://m.blog.zdvgjr.cn/Article/186256.shtml
- http://m.blog.zdvgjr.cn/Article/33397.shtml
- http://m.blog.zdvgjr.cn/Article/0791.shtml
- http://m.blog.zdvgjr.cn/Article/6307.shtml
- http://m.blog.zdvgjr.cn/Article/8980503.shtml
- http://m.blog.zdvgjr.cn/Article/19763.shtml
- http://m.blog.zdvgjr.cn/Article/95144.shtml
- http://m.blog.zdvgjr.cn/Article/958191.shtml
- http://m.blog.zdvgjr.cn/Article/98098.shtml
- http://m.blog.zdvgjr.cn/Article/6001142.shtml
- http://m.blog.zdvgjr.cn/Article/991715.shtml
- http://m.blog.zdvgjr.cn/Article/896575.shtml
- http://m.blog.zdvgjr.cn/Article/8177190.shtml
- http://m.blog.zdvgjr.cn/Article/0745384.shtml
- http://m.blog.zdvgjr.cn/Article/7250.shtml
- http://m.blog.zdvgjr.cn/Article/342589.shtml
- http://m.blog.zdvgjr.cn/Article/45321.shtml
- http://m.blog.zdvgjr.cn/Article/48308.shtml
- http://m.blog.zdvgjr.cn/Article/914626.shtml
- http://m.blog.zdvgjr.cn/Article/7422278.shtml
- http://m.blog.zdvgjr.cn/Article/03642.shtml
- http://m.blog.zdvgjr.cn/Article/4900195.shtml
- http://m.blog.zdvgjr.cn/Article/1974976.shtml
- http://m.blog.zdvgjr.cn/Article/55588.shtml
- http://m.blog.zdvgjr.cn/Article/41791.shtml
- http://m.blog.zdvgjr.cn/Article/0075679.shtml
- http://m.blog.zdvgjr.cn/Article/5998.shtml
- http://m.blog.zdvgjr.cn/Article/59890.shtml
- http://m.blog.zdvgjr.cn/Article/6909556.shtml
- http://m.blog.zdvgjr.cn/Article/8691.shtml
- http://m.blog.zdvgjr.cn/Article/80420.shtml
- http://m.blog.zdvgjr.cn/Article/43775.shtml
- http://m.blog.zdvgjr.cn/Article/261562.shtml
- http://m.blog.zdvgjr.cn/Article/129192.shtml
- http://m.blog.zdvgjr.cn/Article/896717.shtml
- http://m.blog.zdvgjr.cn/Article/6957738.shtml
- http://m.blog.zdvgjr.cn/Article/058756.shtml
- http://m.blog.zdvgjr.cn/Article/0218.shtml
- http://m.blog.zdvgjr.cn/Article/92516.shtml
- http://m.blog.zdvgjr.cn/Article/579050.shtml
- http://m.blog.zdvgjr.cn/Article/0574.shtml
- http://m.blog.zdvgjr.cn/Article/3048.shtml
- http://m.blog.zdvgjr.cn/Article/0705.shtml
- http://m.blog.zdvgjr.cn/Article/9586.shtml
- http://m.blog.zdvgjr.cn/Article/9926278.shtml
- http://m.blog.zdvgjr.cn/Article/1342439.shtml
- http://m.blog.zdvgjr.cn/Article/14183.shtml
- http://m.blog.zdvgjr.cn/Article/4396074.shtml
- http://m.blog.zdvgjr.cn/Article/229472.shtml
- http://m.blog.zdvgjr.cn/Article/4525.shtml
- http://m.blog.zdvgjr.cn/Article/016341.shtml
- http://m.blog.zdvgjr.cn/Article/93112.shtml
- http://m.blog.zdvgjr.cn/Article/4312.shtml
- http://m.blog.zdvgjr.cn/Article/21007.shtml
- http://m.blog.zdvgjr.cn/Article/9328.shtml
- http://m.blog.zdvgjr.cn/Article/66431.shtml
- http://m.blog.zdvgjr.cn/Article/428844.shtml
- http://m.blog.zdvgjr.cn/Article/7533350.shtml
- http://m.blog.zdvgjr.cn/Article/98404.shtml
- http://m.blog.zdvgjr.cn/Article/43323.shtml
- http://m.blog.zdvgjr.cn/Article/480368.shtml
- http://m.blog.zdvgjr.cn/Article/98520.shtml
- http://m.blog.zdvgjr.cn/Article/471033.shtml
- http://m.blog.zdvgjr.cn/Article/0079623.shtml
- http://m.blog.zdvgjr.cn/Article/3053.shtml
- http://m.blog.zdvgjr.cn/Article/1250.shtml
- http://m.blog.zdvgjr.cn/Article/2725714.shtml
- http://m.blog.zdvgjr.cn/Article/2257141.shtml
- http://m.blog.zdvgjr.cn/Article/10800.shtml
- http://m.blog.zdvgjr.cn/Article/7437457.shtml
- http://m.blog.zdvgjr.cn/Article/617509.shtml
- http://m.blog.zdvgjr.cn/Article/0275311.shtml
- http://m.blog.zdvgjr.cn/Article/83105.shtml
- http://m.blog.zdvgjr.cn/Article/12872.shtml
- http://m.blog.zdvgjr.cn/Article/3287093.shtml
- http://m.blog.zdvgjr.cn/Article/2873479.shtml
- http://m.blog.zdvgjr.cn/Article/9455.shtml
- http://m.blog.zdvgjr.cn/Article/5555810.shtml
- http://m.blog.zdvgjr.cn/Article/6884834.shtml
- http://m.blog.zdvgjr.cn/Article/0670368.shtml
- http://m.blog.zdvgjr.cn/Article/82923.shtml
- http://m.blog.zdvgjr.cn/Article/8538.shtml
- http://m.blog.zdvgjr.cn/Article/8305801.shtml
- http://m.blog.zdvgjr.cn/Article/6549910.shtml
- http://m.blog.zdvgjr.cn/Article/15170.shtml
- http://m.blog.zdvgjr.cn/Article/77041.shtml
- http://m.blog.zdvgjr.cn/Article/4170.shtml
- http://m.blog.zdvgjr.cn/Article/8194.shtml
- http://m.blog.zdvgjr.cn/Article/5608770.shtml
- http://m.blog.zdvgjr.cn/Article/384629.shtml
- http://m.blog.zdvgjr.cn/Article/9756.shtml
- http://m.blog.zdvgjr.cn/Article/361622.shtml
- http://m.blog.zdvgjr.cn/Article/2237767.shtml
- http://m.blog.zdvgjr.cn/Article/550152.shtml
- http://m.blog.zdvgjr.cn/Article/73567.shtml
- http://m.blog.zdvgjr.cn/Article/20418.shtml
- http://m.blog.zdvgjr.cn/Article/933101.shtml

## 项目结构

```
gateway/
├── cli.py                      # 命令行入口，注册所有子命令（import/export/query/serve）
├── requirements.txt            # Python 依赖列表（FastAPI, click, sqlite-utils, pytz）
├── .env.example                # 环境变量模板（数据库路径、日志级别、导出模板目录）
├── scripts/
│   ├── init_db.py              # 初始化 SQLite 数据库表结构（links, batches, tags）
│   └── migrate_v1_to_v2.py     # 数据库迁移脚本（增加备注字段与状态列）
├── src/
│   ├── core/                   # 核心业务逻辑层
│   │   ├── importer.py         # 链接导入器，支持 txt/csv 解析与去重
│   │   ├── exporter.py         # 导出引擎，注册 markdown/json/csv/html 渲染器
│   │   └── query_builder.py    # SQL 查询构造器，处理多条件组合与正则过滤
│   ├── storage/                # 存储适配层
│   │   ├── sqlite_store.py     # SQLite 具体实现，包含连接池与事务管理
│   │   └── schema.py           # 表结构定义与索引创建语句
│   ├── parser/                 # URL 解析与元数据提取
│   │   ├── url_parser.py       # 基于 urllib.parse 的域名、路径、参数提取
│   │   └── tag_rules.py        # 正则规则引擎，根据路径关键词自动打标签
│   ├── server/                 # HTTP 服务模块
│   │   ├── app.py              # FastAPI 应用实例与路由注册
│   │   └── middlewares.py      # 请求日志、异常处理、CORS 中间件
│   └── utils/                  # 通用工具函数
│       ├── logger.py           # 日志配置（按天轮转，保留 30 天）
│       └── validator.py        # URL 合法性校验（协议、长度、非法字符）
├── tests/                      # 单元测试与集成测试
│   ├── test_importer.py        # 导入器测试用例（覆盖去重、批次生成）
│   └── test_exporter.py        # 导出格式正确性测试（对比预期模板输出）
├── docs/                       # 文档源码（用户手册与运维指南）
│   ├── user/                   # 面向终端用户的操作文档
│   └── ops/                    # 面向运维人员的部署与调优文档
└── exports/                    # 默认导出文件存储目录（可被 .env 覆盖）
```

## 贡献指南

1. 在 GitHub 仓库页面点击 Fork 按钮，将项目复制到个人账户下，然后克隆到本地开发环境。建议使用 Python 3.10 及以上版本进行开发，并创建独立的虚拟环境。

2. 安装开发依赖包，包括 pytest、black、flake8 和 mypy。运行 `make install-dev` 可一键安装所有开发工具。新增功能前，请先查阅 docs/dev/ 下的设计文档，了解模块划分与接口约定。

3. 代码提交前执行 `make lint` 和 `make test` 确保代码风格符合 PEP 8 规范且所有测试用例通过。新增功能需同步补充对应的单元测试，测试覆盖率不低于 85%。

4. 提交 Pull Request 时，请按照模板填写变更说明，明确描述改动动机、影响范围以及是否包含数据库迁移脚本。如果新增配置项，需同步更新 .env.example 文件。

5. 重大功能变更或架构调整前，建议先创建 Discussion 议题与维护者沟通方案，避免重复开发或设计偏离项目定位。

## 常见问题

Q: 导入链接时提示 "URL format invalid"，但链接在浏览器中可以正常打开。

A: 本项目默认只接受 http 和 https 协议，且会校验 URL 长度不超过 2048 字符。如果链接包含非 ASCII 字符或未编码的空格，请先进行百分号编码。可以使用 --strict 参数关闭部分校验，但不建议在生产环境关闭。

Q: 去重检测是否区分查询参数？例如同一路径不同 query 是否算重复。

A: 默认去重策略基于完整 URL（包含协议、主机、路径和查询参数）进行精确匹配。如果需要忽略查询参数进行去重，可以在导入时启用 --ignore-query 标志，此时仅比较协议+主机+路径部分。

Q: 导出为 Markdown 时，能否自定义列表的缩进或额外前缀符号？

A: 支持通过 --template 参数指定自定义 Jinja2 模板文件。项目内置的 Markdown 模板位于 src/export/templates/markdown.j2，用户可以复制该文件到自定义目录后修改列表渲染逻辑，然后通过 --template-dir 指向该目录。

## 许可证

MIT

> 外链数量: 150 | 生成时间: 2026-07-10 17:52:39
