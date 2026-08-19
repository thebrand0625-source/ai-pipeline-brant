# 角色姿態/動作 pose 通用模板

沿用 compare/c1-c5 萃取的四段結構(任務句鎖不可變項 → 版面/動作約束 → 角色描述 → 風格鎖定+負面約束)。`{...}` 為填空槽,其餘一字不改。

**與視角/表情組的差異**:動作是「一個動作一條 prompt、單張全身圖」,不是集合圖——動作彼此差異大,塞同一張畫布會互相干擾;影片素材也需要單張取用。動作清單依劇本關鍵時刻挑選(招牌動作優先),先經使用者確認。

**參考圖可以有多張**:角色五視圖(定形)為主參考;若該動作的表情已在表情集中生成過,把表情集也一併上傳作為第二參考,prompt 中指名用哪一格。

## 模板 A:有參考圖(首選)

```
Generate a full-body action pose illustration based on the uploaded reference images, keeping the same art style, brushwork, lighting treatment, color palette, facial structure, outfit design, and character proportions unchanged. Use the character turnaround sheet as the primary reference for the character's design{有表情參考時加:, and match the facial expression to portrait #{編號} ({表情名}) in the uploaded expression sheet}.

The image should be a single full-body illustration of the character in the following pose: {動作核心一句話,例:mid-leap forward with her light erupting from her back}. Body: {軀幹/重心/腿的狀態}. Arms and hands: {雙手各自在做什麼,含手持物}. {Head/gaze 朝向}. {沒有表情參考時加:Facial expression: {眉/眼/嘴拆解}, conveying {劇中錨點}.}{動作有特效時加: {光效/粒子/披風飄動等,綁顏色}.}

The character is {一句角色定位} wearing {服裝一句摘要——細節以參考圖為準,只點名關鍵件+顏色}. The outfit, hairstyle, and accessories must exactly match the reference turnaround.

Keep the art style consistent with the reference: {風格關鍵詞 3-5 個}, and a clean {white/light gray} background. Do not convert to {相鄰風格漂移防線}, do not redesign or simplify the outfit, do not add background elements, and do not include text, labels, or panels. The character must be fully visible from head to toe, with correct anatomy in the dynamic pose, consistent proportions with the reference, and a single unified lighting direction.
```

## 模板 B:無參考圖(純文字)

第一段改為:

```
Full-body action pose illustration of {角色名}, single character on a clean background, in the following pose: {動作核心一句話}.
```

角色段改用五視圖模板 B 的完整外觀描述(由上而下、材質+顏色),風格段開頭改 `Art style: {完整風格描述}` 並補 `Color palette: {3-5 個主色}`。

## 動作槽的寫法(關鍵)

每個動作固定拆四件事——只寫 "attacking pose" 模型會自由發揮:

1. **動作核心一句話**:這一瞬間在做什麼(mid-leap / kneeling after impact / walking away)
2. **身體拆解**:軀幹重心、腿、雙手(含手持物)、頭與視線,分開講
3. **表情來源**:二選一——指名表情集第幾格,或現場給眉/眼/嘴拆解+劇中錨點
4. **特效與布料**:光效、粒子、披風/裙擺的飄動方向,綁顏色(動態感主要來自這裡)

範例(奧羅拉《教堂裡的光》):
```
pose: kneeling at the altar in prayer, back straight, both knees on the stone floor. Arms and hands: both hands clasped together at chest height, the removed left glove lying beside her on the altar. Head bowed, eyes closed. Match the facial expression to portrait #3 (silent resolve) in the uploaded expression sheet. Her white umbrella leans closed against the altar; faint golden light beginning to seep from the seams of her back.
```

## 填空槽清單

| 槽位 | 內容 | 來源 |
|---|---|---|
| 動作清單 | 每個動作:核心句+身體拆解+表情來源+特效布料 | 劇本關鍵時刻(先給使用者確認) |
| 表情參考編號 | 表情集第幾格+表情名;沒有就現場拆眉/眼/嘴 | 已生成的表情集 |
| 角色定位+服裝摘要 | 細節交給參考圖,只點名關鍵件防漏 | 角色設定小抄/五視圖 |
| 風格關鍵詞/漂移防線/背景色 | 與五視圖、表情模板共用同一組值 | 風格基底.md |

## 已知反模式(實戰教訓 2026-07-28)

- **兒童+受難情緒詞觸發平台安全過濾**:terrified / tears / desperate / crying 搭配 child 會被生成平台整批擋下(status: nsfw)。寫法:情緒強度詞降級(hiding quietly / calling out),恐懼感由場景氛圍與分鏡承擔,不寫在孩童身上。
- **遮擋+交錯肢體=肢體複製高發**:「半身藏在物件下+左右交錯爬姿」易生成四隻腳。寫法:讓角色完全露出、肢體姿勢對稱化(雙膝跪地),遮擋物改為手扶道具,並在負面清單加 extra limbs / duplicated legs。

## 檢核(每條 prompt 出手前)

- [ ] 任務句是否鎖了 facial structure + outfit design(動作組最易在動態下重畫服裝)
- [ ] 是否指名主參考(turnaround);有表情集時是否指名第幾格
- [ ] 動作是否拆解了軀幹/腿/雙手/頭視線,而非只給動作詞
- [ ] 表情是否有來源(參考格 or 眉眼嘴拆解+劇中錨點)
- [ ] 是否有 correct anatomy in the dynamic pose 檢核句(動態姿勢是解剖錯誤高發區)
- [ ] 負面清單是否含「不得重新設計/簡化服裝」+ 禁背景/文字標籤
