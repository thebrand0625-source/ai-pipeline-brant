# Higgsfield 生成參數預設(依素材類型)

供步驟 2.5「生成任務清單」取值。`generate_image` 的參數:`model`(必填)、`aspect_ratio`、`count`(1-4)、`medias[]`(reference,值須先經 `media_upload_widget`/`media_import_url` 取得 media_id,或用前次生成的 job_id)、模型專屬參數(如 `resolution`)。派工前可用 `get_cost:true` 預估點數。

模型速記(用 `models_explore` 查最新):
- **nano_banana_pro**(預設):風格化插畫/多比例(含 21:9)/image-to-image/最高 4K;適合本 skill 全部素材
- soul_2:寫實人像取向,風格化角色**不適用**(明確排除,避免誤選)
- 模型清單會更新,執行前若對模型有疑慮先 `models_explore(action:'recommend')`

## 影片段落參數預設(storyboard-generation 步驟 4 用)

| 項目 | 預設 | 可選 |
|---|---|---|
| model | **seedance_2_0**(std)——支援 start_image+element、單段 4-15s、1080p/4k、genre 提示 | seedance_2_0_mini(快省但上限 720p)、grok_video_v15(無 element)、gemini_omni(上限 10s) |
| aspect_ratio | 依分鏡確認的比例(16:9/9:16) | auto/4:3/3:4/1:1/21:9 |
| resolution | **480p**(草稿驗收用,省點數) | 720p/1080p/4k(段落全定稿後,以定稿 prompt 升解析度重生成交付版) |
| duration | 依分段表逐段填(4-15s) | — |
| genre | 依調性(史詩=epic) | auto/action/horror/comedy/noir/drama |
| generate_audio | 依使用者決定(native audio 可能自行配音/雜訊,對白重要時建議 false 改後製) | true/false |
| medias | start_image=該段首幀定稿圖 media/job_id;element 以 element_id 嵌入 prompt | end_image 可選(鎖尾幀) |

執行前 `get_cost:true` 估點數;模型清單會變,生成前可再 `models_explore` 確認。

## 素材類型參數預設

| 素材類型 | model | aspect_ratio | count | resolution | medias(reference) |
|---|---|---|---|---|---|
| 角色五視圖 | nano_banana_pro | **21:9**(寬畫布五格) | 1 | 2k | 角色參考圖 |
| 角色三視圖 | nano_banana_pro | 16:9 | 1 | 2k | 角色參考圖 |
| 表情集(2×2) | nano_banana_pro | **1:1** | 1 | 2k | 角色參考圖(或五視圖 job_id) |
| 姿態/動作(單張全身) | nano_banana_pro | **3:4** 直式(橫向動作改 4:3) | 2(挑一) | 2k | 五視圖 job_id + 表情集 job_id |
| 場景主場景 | nano_banana_pro | **16:9** | 2(挑一) | 2k | 無(純文字) |
| 場景延伸/視角 | nano_banana_pro | 16:9(直式構圖如穹頂仰角改 9:16) | 2(挑一) | 主場景 job_id |
| 場景氛圍調整 | nano_banana_pro | **與基準圖同比例**(必須) | 1 | 2k | 要變化的那張圖 job_id |
| 造型定調(配角單視角) | nano_banana_pro | 3:4 | 2(挑一) | 2k | 無(純文字) |

預設原則:定調圖 count=1(它是唯一基準,多張反而要選)、探索性素材 count=2 留挑選空間;resolution 預設 2k,要印刷/放大才用 4k(成本高)。

## 生成任務清單格式(步驟 2.5 產出)

存於 `圖像生成/生成任務清單.md`。每個任務一節,參數欄標示預設值與可選範圍,**逐項讓使用者確認/改參後才執行**:

```
## Task N:<素材名>
- 來源 md:圖像生成/角色/xxx.md → <prompt 項目名>
- 用途:(該 md 內寫的用途)
- 依賴:(需先完成的 task,例:Task 1 的 job_id 作 reference)
- 參數:
  - model: nano_banana_pro(可選:models_explore 查詢結果)
  - aspect_ratio: 21:9(可選:1:1/3:2/2:3/4:3/3:4/4:5/5:4/9:16/16:9/21:9)
  - count: 1(可選:1-4)
  - resolution: 2k(可選:1k/2k/4k)
  - medias: <參考圖 media_id 或前置 task job_id + role>
- 狀態:待確認 / 已確認 / 已生成(job_id: ...)
```

任務排序按依賴鏈:無依賴的(五視圖、表情集、主場景、配角定調)排前並可同批送出;姿態、延伸/視角、氛圍排後,等前置 job_id。

## 執行規則

1. 任務清單先給使用者過目,用 AskUserQuestion 分批確認參數(有異動就更新清單檔)。
2. 依賴鏈分批執行:前置任務生成 → 使用者挑選定稿(count>1 時)→ 定稿 job_id 填入後置任務 → 執行後置。
3. 驗收依 SKILL.md 步驟 2.5 的「成品驗收流程」(使用者確認後才下載定稿;不滿意進 ${CLAUDE_PLUGIN_ROOT}/reference/refine-loop.md);job_id 一律回填任務清單狀態欄。
4. 本地參考圖(如 角色圖/xxx.png)需先 `media_upload_widget` 取得 media_id,不能直接給路徑或 URL。
5. **Element 註冊與引用**:定稿後用 `show_reference_elements(action='create', medias=[{id: <定稿 image_job id>, type: 'image_job', url: <定稿圖 https url>}], name: '<製作標題>_<名稱>', category: character/environment/prop)` 註冊。之後的 `generate_image`/`generate_video` 在 prompt 內嵌 `<<<element_id>>>` 即可代入該 element(平台自動改寫為 `@element_name`,一條 prompt 可嵌多個);支援模型含 nano_banana_2、seedream、kling、cinema studio 系列——Soul V2 不支援,勿混用。
