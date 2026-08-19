# 場景延伸/視角通用模板

依 `prompt-structure.md` 的四段結構構成。`{...}` 為填空槽,其餘一字不改。

**定位**:主場景建立圖(`scene-main-template.md` 產出)定調後,同一場景的**新區域(延伸)**或**同區域換機位(視角)**都用此模板——兩者共用,差別只在第二段填「空間關係」還是「機位」。一律以主場景圖為參考圖,不從文字重建。

**輸入**:主場景圖(上傳為 reference)+ 主場景的標誌性元素清單 + 風格基底。變因單一化:只放行「區域/機位」,建築風格、材質、光線、時段全鎖。

## 模板

```
Generate a scene concept art based on the uploaded reference image, keeping the same art style, brushwork, lighting treatment, color palette, architectural style, and materials unchanged. This is {a different area of / a different camera angle of} the same location as the reference.

The image shows: {延伸→新區域與參考圖的空間關係+新區域內容,例:the entrance hall connected to the main nave shown in the reference / 視角→明確機位詞:low-angle looking up at the vaulted ceiling / top-down overhead view / POV from beneath a fallen pew}. {該畫面的構圖重點與入鏡元素}. Reuse the signature elements from the reference where visible: {主場景的標誌性元素點名}.

Art style, lighting direction, and atmosphere must exactly match the reference. Empty scene with no characters. Do not redesign the architecture, do not change the time of day or weather, do not include text, labels, or panels. Consistent perspective and unified lighting direction.
```

## 第二段的寫法(關鍵)

- **延伸(新區域)**:必寫「與參考圖的空間關係」(connected to / behind / beneath / outside)——沒有空間關係,模型會生成一個「風格像但拓撲無關」的新場景。
- **視角(換機位)**:用明確機位詞(low-angle / top-down / POV from…),並點名這個機位下哪些標誌性元素會入鏡。
- **POV/視角必寫「看向哪裡」且與敘事動線一致**:先問劇情裡這顆鏡頭觀眾要看到什麼(誰從哪裡來/往哪裡去),朝向寫錯的視角圖在影片生成時會把空間邏輯整個帶反(實戰教訓 2026-07-28:朝祭壇的孩童 POV 被當「看她從大門進場」的 start_image,兩個模型都被帶溝)。同一藏身處往往需要多張不同朝向的 POV(朝門=看她進場、朝祭壇=看她儀式),盤點時分開列。
- **POV 機位必寫「機位物在場景中的位置」**:只寫視線方向(looking down the nave)模型會把藏身物/機位放在拓撲矛盾的位置(例:躲藏的長椅出現在淨空的走道中央)。要寫成「from beneath a pew **lying among the scattered pews along the side**, looking **diagonally across** …」,並加一句 `The camera position must be consistent with the reference layout: …`(實戰教訓 2026-07-27)。
- **標誌性元素必重複點名**:延伸與視角靠它們證明「還是同一個場景」,這是場景一致性最容易被忽略的一環。

範例(大教堂・視角:孩童主觀):
```
The image shows: POV from beneath an overturned wooden pew, low to the ground, looking down the main nave toward the marble altar with faint golden engravings. Overturned pews frame the foreground; the blackened stained glass windows loom high above in the background. Reuse the signature elements from the reference where visible: the blackened stained glass windows, the scattered overturned pews, the gold-engraved marble altar.
```

## 填空槽清單

| 槽位 | 內容 | 來源 |
|---|---|---|
| 延伸/視角二選一 | a different area of / a different camera angle of | 步驟 1 盤點結果 |
| 空間關係 or 機位詞 | 與參考圖的相對位置 / 明確機位 | 劇本的畫面需求 |
| 構圖重點與入鏡元素 | 這張圖為了劇中哪個畫面 | 劇本 |
| 標誌性元素 | 沿用主場景模板定稿的那 2-3 個,逐字一致 | scene-main 產出 |

## 檢核(出手前)

- [ ] 任務句是否鎖了 architectural style + materials
- [ ] 延伸是否寫明空間關係;視角是否用明確機位詞
- [ ] 是否重複點名主場景的標誌性元素(逐字沿用,不改寫)
- [ ] 是否鎖死時段與天候(do not change the time of day or weather)
- [ ] 是否指定 empty scene / no characters
- [ ] 變因是否只有一組(區域或機位),其餘全鎖
