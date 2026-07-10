# WebArchive Navigator

WebArchive Navigator 是一个面向技术研究人员、历史数据分析师和数字档案爱好者的结构化外链资源聚合系统。该项目专注于对分散在网络各处的历史文章、技术快照和事件记录进行系统性梳理与索引，通过统一的条目映射机制，将大量原始材料组织为可检索、可追溯的知识库。项目本身不存储任何实体内容，仅提供指向原始来源的稳定导航路径，适用于需要长期跟踪特定域名下内容演变的场景。

目标用户包括从事网络考古的独立研究员、需要回溯技术决策背景的软件工程师、以及对特定领域事件进行纵向对比分析的数据工作者。WebArchive Navigator 通过标准化的条目编号体系和分类索引规则，帮助用户从海量散落链接中快速定位目标区间，显著降低人工翻阅和手工整理的时间成本。

## 功能概览

- 自动化条目索引：根据链接内部编号自动提取关键元数据，生成可排序的索引列表。
- 分类标签推断：依据路径结构和文件名模式，为每个条目附加初步的类型标签。
- 批量校验机制：支持对已收录链接进行可用性批量检查，标记异常条目。
- 区间检索能力：用户可按编号范围、日期模式或自定义关键词筛选特定子集。
- 导出与集成：索引结果可导出为 JSON、CSV 或纯文本格式，便于导入其他分析工具。
- 增量更新支持：新增链接可通过配置文件追加，无需重建全量索引。
- 本地缓存记录：对访问过的条目保留基础响应头信息，辅助判断内容变更历史。

## 应用场景

技术事件回溯分析
当需要对某一时间段内发布的技术文章或事件记录进行集中查阅时，可通过编号范围快速锁定候选条目，按时间顺序逐个访问原始页面，适用于版本发布记录追踪或安全公告梳理。

历史内容结构演化研究
针对同一域名下的长期内容积累，可提取不同编号段的条目分布密度，分析该站点的内容产出节奏和主题偏移趋势，为网络内容生命周期研究提供数据支撑。

自动化监测任务前置筛选
在搭建自定义监控机器人之前，可利用本项目的索引数据作为初始种子列表，过滤出符合特定路径或编号规则的目标链接，减少无效抓取。

离线文档整理辅助
对于需要将分散页面整合为离线文档集的场景，可先通过本项目导出所有目标链接的清单，再配合第三方下载工具进行批量保存，保证整理过程的完整性。

## 快速开始

以下命令可在本地环境中完成项目的克隆、依赖安装和基础索引服务的启动。

```bash
git clone https://github.com/webarchive-navigator/webarchive-navigator.git
cd webarchive-navigator
pip install -r requirements.txt
python build_index.py --input ./data/urls.txt --output ./output/index.json
python serve.py --port 8080 --index ./output/index.json
```

如需自定义链接数据源，可替换 `./data/urls.txt` 文件内容，每行一个原始链接，格式需与已有条目保持一致。项目默认监听 8080 端口，启动后可通过 `http://localhost:8080` 访问本地索引查询界面。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.8 及以上 | 核心运行环境，用于索引构建和本地服务 |
| pip | 20.0 及以上 | Python 包管理工具，用于安装依赖库 |
| requests | 2.25.0 及以上 | 用于链接可用性校验和响应头提取 |
| click | 8.0.0 及以上 | 命令行交互框架，提供子命令解析能力 |
| jsonschema | 4.0.0 及以上 | 校验配置文件和导出数据的结构合法性 |
| pytest | 7.0.0 及以上 | 可选依赖，用于运行项目自测套件 |
| flask | 2.0.0 及以上 | 可选依赖，用于启动本地 Web 查询界面 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user_guide.md | 如何添加链接、执行批量校验、导出索引结果 |
| 配置参考 | docs/configuration.md | 每个配置项的含义、默认值和可选范围 |
| 开发者指南 | docs/developer_guide.md | 索引构建流程、插件扩展接口和测试规范 |
| 常见问题 | docs/faq.md | 处理校验超时、编号冲突、编码异常的解决方案 |

## 资源列表

