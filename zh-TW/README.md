# 詳解 HTTP/3

撰寫此書的計畫始於2018年3月。 目的是要記錄 HTTP/3 及其基礎協定: QUIC。包含為什麼，它們是如何運作，協定的內容及如何實作...等等。

此書完全免費並且是協作的成果，代表著需要任何和所有想提供幫助的人共同努力。

## 前提

在閱讀此書前，我們期望您對 TCP/IP 網路架構，HTTP 和 Web 的基礎知識有基本的了解。
若想要進一步了解 HTTP/2，我們建議您先閱讀以下的內容 [http2 explained](https://daniel.haxx.se/http2/)。

## 作者

本書作者為 [Daniel Stenberg](https://daniel.haxx.se/)，他是世界上最流行的 HTTP 客戶端程式 [curl](https://curl.haxx.se/) 的創造者與領頭開發者。 Daniel 在 HTTP 與網路通訊協定中已有20多年的開發經驗，他也是 [詳解 HTTP/2](https://daniel.haxx.se/http2/) 的作者。

繁體中文譯者：[Wei Jhih Lian](https://github.com/ByronLian)

## 主頁

本書的主頁位於 [daniel.haxx.se/http3-explained](https://daniel.haxx.se/http3-explained)。

## 協助我們

如果您發現了本書中的任何錯字、遺漏或是錯誤的訊息內容，歡迎您將受影響章節的修正版本回報給我們，我們將根據情況修正。
我們將為提供幫助的每個人給予適當的表彰。同時我們希望隨著時間推移，此書的內容能越來越好。

您可以提交 [issue](https://github.com/bagder/http3-explained/issues) 或是 [pull request](https://github.com/bagder/http3-explained/pulls) 於此書的 GitHub 頁面。

## 許可協議

本文檔及其所有内容遵循 [Creative Commons Attribution 4.0 license](https://creativecommons.org/licenses/by/4.0/) 授權。
