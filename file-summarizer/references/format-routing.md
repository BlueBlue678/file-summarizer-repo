# 格式与来源处理路由

供 file-summarizer 在"Step 2: 选择读取方式"时参考。核心原则：复用 WorkBuddy 已有专用能力，避免重复实现二进制解析。

## 本地文件

| 类型 | 扩展名 | 推荐方式 | 备注 |
|------|--------|----------|------|
| PDF | .pdf | workbuddy-pdf skill | 支持文本/表格/图片核查；扫描件走 OCR |
| Word | .doc/.docx/.wps/.wpt | workbuddy-office-routing 路由 → workbuddy-docx / workbuddy-local-office-edit | 只需内容时走读取能力 |
| Excel/表格 | .xls/.xlsx/.xlsm/.csv/.tsv | workbuddy-sheetagent skill | 关注表头、关键行列、汇总值 |
| PPT | .ppt/.pptx/.pps | workbuddy-pptx skill | 逐页提取标题与要点 |
| 思维导图 | .xmind | tencent-xmind skill | 提取节点层级 |
| 文本/Markdown | .txt/.md/.json/.xml/.yaml/.log | 直接 Read | 大文件分段读取 |
| 代码 | .py/.js/.ts/.java/.go/... | 直接 Read | 关注入口、接口、核心逻辑 |
| 图片 | .png/.jpg/.jpeg/.webp/.gif/.bmp | 视觉识别 / OCR | 含文字则先 OCR |
| 音频 | .mp3/.wav/.m4a | 语音转写工具 | 转文字后进入流程 |

## 在线内容

| 来源 | 推荐方式 |
|------|----------|
| 网页 URL | WebFetch 抓取并提取正文 |
| 腾讯文档 / 在线文档 | tencent-docs / tencent-saas-docs skill |
| 企业微信文档 | 对应 WeCom 文档能力 |
| 资讯检索结果 | WebSearch + WebFetch 组合 |

## 注意事项

- 目录/批量文件：先用 Glob 列出文件，再按类型分批处理。
- 无法读取的格式：向用户说明原因，请求转换为文本或 PDF。
- 保留来源信息：摘要中标注文件名或 URL，便于追溯。
- 隐私：敏感内容只在本地处理，不要外发。
- 若某个专用 skill 不可用，降级为通用读取方式（如 python 库、直接 Read），并在结果中说明。