- http://map.blog.zdvgjr.cn/Article/080187.shtml
- http://map.blog.zdvgjr.cn/Article/0473476.shtml
- http://map.blog.zdvgjr.cn/Article/6651.shtml
- http://map.blog.zdvgjr.cn/Article/0971311.shtml
- http://map.blog.zdvgjr.cn/Article/1489308.shtml
- http://map.blog.zdvgjr.cn/Article/028401.shtml
- http://map.blog.zdvgjr.cn/Article/53688.shtml
- http://map.blog.zdvgjr.cn/Article/2158.shtml
- http://map.blog.zdvgjr.cn/Article/9967912.shtml
- http://map.blog.zdvgjr.cn/Article/5922.shtml
- http://map.blog.zdvgjr.cn/Article/278917.shtml
- http://map.blog.zdvgjr.cn/Article/9270966.shtml
- http://map.blog.zdvgjr.cn/Article/0155000.shtml
- http://map.blog.zdvgjr.cn/Article/21717.shtml
- http://map.blog.zdvgjr.cn/Article/36285.shtml
- http://map.blog.zdvgjr.cn/Article/49217.shtml
- http://map.blog.zdvgjr.cn/Article/71785.shtml
- http://map.blog.zdvgjr.cn/Article/2367133.shtml
- http://map.blog.zdvgjr.cn/Article/0036.shtml
- http://map.blog.zdvgjr.cn/Article/6501115.shtml
- http://map.blog.zdvgjr.cn/Article/4981436.shtml
- http://map.blog.zdvgjr.cn/Article/539051.shtml
- http://map.blog.zdvgjr.cn/Article/30345.shtml
- http://map.blog.zdvgjr.cn/Article/8858415.shtml
- http://map.blog.zdvgjr.cn/Article/4313.shtml
- http://map.blog.zdvgjr.cn/Article/79245.shtml
- http://map.blog.zdvgjr.cn/Article/926273.shtml
- http://map.blog.zdvgjr.cn/Article/942376.shtml
- http://map.blog.zdvgjr.cn/Article/275874.shtml
- http://map.blog.zdvgjr.cn/Article/884812.shtml
- http://map.blog.zdvgjr.cn/Article/0284.shtml
- http://map.blog.zdvgjr.cn/Article/0672.shtml
- http://map.blog.zdvgjr.cn/Article/0253148.shtml
- http://map.blog.zdvgjr.cn/Article/25738.shtml
- http://map.blog.zdvgjr.cn/Article/3717704.shtml
- http://map.blog.zdvgjr.cn/Article/834171.shtml
- http://map.blog.zdvgjr.cn/Article/5843.shtml
- http://map.blog.zdvgjr.cn/Article/97652.shtml
- http://map.blog.zdvgjr.cn/Article/812609.shtml
- http://map.blog.zdvgjr.cn/Article/6808959.shtml
- http://map.blog.zdvgjr.cn/Article/31120.shtml
- http://map.blog.zdvgjr.cn/Article/40684.shtml
- http://map.blog.zdvgjr.cn/Article/3835508.shtml
- http://map.blog.zdvgjr.cn/Article/6722.shtml
- http://map.blog.zdvgjr.cn/Article/6646.shtml
- http://map.blog.zdvgjr.cn/Article/3250803.shtml
- http://map.blog.zdvgjr.cn/Article/64231.shtml
- http://map.blog.zdvgjr.cn/Article/9303.shtml
- http://map.blog.zdvgjr.cn/Article/7793.shtml
- http://map.blog.zdvgjr.cn/Article/5046.shtml
- http://map.blog.zdvgjr.cn/Article/3576187.shtml
- http://map.blog.zdvgjr.cn/Article/4569443.shtml
- http://map.blog.zdvgjr.cn/Article/510385.shtml
- http://map.blog.zdvgjr.cn/Article/8628108.shtml
- http://map.blog.zdvgjr.cn/Article/2298.shtml
- http://map.blog.zdvgjr.cn/Article/4277.shtml
- http://map.blog.zdvgjr.cn/Article/8818916.shtml
- http://map.blog.zdvgjr.cn/Article/4983558.shtml
- http://map.blog.zdvgjr.cn/Article/6110.shtml
- http://map.blog.zdvgjr.cn/Article/6238991.shtml
- http://map.blog.zdvgjr.cn/Article/575527.shtml
- http://map.blog.zdvgjr.cn/Article/1493.shtml
- http://map.blog.zdvgjr.cn/Article/0248.shtml
- http://map.blog.zdvgjr.cn/Article/0696021.shtml
- http://map.blog.zdvgjr.cn/Article/25359.shtml
- http://map.blog.zdvgjr.cn/Article/69723.shtml
- http://map.blog.zdvgjr.cn/Article/611942.shtml
- http://map.blog.zdvgjr.cn/Article/7983.shtml
- http://map.blog.zdvgjr.cn/Article/1277.shtml
- http://map.blog.zdvgjr.cn/Article/65462.shtml
- http://map.blog.zdvgjr.cn/Article/8908744.shtml
- http://map.blog.zdvgjr.cn/Article/899747.shtml
- http://map.blog.zdvgjr.cn/Article/8071.shtml
- http://map.blog.zdvgjr.cn/Article/6314261.shtml
- http://map.blog.zdvgjr.cn/Article/597268.shtml
- http://map.blog.zdvgjr.cn/Article/1938.shtml
- http://map.blog.zdvgjr.cn/Article/7008.shtml
- http://map.blog.zdvgjr.cn/Article/85431.shtml
- http://map.blog.zdvgjr.cn/Article/298189.shtml
- http://map.blog.zdvgjr.cn/Article/84888.shtml
- http://map.blog.zdvgjr.cn/Article/1057330.shtml
- http://map.blog.zdvgjr.cn/Article/166836.shtml
- http://map.blog.zdvgjr.cn/Article/337540.shtml
- http://map.blog.zdvgjr.cn/Article/3369.shtml
- http://map.blog.zdvgjr.cn/Article/5699686.shtml
- http://map.blog.zdvgjr.cn/Article/2842089.shtml
- http://map.blog.zdvgjr.cn/Article/44401.shtml
- http://map.blog.zdvgjr.cn/Article/08851.shtml
- http://map.blog.zdvgjr.cn/Article/94943.shtml
- http://map.blog.zdvgjr.cn/Article/85728.shtml
- http://map.blog.zdvgjr.cn/Article/336966.shtml
- http://map.blog.zdvgjr.cn/Article/7801.shtml
- http://map.blog.zdvgjr.cn/Article/876504.shtml
- http://map.blog.zdvgjr.cn/Article/0913593.shtml
- http://map.blog.zdvgjr.cn/Article/3991.shtml
- http://map.blog.zdvgjr.cn/Article/553043.shtml
- http://map.blog.zdvgjr.cn/Article/1010.shtml
- http://map.blog.zdvgjr.cn/Article/9723.shtml
- http://map.blog.zdvgjr.cn/Article/2669376.shtml
- http://map.blog.zdvgjr.cn/Article/5317643.shtml
- http://map.blog.zdvgjr.cn/Article/7277.shtml
- http://map.blog.zdvgjr.cn/Article/65167.shtml
- http://map.blog.zdvgjr.cn/Article/9825.shtml
- http://map.blog.zdvgjr.cn/Article/200791.shtml
- http://map.blog.zdvgjr.cn/Article/87209.shtml
- http://map.blog.zdvgjr.cn/Article/9083559.shtml
- http://map.blog.zdvgjr.cn/Article/54603.shtml
- http://map.blog.zdvgjr.cn/Article/8118.shtml
- http://map.blog.zdvgjr.cn/Article/18712.shtml
- http://map.blog.zdvgjr.cn/Article/029554.shtml
- http://map.blog.zdvgjr.cn/Article/0904.shtml
- http://map.blog.zdvgjr.cn/Article/16007.shtml
- http://map.blog.zdvgjr.cn/Article/06908.shtml
- http://map.blog.zdvgjr.cn/Article/22385.shtml
- http://map.blog.zdvgjr.cn/Article/490978.shtml
- http://map.blog.zdvgjr.cn/Article/4890762.shtml
- http://map.blog.zdvgjr.cn/Article/495012.shtml
- http://map.blog.zdvgjr.cn/Article/9021569.shtml
- http://map.blog.zdvgjr.cn/Article/193042.shtml
- http://map.blog.zdvgjr.cn/Article/4417.shtml
- http://map.blog.zdvgjr.cn/Article/1619.shtml
- http://map.blog.zdvgjr.cn/Article/0796085.shtml
- http://map.blog.zdvgjr.cn/Article/302447.shtml
- http://map.blog.zdvgjr.cn/Article/24818.shtml
- http://map.blog.zdvgjr.cn/Article/8009733.shtml
- http://map.blog.zdvgjr.cn/Article/54787.shtml
- http://map.blog.zdvgjr.cn/Article/515035.shtml
- http://map.blog.zdvgjr.cn/Article/40064.shtml
- http://map.blog.zdvgjr.cn/Article/267927.shtml
- http://map.blog.zdvgjr.cn/Article/832743.shtml
- http://map.blog.zdvgjr.cn/Article/1558576.shtml
- http://map.blog.zdvgjr.cn/Article/2682.shtml
- http://map.blog.zdvgjr.cn/Article/9116012.shtml
- http://map.blog.zdvgjr.cn/Article/2313.shtml
- http://map.blog.zdvgjr.cn/Article/74170.shtml
- http://map.blog.zdvgjr.cn/Article/44738.shtml
- http://map.blog.zdvgjr.cn/Article/9326718.shtml
- http://map.blog.zdvgjr.cn/Article/515269.shtml
- http://map.blog.zdvgjr.cn/Article/6187395.shtml
- http://map.blog.zdvgjr.cn/Article/1065.shtml
- http://map.blog.zdvgjr.cn/Article/9894641.shtml
- http://map.blog.zdvgjr.cn/Article/94832.shtml
- http://map.blog.zdvgjr.cn/Article/986788.shtml
- http://map.blog.zdvgjr.cn/Article/7950425.shtml
- http://map.blog.zdvgjr.cn/Article/739351.shtml
- http://map.blog.zdvgjr.cn/Article/364953.shtml
- http://map.blog.zdvgjr.cn/Article/347511.shtml
- http://map.blog.zdvgjr.cn/Article/0403.shtml
- http://map.blog.zdvgjr.cn/Article/31164.shtml
- http://map.blog.zdvgjr.cn/Article/5447.shtml

