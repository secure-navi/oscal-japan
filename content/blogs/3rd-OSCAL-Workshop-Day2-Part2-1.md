+++
date = '2024-10-30T14:09:33+09:00'
draft = false
title = 'AWSにおける顧客体験の重要性とOSCALの採用'
categories = [
    "3rd OSCAL Workshop",
]
image = 'images/blogs/3rd-OSCAL-Workshop-Day2-Part2-1_eyecatch.jpg'
+++

この記事は、2022年3月にNISTが開催した「[3rd Open Security Controls Assessment Language (OSCAL) Workshop](https://csrc.nist.gov/Events/2022/3rd-oscal-workshop)」の、Day2 Part2の公演内容をもとに、一部要約を行い、日本語に翻訳したものです。

Day2 Part2 では大きく2つのテーマについて公演が行われました。この記事では、AWS チームによる「AWS と OSCAL の実装」について紹介しています。

ぜひ、実際の資料は動画も確認しながらご覧ください。

{{< iframe src="https://cdnapisec.kaltura.com/p/684682/sp/68468200/embedIframeJs/uiconf_id/33598632/partner_id/684682?iframeembed=true&playerId=kaltura_player_1647535799&entry_id=1_c2gqy160&flashvars[streamerType]=auto" >}}

---

### 自己紹介

皆さん、こんにちは。AWS のマシュー・ダンカンと申します。始めるにあたり、まずはオーガナイザーであり、OSCAL を生み出したミケーラ・イオルガ博士に感謝を申し上げます。このイベントを企画いただき、さらに AWS にも声をかけてくださったこと、本当にありがたく思います。

これは AWS としての OSCAL 実装に関するプレゼンテーションです。先ほどミケーラも言ったように、私の他にジェームズ・ミューラー、ダグラス・ボルトが一緒に参加しています。次のスライドをお願いします。

目次としては、AWS での実装や、そこから期待されるお客様へのメリット、そして AWS が提供しているドキュメントについて、お客様体験の向上や、OSCAL 実装時の課題、最後にまとめと Q&A の時間を設けます。次のスライドをお願いします。

### AWS における OSCAL の活用

では、AWS における OSCAL 実装について。次のスライドを。

AWS としては、Telos 社の Xacta というガバナンスリスクマネジメント（GRC）ツールを使って、OSCAL 形式の認証パッケージを複数分類レベル（機密度合い）で提供できるようにしようと考えています。具体的には、機密区分として Unclassified、Secret、Top Secret の3つすべてに対応した OSCAL ファイルを提供することが狙いです。こうした取り組みには、FedRAMP テンプレートを用いる予定です（昨日のセッションでも FedRAMP のチームがリンクを示していましたね）。当社がこれを行う理由は、認証パッケージの一部を自動化し、人間が行う作業によるミスを減らしたいからです。たとえば何百ページ、あるいは千ページ超のドキュメントを人力でチェックしていると、どんなに注意してもヒューマンエラーが発生します。そこを機械可読化、機械処理によって防ぎたい。

そうすれば我々が作成する認証パッケージもタイムラインを圧縮できるし、それをレビューする第三者評価機関（3PAO）にとっても時間を削減できます。結果的に認可取得の時間軸が短縮され、お客様へのサービス提供開始を早められるわけです。次のスライドを。

### OSCAL の利用による顧客へのメリット

続いて、OSCAL が提供するお客様メリットについてお話しします。たとえば FedRAMP の場合、AWS のサービス認可にあたり、FedRAMP 認証までの時間を2週間ほど短縮できると見込んでいます。つまり、認定済みの新サービスをいち早くお客様が利用できるようになるということです。さらに DoD（米国国防総省）のCC SRGインパクトレベル4、5においては、FedRAMP 同様に OSCAL形式でファイルを提出することで、審査機関（DISA RME）側の処理が早まり、追加で2週間ほど短縮できると予想しています。

また、これによってセキュリティコントロールに関するドキュメントの取り回しや取り込みがシンプルになり、コピー＆ペーストや手動の転記といった作業が不要になります。お客様がコントロールドキュメントをレビューしたり更新したりする負担も減るでしょう。すべては“ATO（認可）プロセスの円滑化”に向けた取り組みです。機械可読化によって、人間ではなくマシン同士でやり取りが行われ、ヒューマンエラーや中間処理を極力排除できる。そうすることで、継続的なセキュリティ姿勢に対する透明性が高まり、また POA&M（是正計画など）のステータスをお客様が即座に把握しやすくなるわけです。次のスライドを。

ではここからはジェームズ・ミューラー（James Mueller）にバトンタッチして、AWS ドキュメントについて説明します。

### AWS 社内での OSCAL の利用

皆さん、こんにちは。私のパートでは、“OSCALを導入すると組織にどんな影響があるか”という視点で、NIST SP 800-53 のコントロールを例にとってみましょう。ご存じのとおり、選択するベースライン（Low、Moderate、High）に応じて相当数のコントロールを文書化しなくてはならず、High となるとおよそ400近いコントロールに対して実装内容を書かなければいけない。ここで登場するのがシステムセキュリティ計画、いわゆる SSP です。

AWS では IaaS のソリューションごとに、2つの SSP を維持しています。1つは East-West（商用リージョン）向け、もう1つは GovCloud 向け。イノベーションスピードの速い AWS では、毎月アップデートが入り、新しいサービスや機能、または既存サービスの変更などが SSP に反映されます。また年に1回、“SSPリフレッシュ”と呼ぶ大幅更新も行います。

SSP は Word 文書で、非常に長大です。たとえば GovCloud 向けは700ページを超えるんです。これを継続的に更新し続けるだけでもかなりの手間と人件費がかかることがおわかりかと思います。しかし SSP だけではありません。AWS では、お客様向けに SSP と関連したドキュメントを追加で提供しており、代表的なのが以下の2種類です。

- カスタマー・レスポンシビリティ・マトリックス（CRM）（IaaS 利用時のセキュリティ責任分担を示す文書）
- カスタマー・コンフィギュレーションガイド（CCG）（各サービスごとの構成手順をまとめたガイド）

GovCloud だけでも 110 種類、East-West 商用リージョンではさらに 200 種類のサービスを認可しているので、それぞれに関連する CRM や CCG も存在します。これらに対して、年間24回くらいの更新が行われています。利用実態を見ると、2022年には CRM/CCG 合わせて27,000超のビューダウンロードがあり、SSP のほうは昨年だけで 34,000 回ものダウンロード/閲覧がありました。

ここで OSCAL が生きてきます。ガバナンスリスクマネジメント（GRC）ツールなどにセキュリティコントロールを格納し、SSP を自動生成できるようになれば、膨大な時間を削減できます。さらにお客様が受け取る認証パッケージも、Word 文書ではなく OSCAL 形式ならば、手動更新の手間を大幅に省けるのです。まさに OSCAL は“ゲームチェンジャー”だと感じています。次のスライドをお願いします。

続いてダグラス・ボルト（Douglas Bolt）にマイクを渡します。

### AWS における「顧客体験」の考え方

ありがとうございます。AWS のソリューションアーキテクト、ダグラス・ボルトと申します。OSCAL を使ったときの運用効率についてお話しできることを嬉しく思います。次のスライドを。

AWS では“カスタマーオブセッション”という理念があり、あらゆる社員が“顧客体験を向上させる責任”を持つという考え方を徹底しています。新しいサービスの90%は顧客の要望に基づいて作られる、と言われるくらいです。現在、多くのお客様が“セキュリティ文書の管理にあまりにも時間を取られている”と訴えています。私たちが試算したところ、年間4,100時間、つまりフルタイム2人分の労力をセキュリティ文書作成や ATO パッケージ作成に割いているケースがある。手動でコピペして微調整をし……といった作業は“差別化されない重作業”（undifferentiated heavy lifting）だと言えます。

一方、OSCAL によってこうした文書管理が20～40時間程度で済むなら、2名分の人件費が大幅に節約できる。しかもこれは1組織の事例に過ぎません。多くの組織が同様に効率化できる可能性を秘めています。言い換えれば、今までフルタイム2名が文書作業に割いていた時間を、例えばセキュリティオペレーションセンターの構築など、より価値の高い業務に回せるわけです。次のスライドを。

以上が私からの説明で、マシューに再び戻し、“OSCAL 導入の課題” について話してもらいます。

### OSCAL の導入における課題

ありがとうございます。では続いて、AWS が OSCAL を実装するにあたり直面した課題についてお話します。次のスライドを。

大きく3点、①採用（Adoption）、②統合（Integration）、③協調（Collaboration）があります。採用に関しては、OSCAL が正しく機能するには、多くの人・組織がそれを扱える必要があります。GRC ツールやその他のツールにファイルを取り込み、“相互運用” ができないといけない。次に統合では、既存ツールとの連携において OSCAL は複雑な面があるものの、十分な意義があると考えています。
協調について言うと、CSP（クラウドサービスプロバイダ）や GRC ツールごとに微妙に違うテンプレートを使っていると、その差異が実装面で障壁になる恐れがあります。たとえばあるお客様が独自の OSCAL テンプレートを使いたいと言ってくるケースがあるかもしれませんが、当社としては“FedRAMP テンプレートを採用する”と決めており、バラバラな仕様になるのは好ましくない。また、政府と業界では優先事項に微妙なズレがある——政府はセキュリティを最優先する傾向があり、業界は（最終的に政府も顧客とはいえ）カスタマーオブセッションという考え方で動く。ただ、OSCAL が出てきたことで、両者の目線が合流しつつある。昨年・一昨年に比べると採用も増えています。次のスライドを。

### まとめ

最後にまとめです。OSCAL がもたらす可能性は非常に大きい。認証パッケージをより早く作成でき、セキュリティ文書作成の負担を下げ、認証取得までの期間を短縮し、お客様にとってもドキュメント周りの体験が向上する。とはいえ、広範な採用が必要で、既存ツールへの統合に伴う困難や、テンプレートを統一することの難しさもある。Telos などが真剣に取り組んでいるので、近い将来に素晴らしい成果が得られると信じています。
