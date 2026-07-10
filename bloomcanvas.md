# WebMap Blog Archive Indexer

WebMap Blog Archive Indexer 是一个面向技术博客与知识库的轻量级外链资源聚合系统。该项目定位于帮助技术研究者、运维工程师和开发人员快速检索、分类和引用分散在多个文章页面中的外部链接与参考资源。通过自动抓取目标博客站点的文章元数据与正文外链，生成结构化的资源索引，解决人工整理效率低、链接失效难追踪、上下文缺失等问题。

本项目适用于需要长期维护技术文献引用库、构建个人知识图谱或对特定博客站点进行内容审计的场景。项目以非侵入式方式运行，仅依赖目标站点公开可访问的 HTML 页面，不涉及任何数据写入或用户隐私采集。

## 功能概览

- **批量文章抓取**：支持按文章 ID 列表批量拉取指定博客站点的 HTML 页面，自动处理 HTTP 请求重定向与超时重试。

- **外链自动提取**：从每篇文章正文中解析出所有 `<a>` 标签的 href 属性，过滤站内导航、分页、评论等非内容链接，保留指向外部域名的引用链接。

- **链接状态检测**：对提取出的外链进行实时的 HTTP 状态码检查，标记 4xx/5xx 异常状态，生成链接健康度报告。

- **上下文片段保存**：每条外链记录其所在文章标题、段落上下文（前后各 50 个字符）以及出现位置，便于后续追溯引用意图。

- **多维度索引输出**：支持按文章 ID、目标域名、链接状态、提取时间四种维度生成 CSV / JSON / Markdown 三种格式的索引文件。

- **增量更新机制**：支持记录已处理文章的时间戳，下次运行时仅抓取新增或更新的文章，避免重复全量扫描。

- **配置化过滤规则**：允许用户通过 YAML 配置文件自定义域名黑名单、URL 正则过滤规则以及自定义 HTTP 请求头。

- **日志与监控**：输出结构化运行日志，记录每篇文章的处理耗时、提取链接数量、异常信息，便于运维审计。

## 应用场景

**技术文献归档与引用管理**：技术团队在撰写内部周报、技术方案或对外博客时，需要引用大量外部资料。使用本项目可以快速抓取指定博客站点的所有历史文章外链，构建可检索的引用库，避免手动收集遗漏。

**网站外链审计与 SEO 检查**：SEO 工程师或网站管理员需要定期检查站点的外部链接是否有效、是否存在被垃圾域名污染的情况。本项目可对目标博客站点的全部文章进行外链扫描，生成链接状态报表，定位失效链接和可疑域名。

**知识图谱关系构建**：知识管理研究者可以通过本项目提取博客文章中的引用网络，分析不同技术主题之间的关联强度，为后续构建概念图谱或推荐系统提供原始数据支撑。

**博客站点迁移前的资源盘点**：在更换博客系统或域名时，需要全面盘点现有文章中的外部资源引用情况，避免迁移后链接混乱。本项目可输出完整的引用清单，辅助迁移决策。

## 快速开始

