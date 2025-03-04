---
title: 以太坊擴容
description: 卷軸可在鏈外批次處理交易，從而降低使用者的成本。 但現今卷軸使用資料的方式還是過於昂貴，限制了交易金額的下限。 Proto-Danksharding 可以解決這個問題。
lang: zh-tw
image: ../../../../../assets/roadmap/roadmap-transactions.png
alt: "以太坊開發藍圖"
template: roadmap
---

以太坊利用[二層網路](/layer-2/#rollups)（也稱「卷軸」）實現擴容，可批次處理交易並將輸出傳送至以太坊。 儘管成本已比以太坊主網低八倍，卷軸還有進一步最佳化的空間，進而幫助降低最終使用者的成本。 此外，卷軸還仰賴於一些中心化組件，隨著其不斷發展成熟，開發者可以移除這些組件。

<InfoBanner mb={8} title="交易成本">
  <ul style="margin-bottom: 0">
    <li>現今卷軸的成本比以太坊一層網路便宜<strong>大約 3-8 倍</strong></li>
    <li>ZK 卷軸很快會讓費用降低<strong>大約 40-100 倍</strong></li>
    <li>以太坊即將更動，會帶來<strong>大約 100-1000 倍</strong>的擴容</li>
    <li style="margin-bottom: 0">使用者應該能夠從<strong>成本低於 $0.001</strong> 的交易中受益</li>
  </ul>
</InfoBanner>

## 降低資料使用費用 {#making-data-cheaper}

卷軸會集合大量交易，執行它們並將結果提交到以太坊。 這會產生大量需要公開的資料，以便所有人都可以自己執行交易並驗證卷軸營運者是否誠實。 若有人發現矛盾之處，可以提起質詢。

### Proto-Danksharding {#proto-danksharding}

卷軸資料會永久儲存在以太坊上，成本非常高昂。 使用者為卷軸支付的交易費用中，超過 90% 都是花在資料儲存上。 為了降低交易費用，我們可以將資料移至新的「blob」（註：二進位大型物件）臨時儲存區。 Blob 更便宜，因為它們不是永久性的，一旦不再需要，就會從以太坊中刪除。 長期儲存卷軸資料成為需要它的人的責任，例如卷軸營運者、交易所、索引服務等。 將 blob 交易新增至以太坊是「Proto-Danksharding」升級的一部分。 我們預計這一功能很快（可能在 2023 年年底）會發佈。

當 blob 交易透過「Proto-Danksharding」成為以太坊協定的一部分後，可以將多個 blob 新增至以太坊區塊。 這將是以太坊吞吐量的又一次大幅（>100 倍）擴容和交易成本的縮減。

### Danksharding {#danksharding}

擴展 blob 資料的第二階段很複雜，因為需要新的方法來檢查網路上可用的卷軸資料，並仰賴驗證者將其區塊構建和區塊提案職責分開。 它還需要一種方法來以加密方式證明驗證者已驗證一小部分 blob 資料。

這個第二步也稱作[「Danksharding」](/roadmap/danksharding/)， 全面實作可能還需要數年時間。 Danksharding 還需要仰賴其他的技術開發，例如[將區塊構建和區塊提案分開](/roadmap/pbs)，以及新的網路設計，使得網路能夠透過一次隨機採樣幾千字節來有效地確認資料可用（也稱作[資料可用性採樣，簡稱 DAS](/developers/docs/data-availability)）。

<ButtonLink variant="outline-color" to="/roadmap/danksharding/">有關分片的更多資訊</ButtonLink>

## 卷軸去中心化 {#decentralizing-rollups}

[卷軸](/layer-2)已在推動以太坊擴容。 憑藉[豐富的卷軸專案生態系統](https://l2beat.com/scaling/tvl)，使用者可以在有安全保證的狀況下快速實惠地完成交易。 然而，一直以來卷軸都是使用中心化排序者（先完成所有交易處理和匯總，再將結果提交至以太坊的電腦）啟動的。 這讓審查制度變得十分脆弱，因為排序者營運者可能被制裁、賄賂或者做出其他讓步。 同時，[卷軸也會採取不同方式](https://l2beat.com)驗證傳入的資料。 最好的方法是「證明者」提交欺詐證明或有效性證明，但並非所有卷軸都已存在。 即使是確實使用有效性/欺詐證明的卷軸也只使用一小部分已知的證明者。 因此，以太坊擴容的下一個關鍵步驟就是將運行排序者和證明者的責任分配給更多人。

<ButtonLink variant="outline-color" to="/developers/docs/scaling/">關於卷軸的更多資訊</ButtonLink>

## 目前進度 {#current-progress}

Proto-Danksharding 可能是較早實作的開發藍圖專案之一。 設定它所需的去中心化計算步驟已在進行當中，有些用戶端已經實作處理 blob 資料的原型。 完整的 Danksharding 可能還需要幾年的時間，因為它要求先完成其他幾個開發藍圖專案。 卷軸基礎設施的去中心化可能是一個漸進的過程，有許多不同的卷軸正在構建略有不同的系統，並將以不同的速率完全去中心化。
