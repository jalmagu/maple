# Map Blog Article Aggregator

Map Blog Article Aggregator 是一个面向技术内容聚合与知识图谱构建的开源工具，专注于从 map.blog.zdvgjr.cn 域名下的文章资源中提取、整理和索引结构化数据。该项目为研究人员、内容策展人和技术文档编写者提供了一套轻量级的文章元数据采集与检索方案，能够将散落在大量 .shtml 页面中的信息转化为可查询、可关联的知识节点。

本项目不是一个通用的爬虫框架，而是一个针对特定数据源（map.blog.zdvgjr.cn）设计的专项解析器。它解决了从大量同类页面中手工提取信息效率低下、容易遗漏的问题，通过自动化的元数据抽取和本地索引构建，帮助用户快速定位感兴趣的文章主题、建立文章之间的引用关系网络，并支持导出为 JSON、CSV 或 Markdown 表格等通用格式，便于下游分析或静态站点生成。

## 功能概览

- 批量文章元数据抽取：自动解析 .shtml 页面中的标题、发布时间、正文摘要、标签分类及内部链接，输出标准化字段。

- 本地索引构建与去重：基于文章唯一标识（URL 末尾的数字编号）建立哈希索引，支持增量更新，避免重复处理。

- 关键词与标签云生成：统计高频词汇和标签分布，生成可视化的标签权重列表，辅助内容主题分析。

- 文章间引用关系图导出：识别页面内指向其他文章的超链接，生成边列表（edge list），可导入 Gephi 或 Graphviz 进行关系网络可视化。

- 多格式数据导出：支持将索引结果导出为 JSON Lines、CSV 表格或 Markdown 格式的目录清单，便于集成到静态站点或文档系统中。

- 定时任务与变更监控：内置简单的轮询调度器，可定期检查指定文章列表的更新状态，并输出变更报告。

- 查询过滤器与正则匹配：提供基于标题关键词、发布时间范围、标签组合的过滤查询接口，支持正则表达式模式匹配。

## 应用场景

内容策展与每周技术简报生成：编辑团队可使用本工具定期扫描 map.blog.zdvgjr.cn 下的最新文章，自动提取标题和摘要，生成每周技术简报的原始素材列表，减少手动复制粘贴的工作量。

技术文章知识图谱构建：研究人员可以将文章间的引用关系导出为图结构数据，结合其他数据源（如 GitHub 仓库、论文数据库）构建跨领域的知识图谱，分析技术主题的演进路径。

历史文章归档与全文检索：对于需要长期保存文章快照的团队，本工具可配合 wget 或 curl 下载页面源码，同时生成带时间戳的索引文件，实现基于元数据的快速检索，而不必依赖原始站点的搜索功能。

文档站自动导航生成：技术文档维护者可以将本工具输出的标签和分类数据，直接用于生成文档站的侧边栏导航或标签聚合页面，实现文档结构的自动更新。

## 快速开始

以下命令演示了从克隆仓库到完成首次文章索引的全过程。

