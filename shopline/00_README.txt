ruff. 藍夫｜SHOPLINE 部落格上稿指南
====================================

【結論】用 05_shopline_final.html，其他檔案留作紀錄
------------------------------------------------
貼法：文章編輯器 > 按 <> 進 HTML 模式 > 貼上 > 再按 <> 切回一般模式 > 儲存
（HTML 模式下不能直接按儲存，SHOPLINE 會擋）


SHOPLINE 實測出來的樣式白名單（2026/09 驗證）
--------------------------------------------
這是「存檔後重新載入」實測的結果，伺服器端比編輯器更嚴。

✅ 可用
   background-color（含 rgba）
   color
   border / border-top / border-left
   padding / margin
   width / max-width
   text-align / vertical-align
   line-height / font-size / letter-spacing
   float
   overflow
   <table> <td>：td 的 background-color / padding / width / vertical-align 全部保留
   <img> 的 width
   <a> 的 background-color / color / padding / text-decoration

❌ 會被拔掉
   <style> 標籤（整段消失，所以不能用 class）
   display 全系列（flex / inline-block / table-cell 都不行）
   background 簡寫（要寫成 background-color）
   background-image（含 linear-gradient，所以沒有漸層）
   border-radius（沒有圓角）
   box-shadow（沒有陰影）
   font-weight（會被轉成 <strong>）
   <video>（影片標籤整個消失）
   <figure> / <blockquote>（會被轉成 <p> 並丟掉樣式）
   <span> 的 background-color 與 color（要改用 <strong>）
   <b>（會被轉成 <strong>）


因此最終版做了這些調整
----------------------
1. 全部改行內樣式，不用 class
2. 漸層改純色：主題卡 #0041B3、引言與 CTA #002A6E
3. 圓角與陰影拿掉，改用邊框與背景色區隔
4. 多欄改法：VS 對照用 <table> 三欄（灰 / VS / 藍）；
   其餘卡片改單欄堆疊，手機閱讀反而更好
5. 三支產線影片移除（SHOPLINE 不吃 <video>），
   雷射裁切的內容改寫成文字段落保留
6. 兩張產線照片改上下排列，看得更清楚


待辦
----
1. 圖片目前指向 GitHub 預覽站，建議改上傳到 SHOPLINE 圖片庫再換網址：
   設定 > 圖片庫
2. 三支影片若要放，需上傳 YouTube（可設不公開）再用編輯器的影片按鈕嵌入
3. SEO 欄位見 01_seo_fields.txt
4. 發佈狀態目前是「隱藏」，確認後自行改成「發佈」


檔案
----
05_shopline_final.html   ← 實際貼上的版本（已上稿）
04_inline_for_shopline.html  行內化中間版本（含漸層與 flex，SHOPLINE 不支援）
01_shopline_paste.txt    最初的 <style> 版本（SHOPLINE 會拔掉 style，不可用）
02_css_only.txt / 03_body_only.txt  拆開版（SHOPLINE 無自訂 CSS 欄位，不可用）
preview.html             瀏覽器渲染確認頁
01_seo_fields.txt        SEO 欄位與媒體檔案清單
