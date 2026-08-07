# 論文結構問題整合分析

> 來源：老師 `260804_highlights.md` 的 27 條評語 ＋ 先前的「前向引用（forward reference）」結構分析。
> 目的：解釋**老師為什麼覺得「怪怪的」**，並把散落的評語歸納成少數幾個根因。
> 狀態：**純分析，論文尚未做任何改動。**

---

## 一、一句話總診斷

老師的 27 條評語看起來很零散，其實**絕大多數指向同一件事：這篇論文無法「線性閱讀」**——要看懂某一句，讀者常常得先跳到後面（甚至還沒寫的地方）才知道你在講什麼。

老師在第 4 頁 "uses only labelled edges" 那條把病根講得最白：

> 「為了要讀懂這篇 paper，讀者還需要另外一份指引，告訴大家要先去看第幾頁的什麼、再去看第幾頁的什麼。這變成不是線性的閱讀，而是要跳著讀。但我們讀 paper 預設的閱讀方式就是要線性地讀，你必須讓依序閱讀文章的讀者能夠看得懂。」

這跟我先前的結構分析結論**完全一致**：核心定義（temporal path、canonical route、`Assign-Dual-Labels`、$T_i$、MAL）都在「被使用」之後才定義。

---

## 二、根因分層（老師其實在講三個層次）

| 層次 | 病灶 | 佔比 | 老師的代表語 |
|---|---|---|---|
| **L1 資訊位置 / 前向引用**（最核心） | 定義出現在使用之後；章節職責錯置 | 最多 | 「你想到什麼、忘記什麼，就補什麼，不太管出現的位置在哪裡才合適」 |
| **L2 notation 不完整** | 符號裡的參數（上下標、input）沒在定義裡交代 | 中 | 「每次定義一個東西，那個符號裡出現的 input 或上標下標，都應該出現在你的定義裡面」 |
| **L3 表層（用詞 / 冗句 / AI 痕跡）** | freight/dual/trucks、該刪的句子、對話殘留 | 中 | 「這一句很明顯不應該出現在 paper 裡，一看就知道是你之前跟 AI 對話的東西」 |

**最深層的「為什麼」**：L1 是病根，L3 是讓老師「一眼看穿是 AI 拼湊」的表面證據。兩者其實同源——這份文件是**反覆 patch 出來的**：每次修一個問題（例如補嚴謹性、補一個假設），就地插入一段定義/假設，而不是回頭重排全域順序。於是定義落在「當初 patch 的地方」，不是「邏輯上該在的地方」。老師感覺到的「想到什麼補什麼」，正是這種 accretion（層層堆積）的痕跡。

---

## 三、L1：資訊位置 / 前向引用（逐條對應）