## 项目结构

```
webarchive-navigator/
├── build_index.py          # 主索引构建脚本，读取原始链接并生成索引文件
├── serve.py                # 本地 Web 服务启动入口，依赖 Flask
├── requirements.txt        # Python 依赖声明文件，包含必须和可选组件
├── data/                   # 数据目录，存放原始链接列表和配置文件
│   ├── urls.txt            # 默认链接输入文件，每行一个 URL
│   └── schema.json         # 索引输出结构的 JSON Schema 校验规则
├── core/                   # 核心逻辑模块
│   ├── parser.py           # URL 解析与编号提取函数
│   ├── validator.py        # 链接可用性校验和响应头分析
│   └── indexer.py          # 索引构建主流程，整合解析与校验结果
├── output/                 # 输出目录，存放生成的索引文件和导出数据
│   ├── index.json          # 默认索引输出文件
│   └── exports/            # 按格式分类的导出子目录（CSV、TXT）
├── tests/                  # 单元测试与集成测试目录
│   ├── test_parser.py      # 解析函数测试用例
│   ├── test_validator.py   # 校验模块测试用例
│   └── test_integration.py # 端到端构建流程测试
└── docs/                   # 文档目录，包含用户手册和开发指南
    ├── user_guide.md
    ├── configuration.md
    ├── developer_guide.md
    └── faq.md
```

