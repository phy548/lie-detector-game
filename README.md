# 測謊機 · LIE DETECTOR

**你能分辨 AI 寫的文字嗎？**

每一輪給你兩段文字——一段真人寫的，一段 AI 生成的。憑直覺猜，看你識破幾題。

🎮 **[點這裡玩遊戲](https://hsini109.github.io/lie-detector-game/)**

---

## 這個專案在問什麼

> 當 AI 越來越擅長模仿人類的語氣與情感，「真實感」在寫作上還重要嗎？

玩家猜完之後，我們用 Python 分析答題數據，看哪一類文字最難被識破——以及 AI 到底靠什麼騙過人類。

---

## 專案結構

```
├── index.html              遊戲主頁面
├── questions.json          題庫（topic / human / ai）
├── lie_detector_v3.ipynb   Python 分析腳本（Google Colab）
└── README.md
```

---

## 技術架構

```
真人文字（朋友手寫）
        +
Groq API 生成 AI 文字          ← lie_detector_v3.ipynb 第 1–7 格
        ↓
questions.json 題庫
        ↓
index.html 遊戲（GitHub Pages）
        ↓
玩家答題 → 自動送出數據 → Google Sheets
        ↓
Python 讀取數據、產生圖表       ← lie_detector_v3.ipynb 第 8–12 格
```

---

## 使用工具

| 工具 | 用途 |
|------|------|
| HTML / CSS / JS | 遊戲前端介面 |
| Groq API（llama-3.3-70b） | 生成 AI 文字 |
| Google Apps Script | 接收玩家數據 |
| Google Sheets | 儲存答題結果 |
| Python（Colab） | 數據分析與圖表 |
| GitHub Pages | 網站部署 |

---

## Colab 筆記本說明

**第一部分：生成 AI 文字（只需做一次）**

| 格子 | 功能 |
|------|------|
| 第 1–2 格 | 安裝、載入套件 |
| 第 3 格 | 設定 Groq API Key |
| 第 4 格 | 設定 AI 人格（SOUL） |
| 第 5 格 | 上傳 questions.json |
| 第 6 格 | 自動補上 AI 文字 |
| 第 7 格 | 下載新的 questions.json |

**第二部分：分析玩家數據（收到數據後跑）**

| 格子 | 功能 |
|------|------|
| 第 8 格 | 從 Google Sheets 讀取數據 |
| 第 9 格 | 基本統計（猜對率、得分） |
| 第 10 格 | 圖表：猜對率 + 得分分佈 |
| 第 11 格 | 圖表：答題熱力圖 |
| 第 12 格 | 文字特徵分析（字數、轉折詞） |