> 這一類最重要，且與我先前的分析點（標為 [先前#n]）幾乎一一對應。

| # | 頁 | 老師 highlight | 老師的意思 | 對應先前分析 | 為什麼是問題 |
|---|---|---|---|---|---|
| 7 | 1 | Minimum Aged Labelling | 還沒定義 MAL 就說要 augment 它 | 新增 | 讀者不知 MAL 是什麼，無法理解「加上 capacity」在加什麼 |
| 16 | 2 | Assign | 全篇第一次出現這 function，不知為何有它 | [先前#3] `Assign-Dual-Labels` 黑箱 | 呼叫一個還沒說明的子程序 |
| 17 | 3 | Section title「Temporal Feasibility…」 | 標題像在做分析/證明，但演算法還沒講完 | [先前 §2 把核心丟給 §3] | §3 身兼「補完演算法」＋「證明」兩職，標題與內容錯位 |
| 18 | 3 | Assumption 1（免費等待） | abstract 就冒出、正式定義後仍不知為何要它 | [先前#8] 全域假設放太後面 | 模型假設該在問題定義處就講，讀者才知道「等待免費」這個前提 |
| 19 | 3 | Definition 1（temporal path） | 定義需要更早出現，因為前面講演算法/問題時就用過 | [先前#2] temporal path 前向引用 | 核心詞彙在 §2 用、§3.1 才定義 |
| 23 | 4 | recurrences invoked in Lemma 1 | 沒先講 Lemma 1 在做什麼，就引用它 | [先前#9] | 引用一個讀者還沒讀到的引理 |
| 24 | 4 | uses only labelled edges | 到這裡都還沒 assign label（大段抱怨非線性） | [先前#5, 病根] | 用「labelled edges」時 label 尚未定義 |
| 26 | 4 | $T_i$ | $T_i$ 根本還沒定義 | [先前#4] §3.1 內部順序錯位 | 「Rooted trees」段用 $T_i$，但 $T_i$ 在下一段「Base times」才定義 |

**補充（我先前另外抓到、老師這次沒特別圈但同源的）**：
- Route-SF ↔ canonical route **互相循環定義**（§2 line 148–150 ↔ Definition 3 line 289）。這是 #16、#19 的更深層版本：連定義本身都互相依賴，讀者在 §2 完全無法得知「小數流量在骨幹上怎麼走」。
- 「terminal pair」從未正式定義，只在 DSF 段落隱約帶過。

---

## 四、L2：notation 定義不完整

> 老師的通則：**「符號裡出現的每個 input / 上下標，都要在定義裡交代」。**

| # | 頁 | highlight | 問題 | 對應先前 |
|---|---|---|---|---|
| 15 | 2 | len(SP$_{s,t}$) | 定義了 $\mathrm{len}(SP_{s,t})$，但後文只用 $\mathrm{len}(SP_i)$，$s,t$ 這組下標沒被用到／沒交代 | [先前#10] $\SP_{s,t}$ vs $\SP_i$ 符號不一致 |
| 25 | 4 | cross edge $t_{\mathrm{cross}}(x,y)$ | 定義有 $x,y$ 兩個 input，但後續解釋只講 $x$、沒講 $y$ | 新增 |
| 14 | 2 | $\lambda(v_{k-1}v_k)$ | 把兩個 vertex 直接並排當 $\lambda$ 的 input，記號怪 | 新增（符號寫法） |

---

## 五、L3：用詞 / 術語

| # | 頁 | highlight | 老師建議 |
|---|---|---|---|
| 1 | 1 | freight | 演算法 paper 很少用這個字 |
| 3,4 | 1 | dual（兩處） | 「dual」在演算法界另有含義（LP duality 等），避免使用 |
| 10 | 2 | Trucks | 用「卡車」下**正式定義**很怪；trucks 適合放在前面的 example/應用，正式定義不該出現 trucks |
| 21 | 4 | SCC of $\ESF$ | 通常說「一個 **graph** 的 SCC」，不說「一個 **edge set** 的 SCC」 |

---

## 六、L3：該刪的句子 / AI 痕跡 / 冗句

| # | 頁 | highlight | 老師意見 |
|---|---|---|---|
| 2 | 1 | where the flow … rounded up to a whole truck | 可刪 |
| 8 | 1 | h truck- | 可刪 |
| 13 | 2 | consistent with our omission of release times | **明顯是跟 AI 對話的殘留，絕不該出現在 paper** |
| 5 | 1 | abstract「the canonical route is a temporal path…」 | 看不懂、abstract 該講重點就好，可不寫 |

> 這幾條就是讓老師「一眼認出 AI 拼裝」的證據。#13 尤其致命——它直接把「我們把 release time 拿掉」這種**跟我對話時的理由**寫進論文了。

---

## 七、Abstract 應精簡（high-level）

| # | 頁 | highlight | 問題 |
|---|---|---|---|
| 6 | 1 | a splitting threshold θ | θ 突然冒出，讀者不知它在幹嘛 |
| 5 | 1 | canonical route is a temporal path… | 細節太多、abstract 不該講到這層 |

> abstract 現在把 temporal path、canonical route、two-label 這些**內文才會定義**的東西都塞進去了 → 又是一種前向引用（abstract 允許 preview，但老師覺得太細且看不懂）。

---

## 八、問題定義的寫法

| # | 頁 | highlight | 老師建議 |
|---|---|---|---|
| 10 | 2 | Trucks | **先把式 (1) 交代出來，再解釋為什麼要 minimize (1)**；不要從 $f_i$ 突然跳到 trucks |
| 9 | 1 | the routing | 「the routing」指誰不清楚，猜是 $f_i$ |
| 12 | 2 | {(src, dst)} | 沒講清楚是 **DSF 的** source/destination 還是**你問題的** source/destination |

---

## 九、演算法呈現細節

| # | 頁 | highlight | 老師建議 |
|---|---|---|---|
| 11 | 2 | Backbone via Directed Steiner Forest | 這段混了兩件事：(1) 解釋什麼是 DSF、(2) 解釋你的 subroutine `Build-Backbone`。**應分開**：先講 DSF 是什麼，別處再講你怎麼建 backbone |
| 20 | 3 | Algorithm 1 | overview 該加一句「pseudocode 見 Algorithm 1」；前面的解釋最好 **refer 到行號** |
| 27 | 5 | Algorithm 2 title / function 行 | 標題直接寫「Assign Dual Labels」即可，刪掉多餘的 `function` 行；前面解釋沒有 refer 到 Algorithm 2 |

---

## 十、一個需要你決策的「兩難」

老師第 4 頁 #22 圈了這段：

> "Because $\ESF[C_i]$ is strongly connected, … arborescences that span $C_i$ and consist solely of $\ESF$ edges"
> 老師：「我不知道寫這段要幹嘛…直接講 in-tree/out-tree 是什麼就好。」

**但這段正是先前 graph-verifier 判 FAIL、我補上去修「最短路徑樹是否 spanning 且只用 $\ESF$ 的邊」那個致命漏洞的關鍵**。所以這裡有張力：
- **嚴謹性（verifier）**：這段不能刪，否則 Lemma 1/2 的地基會塌。
- **可讀性（老師）**：這段夾在敘述中間，讓人分心、看不出用意。

**建議的折衷**（尚未執行）：不是刪掉，而是**換位置＋換包裝**——正文先直接講「in-tree/out-tree 是什麼」，把「它們存在、spanning、且只用 $\ESF$ 的邊」收成一個**小 Lemma 或一句 remark**，讓需要嚴謹的人有依據、不需要的人可略過。這樣同時滿足兩邊。

---

## 十一、把根因收斂成 4 條可執行主線（roadmap，尚未動手）

1. **建立「定義在前」的骨架**：新增一個 *Preliminaries* 節（或併入 §1/§2 開頭），集中安置：MAL 的定義、temporal graph / temporal path / temporally connected、terminal pair、Assumption 1（免費等待）。之後所有使用都在定義之後。→ 一次解決 #7, #16(部分), #18, #19, #23(部分), #24, L1 大半。

2. **§3.1 內部重排 + 打破循環**：先定義 $T_i$（base time），再一起定義三種 label（含 $t_{\mathrm{cross}}$）；把 canonical route 提前並獨立定義，斬斷 Route-SF ↔ canonical route 的互相定義。→ 解決 #26, #25, 循環問題。

3. **notation 衛生**：每個符號的參數都在定義裡交代並一致使用（$\SP_{s,t}$/$\SP_i$、$R(u,v)$/$R_i$、$\lambda$ 的 input 寫法）。→ 解決 #14, #15, #25, #10。

4. **表層清理**：刪 AI 痕跡與冗句（#2, #8, #13）、換用詞（freight/dual/trucks/edge-set SCC，#1,#3,#4,#10,#21）、精簡 abstract（#5,#6）、問題定義改成「先給式(1)再解釋」（#9,#10,#12）、演算法加行號引用與拆分 DSF 說明（#11,#20,#27）。

---

## 附：老師 27 條 → 根因對照速查

- **L1 位置/前向引用**：#7, #16, #17, #18, #19, #23, #24, #26（＋循環定義、terminal pair 未定義）
- **L2 notation 不完整**：#14, #15, #25
- **L3 用詞**：#1, #3, #4, #10, #21
- **L3 該刪/AI 痕跡**：#2, #5, #8, #13
- **Abstract 精簡**：#5, #6
- **問題定義寫法**：#9, #10, #12
- **演算法呈現**：#11, #20, #27
- **嚴謹 vs 可讀兩難**：#22
