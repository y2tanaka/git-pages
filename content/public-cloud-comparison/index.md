---
title: パブリッククラウド市況と比較
author: 田中(゜p゜)
type: page
date: 2020-09-05T06:45:20+00:00
catchbox-sidebarlayout:
  - default
og_img:
  - /wp-content/uploads/2020/09/image-22.png

---
<div class="wp-block-image">
  <figure class="aligncenter size-large"><img src="/wp-content/uploads/2020/09/image-22.png" alt="" /></figure>
</div>

これまた大きく出ましたが、田中(゜p゜)が**なまくら刀でパブリッククラウドを比較**しまーす。  
  
比較表とかはいろいろなところで出回ってますし、**どこかのクラウドを押したくてバイアスかかってるコメントが多い**ので、あくまで田中(゜p゜)視点＋主観ということで。  
  
それと、「[クラウド化の足音][1]」で書いた内容について、過去作成した資料出てきたんで、冒頭で捕捉しますね。

## クラウドに移行すると幸せ？

オンプレからクラウドに移行すると費用は割高ですよ、という話しましたが、どっかの会社のインフラ基盤公開の例でざっっくりAWSと5年比較してみた資料があったので載せてみます。

**・前提**  
　2000人収容のリモートデスクトップ基盤  
　150台の仮想サーバ  
　ストレージ計50TB  
　月間トラフィック86TB

**・オンプレ実績**  
　HW＋構築費用＋60か月維持費用  
　=<span class="has-inline-color has-blue-color"><strong> 9億7千万円</strong></span>

**・AWS(Calculatorで比較)  
** 　EC2 150台＋SSD 50TB＋ Workspaces2000台(稼働100%と稼働20% 半々)  
　= <span class="has-inline-color has-blue-color"><strong>10億5千万円</strong></span>

<div class="wp-block-image">
  <figure class="aligncenter size-large is-resized"><img loading="lazy" src="/wp-content/uploads/2020/09/image-15.png" alt="" class="wp-image-472" width="561" height="382" srcset="https://tmp-net.biz/wp-content/uploads/2020/09/image-15.png 444w, https://tmp-net.biz/wp-content/uploads/2020/09/image-15-300x204.png 300w" sizes="(max-width: 561px) 100vw, 561px" /></figure>
</div>

  
**あれ？ 10%や20%高いどころじゃなくね？**  
だってこの資料、AWSの移行費用見積もり取るのがしんどくて、移行とか運用の工数とか入ってないですもん。  
  
…まあいいか。高くなってしまうことは伝わったはずなので。

## クラウド化によるメリット

単純に移行しただけだとITインフラの維持コストは高くなってしまいますが、それとトレードオフになるクラウド化によるメリットは概ね以下の三つで、うまく生かせば**人件費も含めたコスト削減が図れる**んだと思います。<figure class="wp-block-image size-large">

<img loading="lazy" width="775" height="405" src="/wp-content/uploads/2020/09/2020-09-12-170304_1366x768_scrot.png" alt="" class="wp-image-618" srcset="https://tmp-net.biz/wp-content/uploads/2020/09/2020-09-12-170304_1366x768_scrot.png 775w, https://tmp-net.biz/wp-content/uploads/2020/09/2020-09-12-170304_1366x768_scrot-300x157.png 300w, https://tmp-net.biz/wp-content/uploads/2020/09/2020-09-12-170304_1366x768_scrot-768x401.png 768w" sizes="(max-width: 775px) 100vw, 775px" /> </figure> 

<div class="wp-block-group">
  <div class="wp-block-group__inner-container">
    <p>
      が、「<a href="/article/footsteps-of-cloud/">クラウド化の足音</a>」で書いたように、日本では企業内の政治的な理由により、なかなか進まんのが現実だと田中(゜p゜)は思ってます。
    </p>
  </div>
</div>

## 日本固有？の課題

  * 終身雇用と雇用制限のおかげで、情報システム部門がイケてない人たちの受け皿と化しており、技術をベンダーに丸投げせざるを得ない。
  * 開発も運用も**ベンダー丸投げ/ウォーターフォール**にどっぷり。
  * ベンダーが積極的にパイの削減に努力はしないため、先進的な開発手法も身につかない。
  * 逆に欧米は自前でシステムを開発するので、スピード、コスト削減に対するモチベーションは高い。

**とは言え…**  
国内のインテリジェント(笑)な企業は、長期的な視点で情報システムに効果があることに気づいており、インフラ移行レベルの低レイヤのクラウドの活用は一巡していて、**①②③のようなメリットを生かすクラウド活用にシフトして**ます。

