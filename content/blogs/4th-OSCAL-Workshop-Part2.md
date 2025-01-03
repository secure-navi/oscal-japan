+++
date = '2024-11-04T18:13:47+09:00'
draft = false
title = 'OSCALを巡る文化とセキュリティカルチャー'
categories = [
    "4th OSCAL Conference and Workshop",
]
image = 'images/blogs/4th-OSCAL-Workshop-Part2_eyecatch.jpg'
+++

この記事は、2023年5月にNISTが開催した「[4th Annual OSCAL Conference and Workshop](https://csrc.nist.gov/Events/2023/4th-annual-oscal-conference)」の、Part2の公演内容をもとに、一部要約を行い、日本語に翻訳したものです。

Part2 では、米国保健福祉省傘下でメディケア・メディケイドサービスセンターのCISOを務めるロバート・ウッドさんによる基調講演が行われました。彼は1億人以上のアメリカ国民の医療情報を扱う立場におり、LinkedInでは「ソフトサイド・オブ・サイバー」というブログでも知られています。

ぜひ、実際の資料は動画も確認しながらご覧ください（48:25 あたりから）。

{{< iframe src="https://cdnapisec.kaltura.com/p/684682/sp/68468200/embedIframeJs/uiconf_id/31013851/partner_id/684682?iframeembed=true&playerId=kaltura_player_1684176576&entry_id=1_e861yoyu&flashvars[streamerType]=auto" >}}

---

### OSCAL and a New Way of Doing Software in Federal

私は、CMSでCISOとして働いていて、メディケアやメディケイドのプログラム、それから病院調整や臨床基準の策定に関わる部分を幅広くカバーしており、合わせて1億4000万から5000万人分の医療情報を扱う立場にあります。だからこそサイバーセキュリティは非常に重要ですが、今日は少し違う観点で、OSCALをめぐる「文化」について話したいと思います。OSCALは、連邦政府のITエコシステム、とりわけソフトウェアのコンプライアンス部分を新しく、より良い形に変える動きで、とてもワクワクしています。なかでも「従来どおりのやり方」が根強いと言われる連邦政府において、コンプライアンスを変革するこの動きは本当に楽しみです。私たちは継続的ATOやソフトウェア開発、ソフトウェアサプライチェーン、ソフトウェアセキュリティをOSCALの観点で大きく前進させようとしていて、それを推進しているのは最終的には「人」や「人々のカルチャー」だと思っています。

私がキャリアを通じて学んできたのは、「文化は戦略を朝食にして食べてしまう」という言葉です。ゼロトラストだとかSBOMだとか技術的にどれだけ優れていても、組織の文化が悪ければその価値は損なわれてしまいます。セキュリティのリーダーやコンプライアンスのリーダー、あるいは連邦の場で影響力を持つ人々は、自分たちが働く組織の文化に本気で向き合い、前向きに変えていく必要があります。私の話は大きく、今の課題は何で、どう痛んでいるのか、そして文化を強くする要素として何が大切か、さらにOSCALでどうその文化を支えられるか、という流れになります。まず「連邦の場でソフトウェアを作る」ということは、色々とわかりにくくて複雑です。独自の用語やルール、レガシーな仕組みもあって、SSPをどう書くか、クラウド環境やコンテナのセキュリティをどう扱うか、ペンテストをどのように管理するか、など多岐にわたる問題があります。そうしたなかで、OSCALをセキュリティ態勢を伝える核として据えれば、制御文書やSSPを標準化しやすくなり、全体の混乱を少しずつ整理できると思います。

もう一つ、悪い文化が招く問題として、セキュリティ対ITや開発者、あるいはプログラム担当といった「セキュリティ部門対その他」という対立構造を生むことがあります。しかし本来「私たち対向こう」というのは、脅威アクターや攻撃者を想定すべきであって、同じ組織内の同僚やチームを敵視すべきではありません。OSCALは、セキュリティ態勢を示す文書の書き方を標準化し、セキュリティエンジニアやコンプライアンス担当、プライバシー担当などが共通の言語で話せる道を拓きます。大きな組織が拡大・発展していく際の鍵の一つが標準化という考え方ですが、セキュリティドキュメントもそこに当てはまります。制御文書をバラバラの書き方で作っていると、後で活用するときに話がかみ合わなくなります。標準化することで、より一貫したストーリーや明確な情報共有が可能になります。

私が大切だと思う文化の柱は、エンゲージメント（積極的な関与）、アウェアネス（意識向上）、トランスペアレンシー（透明性）、インセンティブ（動機づけの整合）、そして責任のなすり合いをなくすことです。インセンティブについて言うと、人は罰則や恐怖ではなく、「これをやるとこういう良いことがある」という形で引っ張られたほうが、意欲的に動きます。エンジニアやプロダクトマネージャーは、プロダクトを完成させて価値を届けたいのだから、OSCALを使うことでテストしやすくなる、メンテしやすくなる、継続的ATOを取りやすくなる、といった利点をきちんと示すことが大事です。また責任転嫁や指摘合戦に陥らず、「誰々が失敗した」のではなく「問題が起きたならどう改善できるか」を建設的に考える文化が必要です。例えばCMSでは、新しいSaaSプロバイダにFedRAMPをとってもらう際、SSPをOSCALで作ってほしいという方針を打ち出していますが、その際も「あれが古い」「これが足を引っ張っている」と責めるより、「どうすればテストしやすくなるか」「どうすれば持続可能なコンプライアンス体制を築けるか」を皆で考える姿勢を持つようにしています。

セキュリティは孤立して進めるべきではありません。組織全体で密にやり取りをしないと、うまく機能しません。ウォーターフォール的な縦割りのコミュニケーションは、人と情報のやり取りが少なく、所有意識も希薄で、リスクを共有しにくい状態を生みます。だからこそ私たちはフォーラムやオフィスアワー、AMAなどを積極的に開いて、チーム間の対話や意見交換の機会を増やしています。ここにはアジャイルの精神があり、コードの開発プロセスだけでなく、組織全体のやり取りにもアジャイル的な姿勢が必要だと思います。

アウェアネスに関しては、連邦でありがちな「年に一度の味気ないセキュリティ研修」で終わらせず、話す相手が誰かによって伝え方を変えることが大切です。管理職や政治任用職と開発者では、必要とする情報も使う用語も違います。せっかく全体周知の場を設けても、対象に合わせたメッセージになっていなければ効果は薄いです。最後に透明性についてですが、セキュリティチームは「自分たちだけが知るべき機密」と思い込み、情報を開示しないことが多い。しかし何でもかんでも秘匿すべきわけではなく、特に方針やプロジェクトの意図、決定プロセスなどはむしろ開かれているほうが信頼を得やすい。AMAやオフィスアワーを設けて開かれた対話をするのも、組織内の信頼関係を築くうえで非常に有効です。誰かに大きな変革を強いたいなら、（ポリシーで無理やりやらせる方法もあるが）多くの場合、人々が「そこに参加したい」と思えるよう信頼を育てるほうが結果的にうまくいきます。

スライドで紹介したQRコードのリンク先には、こうした文化づくりのために私が挙げた30ほどの具体的なアイデアがあります。文化を変えるのは簡単ではなく、投げ込んだ石が本当に何を変えているのかすぐには見えないかもしれません。でも、6か月、1年、2年と続けていくうちに、周りの人が自分たちのリスクや脆弱性、抱えている課題を率直に話すようになったり、セキュリティチームへの関わり方が変わってきたりするのを感じられると思います。連邦のコンプライアンスやソフトウェアの作り方をOSCALという形で大きく変えていくには、このように信頼関係と良い文化が下支えになっていることが必要だと信じています。

質問を受け付けます。まずPHI（保護対象医療情報）を扱う立場としてOSCALがプライバシーをどう改善できるか、というご質問。私としては、システムが何をしているかをより透明化することが最大の強みになると思います。制御文書にはデータ利用やデータ保護の制御項目が含まれるので、そこをしっかり標準化し整備することで、プライバシーの観点でも得られるメリットは大きいはずです。ただ、プライバシーはセキュリティとは別枠として扱われがちで、あまり技術的な議論に引き込まれない傾向があります。そこはセキュリティ側もプライバシー側もお互い歩み寄る必要があり、OSCALのような文書の透明化はその手助けになると思います。次の質問ですが、CMSはHIPAAやHITRUSTなど他のフレームワーク向けにOSCAL定義をサポートする予定はあるか。実はHSCCの作業部会でまさにそれに取り組んでいます。というわけで、私の話は以上です。皆さんありがとうございました。もう少し会場にいるので、直接話しかけていただいても構いませんし、リストもぜひ活用してください。ありがとうございました。
