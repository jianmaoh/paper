# PDF 高亮與筆記提取結果

### Page: 1
- **Highlight**: freight
- **comment**: 我的經驗告訴我，很少在演算法的 paper 裡面出現這個字。

---

### Page: 1
- **Highlight**: where the ﬂow on each (edge, time) pair must be rounded up to a whole truck.
- **comment**: 我覺得這句應該可以刪掉

---

### Page: 1
- **Highlight**: dual
- **comment**: 在演算法領域裡面，Dual 常常是用在其他的情境，所以我會建議避免使用 Dual 這個詞。

---

### Page: 1
- **Highlight**: dual
- **comment**: 同上，避免使用「dual」。

---

### Page: 1
- **Highlight**: the canonical route is a temporal path, whether the endpoints lie in one strongly connected component or across several—and that every backbone edge carries at most two distinct departure labels, so that fractional ﬂows from diﬀerent demands genuinely share trucks.
- **comment**: 我看不太懂這邊要寫什麼。事實上，Abstract 應該是講重點就好，所以我的直覺是，雖然我看不懂這在寫什麼，但我覺得這個可以不用寫。

---

### Page: 1
- **Highlight**: a splitting threshold θ
- **comment**: 這裡突然間冒出一個 splitting threshold，不知道在做什麼？

---

### Page: 1
- **Highlight**: Minimum Aged Labelling
- **comment**: 我知道你到時候論文前面可能還有 introduction 之類的，但是就這一個文件裡面，你都還沒有定義什麼是 minimal edge labeling，然後就說你會去 augment 它，我覺得對讀者來講會無法理解。

---

### Page: 1
- **Highlight**: h truck-
- **comment**: 這可以刪掉

---

### Page: 1
- **Highlight**: the routing
- **comment**: 這裡的 the routing，不知道你的 the routing 是在指誰。  我猜你要說的應該是 f_i？

---

### Page: 2
- **Highlight**: Trucks
- **comment**: 我覺得把題目透過卡車來定義是有點奇怪。  非正式的定義我覺得是 OK，可能前面想要給大家一些 example、一些應用，提到 trucks 是很合理的。但是問題的正式定義應該不會出現 trucks。  另外，前面都在提 f_i，然後這邊突然間跳到 trucks，我覺得很奇怪。  其實你就是把式子(1)交代出來，然後再去解釋為什麼要minimize (1)？

---

### Page: 2
- **Highlight**: Backbone via Directed Steiner Forest
- **comment**: 我覺得這邊你傳遞了兩個資訊：  1. 第一個是去解釋什麼是 Directed Steiner Forest 2. 第二個是你去解釋了你自己用的 subroutine「Build Backbone」  我會建議把這兩個資訊分開，先講什麼是 Directed Steiner Forest，然後在其他地方再去講你怎麼建那個 Backbone。

---

### Page: 2
- **Highlight**: {(src(di), dst(di))}h i= =1
- **comment**: 現在合在一起講的缺點，就是像這個地方 source destination，就不知道是在指 DSF 的 source destination，還是你的問題的 source destination。  當然，如果硬要看，我是可以分辨得出來，但對讀者來講，這就不是最友善的閱讀方式。

---

### Page: 2
- **Highlight**: consistent with our omission of release times
- **comment**: 這一句很明顯是不應該出現在 paper 裡面，這個一看就知道是你之前跟 AI 對話的東西。

---

### Page: 2
- **Highlight**: λ(vk−1vk).
- **comment**: 我不確定你的 notation lambda 裡面要放的是什麼，但是直覺告訴我，不會是放兩個 vertex 然後直接連接在一起。

---

### Page: 2
- **Highlight**: len(SPs,t) for the number of edges on the shortest path.
- **comment**: 你後面的定義都沒有提到 $SP_{s,t}$。  記得每次在定義一個東西，那個符號裡面有出現的 input 或上標、下標，都應該出現在你的定義裡面。

---

### Page: 2
- **Highlight**: Assign
- **comment**: 整篇 paper 第一次出現這個 function，所以讀者會完全不知道為什麼會有這個 function，還有為什麼你要去解釋它。

---

### Page: 3
- **Highlight**: Temporal Feasibility and the Two-Label Guarantee
- **comment**: 這個 section 的 title 會讓人家讀起來感覺是在做分析或證明，但其實你演算法都還沒講完。

---

### Page: 3
- **Highlight**: Assumption 1 (Free store-and-forward). Freight may wait at any node for an arbitrary time at no cost. This is consistent with the objective (1), which charges only for trucks dispatched on edges and never for freight resting at a node.
- **comment**: 這個其實你在前面的 abstract 就出現過了。那我那時候不知道為什麼要寫這個，然後讀到這邊你正式定義之後，我還是不知道為什麼要定義這個

