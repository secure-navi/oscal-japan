+++
date = '2024-10-14T17:29:43+09:00'
draft = false
title = 'IBMが提供するSecurity and Compliance Center(SCC)とOSCALとの関係性'
categories = [
    "3rd OSCAL Workshop",
]
image = 'images/blogs/3rd-OSCAL-Workshop-Day2-Part1-1_eyecatch.jpg'
+++

この記事は、2022年3月にNISTが開催した「[3rd Open Security Controls Assessment Language (OSCAL) Workshop](https://csrc.nist.gov/Events/2022/3rd-oscal-workshop)」の、Day2 Part1の公演内容をもとに、一部要約を行い、日本語に翻訳したものです。

Day2 Part1 では大きく2つのテーマについて公演が行われました。この記事では、IBM Research チームによるSCCにおけるOSCALの活用について、紹介しています。後半の「EUのサイバーセキュリティ認証におけるOSCALの活用」については、別の記事で紹介する予定です。

ぜひ、実際の資料は動画も確認しながらご覧ください。

{{< iframe src="https://cdnapisec.kaltura.com/p/684682/sp/68468200/embedIframeJs/uiconf_id/33598632/partner_id/684682?iframeembed=true&playerId=kaltura_player_1647535799&entry_id=1_mnivm99p&flashvars[streamerType]=auto" >}}

---

### 自己紹介

本日は、OSCAL を活用して複数のコンプライアンス情報をツール間で連携するための「Exchange Protocol」を使った統合手法についてお話しします。まずなぜそれが必要なのか、その背景とアーキテクチャの詳細、そして実際に私たちがどのように OSCAL の言語やスキーマを活用しているのかをご紹介します。

次のスライドをお願いします。

### Security and Compliance Center (SCC)

IBM Cloud には、2～3年ほど前から「Security and Compliance Center (SCC)」という提供サービスがあり、これはお客様のセキュリティとコンプライアンスの状況を一元的に把握できるものです。コンフィギュレーションの管理やルール設定、それを守らない設定を防ぐガードレールを設置する仕組み、さらにセキュリティインサイト機能で脆弱性や脅威を可視化できるようになっています。当初は SCC 自体が一括してコントロールを検証していましたが、規模拡大やお客様要件により、たとえば Tanium や OpenShift Compliance Operator といったお客様独自のポリシーチェックツールを使いたいというニーズに対応しなければならなくなりました。

そこで、SCC の役割を「自らバリデーションを行う」から「外部ツールをオーケストレーションする」方向へ拡張し、さまざまなツールのコンプライアンス結果をまとめて把握できる、いわば「単一のビュー」を提供する必要が出てきたのです。このように複数形式の結果をどのようにアラインし、さまざまなフォーマットを扱うか、という課題を解決するために Exchange Protocol を導入したという流れになります。

次のスライドをお願いします。

### Exchange Protocol と OSCAL

IBM SCC はこれまで自前でコンプライアンスの検証を行っていましたが、Tanium や OpenShift Compliance Operator などの外部ツールを統合し、複数の検証結果を一箇所で表示できるようにすることが求められるようになりました。SCC をコンプライアンス結果を集約する “オーケストレーター” として機能させるわけです。これを実現するために私たちが設計したのが Exchange Protocol で、SCC と各検証ツール（PVP; Policy Validation Point）の間で、標準化された形でコンプライアンス情報をやりとりします。

Exchange Protocol には大きく2つの要素があります。1つ目は、PVP 同士あるいは PVP と SCC の間で結果をやりとりする「実際の通信手順（Exchange Protocol）」です。2つ目は、その手順を行う前段として「SCC に対してツール側が必要な情報を登録するプロセス」があります。具体的には、各ツールベンダーが持っているコントロール実装やチェックルールの定義などを “コンポーネント定義（component definition）” という形で SCC に登録し、SCC 側はそれらを把握した上でお客様（ユーザ）が「このコントロール群を満たしたい」というコンプライアンス意図（プロファイル）を作成します。SCC はその情報を基に、必要なルールセットを PVP に渡し、PVP はシステムの実環境でチェックを行って証拠を収集し、その結果を再度 SCC に返すという流れです。このように1つの場所（SCC）で多様な検証結果を統合し、コンプライアンス担当者が一括で把握できるようになります。

次のスライドをお願いします。

この Exchange Protocol を実現するために、私たちは複数の OSCAL モデルを使っています。たとえば PVP から SCC へコンプライアンス結果を送信する際には、Assessment Results モデルを使います。一方、SCC から PVP へ「このコントロールを検証せよ」というルールやパラメータの情報を渡す際には、現在 System Security Plan（SSP）モデルを使っていますが、将来的には Assessment Plan モデルを活用して、より高度な評価手順まで明示的に指定できるようにしたいと考えています。

OSCAL の SSP は、コンポーネントやインベントリ情報、パラメータなどを含む形でシステムの実装状況を示すことが可能です。そこに加えて Assessment Plan を使えば、どのコントロールをどう評価するかを明確に示し、その結果をコントロール単位で集約して Assessment Results として返せるようになるわけです。

次のスライドをご覧ください。

### OSCAL を利用した API の具体例

実際の API としては2種類あります。1つ目が「Policy Retrieval API」で、PVP が SCC に対して「どのコントロールやルールセットを検証すればよいか」を問い合わせるためのものです。2つ目が「Results API」で、PVP が検証結果を Assessment Results として SCC にアップロードします。

Policy Retrieval API では、あらかじめ SCC 上に「プロファイル」（どのコントロールやルールを対象とするか）や「コンポーネント定義」（各ベンダー製品がどのようなコントロールをどう実装しているか）、「チェック定義」（同じルールでも複数のツールで異なる実装があり得る）、「スコープ」（どのシステム群に対して適用するか）などの情報が登録されていると想定します。PVP はこうした情報をまとめて取得し、対象となるシステム群に対して検証を実行したうえで、Evidence を収集します。

次のスライドをご覧ください。

ここに示しているのは実際に返される “policy response” の一例です。現在は SSP を使って返しているのですが、内部的にはプロファイル相当の情報を埋め込んでおり、どのコントロールを検証すべきかや、そのパラメータ値、スコープやリソースグループなどを示す「property」などが含まれます。現状、OSCAL スキーマ上はプロパティをグルーピングする仕組みがないため、remarks フィールドを使った作業的な回避策をとっていますが、今後この辺りをより正式に扱えるようにしたいと考えています。

次のスライドをご覧ください。

2番目の「Results API」は、PVP が Assessment Results を SCC へアップロードするのに使います。具体的には、検証したインベントリ情報（Inventory Items）、各ルールに対する観測結果（Observations）、どのスコープやプロファイルに基づく検証か、といった情報を送ります。次のスライドで示す例のように、Assessment Results の “results” セクションを使い、プロファイルやスコープの情報を property として記載し、各インベントリアイテムがどのルールをどう満たしているかという観測をまとめて送信します。

それぞれのツールがルールを異なる名称で呼ぶことがあるため、私たちは “class” フィールドで概念を統一し、SCC が解釈できるようにしています。たとえばあるツールが「IDREF」という名前でルールのIDを表すなら、それに対応する “class” を設定し、SCC はそれを共通のルールIDとして解釈できるようになっています。

次のスライドをご覧ください。

### Tanium との連携の例

Tanium はエンドポイントにクライアントをインストールし、そこから得たデータをセキュリティ設定や脆弱性の観点で評価する仕組みを提供しています。私たちはこれを IBM Cloud の Security and Compliance Center と連携させたいと考えました。

IBM Cloud のドキュメントを参照していただくと、Tanium を SCC と連携させるステップが示されています。ユーザはまず scope を作成し、Tanium 側を SCC にデータを送れるよう設定します。裏側では Tanium がネイティブなフォーマットで生成した情報を受け取り、OSCAL の Assessment Results に変換してから SCC に渡すという流れになります。

こちらのスライドにあるように、Tanium が出力するネイティブフォーマットは独自の JSON ですが、これを標準化するため、私たちはスプレッドシートでフィールドの対応表を作りました。Trestle というツールや、少量の Python コードを使って、このネイティブフォーマットを OSCAL の Assessment Results 形式に変換しています。

では Trestle について簡単に説明します。これは以前の NIST ワークショップでも紹介しましたが、Python ベースのオープンソースツールで、OSCAL ドキュメントを編集・管理するワークフロー自動化を支援するものです。Trestle は、OSCAL スキーマの制約を厳密に enforce するオブジェクトモデルを提供し、データが常に OSCAL 準拠となるよう導いてくれます。また、Flask などの Web フレームワークと統合して、API 入出力を自動でバリデーションすることも可能です。

これにより、たとえばネイティブな Tanium JSON を OSCAL Assessment Results に変換するような処理を、非常に少ない行数のコードで実装できます。私たちは Trestle に「トランスフォーマ（Transformer）」と呼ばれる機能を追加し、Tanium や OpenShift Compliance Operator などのフォーマットを OSCAL にマッピングする仕組みを作りました。Trestle のドキュメントには、Excel から OSCAL Catalog や Component Definition に変換する例などのデモも掲載していますし、独自のツールや形式を OSCAL へ変換したい場合のチュートリアルも用意しています。