```bash
# 克隆代码仓库
git clone https://github.com/webmap-labs/blog-archive-indexer.git
cd blog-archive-indexer

# 安装 Python 依赖（Python 3.9+ 环境）
pip install -r requirements.txt

# 配置目标站点与文章列表（编辑 config.yaml）
cp config.example.yaml config.yaml
vim config.yaml

# 运行索引任务
python main.py --config config.yaml --output ./output
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.9 - 3.11 | 核心运行环境，不支持 3.12 以下版本 |
| requests | 2.28.0+ | HTTP 请求库，用于页面抓取和状态检测 |
| beautifulsoup4 | 4.11.0+ | HTML 解析库，用于外链提取和上下文截取 |
| lxml | 4.9.0+ | 解析器后端，提升 beautifulsoup 性能 |
| pyyaml | 6.0+ | 配置文件解析，支持自定义过滤规则 |
| pandas | 1.5.0+ | 索引数据存储与多格式导出（CSV/JSON） |
| tqdm | 4.64.0+ | 进度条显示，用于批量任务可视化 |
| urllib3 | 1.26.0+ | 连接池管理，支持重试策略配置 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | docs/user-guide.md | 如何配置抓取参数、自定义过滤规则、输出格式选择 |
| 运维手册 | docs/ops-guide.md | 如何部署定时任务、监控运行日志、处理异常中断 |
| 开发指南 | docs/developer-guide.md | 如何扩展新的提取器、自定义输出格式、贡献代码规范 |
| API 参考 | docs/api-reference.md | 各模块类与方法签名、参数说明、异常类型定义 |
| 设计文档 | docs/design.md | 系统架构图、数据流说明、关键算法选型理由 |
| 变更日志 | CHANGELOG.md | 各版本新增功能、修复缺陷、破坏性变更说明 |

## 资源列表

- http://map.blog.zdvgjr.cn/Article/289071.shtml
- http://map.blog.zdvgjr.cn/Article/47666.shtml
- http://map.blog.zdvgjr.cn/Article/2727206.shtml
- http://map.blog.zdvgjr.cn/Article/60344.shtml
- http://map.blog.zdvgjr.cn/Article/566070.shtml
- http://map.blog.zdvgjr.cn/Article/5835994.shtml
- http://map.blog.zdvgjr.cn/Article/975765.shtml
- http://map.blog.zdvgjr.cn/Article/54839.shtml
- http://map.blog.zdvgjr.cn/Article/3283.shtml
- http://map.blog.zdvgjr.cn/Article/53603.shtml
- http://map.blog.zdvgjr.cn/Article/705852.shtml
- http://map.blog.zdvgjr.cn/Article/8789012.shtml
- http://map.blog.zdvgjr.cn/Article/004900.shtml
- http://map.blog.zdvgjr.cn/Article/178427.shtml
- http://map.blog.zdvgjr.cn/Article/2672.shtml
- http://map.blog.zdvgjr.cn/Article/91327.shtml
- http://map.blog.zdvgjr.cn/Article/90568.shtml
- http://map.blog.zdvgjr.cn/Article/43619.shtml
- http://map.blog.zdvgjr.cn/Article/7473.shtml
- http://map.blog.zdvgjr.cn/Article/6739781.shtml
- http://map.blog.zdvgjr.cn/Article/7043.shtml
- http://map.blog.zdvgjr.cn/Article/78353.shtml
- http://map.blog.zdvgjr.cn/Article/392165.shtml
- http://map.blog.zdvgjr.cn/Article/64250.shtml
- http://map.blog.zdvgjr.cn/Article/53444.shtml
- http://map.blog.zdvgjr.cn/Article/32769.shtml
- http://map.blog.zdvgjr.cn/Article/7683405.shtml
- http://map.blog.zdvgjr.cn/Article/0641.shtml
- http://map.blog.zdvgjr.cn/Article/21493.shtml
- http://map.blog.zdvgjr.cn/Article/3041613.shtml
- http://map.blog.zdvgjr.cn/Article/67360.shtml
- http://map.blog.zdvgjr.cn/Article/4480367.shtml
- http://map.blog.zdvgjr.cn/Article/285763.shtml
- http://map.blog.zdvgjr.cn/Article/3583763.shtml
- http://map.blog.zdvgjr.cn/Article/9362.shtml
- http://map.blog.zdvgjr.cn/Article/6931245.shtml
- http://map.blog.zdvgjr.cn/Article/08631.shtml
- http://map.blog.zdvgjr.cn/Article/049902.shtml
- http://map.blog.zdvgjr.cn/Article/8283373.shtml
- http://map.blog.zdvgjr.cn/Article/183937.shtml
- http://map.blog.zdvgjr.cn/Article/81971.shtml
- http://map.blog.zdvgjr.cn/Article/008885.shtml
- http://map.blog.zdvgjr.cn/Article/837973.shtml
- http://map.blog.zdvgjr.cn/Article/0177892.shtml
- http://map.blog.zdvgjr.cn/Article/73817.shtml
- http://map.blog.zdvgjr.cn/Article/1662820.shtml
- http://map.blog.zdvgjr.cn/Article/522416.shtml
- http://map.blog.zdvgjr.cn/Article/712264.shtml
- http://map.blog.zdvgjr.cn/Article/880214.shtml
- http://map.blog.zdvgjr.cn/Article/9789.shtml
- http://map.blog.zdvgjr.cn/Article/4121437.shtml
- http://map.blog.zdvgjr.cn/Article/2849.shtml
- http://map.blog.zdvgjr.cn/Article/9571.shtml
- http://map.blog.zdvgjr.cn/Article/01123.shtml
- http://map.blog.zdvgjr.cn/Article/5349074.shtml
- http://map.blog.zdvgjr.cn/Article/633194.shtml
- http://map.blog.zdvgjr.cn/Article/842932.shtml
- http://map.blog.zdvgjr.cn/Article/87798.shtml
- http://map.blog.zdvgjr.cn/Article/08501.shtml
- http://map.blog.zdvgjr.cn/Article/97713.shtml
- http://map.blog.zdvgjr.cn/Article/767239.shtml
- http://map.blog.zdvgjr.cn/Article/667770.shtml
- http://map.blog.zdvgjr.cn/Article/45167.shtml
- http://map.blog.zdvgjr.cn/Article/1454080.shtml
- http://map.blog.zdvgjr.cn/Article/765328.shtml
- http://map.blog.zdvgjr.cn/Article/4731.shtml
- http://map.blog.zdvgjr.cn/Article/4892368.shtml
- http://map.blog.zdvgjr.cn/Article/11576.shtml
- http://map.blog.zdvgjr.cn/Article/293141.shtml
- http://map.blog.zdvgjr.cn/Article/3285.shtml
- http://map.blog.zdvgjr.cn/Article/222768.shtml
- http://map.blog.zdvgjr.cn/Article/3128.shtml
- http://map.blog.zdvgjr.cn/Article/4251367.shtml
- http://map.blog.zdvgjr.cn/Article/468697.shtml
- http://map.blog.zdvgjr.cn/Article/563283.shtml
- http://map.blog.zdvgjr.cn/Article/4250691.shtml
- http://map.blog.zdvgjr.cn/Article/8545539.shtml
- http://map.blog.zdvgjr.cn/Article/22257.shtml
- http://map.blog.zdvgjr.cn/Article/9760.shtml
- http://map.blog.zdvgjr.cn/Article/1796875.shtml
- http://map.blog.zdvgjr.cn/Article/387311.shtml
- http://map.blog.zdvgjr.cn/Article/33153.shtml
- http://map.blog.zdvgjr.cn/Article/7449608.shtml
- http://map.blog.zdvgjr.cn/Article/574078.shtml
- http://map.blog.zdvgjr.cn/Article/4980.shtml
- http://map.blog.zdvgjr.cn/Article/1752.shtml
- http://map.blog.zdvgjr.cn/Article/41015.shtml
- http://map.blog.zdvgjr.cn/Article/022631.shtml
- http://map.blog.zdvgjr.cn/Article/135289.shtml
- http://map.blog.zdvgjr.cn/Article/3282392.shtml
- http://map.blog.zdvgjr.cn/Article/2062279.shtml
- http://map.blog.zdvgjr.cn/Article/2800950.shtml
- http://map.blog.zdvgjr.cn/Article/6522530.shtml
- http://map.blog.zdvgjr.cn/Article/80941.shtml
- http://map.blog.zdvgjr.cn/Article/6975.shtml
- http://map.blog.zdvgjr.cn/Article/6644.shtml
- http://map.blog.zdvgjr.cn/Article/7285711.shtml
- http://map.blog.zdvgjr.cn/Article/397891.shtml
- http://map.blog.zdvgjr.cn/Article/533828.shtml
- http://map.blog.zdvgjr.cn/Article/86247.shtml
- http://map.blog.zdvgjr.cn/Article/3440.shtml
- http://map.blog.zdvgjr.cn/Article/650136.shtml
- http://map.blog.zdvgjr.cn/Article/2467.shtml
- http://map.blog.zdvgjr.cn/Article/774261.shtml
- http://map.blog.zdvgjr.cn/Article/9114490.shtml
- http://map.blog.zdvgjr.cn/Article/366528.shtml
- http://map.blog.zdvgjr.cn/Article/1397574.shtml
- http://map.blog.zdvgjr.cn/Article/22583.shtml
- http://map.blog.zdvgjr.cn/Article/4469182.shtml
- http://map.blog.zdvgjr.cn/Article/1764.shtml
- http://map.blog.zdvgjr.cn/Article/7967095.shtml
- http://map.blog.zdvgjr.cn/Article/1355.shtml
- http://map.blog.zdvgjr.cn/Article/0352050.shtml
- http://map.blog.zdvgjr.cn/Article/7287932.shtml
- http://map.blog.zdvgjr.cn/Article/5769.shtml
- http://map.blog.zdvgjr.cn/Article/326039.shtml
- http://map.blog.zdvgjr.cn/Article/4545116.shtml
- http://map.blog.zdvgjr.cn/Article/19676.shtml
- http://map.blog.zdvgjr.cn/Article/94582.shtml
- http://map.blog.zdvgjr.cn/Article/4133061.shtml
- http://map.blog.zdvgjr.cn/Article/5242.shtml
- http://map.blog.zdvgjr.cn/Article/55094.shtml
- http://map.blog.zdvgjr.cn/Article/4622.shtml
- http://map.blog.zdvgjr.cn/Article/8541909.shtml
- http://map.blog.zdvgjr.cn/Article/2015.shtml
- http://map.blog.zdvgjr.cn/Article/43029.shtml
- http://map.blog.zdvgjr.cn/Article/8757.shtml
- http://map.blog.zdvgjr.cn/Article/9295.shtml
- http://map.blog.zdvgjr.cn/Article/485275.shtml
- http://map.blog.zdvgjr.cn/Article/310150.shtml
- http://map.blog.zdvgjr.cn/Article/158225.shtml
- http://map.blog.zdvgjr.cn/Article/0538098.shtml
- http://map.blog.zdvgjr.cn/Article/8827.shtml
- http://map.blog.zdvgjr.cn/Article/983092.shtml
- http://map.blog.zdvgjr.cn/Article/7013.shtml
- http://map.blog.zdvgjr.cn/Article/5869.shtml
- http://map.blog.zdvgjr.cn/Article/9297.shtml
- http://map.blog.zdvgjr.cn/Article/20140.shtml
- http://map.blog.zdvgjr.cn/Article/9926.shtml
- http://map.blog.zdvgjr.cn/Article/5973.shtml
- http://map.blog.zdvgjr.cn/Article/0027.shtml
- http://map.blog.zdvgjr.cn/Article/252455.shtml
- http://map.blog.zdvgjr.cn/Article/6781.shtml
- http://map.blog.zdvgjr.cn/Article/222229.shtml
- http://map.blog.zdvgjr.cn/Article/4493250.shtml
- http://map.blog.zdvgjr.cn/Article/644566.shtml
- http://map.blog.zdvgjr.cn/Article/4382.shtml
- http://map.blog.zdvgjr.cn/Article/4987.shtml
- http://map.blog.zdvgjr.cn/Article/9454.shtml
- http://map.blog.zdvgjr.cn/Article/5965237.shtml

## 项目结构

```
blog-archive-indexer/
├── main.py                          # 程序入口，解析命令行参数并调度主流程
├── config.yaml                      # 用户配置文件（需自行创建，包含目标站点与过滤规则）
├── config.example.yaml              # 配置模板，含完整注释与默认值
├── requirements.txt                 # Python 依赖清单
├── CHANGELOG.md                     # 版本变更记录
├── LICENSE                          # MIT 许可证文本
│
├── core/                            # 核心业务逻辑模块
│   ├── __init__.py
│   ├── fetcher.py                   # HTTP 请求封装，含重试、超时、会话管理
│   ├── parser.py                    # HTML 解析器，提取正文外链与上下文
│   ├── inspector.py                 # 链接状态检测器，并发检查 HTTP 状态码
│   └── indexer.py                   # 索引生成器，聚合数据并输出多格式文件
│
├── models/                          # 数据模型与类型定义
│   ├── __init__.py
│   ├── article.py                   # Article 类，表示单篇文章元数据
│   ├── link.py                      # Link 类，表示单个外链及检测结果
│   └── result.py                    # Result 类，表示一次完整任务的汇总数据
│
├── utils/                           # 工具函数集合
│   ├── __init__.py
│   ├── logger.py                    # 日志模块，支持文件与控制台双输出
│   ├── config_loader.py             # YAML 配置加载与校验
│   └── file_writer.py               # CSV/JSON/Markdown 文件写入辅助
│
├── filters/                         # 可扩展的过滤规则实现
│   ├── __init__.py
│   ├── domain_filter.py             # 域名黑名单/白名单过滤
│   └── regex_filter.py              # 基于正则表达式的 URL 过滤
│
├── tests/                           # 单元测试与集成测试
│   ├── test_fetcher.py
│   ├── test_parser.py
│   └── test_inspector.py
│
└── output/                          # 默认输出目录（由程序自动创建）
    ├── summary.json                 # 完整索引数据（JSON 格式）
    ├── links.csv                    # 外链清单（CSV 格式，按状态排序）
    └── report.md                    # 人工可读的 Markdown 摘要报告