また、AIやビッグデータ領域での活用が盛んになっており、**学問＋IT技術を備えたエンジニアがウン千万で直接雇用されてたり**する。

## クラウド市況

2018年の情報なんでちょい古いですが。各クラウドベンダーのシェア状況比較です。

<div class="wp-block-image">
  <figure class="aligncenter size-large is-resized"><img loading="lazy" src="/wp-content/uploads/2020/09/image-20.png" alt="" class="wp-image-478" width="498" height="310" srcset="https://tmp-net.biz/wp-content/uploads/2020/09/image-20.png 592w, https://tmp-net.biz/wp-content/uploads/2020/09/image-20-300x188.png 300w" sizes="(max-width: 498px) 100vw, 498px" /></figure>
</div>

まとめると、以下のような感じでしょうか。

  * 相変わらずAWSのシェアがぶっちぎりだが、**AzureがOffice365、ADとの連携を武器にシェアを大きく伸ばす展開**。
  * 他、IBMは自前のハードウェアとカニバっていたが、クラウドにシフトする意思決定をした模様。シェアは下がり気味。
  * Alibaba(Softbankが出資)は中国に特化しており、シェアを伸ばす状況。
  * その他大勢はシェアを大きく減少しており、**市場は上位クラウドベンダーに絞り込まれつつある**。

田中(゜p゜)が好きではないホワイトクラウド系が軒並みシェアを失っていて、まあ、なんだかなぁ、という状況。

それと、IBMはオンプレとカニばっててたぶんこの先厳しいので、**AWS、Azure、GCPが生き残る感じ**でしょうか。

…すみません。  
この三つは田中(゜p゜)使ったことあるんで、結論ありきです。

## 三大クラウドの比較

ようやく本題です。  
費用とか性能とか、客観的なデータはインターネット検索すれば転がってると思うので、田中の主観ではありますが、三大クラウド比較してみました。<figure class="wp-block-image size-large">

<img loading="lazy" width="774" height="500" src="/wp-content/uploads/2020/09/2020-09-12-165802_1366x768_scrot.png" alt="" class="wp-image-617" srcset="https://tmp-net.biz/wp-content/uploads/2020/09/2020-09-12-165802_1366x768_scrot.png 774w, https://tmp-net.biz/wp-content/uploads/2020/09/2020-09-12-165802_1366x768_scrot-300x194.png 300w, https://tmp-net.biz/wp-content/uploads/2020/09/2020-09-12-165802_1366x768_scrot-768x496.png 768w" sizes="(max-width: 774px) 100vw, 774px" /> </figure> 

**AWSについて  
** まじでホスピタリティがすごいです。AWSそのものの営業とかサポートの優秀さもそうですが、コミュニティも強力でインターネットのドキュメントも豊富だし、困っても誰かがナレッジを持っている。サポートも、AWSじゃない範囲にまでグイグイ踏み込んでサポートしてくれます。  
  
言い換えますが、**田中(゜p゜)はベンダーと相対していてこんなにやさしくされたことない**っす。  
  
**GCPについて**  
田中(゜p゜)はGCP使うベンチャーに居たので、比較的よくわかるのですが、この中でGCPだけがプロダクトアウト型のような気がするんですよ。「**自分らがカッコいいと思うものはユーザーもかっこいいと思うに違いない**」というような。  
  
いや、Googleの人たちは基本的に頭いいし、技術に寄ってるから…。一般庶民とのニーズとギャップある気がするんですよね。  
ユーザがヴォクシー乗りたがってるのに、86提案しちゃう感じ？  
  
このあたりの企業のカルチャーが、今後、市場に対してどう影響するかは気になります。  
  
**Azure/o365について**  
正直パフォーマンスも悪いし、APIもイケてないないので、クラウド単体としてはあまり好きじゃないのですが、**Microsoftの戦略はかなりヤバい(いい意味で)**と思うので、**[別記事に記載][2]**します。

## まとめ

  * クラウド化しただけではコスト削減にならない。運用の工夫が必要。
  * 日本は、組織的な制約があり、クラウド化は遅れているが、いずれクラウドにシフトしていく。
  * クラウドベンダーの淘汰は進み、3～4のメガクラウドに絞られつつある。
  * メガクラウドはどこも似たようなサービスを提供しているが、それぞれの文化、戦略に違いはあるので、ITインフラとしてどうすべきか見極めが必要。

 [1]: /article/footsteps-of-cloud/
 [2]: /article/how-dericious-is-o365/