## 贡献指南

1. 复刻主仓库至个人账户，在本地切换到开发分支。所有新增功能或修复均应在独立分支上进行，避免直接修改主分支。
2. 在 `data/urls.txt` 中追加新链接时，需确保每行一个完整 URL，且不包含多余空白字符。提交前运行 `python build_index.py --check-only` 执行基础语法校验。
3. 若新增或修改解析逻辑，需同步更新 `tests/` 目录下的对应测试文件，确保覆盖率不低于 85%。使用 `pytest` 执行全部测试用例。
4. 文档更新应随代码变更一同提交。若涉及用户可见的功能调整，须同步修改 `docs/user_guide.md` 中的相关章节。
5. 提交合并请求时，请在描述中注明变更类型（特性、修复、文档）、影响范围以及测试结果摘要。合并前需通过持续集成检查。

## 常见问题

问：索引构建过程中出现链接超时错误，如何处理？

答：超时通常由目标服务器响应缓慢或网络波动引起。可调整 `core/validator.py` 中的 `REQUEST_TIMEOUT` 变量（默认 10 秒）以延长等待时间。若大量链接持续超时，建议使用 `--skip-unreachable` 参数跳过不可达条目，待网络稳定后重新运行校验。

问：如何批量导出所有链接的编号和标题信息？

答：索引生成后，使用导出子命令即可。例如 `python build_index.py --export csv --output ./output/exports/list.csv` 可生成包含编号、原始 URL 和基础状态列的 CSV 文件。支持 JSON 和纯文本格式，可通过 `--format` 参数切换。

问：项目是否支持增量更新，避免每次全量重建？

答：支持。在配置文件中设置 `incremental: true` 并指定 `state_file` 路径后，系统会记录上一次构建的条目哈希值。再次运行时仅处理新增或发生变化的链接，大幅缩短大型数据集的构建时间。具体配置方法参见 `docs/configuration.md` 中的增量更新章节。

## 许可证

MIT

> 外链数量: 150 | 生成时间: 2026-07-10 17:52:39