```

## 贡献指南

1. 阅读设计文档 docs/design.md 了解系统架构与数据流，确认您的改动方向与项目定位一致。建议先在 GitHub Issues 中提出改进建议或报告缺陷，避免重复劳动。

2. 从 main 分支新建功能分支，命名规范为 feature/功能简述 或 fix/问题简述。提交代码前请运行现有单元测试，确保未破坏既有功能。若新增功能，需在 tests/ 目录下补充对应的测试用例。

3. 代码风格遵循 PEP 8 规范，使用 4 空格缩进，行宽不超过 120 字符。提交信息格式采用 Conventional Commits 规范，即 type(scope): subject 的形式，例如 feat(parser): 增加对图片链接的提取支持。

4. 提交 Pull Request 至 main 分支，描述中需明确说明改动目的、实现方式以及是否影响现有配置或输出格式。PR 需要至少一位维护者审阅通过后方可合并。

5. 若涉及新增外部依赖，需在 requirements.txt 中添加并注明版本范围，同时在文档中说明新增依赖的用途与替代方案。

## 常见问题

**问：程序运行时提示 "Too many redirects"，该如何处理？**

答：目标站点的某些文章页面可能设置了循环重定向或过深的跳转链。解决方案有两种：其一，在 config.yaml 中将 max_redirects 参数调整为 5 或更小值，并观察是否影响正常页面访问；其二，在 fetcher.py 中启用 allow_redirects=False 选项，程序将仅获取第一次响应的状态码，不再跟随重定向。建议先通过浏览器访问对应文章 URL，确认目标页面实际可访问后再调整配置。

**问：提取出的外链数量远少于预期，可能是什么原因？**

答：首先检查目标站点的文章页面是否使用了动态加载（AJAX 渲染），本项目的 parser 模块仅解析初始 HTML 内容，不执行 JavaScript。若文章正文依赖前端异步加载，则无法提取完整外链。其次，检查 config.yaml 中的 domain_whitelist 或 url_regex_include 过滤规则，确认没有误将目标外链排除。最后，可开启调试日志（log_level: DEBUG）查看每条链接被丢弃的具体原因，通常记录在运行日志的 WARNING 级别中。

**问：如何增量更新已有索引，避免重复抓取已处理文章？**

答：程序默认在 output/ 目录下维护一个 .state 文件，记录每次成功处理文章的 ID 与最后抓取时间戳。再次运行时，会读取该文件并与本次待处理列表比对，自动跳过已在有效时间窗口内（默认 24 小时）处理过的文章。若需强制全量刷新，可在命令行添加 --force 参数。增量更新的时间窗口可在 config.yaml 的 update_window_hours 字段中调整。

## 许可证

MIT

> 外链数量: 150 | 生成时间: 2026-07-10 17:52:39
