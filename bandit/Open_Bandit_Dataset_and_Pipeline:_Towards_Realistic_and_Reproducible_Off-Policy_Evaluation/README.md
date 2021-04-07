# [Open Bandit Dataset and Pipeline: Towards Realistic and Reproducible Off-Policy Evaluation](https://arxiv.org/abs/2008.07146)

- Auther
  - Yuta Saito
  - Shunsuke Aihara (ZOZO)
  - Megumi Matsutani (ZOZO)
  - Yusuke Narita
- Source
  - ICML 2020 WorkShop
- GitHub
  - https://github.com/st-tech/zr-obp

# Why Selected this Paper?

banditの研究は盛んだが、ほとんどの論文では以下の2通りで手法の検証をしている（基本的には証明＋実験検証）。小論文ではより現実的なbanditの実験データを提示している。また、banditで使用できるパッケージを開発している点も興味が惹かれた。

- シミュレーター（多クラス分類を用いた）→現実的なタスクではない
- 独自のデータを使用→再現性がない

# どんなもの？

以下の3つの貢献を行った

- ZOZOのオンラインシステム上にて2種類の方策（今後増やす予定）で収集されたログを含むデータセットの公開
- OPEを実験するためのPythonパッケージの公開。LinUCBやLinTSなどの基本的な方策の実装もされている。
- 公開するデータセットを用いたベンチマーク実験を行い、既存のOPE手法の定量的・定性的評価をおこなった。

# 関連研究・比較研究は？

実際のbanditのログデータセットは他にも以下の2種類が公開されている。それぞれ、contextやaction、rewardがある。しかし、収集した方策が1つしかないため、OPEの手法比較をすることはできない。

- Yahoo Dataset
- Criteo Dataset

# どういうデータセット？

Open Bandit Dataseを収集したのは以下のような問題設定において。

- 期間：2019-07の7日間
- 以下の画像の様に、アーム（服）から3つの表示するアイテムを求め、それぞれを3つの位置に表示する
- 方策：RandomとBernoulli TS（今後追加予定）の2種類

<img src="https://raw.githubusercontent.com/st-tech/zr-obp/master/images/recommended_fashion_items.png" alt="エビフライトライアングル" title="サンプル">

３つのキャンペーンに対して（３種類の集め方で）上記の設定でログを収集。統計量は以下の通り
<img src="https://raw.githubusercontent.com/st-tech/zr-obp/master/images/obd_stats.png" alt="エビフライトライアングル" title="サンプル">

# どうやって有効だと検証した？

上記のデータセットにおいて基本的なOPE手法の性能を測った。結果は以下の通り。

これから言えることは以下の通り

- 基本的にはDMはあまり良くない
- シンプルなIPWやSNIPWはそれなりの結果を出している
- DRはIPWよりも分散が小さいことが提案論文で示されているが、本実験ではそれは観測されなかった。
- Out-sample（オフラインの分布とオンラインの分布が変化した場合。普通にありえる）はIn -sample（オンラインとオフラインの分布が完全に一致している）での推定結果よりもかなりおとる。

![image-20210408014854341](https://i.imgur.com/gHSyMpf.png)

また、報酬予測手法を変更した場合に精度はどの程度変化するのかも確認した。

- 当然だが、報酬予測手法の精度もOPEの精度に寄与するためOPE手法の選択に加えてハイパーパラメータの選択は大事

![image-20210408014854341](https://i.imgur.com/N0XXef6.png)

# 議論はある？



# 次に読むべき論文は？