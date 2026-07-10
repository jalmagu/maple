# WebLink Atlas

WebLink Atlas 是一个面向技术研究者、内容聚合者与信息架构师的开源外链资源汇总平台。该项目专注于将分散在互联网各处的深度技术文章、分析报告与工程实践文档进行系统化收集、分类与索引，帮助用户快速定位特定主题下的高质量外部资源。项目本身不存储任何文章内容，仅提供结构化的链接索引与元数据描述，适用于构建个人知识库、技术周报素材源或自动化信息采集管道。

项目定位为轻量级、可扩展的链接管理中间层，通过明确的目录结构与文档化规则，降低信息过载带来的筛选成本。目标用户包括开源社区维护者、技术内容创作者、以及需要定期跟踪特定领域动态的研发团队。

## 功能概览

- 自动抓取链接元数据：通过请求目标页面解析标题、摘要与发布时间，生成结构化索引记录。

- 多级标签分类体系：支持用户自定义标签（如 backend、frontend、devops、security），并允许按标签筛选链接列表。

- 链接状态健康检查：定期检测已收录链接的可访问性，标记失效链接并生成报告。

- 全文搜索支持：基于链接标题、描述与标签提供关键字检索，结果按相关度排序。

- 导入导出标准化：支持 CSV、JSON 与 Markdown 表格格式的批量链接导入导出，便于与其他工具链集成。

- 访问量统计与热度排序：记录每个链接的点击次数，提供按热度、时间或字母序排列的视图。

- 自定义黑名单过滤：支持配置域名或关键字黑名单，自动过滤不符合收录标准的链接。

## 应用场景

1. 技术团队内部知识库建设：研发团队可使用 WebLink Atlas 整理日常阅读的博客、官方文档与 RFC 草案，按项目或技术栈分类，新成员入职时可快速了解团队关注的领域。

2. 开源项目文档外链管理：开源项目维护者可以在项目仓库中嵌入 WebLink Atlas 生成的链接列表，作为 "相关资料" 或 "延伸阅读" 章节的自动更新源。

3. 技术周报或月刊素材收集：内容编辑可定期导出本周新增的高热度链接，快速生成周报草稿，减少手动整理耗时。

4. 个人学习路径规划：学习者可将发现的优质文章加入收藏，通过标签跟踪自己的学习进度，并定期回顾已读内容。

## 快速开始

以下命令将在本地启动 WebLink Atlas 服务实例。

```bash
# 克隆代码仓库
git clone https://github.com/weblink-atlas/weblink-atlas.git
cd weblink-atlas

# 安装依赖（使用 pip 管理 Python 后端）
pip install -r requirements.txt

# 初始化本地数据库
python scripts/init_db.py

# 运行开发服务器
python app.py
```

服务启动后，访问 http://localhost:5000 即可进入 Web 界面。首次启动会自动创建默认管理员账户，用户名 admin，密码在控制台日志中输出，请及时修改。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|----------|----------|------|
| Python | 3.9 及以上 | 后端运行时环境，推荐使用 3.11 |
| SQLite | 3.35 及以上 | 默认内置数据库，无需额外安装 |
| Redis | 6.0 及以上 | 可选，用于缓存与任务队列，生产环境建议启用 |
| Node.js | 18.x LTS | 仅用于前端构建，开发模式可不安装 |
| git | 2.25 及以上 | 用于克隆仓库及版本管理 |
| curl | 7.68 及以上 | 用于健康检查脚本中的 HTTP 探测 |
| cron | 系统自带 | 用于定时任务调度，生产环境需配置 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | docs/user-guide/ | 如何添加链接、管理标签、导入导出数据以及使用搜索功能 |
| 管理员指南 | docs/admin-guide/ | 如何配置黑名单、调整健康检查频率、备份数据库与迁移 |
| 开发文档 | docs/developer-guide/ | 如何扩展元数据解析器、增加新的分类规则或修改前端界面 |
| API 参考 | docs/api-reference/ | 所有 RESTful 接口的请求参数、响应格式与错误码说明 |
| 部署指南 | docs/deployment/ | 如何基于 Docker、Nginx 与 Gunicorn 进行生产环境部署 |

