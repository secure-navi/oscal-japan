+++
date = '2024-11-07T17:41:38+09:00'
draft = false
title = 'OSCALの今後のビジョンと戦略を中の人が語る'
categories = [
    "4th OSCAL Conference and Workshop",
]
image = 'images/blogs/4th-OSCAL-Workshop-Part3_eyecatch.jpg'
+++

この記事は、2023年5月にNISTが開催した「[4th Annual OSCAL Conference and Workshop](https://csrc.nist.gov/Events/2023/4th-annual-oscal-conference)」の、Part3の公演内容をもとに、一部要約を行い、日本語に翻訳したものです。

Part3 では「OSCALの新情報」をテーマに、OSCALプログラムの共同リードを務めるアレクサンダー・スタインさんと、OSCALの戦略的アウトリーチディレクターを務めるミカエラ・イオルガさんによる講演が行われました。

ぜひ、実際の資料は動画も確認しながらご覧ください（1:15:40 あたりから）。

{{< iframe src="https://cdnapisec.kaltura.com/p/684682/sp/68468200/embedIframeJs/uiconf_id/31013851/partner_id/684682?iframeembed=true&playerId=kaltura_player_1684176576&entry_id=1_e861yoyu&flashvars[streamerType]=auto" >}}

---

### What is New in OSCAL

最初はこのセッションを「What's Up With OSCAL」と呼ぼうと考えていましたが、もう少し上品なタイトルにしようということで、「What is new in OSCAL（OSCALの新情報）」に変えました。今日のテーマは、実際にOSCALにどんな新しい点があるのかを議論しつつ、コミュニティにも関わってもらおうという意図があります。では、OSCALがデータ形式として、また周辺のプロジェクトとして、ここ1年でどのような動きがあったかを簡単に振り返ります。続いて、今後1年、さらに数年先を見据えて、OSCALがどういうビジョンと戦略で進んでいくかをお伝えします。それから、現在のOSCALの作業状況についても触れ、ビジョンと戦略が短期・長期でどのように結びついていくかを説明します。最後にコミュニティが今後どのような役割を担っていくか、特にC3の話題を中心にお話しする予定です。ビジョンと戦略のポイントとしても大きな要素になると思います。

ありがとうございます。すでにロブの話を聞かれた方なら、皆さんご存じだと思いますが、念のためオンライン視聴の方に向けてOSCALが何かを簡単に説明します。OSCALとは、セキュリティとプライバシーのコントロール、それに関連する実装や評価の手法を機械可読なフォーマットで表現する、標準化されたオープンソースかつ柔軟な言語です。私たちのチームはOSCALを3階層に分け、7つのモデルを用意し、一般的なリスクマネジメントプロセスに沿う形で設計しています。さらに、そのモデルはXML、JSON、YAMLの3種類のフォーマットで保守されています。

ここで、この1年の実績を高い視点で振り返ってみましょう。まず2021年6月、OSCALの最初の安定版である1.0.0を正式リリースしました。その後、最近1.0.5のプレリリースを出し、すでにコミュニティからいくつか有益なフィードバックをいただいています。そのフィードバックを短期的にも長期的にも取り込みながら、追加のパッチリリースなどを検討していく予定です。スライドの細かい字にもあるとおり、大きな互換性崩れを起こさずにバグ修正や新機能を追加できるよう配慮していますので、皆さんが安心してソフトウェアを開発できるようになるかと思います。また、ここで特筆すべきは、商務省（NISTを管轄する省庁）からゴールドメダル賞を受賞したということです。これは私たち自身にとってもそうですし、もっと広いコミュニティの努力としての成果だと考えています。拍手してもらえてよかったです（笑）。

では、現在の状況とこれからOSCALプログラムをどこへ舵取りしていくのかをお話しします。私たちには新しいビジョンがありますが、あとでミカエラがその内容を説明します。その新しいビジョンに基づいて戦略を立て、新たな重点項目を決めています。今後はOSCALに関わるさまざまな活動を、「定義（Define）」という柱とエンジニアリングの柱、それからユーザーリサーチや可用性の検討、人間中心の視点を取り入れたアプローチで進めていきます。私の立場上、当然エンジニアリング面の作業もこれまで通り継続しますが、フォーカスの仕方が少し変わる可能性があります。こうした動きによって、7つある既存のモデルにも手が入るでしょうし、新たに別のモデルが加わることもありえます。いずれにせよNISTだけでなくコミュニティの皆さんにとって使いやすいものを目指しますので、そのためにはコミュニティのご協力が必須だと思っています。そこから派生して、「コミュニティとしての新しい期待や役割は何なのか」という話も出てきますが、それについては後ほど詳しくお伝えします。

NISTのチームは当初から大きな理想を持っていて、「将来的にはこうしたい」というイメージはあったのですが、それをきちんと示すにはOSCAL自体の成熟度がある程度高まるまで待つ必要がありました。ようやく「今なら明確に打ち出せる」と判断できたため、このスライドにあるようなビジョンを作ったわけです。読み上げますが、チームとして合意した文言はこうです。「NISTはコミュニティとの協力により、OSCALのモデル群を開発する。このモデルは、組織やクラウドサービスプロバイダが、各システムの情報や評価方法をベンダーロックインなしで共有しながら、シームレスかつ継続的にセキュリティ評価の情報をやり取りできるようにすることを目指している。私たちはコミュニティ、民間セクター、公共セクターとの連携・協力を強化し、OSCALモデルが早期に望ましい成熟度へ到達し、より幅広い国際的な普及をサポートできるよう、このビジョンを達成する。」これがチームが目指すビジョンです。

このビジョンを踏まえ、次は戦略について説明します。今のビジョンにはいくつかキーワードがあって、それをもとに今後のOSCAL戦略を進めるとき、コミュニティ主体の優先順位づけをより重視することになります。OSCALに関してやりたいことは山ほどあるので、安定性を高めるのか、新機能を突き詰めるのか、そのあたりをコミュニティと共に決めていきたいのです。私たちがすでに実施しているように、パブリックなメーリングリストやSNSでコメント募集を継続し、長めのプレリリース期間を設けてフィードバックを集めるなど、コミュニティの合意をより広く得られるように動いています。また、実用性や可用性を検証するために、スパイラル方式でのリサーチも行う予定です。エンジニアリング面では、既存のモデルでの自動化サポートを強化し、下から積み上げる形でアセスメント用のデータを集約する仕組みに力を注ぎます。こうしたアプローチを可能にするうえでも、そして私たちがコミュニティから学び、逆にコミュニティに還元するうえでも、包括的で実践的なサンプルが不可欠になります。そこを重点的に進めることで、OSCALがより多くの現場に広がり使われていくと考えています。

先ほども言っていましたが、OSCALのプログラム活動をよりうまく運用するために、大きく分けて柱を設定することにしました。コミュニティとの連携を担う「コミュニティの柱」が全体を覆う傘のような位置づけとなり、さらに「エンジニアリングの柱」と「Defineの柱（研究および教育を担う）」が主要な役割を果たします。エンジニアリングとDefineが理想的には相互に作用しあい、うまく成果を出すイメージです。Defineは「Develop enhancements, future implementations, and new education（拡張機能の開発、将来的な実装、新たな教育）」の頭文字を取ったものです。研究プロセスに関しては、ここにいるクリスや、このあと話すダニエル・コンプトンなどが指揮しており、スパイラルモデルを使った手堅い仕組みを確立しています。最初にイニシエーションを行い、そこからディスカバリーの段階でいくつかスパイラルを回し、暫定的な成果を共有して合意形成してはまた新しいスパイラルを回す。そして最終的に研究の成果をエンジニアリング担当に引き継ぎ、実装へと進む流れです。教育面でも、サンプルやチュートリアルを増やすことに注力し、すでに「OSCAL 101」と呼ぶ教育ワークショップを始めています。コミュニティの皆さんから「こういう教育プログラムがあればいい」「こういう形が助かる」といった提案をしていただければ、とても助かります。

Defineの活動で得られた研究成果は、エンジニアリングの柱へ還元され、その逆もあるというのが理想のサイクルです。エンジニアリング側では少し視点を変え、リスクマネジメントや、それに基づくセキュリティ・プライバシー・コンプライアンス・ガバナンスの相互運用について重視します。OSCALはすでにそこをサポートしていますが、今回ここで改めて強化していきたいと思っています。ロブ・ウッド氏の話にもあったように、セキュリティをめぐる人や文化の観点も大事で、組織は高度に自動化されたシステムだけでなく、人がその情報を理解しなければならないという難題があります。OSCALはすでに人間向けと機械向けの両方を考慮して設計されており、特に機械が得意とする繰り返し処理や集計を引き受け、人がより上位の判断に専念できるようにすることが目標です。そのためにも、システム間のやりとりや具体的な技術要素をより構造化する方向で、現行のアプローチを適応させたり、新しい手法を検討したりしていきます。

また、このプロジェクトを皆さんの期待に応えられる形で進めるには、コミュニティとのコラボレーションをさらに強化する必要があります。そこで私たちのほうで「何ができるだろうか」と考え、新たにコミュニティ側の主体的な組織づくりを提案したいと思いました。それが「コミュニティ・コラボレーション委員会（Community Collaboration Committee）＝C3」という案です。これはあくまで私たちが考えた呼び名ですが、このような組織ができると新たに参加した人を含めてコミュニティ全体が一つの声としてまとまりやすくなるのではと思います。これにより、フィーチャーの要望や改修の優先順位などをコミュニティ側から明確に示してもらいやすくなり、結果的に私たちがOSCALを開発・保守していく際にも役立つはずです。この提案書は外のテーブルにもありますので、興味のある方はご覧ください。今日のうちに少し考えてもらい、のちほど投票機能を使って意見を伺おうと思います。皆さんからの質問にも答えられるよう用意しています。