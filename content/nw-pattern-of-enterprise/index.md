---
title: 企業のネットワークアクセスパターン
author: 田中(゜p゜)
type: page
date: 2020-09-05T04:35:54+00:00
catchbox-sidebarlayout:
  - default

---
<div class="wp-block-image">
  <figure class="aligncenter size-large"><img loading="lazy" width="180" height="180" src="/wp-content/uploads/2020/09/computer_wireless.png" alt="" class="wp-image-449" srcset="https://tmp-net.biz/wp-content/uploads/2020/09/computer_wireless.png 180w, https://tmp-net.biz/wp-content/uploads/2020/09/computer_wireless-150x150.png 150w" sizes="(max-width: 180px) 100vw, 180px" /></figure>
</div>

美味しいの？ シリーズ3本書いて若干疲れてきたので、少し気分を変えて。  
  
クラウド・サーバー・PCの話ばかり書いてますが、そもそも田中の出自はネットワーク屋なので、たまにはネットワークを軸に記事書きたいな、と思い。  
  
とはいいつつ、この記事は**営業向けにクラウドを使う際のネットワークのデザインパターンについて説明したもの**であって、深い技術の話じゃないですけど。  
  
あとこれ、手弁当で作ったので完全に田中(゜p゜)のオリジナルです。  
特定の企業の工数使って作ったものじゃないので、情報漏洩とかではない。念のため。

## 企業ネットワークの歴史

  * 過去、企業のネットワークといえば、閉じた世界「LAN(Local Area Network)」が中心だった。
  * 1990年後半からのインターネットの爆発的な成長に伴い、**インターネット接続が前提で企業ネットワークが構成される**ようになった。ASP(SaaS)、InternetVPN等。
  * 現在、クラウドファーストでシステムが構築されるようになり、ネットワークのあり方がさらに変わろうとしている。
  * **「閉じた世界」→「開いた世界」**へ。

## 今回は何を説明するか

  * 過去の経緯はさておき、企業の成長フェーズに合わせてどうネットワークが構築されていくのか、順を追って説明します。
  * クラウドのドアノック的な活動として、ネットワークの小話ができるようになれればいいと思います。

## フェーズ1：インターネット使うだけ

  * 10〜20人くらいまでのアクセスであれば、コンシューマ向けの携帯キャリア接続、インターネット回線で事足りる。
  * LANとインターネットを分かつ機器は、(簡易でも)FW機能を備えている。LAN側にある機器にはローカルIPが付与されていることに注意。

<div class="wp-block-image">
  <figure class="aligncenter size-large is-resized"><img loading="lazy" src="/wp-content/uploads/2020/09/image-8.png" alt="" class="wp-image-440" width="601" height="224" srcset="https://tmp-net.biz/wp-content/uploads/2020/09/image-8.png 842w, https://tmp-net.biz/wp-content/uploads/2020/09/image-8-300x112.png 300w, https://tmp-net.biz/wp-content/uploads/2020/09/image-8-768x286.png 768w" sizes="(max-width: 601px) 100vw, 601px" /></figure>
</div>



## フェーズ2：共同作業場が必要になる

  1. 10人を超えてくると、共同作業場が必要となる。手っ取り早く拠点LANにNASやサーバを追加。
  2. システムが増え、安定性が重要になると、InternetVPNなどでデータセンターと接続し、サーバを利用する。

<div class="wp-block-image">
  <figure class="aligncenter size-large is-resized"><img loading="lazy" src="/wp-content/uploads/2020/09/image-9.png" alt="" class="wp-image-441" width="585" height="309" srcset="https://tmp-net.biz/wp-content/uploads/2020/09/image-9.png 842w, https://tmp-net.biz/wp-content/uploads/2020/09/image-9-300x159.png 300w, https://tmp-net.biz/wp-content/uploads/2020/09/image-9-768x407.png 768w" sizes="(max-width: 585px) 100vw, 585px" /></figure>
</div>



## フェーズ3：拠点が増える/大きくなる

  1. 500人以上の規模となり、システムの重要性がさらに高まると、専用線を導入したり。コンシューマ向けの10倍以上の価格と引き換えに、SLA※とセキュリティを得る。
  2. 拠点が大きくなると、L3スイッチを導入し、セグメントを分ける。
  3. 外部とデータを交換するための「DMZ」を作ったりする。<figure class="wp-block-image size-large is-resized">