```bash
# 克隆仓库
git clone https://github.com/your-org/map-blog-aggregator.git
cd map-blog-aggregator

# 安装依赖（使用 pip 和虚拟环境）
python3 -m venv venv
source venv/bin/activate  # Windows 下使用 venv\Scripts\activate
pip install -r requirements.txt

# 运行首次索引任务（示例：处理前 10 篇文章）
python cli.py index --source map.blog.zdvgjr.cn --limit 10 --output ./data/index.json

# 查看索引统计
python cli.py stats --input ./data/index.json
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.8 及以上 | 核心运行环境，建议使用 3.10 LTS |
| requests | 2.28.0 及以上 | HTTP 请求库，用于获取 .shtml 页面内容 |
| beautifulsoup4 | 4.11.0 及以上 | HTML 解析器，用于提取文章元数据 |
| lxml | 4.9.0 及以上 | 高性能 XML/HTML 解析后端，作为 beautifulsoup 的解析器 |
| redis | 5.0.0 及以上（可选） | 用于分布式去重和任务队列，非必需但推荐生产环境使用 |
| pytest | 7.2.0 及以上（开发依赖） | 单元测试框架，仅在开发模式下使用 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|-----|------|----------|
| 入门指南 | docs/getting-started.md | 如何安装、配置并运行第一次索引任务？如何理解输出文件的结构？ |
| 配置参考 | docs/configuration.md | 有哪些可用的命令行参数和环境变量？如何自定义请求头、超时时间和重试策略？ |
| 数据模型 | docs/data-model.md | 索引结果中的每个字段代表什么含义？文章唯一标识如何生成？标签和分类的规范化规则是什么？ |
| 高级主题 | docs/advanced/graph-export.md | 如何导出引用关系图？如何与 Gephi 或 Neo4j 集成？如何进行增量更新和变更检测？ |

## 资源列表

- http://map.blog.zdvgjr.cn/Article/7485.shtml
- http://map.blog.zdvgjr.cn/Article/06759.shtml
- http://map.blog.zdvgjr.cn/Article/533236.shtml
- http://map.blog.zdvgjr.cn/Article/7616.shtml
- http://map.blog.zdvgjr.cn/Article/56364.shtml
- http://map.blog.zdvgjr.cn/Article/501084.shtml
- http://map.blog.zdvgjr.cn/Article/6952437.shtml
- http://map.blog.zdvgjr.cn/Article/2932684.shtml
- http://map.blog.zdvgjr.cn/Article/457113.shtml
- http://map.blog.zdvgjr.cn/Article/9950322.shtml
- http://map.blog.zdvgjr.cn/Article/146581.shtml
- http://map.blog.zdvgjr.cn/Article/419962.shtml
- http://map.blog.zdvgjr.cn/Article/8098.shtml
- http://map.blog.zdvgjr.cn/Article/16321.shtml
- http://map.blog.zdvgjr.cn/Article/5987081.shtml
- http://map.blog.zdvgjr.cn/Article/8266140.shtml
- http://map.blog.zdvgjr.cn/Article/909301.shtml
- http://map.blog.zdvgjr.cn/Article/375195.shtml
- http://map.blog.zdvgjr.cn/Article/7656.shtml
- http://map.blog.zdvgjr.cn/Article/1268.shtml
- http://map.blog.zdvgjr.cn/Article/44158.shtml
- http://map.blog.zdvgjr.cn/Article/12606.shtml
- http://map.blog.zdvgjr.cn/Article/000429.shtml
- http://map.blog.zdvgjr.cn/Article/1615146.shtml
- http://map.blog.zdvgjr.cn/Article/8396.shtml
- http://map.blog.zdvgjr.cn/Article/77296.shtml
- http://map.blog.zdvgjr.cn/Article/507872.shtml
- http://map.blog.zdvgjr.cn/Article/3355.shtml
- http://map.blog.zdvgjr.cn/Article/48480.shtml
- http://map.blog.zdvgjr.cn/Article/14471.shtml
- http://map.blog.zdvgjr.cn/Article/9883.shtml
- http://map.blog.zdvgjr.cn/Article/0134.shtml
- http://map.blog.zdvgjr.cn/Article/5196243.shtml
- http://map.blog.zdvgjr.cn/Article/402839.shtml
- http://map.blog.zdvgjr.cn/Article/3235401.shtml
- http://map.blog.zdvgjr.cn/Article/1909.shtml
- http://map.blog.zdvgjr.cn/Article/7330147.shtml
- http://map.blog.zdvgjr.cn/Article/991663.shtml
- http://map.blog.zdvgjr.cn/Article/39672.shtml
- http://map.blog.zdvgjr.cn/Article/017712.shtml
- http://map.blog.zdvgjr.cn/Article/4402.shtml
- http://map.blog.zdvgjr.cn/Article/89769.shtml
- http://map.blog.zdvgjr.cn/Article/3226.shtml
- http://map.blog.zdvgjr.cn/Article/55181.shtml
- http://map.blog.zdvgjr.cn/Article/9428.shtml
- http://map.blog.zdvgjr.cn/Article/929053.shtml
- http://map.blog.zdvgjr.cn/Article/1161958.shtml
- http://map.blog.zdvgjr.cn/Article/6283334.shtml
- http://map.blog.zdvgjr.cn/Article/21069.shtml
- http://map.blog.zdvgjr.cn/Article/3521.shtml
- http://map.blog.zdvgjr.cn/Article/9706.shtml
- http://map.blog.zdvgjr.cn/Article/25199.shtml
- http://map.blog.zdvgjr.cn/Article/0999.shtml
- http://map.blog.zdvgjr.cn/Article/06442.shtml
- http://map.blog.zdvgjr.cn/Article/08276.shtml
- http://map.blog.zdvgjr.cn/Article/6562930.shtml
- http://map.blog.zdvgjr.cn/Article/4754342.shtml
- http://map.blog.zdvgjr.cn/Article/287018.shtml
- http://map.blog.zdvgjr.cn/Article/1460985.shtml
- http://map.blog.zdvgjr.cn/Article/3747.shtml
- http://map.blog.zdvgjr.cn/Article/5809.shtml
- http://map.blog.zdvgjr.cn/Article/7746822.shtml
- http://map.blog.zdvgjr.cn/Article/828031.shtml
- http://map.blog.zdvgjr.cn/Article/9302287.shtml
- http://map.blog.zdvgjr.cn/Article/12294.shtml
- http://map.blog.zdvgjr.cn/Article/553890.shtml
- http://map.blog.zdvgjr.cn/Article/7972.shtml
- http://map.blog.zdvgjr.cn/Article/1197.shtml
- http://map.blog.zdvgjr.cn/Article/30705.shtml
- http://map.blog.zdvgjr.cn/Article/45484.shtml
- http://map.blog.zdvgjr.cn/Article/39038.shtml
- http://map.blog.zdvgjr.cn/Article/157973.shtml
- http://map.blog.zdvgjr.cn/Article/2682652.shtml
- http://map.blog.zdvgjr.cn/Article/2475.shtml
- http://map.blog.zdvgjr.cn/Article/903861.shtml
- http://map.blog.zdvgjr.cn/Article/9001235.shtml
- http://map.blog.zdvgjr.cn/Article/2428733.shtml
- http://map.blog.zdvgjr.cn/Article/4437.shtml
- http://map.blog.zdvgjr.cn/Article/81133.shtml
- http://map.blog.zdvgjr.cn/Article/3060.shtml
- http://map.blog.zdvgjr.cn/Article/20767.shtml
- http://map.blog.zdvgjr.cn/Article/30246.shtml
- http://map.blog.zdvgjr.cn/Article/1354.shtml
- http://map.blog.zdvgjr.cn/Article/48709.shtml
- http://map.blog.zdvgjr.cn/Article/488725.shtml
- http://map.blog.zdvgjr.cn/Article/28252.shtml
- http://map.blog.zdvgjr.cn/Article/3445585.shtml
- http://map.blog.zdvgjr.cn/Article/86485.shtml
- http://map.blog.zdvgjr.cn/Article/5971252.shtml
- http://map.blog.zdvgjr.cn/Article/0538.shtml
- http://map.blog.zdvgjr.cn/Article/9460.shtml
- http://map.blog.zdvgjr.cn/Article/50301.shtml
- http://map.blog.zdvgjr.cn/Article/2086651.shtml
- http://map.blog.zdvgjr.cn/Article/71159.shtml
- http://map.blog.zdvgjr.cn/Article/24164.shtml
- http://map.blog.zdvgjr.cn/Article/2953.shtml
- http://map.blog.zdvgjr.cn/Article/7343432.shtml
- http://map.blog.zdvgjr.cn/Article/8321355.shtml
- http://map.blog.zdvgjr.cn/Article/96332.shtml
- http://map.blog.zdvgjr.cn/Article/902230.shtml
- http://map.blog.zdvgjr.cn/Article/362461.shtml
- http://map.blog.zdvgjr.cn/Article/2613647.shtml
- http://map.blog.zdvgjr.cn/Article/5372.shtml
- http://map.blog.zdvgjr.cn/Article/464237.shtml
- http://map.blog.zdvgjr.cn/Article/2216.shtml
- http://map.blog.zdvgjr.cn/Article/173027.shtml
- http://map.blog.zdvgjr.cn/Article/85891.shtml
- http://map.blog.zdvgjr.cn/Article/992243.shtml
- http://map.blog.zdvgjr.cn/Article/36296.shtml
- http://map.blog.zdvgjr.cn/Article/32202.shtml
- http://map.blog.zdvgjr.cn/Article/923789.shtml
- http://map.blog.zdvgjr.cn/Article/6968207.shtml
- http://map.blog.zdvgjr.cn/Article/500207.shtml
- http://map.blog.zdvgjr.cn/Article/8963.shtml
- http://map.blog.zdvgjr.cn/Article/253005.shtml
- http://map.blog.zdvgjr.cn/Article/88363.shtml
- http://map.blog.zdvgjr.cn/Article/0273378.shtml
- http://map.blog.zdvgjr.cn/Article/08076.shtml
- http://map.blog.zdvgjr.cn/Article/758928.shtml
- http://map.blog.zdvgjr.cn/Article/3816195.shtml
- http://map.blog.zdvgjr.cn/Article/50093.shtml
- http://map.blog.zdvgjr.cn/Article/293057.shtml
- http://map.blog.zdvgjr.cn/Article/200517.shtml
- http://map.blog.zdvgjr.cn/Article/345150.shtml
- http://map.blog.zdvgjr.cn/Article/2003.shtml
- http://map.blog.zdvgjr.cn/Article/0857.shtml
- http://map.blog.zdvgjr.cn/Article/5579.shtml
- http://map.blog.zdvgjr.cn/Article/309279.shtml
- http://map.blog.zdvgjr.cn/Article/9136.shtml
- http://map.blog.zdvgjr.cn/Article/2423955.shtml
- http://map.blog.zdvgjr.cn/Article/182464.shtml
- http://map.blog.zdvgjr.cn/Article/8354416.shtml
- http://map.blog.zdvgjr.cn/Article/8063.shtml
- http://map.blog.zdvgjr.cn/Article/6327.shtml
- http://map.blog.zdvgjr.cn/Article/7938205.shtml
- http://map.blog.zdvgjr.cn/Article/8622777.shtml
- http://map.blog.zdvgjr.cn/Article/814732.shtml
- http://map.blog.zdvgjr.cn/Article/94934.shtml
- http://map.blog.zdvgjr.cn/Article/6956973.shtml
- http://map.blog.zdvgjr.cn/Article/37017.shtml
- http://map.blog.zdvgjr.cn/Article/66279.shtml
- http://map.blog.zdvgjr.cn/Article/077573.shtml
- http://map.blog.zdvgjr.cn/Article/1547432.shtml
- http://map.blog.zdvgjr.cn/Article/966028.shtml
- http://map.blog.zdvgjr.cn/Article/72994.shtml
- http://map.blog.zdvgjr.cn/Article/13562.shtml
- http://map.blog.zdvgjr.cn/Article/594895.shtml
- http://map.blog.zdvgjr.cn/Article/36402.shtml
- http://map.blog.zdvgjr.cn/Article/4774.shtml
- http://map.blog.zdvgjr.cn/Article/1976.shtml

## 项目结构

```
map-blog-aggregator/
├── cli.py                     # 命令行入口，注册所有子命令（index, stats, export, watch）
├── requirements.txt           # 生产环境依赖列表，固定版本号
├── setup.py                   # 项目打包和发布配置，支持 pip install -e .
├── src/                       # 核心源码目录
│   ├── __init__.py            # 包初始化，暴露主要 API
│   ├── fetcher/               # 网络请求与页面获取模块
│   │   ├── __init__.py
│   │   ├── client.py          # 封装 requests.Session，支持重试和超时
│   │   └── parser.py          # 基于 beautifulsoup 的 .shtml 解析器
│   ├── indexer/               # 索引构建与去重核心
│   │   ├── __init__.py
│   │   ├── builder.py         # 主索引器，协调抓取、解析和存储
│   │   └── dedup.py           # 基于 SHA-256 的 URL 去重与增量判断
│   ├── models/                # 数据模型与序列化
│   │   ├── __init__.py
│   │   ├── article.py         # Article 数据类（url, title, pub_date, tags, refs）
│   │   └── index.py           # Index 容器类，支持合并和导出
│   ├── exporters/             # 多格式输出模块
│   │   ├── __init__.py
│   │   ├── json_exporter.py   # 导出为 JSON Lines 格式
│   │   ├── csv_exporter.py    # 导出为 CSV 表格，包含全部字段
│   │   └── markdown_exporter.py # 生成 Markdown 列表，用于文档展示
│   └── scheduler/             # 定时任务与变更监控
│       ├── __init__.py
│       └── watcher.py         # 轮询调度器，支持 cron 表达式
├── tests/                     # 单元测试与集成测试
│   ├── test_fetcher.py        # 模拟 HTTP 响应的解析测试
│   ├── test_indexer.py        # 去重和增量逻辑的测试用例
│   └── fixtures/              # 测试用的 .shtml 样例文件
├── docs/                      # 完整文档目录
│   ├── getting-started.md
│   ├── configuration.md
│   ├── data-model.md
│   └── advanced/
│       └── graph-export.md
├── data/                      # 运行时数据目录（自动创建）
│   ├── index.json             # 主索引文件
│   └── changelog.log          # 变更日志
└── .github/                   # CI/CD 配置
    └── workflows/
        └── test.yml           # GitHub Actions 自动化测试流程
