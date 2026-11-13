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