## 资源列表

- http://map.blog.zdvgjr.cn/Article/8017.shtml
- http://map.blog.zdvgjr.cn/Article/3628.shtml
- http://map.blog.zdvgjr.cn/Article/3140.shtml
- http://map.blog.zdvgjr.cn/Article/196196.shtml
- http://map.blog.zdvgjr.cn/Article/36266.shtml
- http://map.blog.zdvgjr.cn/Article/3287.shtml
- http://map.blog.zdvgjr.cn/Article/263781.shtml
- http://map.blog.zdvgjr.cn/Article/535991.shtml
- http://map.blog.zdvgjr.cn/Article/806095.shtml
- http://map.blog.zdvgjr.cn/Article/303681.shtml
- http://map.blog.zdvgjr.cn/Article/90400.shtml
- http://map.blog.zdvgjr.cn/Article/564271.shtml
- http://map.blog.zdvgjr.cn/Article/52055.shtml
- http://map.blog.zdvgjr.cn/Article/7945457.shtml
- http://map.blog.zdvgjr.cn/Article/76295.shtml
- http://map.blog.zdvgjr.cn/Article/95996.shtml
- http://map.blog.zdvgjr.cn/Article/11418.shtml
- http://map.blog.zdvgjr.cn/Article/354460.shtml
- http://map.blog.zdvgjr.cn/Article/854366.shtml
- http://map.blog.zdvgjr.cn/Article/064999.shtml
- http://map.blog.zdvgjr.cn/Article/1090710.shtml
- http://map.blog.zdvgjr.cn/Article/5018098.shtml
- http://map.blog.zdvgjr.cn/Article/6096101.shtml
- http://map.blog.zdvgjr.cn/Article/23513.shtml
- http://map.blog.zdvgjr.cn/Article/7449.shtml
- http://map.blog.zdvgjr.cn/Article/6260641.shtml
- http://map.blog.zdvgjr.cn/Article/2582075.shtml
- http://map.blog.zdvgjr.cn/Article/2547.shtml
- http://map.blog.zdvgjr.cn/Article/834469.shtml
- http://map.blog.zdvgjr.cn/Article/1645.shtml
- http://map.blog.zdvgjr.cn/Article/931470.shtml
- http://map.blog.zdvgjr.cn/Article/8699.shtml
- http://map.blog.zdvgjr.cn/Article/6346.shtml
- http://map.blog.zdvgjr.cn/Article/744680.shtml
- http://map.blog.zdvgjr.cn/Article/0426821.shtml
- http://map.blog.zdvgjr.cn/Article/05002.shtml
- http://map.blog.zdvgjr.cn/Article/1813.shtml
- http://map.blog.zdvgjr.cn/Article/8451.shtml
- http://map.blog.zdvgjr.cn/Article/90002.shtml
- http://map.blog.zdvgjr.cn/Article/71330.shtml
- http://map.blog.zdvgjr.cn/Article/195208.shtml
- http://map.blog.zdvgjr.cn/Article/532573.shtml
- http://map.blog.zdvgjr.cn/Article/206271.shtml
- http://map.blog.zdvgjr.cn/Article/870653.shtml
- http://map.blog.zdvgjr.cn/Article/60548.shtml
- http://map.blog.zdvgjr.cn/Article/239698.shtml
- http://map.blog.zdvgjr.cn/Article/117971.shtml
- http://map.blog.zdvgjr.cn/Article/6698519.shtml
- http://map.blog.zdvgjr.cn/Article/2043.shtml
- http://map.blog.zdvgjr.cn/Article/3930727.shtml
- http://map.blog.zdvgjr.cn/Article/8234.shtml
- http://map.blog.zdvgjr.cn/Article/4552494.shtml
- http://map.blog.zdvgjr.cn/Article/502464.shtml
- http://map.blog.zdvgjr.cn/Article/293413.shtml
- http://map.blog.zdvgjr.cn/Article/6588.shtml
- http://map.blog.zdvgjr.cn/Article/5302.shtml
- http://map.blog.zdvgjr.cn/Article/9477.shtml
- http://map.blog.zdvgjr.cn/Article/12095.shtml
- http://map.blog.zdvgjr.cn/Article/829878.shtml
- http://map.blog.zdvgjr.cn/Article/6176130.shtml
- http://map.blog.zdvgjr.cn/Article/06329.shtml
- http://map.blog.zdvgjr.cn/Article/7899233.shtml
- http://map.blog.zdvgjr.cn/Article/5001.shtml
- http://map.blog.zdvgjr.cn/Article/9708142.shtml
- http://map.blog.zdvgjr.cn/Article/1448.shtml
- http://map.blog.zdvgjr.cn/Article/3159703.shtml
- http://map.blog.zdvgjr.cn/Article/8539.shtml
- http://map.blog.zdvgjr.cn/Article/1711689.shtml
- http://map.blog.zdvgjr.cn/Article/9766886.shtml
- http://map.blog.zdvgjr.cn/Article/0342.shtml
- http://map.blog.zdvgjr.cn/Article/7158158.shtml
- http://map.blog.zdvgjr.cn/Article/09709.shtml
- http://map.blog.zdvgjr.cn/Article/21966.shtml
- http://map.blog.zdvgjr.cn/Article/217044.shtml
- http://map.blog.zdvgjr.cn/Article/5314223.shtml
- http://map.blog.zdvgjr.cn/Article/9727162.shtml
- http://map.blog.zdvgjr.cn/Article/9058.shtml
- http://map.blog.zdvgjr.cn/Article/5424.shtml
- http://map.blog.zdvgjr.cn/Article/1878780.shtml
- http://map.blog.zdvgjr.cn/Article/84868.shtml
- http://map.blog.zdvgjr.cn/Article/0074.shtml
- http://map.blog.zdvgjr.cn/Article/5034488.shtml
- http://map.blog.zdvgjr.cn/Article/4226485.shtml
- http://map.blog.zdvgjr.cn/Article/0961899.shtml
- http://map.blog.zdvgjr.cn/Article/511905.shtml
- http://map.blog.zdvgjr.cn/Article/091587.shtml
- http://map.blog.zdvgjr.cn/Article/27214.shtml
- http://map.blog.zdvgjr.cn/Article/72847.shtml
- http://map.blog.zdvgjr.cn/Article/99824.shtml
- http://map.blog.zdvgjr.cn/Article/309710.shtml
- http://map.blog.zdvgjr.cn/Article/152304.shtml
- http://map.blog.zdvgjr.cn/Article/831219.shtml
- http://map.blog.zdvgjr.cn/Article/798942.shtml
- http://map.blog.zdvgjr.cn/Article/7021.shtml
- http://map.blog.zdvgjr.cn/Article/4348123.shtml
- http://map.blog.zdvgjr.cn/Article/669749.shtml
- http://map.blog.zdvgjr.cn/Article/1770.shtml
- http://map.blog.zdvgjr.cn/Article/917329.shtml
- http://map.blog.zdvgjr.cn/Article/695208.shtml
- http://map.blog.zdvgjr.cn/Article/8537076.shtml
- http://map.blog.zdvgjr.cn/Article/5581671.shtml
- http://map.blog.zdvgjr.cn/Article/4895613.shtml
- http://map.blog.zdvgjr.cn/Article/38329.shtml
- http://map.blog.zdvgjr.cn/Article/91559.shtml
- http://map.blog.zdvgjr.cn/Article/027315.shtml
- http://map.blog.zdvgjr.cn/Article/162358.shtml
- http://map.blog.zdvgjr.cn/Article/044606.shtml
- http://map.blog.zdvgjr.cn/Article/6216.shtml
- http://map.blog.zdvgjr.cn/Article/8206305.shtml
- http://map.blog.zdvgjr.cn/Article/36971.shtml
- http://map.blog.zdvgjr.cn/Article/9288272.shtml
- http://map.blog.zdvgjr.cn/Article/5286886.shtml
- http://map.blog.zdvgjr.cn/Article/044930.shtml
- http://map.blog.zdvgjr.cn/Article/903330.shtml
- http://map.blog.zdvgjr.cn/Article/94192.shtml
- http://map.blog.zdvgjr.cn/Article/8252303.shtml
- http://map.blog.zdvgjr.cn/Article/6113.shtml
- http://map.blog.zdvgjr.cn/Article/6979271.shtml
- http://map.blog.zdvgjr.cn/Article/1144.shtml
- http://map.blog.zdvgjr.cn/Article/8709595.shtml
- http://map.blog.zdvgjr.cn/Article/440858.shtml
- http://map.blog.zdvgjr.cn/Article/4007.shtml
- http://map.blog.zdvgjr.cn/Article/557078.shtml
- http://map.blog.zdvgjr.cn/Article/368585.shtml
- http://map.blog.zdvgjr.cn/Article/0092725.shtml
- http://map.blog.zdvgjr.cn/Article/1454913.shtml
- http://map.blog.zdvgjr.cn/Article/8977.shtml
- http://map.blog.zdvgjr.cn/Article/0684.shtml
- http://map.blog.zdvgjr.cn/Article/5121405.shtml
- http://map.blog.zdvgjr.cn/Article/6851366.shtml
- http://map.blog.zdvgjr.cn/Article/7695.shtml
- http://map.blog.zdvgjr.cn/Article/1904.shtml
- http://map.blog.zdvgjr.cn/Article/2068.shtml
- http://map.blog.zdvgjr.cn/Article/097679.shtml
- http://map.blog.zdvgjr.cn/Article/4535.shtml
- http://map.blog.zdvgjr.cn/Article/4579.shtml
- http://map.blog.zdvgjr.cn/Article/9530.shtml
- http://map.blog.zdvgjr.cn/Article/765264.shtml
- http://map.blog.zdvgjr.cn/Article/69694.shtml
- http://map.blog.zdvgjr.cn/Article/13406.shtml
- http://map.blog.zdvgjr.cn/Article/5061.shtml
- http://map.blog.zdvgjr.cn/Article/666607.shtml
- http://map.blog.zdvgjr.cn/Article/57981.shtml
- http://map.blog.zdvgjr.cn/Article/5349142.shtml
- http://map.blog.zdvgjr.cn/Article/48176.shtml
- http://map.blog.zdvgjr.cn/Article/330773.shtml
- http://map.blog.zdvgjr.cn/Article/2613.shtml
- http://map.blog.zdvgjr.cn/Article/4817961.shtml
- http://map.blog.zdvgjr.cn/Article/90661.shtml
- http://map.blog.zdvgjr.cn/Article/7545327.shtml

