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

- raw：`https://raw.githubusercontent.com/hany1123/tilegeti-grade1-question-bank/main/tilegeti-grade1-100.json`
- CDN（国内更快）：`https://cdn.jsdelivr.net/gh/hany1123/tilegeti-grade1-question-bank@main/tilegeti-grade1-100.json`