---

### Page: 3
- **Highlight**: Deﬁnition 1 (Temporal path). Let (G, λ) be a temporal graph: a digraph G = (V, E) together with a label function λ : E →2Z≥0, where λ(e) ⊆Z≥0 = {0, 1, 2, . . . } is the set of available times (labels) of edge e. A temporal path from u to v is a sequence (e1, t1), (e2, t2), . . . , (eℓ, tℓ) subject to the two conditions • Path connectivity: each ei ∈E, and e1e2 · · · eℓ is a walk from u to v in G; • Time monotonicity: ti ∈λ(ei) for every i, and, writing ei = (vi, vi+1), ti+1 ≥ti + w(ei) (1 ≤i < ℓ). The monotonicity condition encodes travel time: departing vi at ti, the freight reaches vi+1 at time ti +w(ei), so the next departure ti+1 must be no earlier than that arrival. (In the classical unit-time case w ≡1 it reduces to the strict increase t1 < t2 < · · · < tℓ.) We call (G, λ) temporally connected on a set of vertex pairs if every such pair admits a temporal path.
- **comment**: 很明顯的，這些定義需要更早出現，因為你在前面的地方講演算法或講問題定義的時候就用過了。  我不確定你是怎麼用 AI 寫這篇 paper 的，但我現在讀起來的感覺是，你想到什麼、忘記什麼，就補什麼。不太管出現的位置在哪裡才合適

---

### Page: 3
- **Highlight**: Algorithm 1 θ-Threshold Dual-Track Flow Splitting
- **comment**: 上面的 overview 應該要加一句話說，pseudocode放在 Algorithm 1。  然後前面的解釋，最好可以 refer 到這個 Algorithm 1 的行號。

---

### Page: 4
- **Highlight**: strongly connected component (SCC) of ESF
- **comment**: 我們通常不會說一個 edge set 的 SCC，我們只會說一個 graph 的 SCC。

---

### Page: 4
- **Highlight**: Because ESF[Ci] is strongly connected, every vertex both reaches and is reached from hi using only edges of ESF, so these distances are ﬁnite and admit shortest-path arborescences (i) th ha at span Ci and consist solely of ESF edges:
- **comment**: 我不知道寫這段要幹嘛。從文句的架構來看，你似乎是要帶出後面的 intree 跟 outree，但我覺得就直接講 intree 跟 outree 是什麼就好了，我不確定解釋這些會有什麼幫助？

---

### Page: 4
- **Highlight**: these are exactly the recurrences invoked in Lemma 1 (i)
- **comment**: 你先前沒有先給前情提要，說明lemma 1在做什麼，所以我不知道為什麼要在這邊講lemma 1。

---

### Page: 4
- **Highlight**: uses only labelled edges.
- **comment**: 看不太懂，因為你到目前為止都還沒有 assign label。  我覺得從第一頁第一行一直讀到這邊，一直反覆出現的問題是，我不確定你提供資訊的位置是否正確。  這感覺好像是，為了要讀懂這篇 paper，讀者還需要另外一份指引，告訴大家要先去看第幾頁的什麼、再去看第幾頁的什麼。這變成不是線性的閱讀，而是要跳著讀。  但我們讀 paper 預設（default）的閱讀方式就是要線性地讀，你必須讓依序閱讀文章的讀者能夠看得懂。但你這邊已經很多次，提供的資訊都出現在很奇怪的位置。

---

### Page: 4
- **Highlight**: cross edge
- **comment**: 跟前面一樣出現的問題，就是你 notation 出現的 input 沒有出現在定義裡面。你這邊有出現的 input 除了 x 之外還有 y，但是你後面後續的解釋都沒有提到 y。當然我猜得到這個 y 指的是你的 crossing edge 是從 x 到 y，但是無論如何，目前的寫法都是不好的。

---

### Page: 4
- **Highlight**: Ti
- **comment**: T_i 根本還沒有定義，又再一次出現了剛才的問題：資訊出現的位置很奇怪，資訊出現的位置是錯的。

---

### Page: 5
- **Highlight**: Algorithm 2 Global Dual-Label Construction 1: function Assign-Dual-Labels(ESF, w)
- **comment**: Algorithm 2 的 title 應該就直接寫 Assign Dual Labels，不需要再額外一個 function，所以第一行就可以刪掉。  然後一樣，前面的解釋都沒有 refer 到 Algorithm 2

---

