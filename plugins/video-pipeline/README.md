# video-pipeline

AI 影片製作四階段管線 plugin,從創意發想一路到成片段落。

## 流程與 Skills

依序執行(每階段的產出是下一階段的輸入):

| 順序 | Skill | 做什麼 | 產出 |
|---|---|---|---|
| 1 | `video-concepting` | 結構化訪談 → 角色/設定收斂 → 3-5 個創意方向(附試吃段子) | `劇本生成/<製作標題>/發想紀錄/` |
| 2 | `script-generation` | 以發想紀錄為憲法展開劇本;element 盤點與 @引用 | `劇本/` |
| 3 | `visual-asset-generation` | 盤點並撰寫角色/場景/關鍵幀的生圖 prompt,驗收後註冊 Higgsfield Element | `圖像生成/` |
| 4 | `storyboard-generation` | 逐鏡分鏡 → 生成分段規劃 → 逐段生成影片與驗收 | `分鏡/` |

呼叫方式:`/video-pipeline:video-concepting` 等,或直接以自然語言觸發。

## 前置需求

- 階段 3、4 的生成透過 **Higgsfield MCP**(generate_image / generate_video / media_upload / show_reference_elements),需先連接該 MCP server 並具備額度。
- 全部產出寫入當前專案的 `劇本生成/<製作標題>/`,風格庫存於專案的 `.claude/style/`。

## 共用檔

- `reference/refine-loop.md`:全管線共用的收斂循環(產出不滿意時的診斷→單變因修改流程)
- `reference/higgsfield-params.md`:生圖/生影片參數預設與任務清單格式

Skill 內以 `${CLAUDE_PLUGIN_ROOT}/reference/...` 引用,安裝後自動解析。