```

## 贡献指南

1. 阅读项目行为准则（CODE_OF_CONDUCT.md）和贡献者许可协议（CLA），确认同意后 fork 本仓库。

2. 在本地开发环境中创建功能分支（如 feature/add-timeout-config），并编写对应的单元测试，确保新增代码的测试覆盖率达到 90% 以上。

3. 运行完整的测试套件（pytest tests/）和代码风格检查（flake8 和 black），确认所有检查通过后再提交。

4. 提交 pull request 时，请附上详细的变更说明、测试结果截图以及相关的 issue 编号（如果有）。PR 描述中需勾选是否进行了文档更新。

5. 项目维护者会在 3 个工作日内进行 review，可能需要你补充测试用例或调整接口设计，请保持关注并积极响应。

## 常见问题

Q: 索引过程中遇到 HTTP 403 或 429 错误，如何解决？

A: 这是由于目标站点启用了访问频率限制或反爬机制。请在命令行中添加 --delay 参数（单位为秒）来增大请求间隔，例如 python cli.py index --delay 3。同时，建议配置环境变量 HTTP_USER_AGENT 为常见的浏览器 UA 字符串。如果持续失败，可尝试使用 --proxy 参数指定代理服务器。

Q: 如何处理文章编号不一致导致的重复索引？

A: 本工具默认使用完整 URL 作为唯一键进行去重。如果同一篇文章通过不同编号路径访问（例如 /Article/123.shtml 和 /Article/00123.shtml），可以通过启用 --normalize-id 参数，将数字编号按 8 位补齐后再进行去重。注意该功能需要事先了解目标站点的编号规则，建议先在测试模式下验证。

Q: 导出的引用关系图数据非常庞大，如何简化？

A: 如果文章之间的引用链接过多，生成的边列表可能达到数万条。可以在 cli.py 的 export 子命令中添加 --min-ref-weight 参数，只保留出现频率高于指定阈值的引用关系。同时，建议配合 --max-depth 参数限制递归深度，仅导出直接引用而非全路径引用，以控制数据量。

## 许可证

MIT

> 外链数量: 150 | 生成时间: 2026-07-10 17:52:39
