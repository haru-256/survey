# A Map of Bandits for E-commerce

- Auther
  - Yi Liu (Amazon.com)
  - Lihong Li (Amazon.com)
- Source
  - KDD 2021 Workshop Marble

# ABSTRACT

Banditはシンプルなアルゴリズムで様々な場面で活用され、それに伴い様々な応用手法が開発されてきました。その反面、実際にbanditを使用する際にどのアルゴリズムを選択すればよいかが分かりづらくなりました。教科書（[Introduction to Multi-Armed Bandits](https://www.amazon.com/Introduction-Multi-Armed-Bandits-Foundations-Learning/dp/168083620X), [Bandit Algorithms](https://www.cambridge.org/core/books/bandit-algorithms/8E39FD004E6CE036680F90DD0C6F09FC)）は主に基礎的なアルゴリズムの設計や分析に重きをおいており、またサーベイ論文([A Survey on Practical Applications of Multi-Armed and Contextual Bandits](https://arxiv.org/pdf/1904.10040.pdf), [Survey of multi­armed bandit algorithms applied to recommendation systems](http://injoit.org/index.php/j1/article/view/1093/1054))の多くはここの応用アルゴリズムを列挙しているだけです。それは、初学者にとっては価値がありますが、実際にBanditを活用しようとしたときに、結局どのアルゴリズムが良いのかが分からないギャップがあります。そこで本論でそのギャップを埋めるために、E-commerceにおいて関連のあるアルゴリズムを実例を上げて説明しています。具体的には報酬・行動・特徴の３つの側面からアルゴリズムを決定するチートシートのような構造化マップを提供しています。

![](https://i.imgur.com/pBRHKHe.png)

# INTRODUCTION AND MOTIVATION

Banditはseaquential decision malingフレームワークです。decision maker (agent) が、連続的にその時点のcontextual情報に基づいてアームと呼ばれる行動を選択し、そレに対する報酬を得るという問題設定です。典型的な目標は、agentが累積報酬を最大化するアームを選択するように学習することです。この問題は強化学習の特別なケースです。

Banditが盛んに研究されている理由は、その応用範囲の広さであり、この論文ではおもにE- commerceドメインの活用を前提としています。例えば、推薦・動的価格変更・サプライチェーン最適化などです。

特にBanditは、Amazon、Google、Netflix、Yahooなどの企業で推薦で活用されてきました。早期では、主にウェブページのコンテンツ提案（新聞記事・広告・マーケティングの文言）が研究されてきましたが、現在はdynamic pricing, revenue management, 在庫最適化などの応用も研究されています。



本論でAbstractで挙げたギャップを埋めるために、E-commerceにおいて関連のあるアルゴリズムを実例を上げて説明しています。具体的には報酬・行動・特徴の３つの側面からアルゴリズムを決定するチートシートのような構造化マップを提供しています。

問題設定は主にE-commerceドメインのものを考えていますが、他のドメインでも使えるようなものです。

# MAP ENTRY: IS BANDIT THE RIGHT FORMULATION?

あるユーザーに対に対して商品候補集合$\mathcal{A}, |\mathcal{A}| = N$から1つの商品を推薦し、クリック有無を報酬$r_ t\in {0, 1}$とする。このとき、Bandit agentは以下のステップを繰り返す。Banditの目的は累積期待報酬和$\sum_{t=1}^T E[r_t]$ を最大化することである。

1. ユーザーに関するcontext $\boldsymbol{x}_t$ を取得
2. context $\boldsymbol{x}_t$ を考慮して商品候補$\mathcal{A}$それぞれに$E[r_t] = g(\boldsymbol{x}_t, \boldsymbol{a})$を推定。$\boldsymbol{a}$はある商品の特徴ベクトル。
3. 推定値が最大である商品$a_t$を一つ選択し推薦する

以下の問題点を認識しておくべきである

- Banditは選択した行動に対しての報酬のみ観測される問題設定を意味している。もし全行動の情報が得られる（full-information）な場合（多クラス分類など）は、Banditではなく、教師あり学習を考えるべきである
- 