## 项目结构

```
weblink-atlas/
├── app/                            # 主应用模块
│   ├── __init__.py                 # 工厂函数与配置加载
│   ├── routes/                     # 路由层，处理 HTTP 请求
│   │   ├── index.py                # 首页与搜索接口
│   │   ├── links.py                # 链接增删改查接口
│   │   ├── tags.py                 # 标签管理接口
│   │   └── admin.py                # 管理员专用接口
│   ├── models/                     # 数据模型层
│   │   ├── link.py                 # 链接实体模型，包含 URL、标题、摘要等字段
│   │   ├── tag.py                  # 标签模型，支持层级关系
│   │   └── user.py                 # 用户与权限模型
│   ├── services/                   # 业务逻辑层
│   │   ├── fetcher.py              # 链接元数据抓取服务，含超时与重试逻辑
│   │   ├── checker.py              # 健康检查服务，异步检测链接状态
│   │   ├── indexer.py              # 全文索引构建与更新服务
│   │   └── exporter.py             # 数据导出服务（JSON/CSV/Markdown）
│   └── utils/                      # 工具函数集合
│       ├── validators.py           # URL 校验与规范化工具
│       ├── filters.py              # 黑名单过滤与内容安全检测
│       └── logger.py               # 日志配置与分级输出
├── frontend/                       # 前端静态资源
│   ├── assets/
│   │   ├── css/                    # 样式表，基于标准化 CSS 框架
│   │   ├── js/                     # 原生 JavaScript 交互逻辑
│   │   └── images/                 # 图标与占位图
│   └── templates/                  # Jinja2 模板文件
│       ├── layout.html             # 基础布局模板
│       ├── index.html              # 首页列表视图
│       ├── detail.html             # 单个链接详情页
│       └── admin.html              # 管理后台页面
├── scripts/                        # 运维与开发辅助脚本
│   ├── init_db.py                  # 初始化数据库表结构
│   ├── seed_data.py                # 填充示例数据用于测试
│   ├── health_check_cron.py        # 定时健康检查任务入口
│   └── backup_db.sh                # 数据库备份脚本
├── tests/                          # 单元测试与集成测试
│   ├── test_models.py              # 模型层测试
│   ├── test_services.py            # 服务层测试，含 mock 外部请求
│   └── test_routes.py              # 路由层端到端测试
├── config/                         # 配置文件目录
│   ├── development.py              # 开发环境配置
│   ├── production.py               # 生产环境配置（敏感信息通过环境变量注入）
│   └── testing.py                  # 测试环境配置
├── docs/                           # 文档源码
├── requirements.txt                # Python 依赖清单
├── Dockerfile                      # 容器化构建文件
├── docker-compose.yml              # 多容器编排配置（应用 + Redis + 可选数据库）
├── Makefile                        # 常用命令封装（lint、test、run）
└── README.md                       # 项目介绍文档（本文件）
```