<img loading="lazy" src="/wp-content/uploads/2020/09/image-10.png" alt="" class="wp-image-442" width="595" height="307" srcset="https://tmp-net.biz/wp-content/uploads/2020/09/image-10.png 868w, https://tmp-net.biz/wp-content/uploads/2020/09/image-10-300x155.png 300w, https://tmp-net.biz/wp-content/uploads/2020/09/image-10-768x396.png 768w" sizes="(max-width: 595px) 100vw, 595px" /> </figure> 

## 中規模以上の拠点LAN構成例

  * 100人以上の拠点のLAN環境は、拡張性のため、階層構造を取る。
  * 有線LANは、全ての配線をラックに集約する統合配線パターンと、島単位でHUBを設置するケースが多い。
  * 多数の無線APを設置する場合は、自動的に無線の電波強度やチャンネルを調整する「無線コントローラ」を入れるケースがある。

<div class="wp-block-image">
  <figure class="aligncenter size-large"><img loading="lazy" width="889" height="411" src="/wp-content/uploads/2020/09/image-11.png" alt="" class="wp-image-443" srcset="https://tmp-net.biz/wp-content/uploads/2020/09/image-11.png 889w, https://tmp-net.biz/wp-content/uploads/2020/09/image-11-300x139.png 300w, https://tmp-net.biz/wp-content/uploads/2020/09/image-11-768x355.png 768w" sizes="(max-width: 889px) 100vw, 889px" /></figure>
</div>



## クラウドのアクセスパターン

だいたいはデータセンターと同じように利用するが、そもそもリソースがインターネットに置かれているので、本質的にはエンド to エンドのセキュリティを強化した上で、(1)のアクセスパターンとした方が、LANも不要となるし、費用対効果が高い。

  1. インターネットのサーバに直接アクセス。
  2. VPNや専用線経由でクラウド側の「VPC(LAN)」に接続。既存環境と同様にサーバを使う。<figure class="wp-block-image size-large">

<img loading="lazy" width="868" height="450" src="/wp-content/uploads/2020/09/image-12.png" alt="" class="wp-image-444" srcset="https://tmp-net.biz/wp-content/uploads/2020/09/image-12.png 868w, https://tmp-net.biz/wp-content/uploads/2020/09/image-12-300x156.png 300w, https://tmp-net.biz/wp-content/uploads/2020/09/image-12-768x398.png 768w" sizes="(max-width: 868px) 100vw, 868px" /> </figure> 

## 素朴な疑問

**<span style="color:#00b40f" class="has-inline-color">Q. クラウドなのにLANって意味あるの？</span>**  
**<span class="has-inline-color has-blue-color">A. 本質的には不要ですが、大人の事情があります。</span>**

  * 論理的にはエンド to エンドでセキュリティが確固としてれば不要。
  * 金融とかセキュリティ的に面倒な規約が背後にある場合は、インターネット経由なんてもってのほか、というケースもある。
  * 過去のLAN資産を抱えているほど、構成的にもルール的にも前頁(1)への移行が難しいケースがあります。
  * 逆に、新興ベンチャーが多量のリソースを使いたい場合は最高にオススメ

※Googleは(1)に寄っており、AWSやAzureはマーケットインの観点で(2)に寄ってます。

**<span style="color:#00a30f" class="has-inline-color">Q. クラウドのネットワークってソフトで動くんじゃないの？</span><span style="color:#009900" class="has-inline-color">物理いる？</span>**  
**<span class="has-inline-color has-blue-color">A. ぐぬぬ。その通りです。</span>**

  * SDN(Software Designed Netwok)はまさにそれで、物理では再現できない柔軟なネットワークを構成できます。
  * 今後クラウドの利用が一巡したら、**物理のネットワークしかできないエンジニアの市場は縮小一方**となると思われます。

## まとめ

  * 企業のフェーズによって、ネットワーク構成は似たり寄ったり。
  * 専用線はセキュリティや品質を担保したい時に高い金を積んで使うもの。
  * クラウドはインターネットアクセスが基本だが、企業の事情によりLANでつないで利用している場合がまだまだある。