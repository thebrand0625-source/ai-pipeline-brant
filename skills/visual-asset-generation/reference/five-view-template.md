# 角色五視圖 turnaround 通用模板

固定四段結構,每段各防一種失敗模式;`{...}` 為填空槽,其餘一字不改。

## 模板 A:有參考圖(首選)

```
Generate a 5-view character turnaround sheet based on the uploaded reference image, keeping the same art style, brushwork, lighting treatment, color palette, and character proportions unchanged.

The image should be a single wide canvas with 5 views arranged in a row: front view, front 3/4 view, side view, back 3/4 view, and back view. All views should use the same neutral standing pose. Hands may either keep {招牌手勢描述,例:the floating flame magic effect / one hand tucked into the trouser pocket}, or be simplified into a relaxed pose with both arms lowered at {his/her} sides, for a clearer turnaround.

The character is {一句角色定位,例:a classic Gothic vampire count} with {膚色/膚質}, {髮型髮色}, {臉部特徵}. {He/She} wears {由上而下逐件描述服裝:每件綁材質+顏色,上身→腰→下身→鞋}. {手持物/特效,可省略}. {His/Her} overall presence feels {整體氣質 2-3 個形容,例:elegant, dangerous, and ancient aristocratic authority}.

Keep the art style consistent with the reference: {風格關鍵詞 3-5 個,例:semi-realistic painterly rendering, soft gradient shading, detailed fabric texture, refined facial rendering}, and a clean {white/light gray} background. Do not convert to {要防的風格漂移,例:flat comic-cel style or 3D render style}, do not add complex background elements, and do not include text, labels, or panels. The character must be fully visible from head to toe in all five views, with consistent proportions, unified lighting direction, and clearly readable details.
```

## 模板 B:無參考圖(純文字)

第一段改為:

```
Character turnaround sheet of {角色名}, showing 5 views arranged in a single horizontal row: front view, front 3/4 view, side profile view, back 3/4 view, and back view. All poses are identical standing poses with a neutral stance.
```

其後沿用模板 A 的第 3、4 段(角色描述、風格鎖定+負面約束),風格段開頭改成 `Art style: {完整風格描述}`,並補上色盤:`Color palette: {3-5 個主色}`。

## 填空槽清單

| 槽位 | 內容 | 來源 |
|---|---|---|
| 招牌手勢 | 保留 or 簡化的二選一 | 參考圖/角色設定 |
| 角色定位句 | 一句話身分 | 角色設定小抄 |
| 外觀逐件描述 | 由上而下,每件綁材質+顏色 | 角色設定/參考圖 |
| 整體氣質 | 2-3 個形容詞 | 角色設定 |
| 風格關鍵詞 | 3-5 個 | 風格基底.md |
| 風格漂移防線 | 「不得轉成 X 風格」——填與本風格最近的相鄰風格 | 風格基底.md |
| 背景色 | white / light gray | 依角色主色挑對比 |

## 檢核(每條 prompt 出手前)

- [ ] 開頭是否鎖了 art style / brushwork / lighting / proportions 四個不可變項(有參考圖時)
- [ ] 五視圖是否逐一點名且指定同一中立站姿
- [ ] 手部是否給了二選一,而非放任自由
- [ ] 每件服裝是否都綁了材質+顏色
- [ ] 是否有負面清單(禁風格漂移/禁背景/禁文字標籤)
- [ ] 是否有收尾檢核句(全身入鏡、比例一致、光源統一)

反模式清單見 `prompt-structure.md`。
