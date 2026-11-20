# Cloudflare Workers AI 免費模型比較表

每日自動更新的 Cloudflare Workers AI 模型比較表，部署於 GitHub Pages。

## 🔗 線上網頁

**https://om0504bot.github.io/cf-workers-ai-free-models/**



## 📊 功能特色

- **每日 21:00 UTC 自動更新** (台灣時間 05:00)
- **完整模型列表**: 所有 Cloudflare Workers AI 可用模型
- **免費/付費區分**: 綠底 = 免費方案可用 (含 10,000 Neurons/天)，紅底 = 需付費方案
- **Model ID 一鍵複製**: 點擊 Model ID 即可複製，直接貼到提供商設定
- **詳細資訊連結**: 模型名稱連結到 Cloudflare 官方詳情頁
- **豐富欄位**: 任務類型、國家/組織、Token 價格、Neurons 價格、免費額度估算、速率限制、棄用/預覽狀態、**工具支援**

## 🏗️ 本地開發

```bash
# 安裝依賴
pip install requests

# 執行抓取
python scrape_models.py

# 輸出在 docs/index.html，可直接用瀏覽器開啟
```

## 📁 專案結構

```
.
├── .github/workflows/update-models.yml  # GitHub Action 定時任務
├── scrape_models.py                      # 抓取腳本
├── docs/                                 # GitHub Pages 靜態網站 (自動生成)
│   ├── index.html                        # 比較表網頁
│   └── models.json                       # 結構化資料 (給程式用)
└── README.md
```

## 🔧 自訂設定

### 修改更新時間
編輯 `.github/workflows/update-models.yml` 中的 `cron`:
```yaml
# 目前: 每日 21:00 UTC (台灣時間 05:00)
- cron: '0 21 * * *'

# 例如每日 00:00 UTC (台灣 08:00):
- cron: '0 0 * * *'
```

### 新增/修改付費模型判定
編輯 `scrape_models.py` 中的 `PAID_MODELS` 集合。

### 新增/修改國家對應
編輯 `scrape_models.py` 中的 `COUNTRY_MAP` 字典。

### 新增/修改棄用模型標記
編輯 `scrape_models.py` 中 `check_deprecated()` 函數裡的 `known_deprecated` 字典。

## 📝 授權

MIT License - 歡迎自由使用與修改。

## 🙏 資料來源

- [Cloudflare Workers AI Models](https://developers.cloudflare.com/workers-ai/models/)
- [Cloudflare Workers AI Pricing](https://developers.cloudflare.com/workers-ai/platform/pricing/)
- [Cloudflare Workers AI Limits](https://developers.cloudflare.com/workers-ai/platform/limits/)
