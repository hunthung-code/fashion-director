# Payshow Fashion Config — Brand Intelligence Layer

> 這是 `fashion-director` plugin 的專案特化層。
> 放這個資料夾到 `notebooklm/OTHER_其他垂直/payshow/.claude/` 或專案根目錄的 `.claude/` 即可覆蓋免費版的通用設定。

## Brand Override Rules

所有 `creative-direction` / `style-specialist` / `output-generator` skill 在這個專案下必須遵守以下規則，優先於免費版通用設定。

---

## 品牌 DNA（Brand DNA）

**品牌名稱**：派秀科技 / Payshow  
**核心業務**：演藝展場 SG（Showgirl）× 經紀 × 品牌 三方媒合 SaaS 平台  
**母公司**：杏泓科技有限公司  
**市場**：台灣演藝展場產業

**三個核心形容詞**：**華麗 · 夜場 · 專業感**  
不是「sexy for the male gaze」，而是「展現在舞台上的自信力量」。

**絕對拒絕（Rejection List）**：
- 廉價情色感（低端夜店風）
- 企業灰（一般 SaaS 的 Boring Blue）
- 過度可愛 / 少女感（kawaii 路線偏離目標客群）
- 任何讓 SG 感覺「被物化」而非「被專業化」的視覺語言

---

## 視覺系統（已凍結）

**四套主題皮膚**，設計為 CSS variable 可切換：

| 主題 | 識別字 | 主色調 | 適用場景 |
|---|---|---|---|
| 賽博精品 Luxury Cyber | `theme-luxury-cyber` | 玻璃黑金 + 洋紅/青霓虹 | 首頁、封面、高端展場 |
| 液態金屬 Liquid Chrome | `theme-liquid-chrome` | 銀色流體、Y2K 金屬 | 限量活動、VIP 頁面 |
| 極簡未來 Editorial Future | `theme-editorial` | 大留白 + 大字 + 螢光點 | 日常工作頁、報表 |
| 全息漸層 Holographic | `theme-holo` | 柔和彩虹漸層 | 節日活動、女性向頁面 |

**預設主題**：`theme-luxury-cyber`  
**色票**（賽博精品）：
```css
--color-bg:       #0a0a0f;
--color-surface:  #12121c;
--color-primary:  #ff2d78;   /* 洋紅 fuchsia */
--color-accent:   #00e5ff;   /* 青霓虹 cyan */
--color-gold:     #f0c040;   /* 金 */
--color-text-hi:  #ffffff;
--color-text-lo:  #8888aa;
--color-border:   rgba(255,255,255,0.08);
```

---

## 硬技術約束（LINE LIFF）

所有視覺提案必須先通過這三關：
1. **跑在 LINE Mini App（LIFF / 手機 WebView）** — iOS WKWebView + Android WebView（含中階機）
2. **動效三層預算**（Signature 3D / Ambient 環境 / Micro 微動效）— 不可越級
3. **WebGL 紀律**：< 500 draw calls、texture atlas、用完 dispose

詳細規則見 `agents/payshow-director.md`。

---

## 輸出偏好

- **Deck**: Gamma 深色主題（slate）+ 繁體中文
- **PDF**: A4 橫向，深色底，適合簡報使用
- **Canva Brand Kit ID**: `kAGQpioZEyQ`（派秀專用）
- **Notion DB**: 任務追蹤 `50671803-f11f-484a-bdbb-78d2d0b48c09`

---

## 觸發此 Config 的指令

「定調這頁」「時尚總監看一下」「設計審查」「給視覺規範」「換版型」「做動效」
→ 自動讀取本 CLAUDE.md + 呼叫 `agents/payshow-director.md`
