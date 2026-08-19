# 主場景建立通用模板

依 `prompt-structure.md` 的四段結構構成。`{...}` 為填空槽,其餘一字不改。

**定位**:場景系的第一張、定調用——之後的延伸/視角(`scene-extend-template.md`)與氛圍調整(`scene-mood-template.md`)全部以這張圖為參考圖延伸,不從文字重建。地位等同角色系的五視圖。

**輸入**:風格槽一律取自已確認的 `風格基底.md`(與角色系共用同一組值);場景內容取自劇本/場景設定的主要場景,缺的視覺細節標 `(AI 提案)`。場景預設**無角色**(empty scene),人物由合成階段放入。

## 模板

```
Generate a scene concept art of {場景名一句話,例:a vast Gothic cathedral interior consumed by black mist}, wide establishing shot, eye-level view.

The scene contains: {由大到小逐層描述——空間結構(尺度/形狀)→ 主要構造物(綁材質+顏色)→ 標誌性元素 2-3 個(觀眾認得這是「這個」場景的記憶點)→ 地面/天空狀態}. Lighting: {主光源+方向+色溫,例:faint cold moonlight through blackened stained glass, deep shadows}. Atmosphere: {空氣中的東西:霧/塵/粒子,綁顏色}.

Art style: {風格關鍵詞 3-5 個,取自風格基底}. Color palette: {3-5 個主色}. Empty scene with no characters, no people. Do not convert to {相鄰風格漂移防線}, do not include text, labels, or panels. The scene must have a clear sense of scale, consistent perspective, and a single unified lighting direction.
```

## 場景描述的寫法(關鍵)

**由大到小四層**,對應角色系的「由上而下逐件綁材質顏色」:

1. 空間結構:尺度與形狀(vast / narrow / vaulted)
2. 主要構造物:每件綁材質+顏色
3. **標誌性元素 2-3 個(必填)**:之後所有延伸/視角/氛圍 prompt 都要重複點名它們,靠它們證明「還是同一個場景」(例:瞎掉的黑彩窗、傾倒的長椅、金紋祭壇)
4. 地面/天空狀態

範例(大教堂):
```
The scene contains: a vast Gothic cathedral interior with soaring vaulted ceilings and rows of stone columns. Towering stained glass windows turned completely black, like blinded eyes. Wooden pews overturned and scattered across the cracked stone floor. A marble altar with faint golden engravings at the far end of the nave. Black mist creeping along the floor and seeping from the walls.
```

## 填空槽清單

| 槽位 | 內容 | 來源 |
|---|---|---|
| 場景名一句話 | 場景定位 | 劇本/場景設定 |
| 四層場景描述 | 結構→構造物(材質+顏色)→標誌性元素→地面/天空 | 場景設定(缺的標 `(AI 提案)`) |
| 光源/氛圍 | 光源+方向+色溫;空氣粒子綁顏色 | 劇本的時間與情緒 |
| 風格關鍵詞/漂移防線/色盤 | **與角色系模板共用同一組值** | 風格基底.md |

## 檢核(出手前)

- [ ] 是否由大到小四層描述、構造物綁材質+顏色
- [ ] 是否點名 2-3 個標誌性元素
- [ ] 光源是否綁方向+色溫;是否有 unified lighting direction 檢核句
- [ ] 風格槽是否取自已確認的風格基底(不得現場另編)
- [ ] 是否指定 empty scene / no characters
- [ ] 負面清單是否含風格漂移防線+禁文字標籤
