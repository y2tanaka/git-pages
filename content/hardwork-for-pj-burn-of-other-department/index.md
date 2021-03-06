---
title: 他部署の炎上食い止めに奮闘
author: 田中(゜p゜)
type: page
date: 2020-09-07T04:55:18+00:00
catchbox-sidebarlayout:
  - default

---
<div class="wp-block-image">
  <figure class="aligncenter size-large is-resized"><img loading="lazy" src="/wp-content/uploads/2020/09/figure_shouka.png" alt="" width="227" height="232" /></figure>
</div>

情報システム部門のマネージャ時代の話。  
社内のサーバをクラウドに上げ、業務を一通り最適化して**ヒマを持て余してたので**、隣の技術開発部門の要請に応じて、**プロジェクト案件を手伝う**ことに。  
  
よく考えたら、結構自由だったな。この会社。

## 案件内容

  * タイトル: 某公共案件 セキュリティクラウド構築案件
  * 案件規模： スポット 予算？？億 メンバー15人 エンドユーザー ？？？？人
  * 田中(゜p゜)のポジション： メールサーバー設計構築 ＆ **にぎやかし(笑)**

## **経緯**

公共のセキュリティクラウド案件で、エンジニアが全般的に足りてないということだったので、支援に入りました。メンバーは15人位の、インフラとしては大所帯。  
  
田中(゜p゜)が担当したのはBlueCoatとFortigateのメールサーバ。  
が、蓋を開てみると…。**ヤベぇポイントがたくさん**。

## **失敗？の内容**

正直、プロジェクトの運営がグダグダでした。  
表面的には以下のような事象が起こってました。

<ul id="block-781c81eb-bf79-4365-936c-dedde7d11264">
  <li>
    進捗会議が一部のメンバーだけで行われ、内容が現場に共有されていない
  </li>
  <li>
    WBSが週単位で更新が遅れている
  </li>
  <li>
    PMが常に深夜残業している。PLが何をしているか分からない
  </li>
  <li>
    プロキシ、メールサーバについて、終わっているはずの設計が終わっていない
  </li>
  <li>
    ネットワーク担当者が何故か怒り狂っている。
  </li>
  <li>
    PM・PLは客に問題ないと報告している。
  </li>
</ul>

うん。**ヤバい。**  
田中(゜p゜)のPMとしての直感も、**赤いパトランプぐーるぐーる回してました**。  
田中(゜p゜)の担当範囲は全力でリカバリできるにしても、このプロジェクトの状況はなんなんだ。  
  
ざっと見積もったところ、**残り3ヶ月にして2weekほどの遅延**。  
**いや、ヤバい。本当にヤバい。**

## **原因**

原因ですが、**結論から言って体制ですね。**  
  
**PMはいい人。とにかくいい人。**  
とにかく周囲と波風立てたくない。トラブってるのもなるべく内密にして、上司に心配かけたくない。でも、**PMっていい人でいられないケースって多い**んですよね。  
  
**PLは**。  
何考えてるか分からなくて、動きも読めず、とにかくタスクの完了予定直前までなにか動いてるように見えない、いけ好かない人物。おそらく技術的、マネジメントスキル的に自信が無かったように思われるが、**最後までよく分からなった**。  
  
ネットワークエンジニアは…。  
あるべき論を通したい人なんだけど、**まっすぐ過ぎて周囲と軋轢を起こしてしまう人**。  
  
と、いう三人が組み合わさった結果、**ネットワークエンジニアの要求するタスクが積み上がり、PLが何もしないため**タスクが消化されず**、PMのみが困り果てる**という図式に。  
  
アウトでしょ、コレ。

## **結果**

田中(゜p゜)はとりあえず恥も外聞も捨てて**全開でにぎやかし**にかかりました。  
つまるところ、プロジェクト**PMの上の偉い人に非公式にプロジェクトの状況を伝え、支援がないとしにますよ**、という話をした。  
  
迷惑極まりない話かもしれないけど、**お客さんに迷惑をかけるより良い**と思いまして。  
**テヘッ。**  
  
しかし、この会社はマトモな会社だったんでしょうね。  
すぐさま**PMの部署の役員が、エース級のPMと、プロジェクト管理のスペシャリストの支援を手配**してくれ、リカバリプランを作成。  
社長にまでエスカレーションが走り、**リカバリプランも承認**。  
  
たぶんここまで行けば、プロジェクトは建て直りますよ。  
**実力のある偉い人がヤベぇ状況を把握していて、そこに対して手当をしようとする意思がある限り、そうそうプロジェクトは崩れない。  
**  
果たしてこのプロジェクトも、部分的な納期遅延、スコープ変更などはあったもの、**無事サービスインしました**。  
  
なおざりにしていた運用設計は強化され、運用の体制も当初より厚くなり、サービスレベルも向上するというオマケ付き。  
  
**めでたしめでたし。**  
  
  
あと書くの忘れてたけど、田中(゜p゜)の**メールサーバーの構築はけっこうしんだ。**  
Fortigateのアプライアンスだったんだけど、メーカーの営業がこの会社にベンダーやらせたくなかったみたいでなかなかサポート情報が回ってこず。  
  
もちろん納期には間に合わせましたが、残業ヤバかった。

## **反省点**

正直田中(゜p゜)の動きとしては悪くなかったと思うけど、普通に堅苦しい会社だったら顰蹙ものだなぁ、と今でも思います。  
  
それと、PLがあまりになにもしないので田中(゜p゜)がガチキレしてしまい、深夜に同じ部署内の大人しいオジサンの袖机にケリ入れてを軽く凹ませてしまいました。  
  
次の日そのオジサンが「…僕の机、凹んでるんだけど、何か悪いことしたかなぁ」なんて言ってて、心が痛くなりました。  
  
ゴメンナサイm(_ _)m

<p class="has-text-align-right">
  2020/09/15
</p>