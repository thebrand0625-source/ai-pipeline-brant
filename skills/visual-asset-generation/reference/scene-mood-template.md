# 場景氛圍調整通用模板

依 `prompt-structure.md` 的四段結構構成。`{...}` 為填空槽,其餘一字不改。

**定位**:同一鏡頭的**狀態變化**(例:被侵蝕→淨化後、白天→夜晚、平靜→戰後)。用途是前後對比,因此不可變項與延伸/視角模板剛好相反:**鎖死構圖+機位+建築,只放行光線/氛圍/天候**——構圖跑掉,對比就廢了。

**輸入**:要變化的那張場景圖(主場景或某延伸/視角圖,上傳為 reference)+ 風格基底。

## 模板

```
Generate a scene concept art based on the uploaded reference image, keeping the same composition, camera angle, architectural structure, materials, and art style completely unchanged. Only the atmosphere, lighting, and weather change.

Transform the mood to: {目標氛圍一句話,例:the moment of purification — every stained glass window blazing with golden light}. Lighting: {新主光源+方向+色溫}. Atmosphere: {新的空氣狀態:霧散/粒子/光束,綁顏色}. {狀態變化元素點名:哪些東西變了、變成什麼,例:the black mist evaporating into golden embers}. Everything else — architecture, layout, camera position — must remain identical to the reference.

Do not move or redesign any structure, do not change the camera angle or composition, do not add characters, and do not include text, labels, or panels.
```

## 第二段的寫法(關鍵)

1. **目標氛圍一句話**:對應劇情轉折點,不是抽象形容(「淨化的瞬間」而非「變亮」)。
2. **光源必綁方向+色溫**:氛圍變化九成是光的變化,寫法與主場景模板的 Lighting 槽同規格,方便前後對照。
3. **狀態變化元素逐一點名**:哪些東西變了、變成什麼(黑霧→金色餘燼);**沒點名的默認不變**,並用 remain identical 句收尾兜底。
4. 標誌性元素若有狀態變化(黑彩窗→點亮的彩窗),在這裡寫清楚變化前後,不要只寫結果。

範例(大教堂・淨化後):
```
Transform the mood to: the moment of purification — every stained glass window blazing with warm golden light, like the cathedral opening its eyes. Lighting: brilliant golden light pouring inward from all windows, soft volumetric god rays, warm high-key illumination replacing the cold darkness. Atmosphere: the black mist evaporating into drifting golden embers, faint dust sparkling in the light beams. The fallen pews and altar remain exactly where they were, now rim-lit in gold.
```

## 填空槽清單

| 槽位 | 內容 | 來源 |
|---|---|---|
| 目標氛圍一句話 | 對應的劇情轉折點 | 劇本 |
| 新光源/新氛圍 | 光源+方向+色溫;粒子綁顏色 | 劇情情緒 |
| 狀態變化元素 | 變化前→變化後逐一點名 | 主場景的標誌性元素+劇情 |

## 檢核(出手前)

- [ ] 任務句是否鎖死 composition + camera angle + structure + materials
- [ ] 變因是否只放行光線/氛圍/天候
- [ ] 光源是否綁方向+色溫
- [ ] 狀態變化元素是否逐一點名(含標誌性元素的前後狀態)
- [ ] 是否有 remain identical 兜底句
- [ ] 負面清單是否含「不得移動/重設計結構」「不得改機位構圖」+ 禁角色/文字標籤
