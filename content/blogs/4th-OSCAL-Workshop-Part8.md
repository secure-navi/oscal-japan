+++
date = '2024-11-09T17:53:27+09:00'
draft = false
title = 'Google内部でOSCALがどう活用されているのか'
categories = [
    "4th OSCAL Conference and Workshop",
]
image = 'images/blogs/4th-OSCAL-Workshop-Part8_eyecatch.jpg'
+++

この記事は、2023年5月にNISTが開催した「[4th Annual OSCAL Conference and Workshop](https://csrc.nist.gov/Events/2023/4th-annual-oscal-conference)」の、Part8の公演内容をもとに、一部要約を行い、日本語に翻訳したものです。

Part8 では、Google Cloudで継続的アシュアランス（Continuous Assurance）の取り組みを率いているヴィクラム・カーさんと、Google Cloudにおけるセキュリティ・プライバシー・コンプライアンスの重要なコントロール全般で継続的アシュアランスを実現するためのツール戦略をリードしているヴァレンティン・ミハイさんによる講演です。

ぜひ、実際の資料は動画も確認しながらご覧ください（5:03:42 あたりから）。

{{< iframe src="https://cdnapisec.kaltura.com/p/684682/sp/68468200/embedIframeJs/uiconf_id/31013851/partner_id/684682?iframeembed=true&playerId=kaltura_player_1684176576&entry_id=1_e861yoyu&flashvars[streamerType]=auto" >}}

---

### Google’s Internal OSCAL Adoption（Google内部でのOSCALの採用）

皆さん、こんにちは。ヴィクラム・カーと申します。先ほど私たち全員の上司でもあるフィルが話しましたが、私はGoogle CloudのCISO組織で継続的アシュアランスのエンジニアリングを担当しています。OSCALとの関わりは最初は調査レベルでしたが、現在は導入段階に入っています。とはいえ、私たちの主眼はOSCALそのものではなく、継続的アシュアランスをどう実現するかという点にあります。OSCALはあくまでそれを助ける手段の一つです。今日は、継続的アシュアランスに向けてどう動いているのか、導入上の課題は何か、データの整合性をどうとるか、そういった話をします。後半はヴァルが具体的なプロセスやシステムの概要、そして将来の展望を少しお話しします。すぐに本題に入りますね。

最初に言ったように、元々はOSCALを目的にしていたわけではなく、私たちの狙いは継続的アシュアランスです。OSCALの良さは、セキュリティ・リスク・コンプライアンスに関するデータを、システムや組織間で交換できる標準形式を提供してくれるところです。自動化を真剣に考えるなら、まずは標準化が欠かせない。標準化せずに自動化は難しいですよね。では継続的アシュアランスとは何か。『Compliance as Code』『Continuous Compliance』『Continuous Auditing』『Policy as Code』『Continuous Controls Monitoring』など様々なバズワードがありますが、私たちの定義では、すべて“継続的アシュアランス”という傘の下に含められます。もっと具体的に言えば、組織が持つコントロールを自動化された方法で保証（assure）できる状態のことです。つまり、コントロールをコード化し、ポリシーやコンプライアンスの義務もすべてコントロールにマッピングする。さらに私たちにとって重要なのはリアルタイムのメトリクスです。コントロールに対して測定基準を定義し、実装面の指標とコントロールそのものの指標の両方を設定します。先ほどフィルも言っていたように、コンプライアンスの不備やコントロールのインシデントをセキュリティ事故やサービス障害と同じ緊急性で扱うことも欠かせません。

ここまでの流れで直面した課題をいくつか紹介します。まず“軽い”課題としては、内部向けのツールを作らなければならないことですね。OSCALという標準自体に取り組むオープンソースの動きも増えていますが、当社としては独自により高度なツールを開発してコントロールの管理を円滑にしたい。それからスキーマの扱いやGRCシステムとの連携をきちんとするには、変更管理が必要です。あとは、OSCAL自体が新しい標準であるため、社内の調整にも時間を要します。より大きな課題として、サードパーティ製ソフトウェアを大規模に導入することは当社のようなスケールでは難しい面があります。よってOSCALの採用傾向を見極めつつ、当社がどうメリットを得るか慎重に考える必要があります。あと、Googleは非常に大きなコントロール在庫（inventory）を抱えているので、それを一斉に運用するのは大変です。またFedRAMP対応で特に実感していますが、継続的アシュアランスを始めると、可視化した不備の対応、いわゆる技術的負債の解消が大量に発生する。それが最大の難題かもしれません。

では具体的にどう進めているか。最初はPoC段階で、スプレッドシートとスクリプトを駆使してOSCALのアーティファクトを生成していました。その後MVPへ移行し、現在はデータの事前入力（プリ・ポピュレーション）を進めています。リスクやコンプライアンスを管理するには通常GRCシステムを使いますよね。そこに必要なデータを整備すれば、規制やフレームワーク対応も自動化しやすくなる。今ちょうどそこをやっていて、“OSCALビルダー”と呼んでいます。次の段階は成熟化で、データ収集の自動化を進める計画です。

OSCAL導入の大きな焦点はデータ整合性です。コントロール・カタログを自動化するには、まず規制の分解が必要。さきほどCSAなどが述べていたように、いろんなフレームワークが徐々にOSCAL化されている。私たちも同様で、新たな規制が来ればAIシステムを通してデータベースに落とし込み、機械可読な形式に抽出する仕組みを持っています。コントロール構造はOSCALで標準化し、資産モデルをどう表すかについても改めて見直しています。最終的には異なるソースからのデータを集約し、多数の規制フレームワークへの対応を自動化していくわけです。GRCデータがしっかり整理され、自動インストルメンテーションで数値を取り込めるようになれば、例えばコントロール評価を事前入力してあちこちの関係者と共有できるようになる。では、これを踏まえてヴァルから要件分解の例を説明してもらいます。

ありがとうございます。まず、規制やフレームワークを内部的にどう扱うか、そこから話しましょう。例としてウイルス対策（アンチウイルス）に関する規定を取り上げます。具体的な画面はお見せできませんが、仮の例を考えてみます。よくあるのは、一つの文書の中に複数の要件がまとめて書かれているパターンです。大規模な組織だと、そういう統合的な要件を一つの担当や一つのグループだけで処理するのは難しい。そこで私たちはそれらを細かく分解して、測定可能で具体的なコントロールとして管理することにしました。ある条文があったとき、それを3つの要件に分けるのです。それぞれが社内では独立したコントロールとして扱われ、割り当てがしやすくなります。誰が担当なのか、どのシステムで実装されるかを明確にし、その結果を測定して報告できるようにするわけです。

アニメーションを使った例ですが、左から右へ向かって要件がどのように処理されるかを示します。私たちのGRCシステムの中では、まず要件からコントロールを作り、さらに親コントロールと補助コントロールの階層関係を設定します。補助コントロールはスコープで分割され、それらが実装形態（Control Implementations）と結びつく。要するに、同じ要件でもデータセンターやリージョンごとに実装が違うかもしれないし、サービスによっても異なるかもしれない。そういう柔軟性を持たせるのが重要です。さらに右側にはコンポーネントがあって、実際にどう実装されているかを詳細に記述できる。そしてCCM（Continuous Controls Monitoring）の概念とつながると、メトリクスを定義し、どのシステムのデータを計測するかも設定できる。こうした「親—子」関係を持つコントロール構造により、全体を統合的に眺めることができます。規制によっては抽象度が違うし、粒度もばらつきがありますが、高レベルの要件とそれを実行する細かいコントロールをつなげられるので、たとえば「合計でどれくらい順守できているか」をパーセンテージなどで把握できるようになります。さらに赤黄緑のような色分けを使って一目で状態を確認し、可視化できるわけです。

次に、私たちが想定しているコントロールのライフサイクルを説明します。大きく分けて3つの段階があります。最初が“インテーク”で、コントロール不足の発見や既存コントロールへのマッピングを行います。ここでは外部の監査や内部レビュー、規制の分解など、いろいろな情報源から問題点が拾い上げられます。次に“カタログ化とオンボーディング”段階があって、要件やスコープ、目的を設定し、実装までつなげます。ここで重要なのは、メトリクスを取れるコントロールにすること。プロセス主導のコントロールであれば、自動観測できる仕組みを追加しないと、継続的な監視はできません。最後は“継続的アシュアランス”の段階で、モニタリングと検証をし続けます。フィルが話していたCRE（Controls Reliability Engineering）のように、常に安定状態を保つためのプロセスを回すわけです。

こうした取り組みを支えるシステム構成はざっと5種類に分かれます。下に示している4つ（青い枠）がOSCALを活用する仕組みで、連続的アシュアランスを実現する枠組みです。典型的なIT企業はすでに多彩なシステムを持っていますが、さらに私たちは“連続モニタリング用の基盤”を追加する形になります。具体的には、GRCシステムやCMDB、Continuous Controlsプラットフォームといった“公的な情報源（System of Record）”を確立し、そこから可視化レイヤーや証拠保管レイヤーにつなぐ。監査対応もあるのでエビデンス保管が必要ですし、コンプライアンス以外のセキュリティ機能とも連携する必要があります。最終的にはさまざまな社内ステークホルダーに情報を提供し、運用に役立てるという流れです。

最後に、OSCALやCCMを活用した自動化により、最適化・加速・大規模化が進めやすくなることを強調しておきたいです。フィルが言ったように、職人技から産業レベルへ移行するためのエンジンの一つでもある。OSCALによってテキストベースの要件を機械的に扱いやすい構造に落とし込めるため、監査対応や規制分析の手間も減らせますし、脆弱性管理や脅威インテリジェンスなど、コンプライアンス以外の領域とも統合しやすくなります。私の方からは以上です。ありがとうございました。