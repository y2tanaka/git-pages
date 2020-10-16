---
title: どーでもいい機器のためにLAN全滅
author: 田中(゜p゜)
type: page
date: 2020-09-06T18:59:52+00:00
catchbox-sidebarlayout:
  - default
og_img:
  - /wp-content/uploads/2020/09/business_group_shock.png

---
<div class="wp-block-image">
  <figure class="aligncenter size-large is-resized"><img loading="lazy" src="/wp-content/uploads/2020/09/business_group_shock.png" alt="" class="wp-image-501" width="233" height="233" srcset="https://tmp-net.biz/wp-content/uploads/2020/09/business_group_shock.png 400w, https://tmp-net.biz/wp-content/uploads/2020/09/business_group_shock-300x300.png 300w, https://tmp-net.biz/wp-content/uploads/2020/09/business_group_shock-150x150.png 150w" sizes="(max-width: 233px) 100vw, 233px" /></figure>
</div>

[前の記事][1]では田中(゜p゜)の炎上経験を取り上げました。  
今回も炎上？しかかった案件について書きたいと思います。前回の記事が重苦しいような気がしますので、今回は内容も文体もライトに。

## **案件内容**

  * タイトル: 某中小企業 本社LAN更改案件
  * 案件規模： スポット1500万 メンバー3人 エンドユーザー200人
  * 田中(゜p゜)のポジション： PM兼NWエンジニア

## **経緯**

正確には、炎上というより炎上しかかった案件。  
200人位の規模の企業の、老朽化による本社L3SW、L2リプレイス。後継機に入れ替えるだけだったので、ローリスクローリターン案件、のはずだった。

## **失敗の内容**

納品、サービスイン後3日後にお客様からコール。**本社LANの機能が全滅した**のですぐ来て欲しいとのこと。  
結果から言うと、たぶん田中(゜p゜)は失敗してない。お客さんが失敗したんじゃないかな。

## **原因**

↓コレ。<figure class="wp-block-image size-large is-resized">

<img loading="lazy" src="/wp-content/uploads/2020/09/computer_hub_loop_setsuzoku-1.png" alt="" class="wp-image-493" width="98" height="83" srcset="https://tmp-net.biz/wp-content/uploads/2020/09/computer_hub_loop_setsuzoku-1.png 400w, https://tmp-net.biz/wp-content/uploads/2020/09/computer_hub_loop_setsuzoku-1-300x254.png 300w" sizes="(max-width: 98px) 100vw, 98px" /> </figure> 

ループガード入れていたが、なぜかブロードキャストストームが発生。突き止めたくても**LAN内はワケわからんパケットで溢れててWireShark読み切れない**し、導入した機器のコンソールは遅くて使えない状態になってる。トレースのしようがない。  
  
どうせ全体が使えないんだし、おそらく端末が悪さしてるんじゃないかという勝手な憶測の元、L3SWとL2SWの間のLANケーブルを一本一本抜き差しして、Floodingが止まるかどうか確認。**特定のL2SWを抜いたらL3SWが復旧する**ことを特定。  
  
同じように、死んでるL2SWのポートを一本一本抜き差しして、特定のポートを抜いた時にL2SWが復旧することを確認。  
  
該当のポートの統合配線の先を辿って行ったら、サーバールームの不要品置き場のような場所にたどり着き、何も繋がっていない古ぼけたBuf○aloのノンインテリジェントHUBを発見。

![][2] 

  
**お前かーい！**  
  
HUBが壊れたのが原因でした。orz  
たぶんサーバー室での作業用に設置してたのを忘れてたんでしょうね。

## **結果**

当然だけどお咎めは特になし。  
だけど、事情を知らない本社の皆様からはひどく冷たい目で見られた。納得いかない。  
というか、酷いタイミングで壊れますなぁ。

## **反省点**

よく考えたら、ループガードは入れてたけど、Floodingガード的なブロードキャストに対して閾値を設けてシャットダウンする機能入れておけば、もう少し被害は軽減できたかもしれない。アライド製品だったので、ひょっとしたらその機能はなかったのかもしれない。記憶に無いです。  
  
あと、**ヤバい機器はLANに参加させちゃいけない。色々な意味で**。

<p class="has-text-align-right">
  2020/09/13
</p>

 [1]: /article/failuer-of-product-choice/
 [2]: /wp-content/uploads/2020/09/image-25.png