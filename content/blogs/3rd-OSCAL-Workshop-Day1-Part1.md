+++
date = '2024-10-03T15:03:58+09:00'
draft = false
title = '爆発的な技術革新とOSCALの進化（3th OSCAL Workshop 基調講演より）'
categories = [
    "3rd OSCAL Workshop",
]
image = 'images/blogs/3rd-OSCAL-Workshop-Day1-Part1_eyecatch.jpg'
+++

この記事は、2022年3月にNISTが開催した「[3rd Open Security Controls Assessment Language (OSCAL) Workshop](https://csrc.nist.gov/Events/2022/3rd-oscal-workshop)」の、Day1 Part1の公演内容をもとに、一部要約を行い、日本語に翻訳したものです。

Day1 Part1 では、米国商務省の最高情報責任者（CIO）に就任し、商務省全体の技術システムについて総合的な責任を負っている、アンドレ・メンデス（Andre Mendez）さんによる、ビジョナリーキーノートが行われました。なお、NIST は商務省の一部です。

ぜひ、実際の資料は動画も確認しながらご覧ください。

{{< iframe src="https://cdnapisec.kaltura.com/p/684682/sp/68468200/embedIframeJs/uiconf_id/33598632/partner_id/684682?iframeembed=true&playerId=kaltura_player_1647535799&entry_id=1_6h8swt6e&flashvars[streamerType]=auto" >}}

---

皆さん、おはようございます。ご紹介ありがとうございます。多くの天才が集まっているこの場でビジョナリー・キーノートをお話しするのは光栄であり、かつ大変チャレンジングですね。ここには、テクノロジー全般や、あるいはサイバーセキュリティのように高度な専門性を要する領域でご活躍される世界トップクラスの知性が揃っていますからね。
私は話を手短にし、皆さんがこの後予定されている素晴らしいプレゼンテーションに集中できるようにしたいと思っています。

テクノロジーに関して私が多くの示唆を得ているのは、技術革新が爆発的に進む社会をいかに生きるかについて深い洞察を示したビジョナリーたちです。たとえば、レイ・カーツワイル（Ray Kurzweil）は2005年に、2035年に「シンギュラリティ」が訪れると予測しました。当時の2005年は、いまから16年前ですが、彼の予測は着実に現実味を帯びています。技術は加速度的に発展し、私たちはその渦中にいるため、80マイル、85マイルで高速道路を走っていても、給油で止まったときにその速さを実感するかのように、日常の中でそのスピードに慣れてしまいがちです。
とはいえ、この常に加速し続ける流れの中でも、社会や経済がつまずくタイミングごとに新たな飛躍が生まれているようにも感じます。何か問題が起こるたびに進化のプロセスが働き、古いレイヤーや古いコンセプトは淘汰され、新しいプレイヤーやコンセプトが登場しては急速に地位を確立し、私たちの組織や社会を変え続けているのです。
要するに、テクノロジーはすでに非常に急激な成長曲線（漸近的な状態）に入り、変化は速く、深く、社会へのインパクトも非常に大きい。しかも、すべてがプラスになるわけではなく、常にポジティブとネガティブが表裏一体となり、互いを駆り立てながら進歩していくのです。

クラウドの分野は、まさに今注目を集めています。マルチクラウドの相互運用性が成熟し始め、いまや実質的に当たり前のようになっています。非常に強固なセキュリティを備えたクラウド環境を、複数のプロバイダと組み合わせて実装できるようになり、可用性やセキュリティも飛躍的に向上しています。一般的に、オンプレミスのデータセンターを保有する従来型のモデルよりも、クラウドを利用する方が量子飛躍的なメリットがあるケースが多いでしょう。ただし、連邦政府（アメリカ国内でも）では、完全に、あるいはほぼ完全にクラウドに移行している省庁もあれば、まだ大きく遅れているところもあります。
このような加速の背景には、コンピュータの計算能力、ストレージ、ネットワークなどの大幅な進化があります。さらに、この能力増大が「マス・カスタマイゼーション（大規模かつ個別化されたサービス）」を推進し、究極のターゲット顧客へのアプローチ方法を変えつつあります。これはビジネスや生活のあらゆる面でパラダイム・シフトを起こしています。たとえばメディアの世界では、ウクライナ情勢に関して、情報拡散の方法が戦争の実態や国際世論さえも左右し、戦況を変えてしまう例が出てきました。かつてのような「戦争の形」を想定して始まったことが、今ではSNSなどの拡散力によって別様に進行している面があります。

従来型の放送（ブロードキャスト）が、一人ひとりに情報をピンポイントで届けるユニキャストに近いモデルになっており、これまでに好みを示してきた情報や、地域情報、個人の興味に合わせてパーソナライズされたコンテンツが絶え間なく流れてきます。ヘルスケアにおいても、大きく状況が変わりました。パンデミックの影響もあり、ここ2年ほどで50%近くの診療が遠隔医療（テレヘルス）で行われるようになり、医療提供のパラダイムそのものが変化しています。家族歴や生活習慣、遺伝的な傾向、バイオメトリクス、リアルタイムで測定されるセンサー情報などを統合し、より包括的で個別化された医療へと移行する流れが加速しています。5年前には考えられなかったような、スマートフォンにつないで使える安価な心電計などが当たり前のように売られています。

このように、私たちが日々の暮らしや仕事を送る社会のかたちそのものが、大きく変化しています。データ分析の世界でも、いまや非常に巨大で多種多様な（構造化・半構造化・非構造化）データを集約し、リアルタイムかつダッシュボード型の意思決定支援へとつなげる仕組みが当たり前になってきています。昔ながらのリレーショナル・データベース（SQLベース）も、もちろん今でも生きていますが、今の分析基盤はさらに幅広く、より柔軟なデータモデルやキュレーション手法が使われ、より高度な分析を可能にしています。

こうした新しい技術がもたらすメリットは絶大ですが、それに伴うリスクも同様に高まっています。特に連邦政府など大規模な組織では、膨大な量の重要情報がIT環境に格納されているがゆえに、悪意のある攻撃者に狙われやすく、被害も甚大化する恐れがあります。したがって、サイバーセキュリティの要件は以前にも増して高度化しています。昔のように各システムや端末、ユーザ単位で細分化して対策するのでは追いつかず、ホリスティックなアプローチが必須となっています。ソフトウェアやサービスの開発段階でサイバーセキュリティを組み込む「セキュア・バイ・デザイン」という考え方は、実は最近になってようやく普及してきたばかりです。かつてはセキュリティが後付けか、場合によっては存在しないことさえありましたが、現在は最初から組み込むことが求められています。

さらに、脅威が進化するにつれ、サイバーセキュリティの要件も刻一刻と変化しています。3年前に「十分だ」と思われていた手法が、いまや不十分と判明する例も少なくありません。実は、どこかで見られたような古典的な攻撃手法の組み合わせが「新しい脅威」扱いになっているケースもあり、「サプライチェーン攻撃」などがその象徴的な例です。2020年12月に起こった SolarWinds 事件では、当初「サプライチェーンが新たな脆弱ポイントだ」と言われましたが、突き詰めると、あれは古典的な管理ミスや運用の甘さが一因となって攻撃者に足がかりを与えてしまったケースとも言えます。とはいえ、この事件によって「内部で正当に動いているように見えるものでも、実は安全とは限らない」という認識が広まり、ゼロトラスト・アーキテクチャへの移行が急速に進むきっかけにもなりました。

こうした出来事によって従来のパラダイムが否定され、さらに強固なセキュリティの仕組みを構築する圧力が高まったわけです。しかし、ゼロトラストの考え方は、すべてのトラフィックを検証し続けるという意味で非常に大きな負荷を伴います。エンドユーザやシステム間、あらゆるやり取りに対し、常時アクセスコントロールや認可プロセスを当てはめるわけですから、オーバーヘッドが膨大です。そのため、これらを実行可能にする人工知能や機械学習の導入が強く求められています。パターン認識やリアルタイム監視を自動的に行い、未知の攻撃ベクターに対してもすぐに検知・対応できる体制を整えることが不可欠だからです。

長期的には、サイバーセキュリティのあらゆる活動を自動化しなければなりません。攻撃が一瞬で広がる現在、人間が手動で対応していては間に合わないからです。ただしそれには新たな課題があります。テクノロジーの進化は光の速さで進んでいますが、それを規制・評価する枠組みやプロセスは、どうしても一昔前のペースに留まりがちです。典型的な例は認可（ATO: Authority to Operate）プロセスです。これは多くの組織にとって非常に負担が大きく、新しい能力を迅速に導入する妨げになっている場面が多々あります。私が商務省に来た当時、暗黙の了解として「すべてのプロジェクトは ATO を取得するために数か月の遅延が生じる」と言われていました。なぜ毎回そうなるのか尋ねると、「従来からそうしてきたから、今後もそうだ」という答えが返ってきました。正直容認し難い理由ですよね。

そんなときに私が初めて OSCAL の話を聞いたとき、「これは画期的だ」と思いました。もし標準化されたプロセスで、セキュリティコントロールが実装されていることを明確に示せるなら、ATO に費やす手間を大幅に減らせる可能性があるからです。開発段階から無駄のない形でコントロール実装を証明できれば、プロジェクトを迅速にリリースできるわけです。しかも、それは今のような複雑化する環境には必須でしょう。

私自身、OSCAL を非常に強く支持しています。OSCAL は、IT 環境がますます複雑・高リスクになっている世界において、まさに不可欠の存在になると思います。人々は巨大ベンダーの名前やソリューションだけに注目しがちですが、私はあえてそうした大手企業だけでなく、真に功績を挙げている方々へスポットライトを当てたいと思っています。具体的には、標準化やリスク管理、開発・運用といった地道なプロセスを深く理解し、それを実現している技術者の皆さん、裏方の皆さんです。こうした人々が「進化とその管理」「標準化と進歩」を両輪で進めながら、私たちに日々の進歩をもたらしてくれています。

振り返れば、生物学の進化や文化の進化、技術や政治組織など、どの分野においても、進化とは常に標準化によって支えられてきた歴史があります。新しい標準の一部は失敗して消えますが、成功した標準は長きにわたって活用され、次なる抽象化レイヤーの土台となり、さらなる機能の高みへ導きます。OSCAL という標準化は、一見すると地味に思えるかもしれませんが、その重要性は計り知れません。私の経験上、こうした取り組みが本質的な技術革新を支え、結果としては社会全体の利益にも直結するのです。

最後になりますが、私の話は以上です。もし Q&A の時間があれば喜んでお答えしますが、なければ次のセッションのホストへお譲りいたします。皆さん、ありがとうございました。そして皆さんが日々取り組まれている作業にも改めて感謝します。機能と安全性を両立しようと努力する皆さんの仕事こそ、私たちのテクノロジーと生活を下支えしているのです。
