# 小学一年级题库（100 题）

「题了个题」导入格式的题库文件，覆盖小学一年级各课程。

## 文件

- `tilegeti-grade1-100.json` — 100 道题，纯 JSON，UTF-8

## 结构

```json
{
  "items": [
    { "type": "single", "q": "题干", "a": ["选项A", "选项B"], "k": 1, "difficulty": 2, "tip": "解析" }
  ]
}
```

| 字段 | 说明 |
| --- | --- |
| type | `single` / `multiple` / `boolean` / `text` / `subjective` |
| q | 题干，纯文本，不含 HTML |
| a | 选项数组；`boolean` 固定为 `["正确","错误"]` |
| k | 正确选项下标（`single` / `boolean`） |
| correctIndices | 正确选项下标数组（`multiple`） |
| answers | 可接受答案数组（`text`，任一命中即正确） |
| modelAnswer / rubric | 参考答案与评分要点（`subjective`） |
| difficulty | 难度 1–5 |
| tip | 解析 |

## 分布

| 学科 | 题量 |
| --- | --- |
| 语文 | 24 |
| 数学 | 29 |
| 英语 | 13 |
| 科学 | 11 |
| 道德与法治 | 8 |
| 音乐 / 美术 / 体育与劳动 | 各 5 |

题型：单选 81、判断 10、多选 5、填空 3、主观 1。难度以 1–2 为主，少量 3。

## 远程访问

2026-11-13 在本机（中国大陆，无代理）实测各链路可达性，结果如下：

| 链路 | 地址 | 实测 |
| --- | --- | --- |
| jsDelivr fastly 节点（推荐） | `https://fastly.jsdelivr.net/gh/hany1123/tilegeti-grade1-question-bank@main/tilegeti-grade1-100.json` | 200 ✅ |
| gh-proxy 反代 | `https://gh-proxy.com/https://raw.githubusercontent.com/hany1123/tilegeti-grade1-question-bank/main/tilegeti-grade1-100.json` | 200 ✅ |
| ghproxy.net 反代 | `https://ghproxy.net/https://raw.githubusercontent.com/hany1123/tilegeti-grade1-question-bank/main/tilegeti-grade1-100.json` | 200 ✅ |
| GitHub raw 直连 | `https://raw.githubusercontent.com/hany1123/tilegeti-grade1-question-bank/main/tilegeti-grade1-100.json` | 000 ❌ |
| cdn.jsdelivr.net | `https://cdn.jsdelivr.net/gh/hany1123/tilegeti-grade1-question-bank@main/tilegeti-grade1-100.json` | 000 ❌ |

`fastly.jsdelivr.net` 走 CDN，缓存约 12 小时；需要立即生效时可用 gh-proxy 链路，或在 GitHub 上提交后追加 `?t=时间戳` 破缓存。

## 文件清单

| 文件 | 结构 | 用途 |
| --- | --- | --- |
| `tilegeti-grade1-100.json` | `{"name","version","items":[…]}` | StudyOnTV 远程题库同步（含 subject / level） |
| `grade1-all.json` | `{"name","version","items":[…]}` | 与 APK 内置题库（`data/banks/`）同构的完整文件 |
| `primary-1-6.json` | `{"items":[…]}` | 1–6 年级上下学期 480 题，StudyOnTV 内置远程题库默认源 |
| `study-resources.json` | `{"items":[…]}` | **学习资源目录**：网课 / 视频入口，供 StudyOnTV「学习资源目录」拉取 |

## 学习资源目录格式（study-resources.json）

只存「标题 + 网址」，不搬运对方服务器上的视频；播放仍发生在原网站，App 只按页面里视频的真实播放时长计时。

| 字段 | 必填 | 说明 |
| --- | --- | --- |
| title | 是 | 显示名称，1–64 字 |
| url | 是 | `http`/`https` 地址；`kind=page` 时是课程网页，`kind=mp4` 时是视频直链 |
| kind | 否 | `page`（默认）或 `mp4`；留空时按 `url` 是否以 `.mp4` 结尾自动判断 |
| level | 否 | 年级，与「答题范围」配合决定先给孩子学哪一条 |
| subject | 否 | 科目，同上 |
| minutes | 否 | 本条的完成时长（1–120 分钟）；留 0 用家长配置的默认值 |
| allow | 否 | 网页课允许跳转的域名，逗号分隔；留空时只放行 `url` 自己的域名 |

设备端行为：每 15 分钟自动拉取启用中的来源；按来源整体替换（改目录内容能覆盖旧条目），手工添加的本地条目不会被覆盖；学完一条自动轮转到下一条。