## 贡献指南

1. 在 GitHub 上 Fork 本仓库，并克隆到本地开发环境。请确保使用 main 分支的最新代码作为基准。

2. 创建新的功能分支，分支命名采用 feat/xxx 或 fix/xxx 格式。提交代码前请运行 make lint 检查代码风格，并确保所有现有测试通过。

3. 新增链接解析器或修改核心服务逻辑时，请在 tests/ 目录下补充对应的单元测试用例，测试覆盖率不应低于 80%。

4. 提交 Pull Request 时，请清晰描述变更内容、动机以及影响范围。若修复了已有 Issue，请在 PR 描述中关联 Issue 编号。

5. 文档更新与代码变更需同步进行。若新增了配置项或 API 接口，必须更新 docs/ 下对应的文档文件。

## 常见问题

Q: 项目支持 HTTPS 链接的抓取吗？对于自签名证书的站点如何处理？

A: 支持 HTTPS。对于自签名证书或证书过期的站点，fetcher 服务默认会拒绝连接以保证安全。若需强制访问，可在配置中将 FETCHER_VERIFY_SSL 设为 false，但生产环境中不推荐此操作。

Q: 健康检查功能会频繁访问目标站点，是否会对源站造成压力？

A: 健康检查间隔默认为 24 小时，且每次检查仅发送一个 HEAD 请求，不下载完整页面内容。对于大量链接，检查任务会分散在时间窗口内随机执行，避免同时发起大量请求。用户也可在管理后台自定义检查周期。

Q: 如何迁移数据到另一台服务器？

A: 默认 SQLite 数据库文件位于 instance/links.db，直接复制该文件即可。若使用 Redis 缓存，可通过 Redis 的 RDB 持久化文件进行迁移。更完整的备份方案请参考 docs/deployment/backup-strategy.md。

## 许可证

MIT

> 外链数量: 150 | 生成时间: 2026-07-10 17:52:39
