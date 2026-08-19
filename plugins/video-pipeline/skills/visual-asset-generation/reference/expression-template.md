# 角色表情集 expression sheet 通用模板

四段結構(任務句鎖不可變項 → 版面約束 → 角色/表情描述 → 風格鎖定+負面約束)。`{...}` 為填空槽,其餘一字不改。

**表情內容不用罐頭全套(喜怒哀樂),由劇本與角色設定挑選**:先從發想紀錄/劇本列出「劇情實際用到的情緒清單」給使用者確認,再填入模板;每個表情都要能對應到劇中某一刻。

## 模板 A:有參考圖(首選)

```
Generate a character expression sheet based on the uploaded reference image, keeping the same art style, brushwork, lighting treatment, color palette, facial structure, and character proportions unchanged.

The image should be a single canvas with {N} head-and-shoulders portraits of the same character arranged in a grid of {列數} rows, all facing front or slight 3/4 angle, identical hairstyle, headwear, and outfit in every portrait. Only the facial expression changes between portraits.

The character is {一句角色定位} with {膚色/膚質}, {髮型髮色}, {臉部固定特徵:眼型/眉/唇/疤痕/妝}. {He/She} wears {頭肩範圍看得到的服裝/頭飾,綁材質+顏色}.

The {N} expressions are:
1. {表情名} — {具體臉部動作描述:眉/眼/嘴各自的狀態}, conveying {劇中對應情緒,例:the calm reassurance when she says "it won't hurt"}
2. {表情名} — {...}
3. {表情名} — {...}
{...}

Keep the art style consistent with the reference: {風格關鍵詞 3-5 個}, and a clean {white/light gray} background. Do not convert to {相鄰風格漂移防線}, do not change the hairstyle, outfit, or face shape between portraits, do not add background elements, and do not include text, labels, or panels. All portraits must have identical proportions, identical lighting direction, and clearly readable facial details.
```

## 模板 B:無參考圖(純文字)

第一段改為:

```
Character expression sheet of {角色名}, showing {N} head-and-shoulders portraits of the same character arranged in a grid, all facing front or slight 3/4 angle, identical hairstyle and outfit, only the facial expression changes.
```

其後沿用模板 A 的第 3、4、5 段;風格段開頭改為 `Art style: {完整風格描述}`,並補 `Color palette: {3-5 個主色}`。

## 表情槽的寫法(關鍵)

每個表情一行,固定三件事:

1. **表情名**:簡短英文(soft reassuring smile / gritted-teeth pain / silent resolve)
2. **臉部動作拆解**:眉、眼、嘴分開講——這是穩定度來源,只寫 "sad" 模型會自由發揮
3. **劇中錨點**:conveying 之後接這個表情在劇裡的時刻,讓表情帶角色的性格而非通用情緒

範例(奧羅拉):
```
1. Soft reassuring smile — gentle eyes slightly narrowed, calm relaxed brows, a faint warm smile, conveying the quiet tenderness when she tells a frightened child "it won't hurt"
2. Resolute gaze — eyes wide open and steady, brows firm, lips pressed into a thin line, conveying her unshakable will the moment before she releases her light
```

## 填空槽清單

| 槽位 | 內容 | 來源 |
|---|---|---|
| N / 列數 | 表情數量與排版(建議 4-6 個,2×2 或 2×3) | 劇情盤點結果 |
| 角色定位句+臉部固定特徵 | 與五視圖模板同源,可直接沿用 | 角色設定小抄 |
| 頭肩服裝 | 只描述入鏡範圍 | 角色設定/參考圖 |
| 表情清單 | 表情名+眉眼嘴拆解+劇中錨點 | 劇本實際用到的情緒(先給使用者確認) |
| 風格關鍵詞/漂移防線/背景色 | 與五視圖模板共用同一組值 | 風格基底.md |

## 檢核(每條 prompt 出手前)

- [ ] 任務句是否鎖了 facial structure(表情集比五視圖多鎖這一項,防臉型漂移)
- [ ] 是否指定「只有表情變,髮型/服裝/臉型不變」
- [ ] 每個表情是否拆解了眉/眼/嘴,而非只給情緒詞
- [ ] 每個表情是否有劇中錨點(conveying ...)
- [ ] 表情清單是否先經使用者確認,而非罐頭全套
- [ ] 負面清單是否含「不得改變髮型服裝臉型」+ 禁背景/文字標籤
