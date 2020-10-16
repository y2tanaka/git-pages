---
title: ADって美味しいの？
author: 田中(゜p゜)
type: page
date: 2020-09-04T22:48:54+00:00
catchbox-sidebarlayout:
  - default
og_img:
  - /wp-content/uploads/2020/09/activedirectory.jpg

---
<div class="wp-block-image">
  <figure class="aligncenter size-large"><img loading="lazy" width="250" height="109" class="wp-image-397" src="/wp-content/uploads/2020/09/activedirectory.jpg" alt="" /></figure>
</div>

美味しいの？ シリーズ第二弾です。  
ActiveDirectory(AD)ってITインフラエンジニアにとってどうなのよ、という話です。  
  
結論から言うと。  
**  
結構おいしいと思う。**  
**知っておいて損はないし、知ってればインフラ全体が見渡せる可能性がある。**  
  
AD単体で切り離してみると、山ほど機能があって、焦点がボケがちなのですが、田中の認識でADは**Windows世界におけるユーザ・PC・サーバーの超便利管理ソフト**です。  
  
ポイントは以下の二点でしょうか。

  * ドメインに参加したユーザ、PC、サーバに対して強力なポリシー適用機能提供する。
  * ユーザの属性情報をため込んでおき、リソース(サーバ)の認証機能を提供する

<div class="wp-block-image">
  <figure class="aligncenter size-large is-resized"><img loading="lazy" class="wp-image-398" src="/wp-content/uploads/2020/09/image-7.png" alt="" width="457" height="354" srcset="https://tmp-net.biz/wp-content/uploads/2020/09/image-7.png 567w, https://tmp-net.biz/wp-content/uploads/2020/09/image-7-300x232.png 300w" sizes="(max-width: 457px) 100vw, 457px" /></figure>
</div>

要するに、**たくさんのサーバーやPCがあった場合に、管理がとても楽になり、工数(コスト)が削減できる**、ということです。  
  
これだけだとよくわからんと思うので、実際のケースで説明します。

## ADがないとしぬケース

**セキュリティ事故があり、PCの設定全部変えないと…。**

  * 情報漏洩があり、USB禁止、パスワード厳しくしろ、となどと突然言われるのは日常茶飯事
  * 1台1台丁寧に丁寧に変えていかなければならない。何千台もあったらしぬ。
  * **<span class="has-inline-color has-blue-color">ADならグループポリシーでボタン一発で解決。</span>**

**システムへのアクセス権限を、情報システム部門や営業などのメンバーで分けたい…。**

  * システム一つ一つにユーザーとグループを登録していかなければならない。
  * システムが多数あり、ユーザがたくさんいたらしぬ。
  * **<span class="has-inline-color has-blue-color">ADならセキュリティグループにユーザ登録すれば一発解決</span>。**

**オフィスに無線入れたので、PCの設定入れたい**

  * 証明書とか使う意識高い系設定なので、ユーザにやらせると絶対間違う…。
  * PC何百台とあるので、管理者が1台1台丁寧に丁寧に変えていったらしぬ。
  * **<span class="has-inline-color has-blue-color">ADならグループポリシーでボタン一発で解決。</span>**

それ以外にも、組織変更でアクセス権を一斉に変えたいとか、PCの設定を一斉に変えたいとか、山ほど要求あるので、この**一斉変更のコスト(工数)を大きく下げられるのがADのメリットで**あり、動かしがたい優位性なわけです。  
  
**<span class="has-inline-color has-blue-color">そう、ADならね</span>**  
  
とか言いたくなっちゃう。  
**キレイに管理できるOSはWindowsに限る**けど…。  
  
このあたりの優位性については、**すでにWindows2000の段階で確立されてた**はずで、あとの機能はだいたい拡張とかオマケだと田中(゜p゜)は思います。  
色々機能があって複雑に見えますけどね…。**コスト削減の主要因はシンプル**なのです。

## とは言いつつも

<div class="wp-block-image">
  <figure class="aligncenter size-large"><img loading="lazy" width="180" height="180" class="wp-image-399" src="/wp-content/uploads/2020/09/caste_company.png" alt="" srcset="https://tmp-net.biz/wp-content/uploads/2020/09/caste_company.png 180w, https://tmp-net.biz/wp-content/uploads/2020/09/caste_company-150x150.png 150w" sizes="(max-width: 180px) 100vw, 180px" /></figure>
</div>

**権限やポリシーというのは企業の組織の構造に深く関わってます。**  
すぐ思いつくのは、部署ごとにフォルダー作ってアクセス権管理したいとか、開発者や偉い人はPCで何でも使わせたいのでポリシー緩めたい、とか。  
  
ま、最初はそういう風に設計していくのでキレイなんですけどね。**組織変更のたびにカオスが広がる**んですよね。  
ADを長く使ってるどの企業も、以下の構造はだいたいカオスです。

  * グループポリシー
  * フォルダ構造とアクセス権
  * セキュリティグループ

以下、**田中(゜p゜)の妄想かもしれない悲劇**の例を紹介します。

## 経年に伴う悲劇の例

<div class="wp-block-image">
  <figure class="aligncenter size-large"><img loading="lazy" width="180" height="180" class="wp-image-403" src="/wp-content/uploads/2020/09/kojinjouhou_rouei_businessman.png" alt="" srcset="https://tmp-net.biz/wp-content/uploads/2020/09/kojinjouhou_rouei_businessman.png 180w, https://tmp-net.biz/wp-content/uploads/2020/09/kojinjouhou_rouei_businessman-150x150.png 150w" sizes="(max-width: 180px) 100vw, 180px" /></figure>
</div>

  * 凸凹社は部署ごとにフォルダとセキュリティグループを作成して、アクセス権を管理してました。そこに突然、**部署統合、分割が社長から言い渡されました**。
  * セキュリティグループの中身は**属人化して複雑に階層構造**になっており、かつフォルダの構造も同様の状態なので、どちらの部署に移せばいいのか、**誰も判断できません**。
  * 仕方ないので古いセキュリティグループを残し、新しいセキュリティグループに引っ越しました。
  * ある日、**情報漏洩事故が起こり、メディアに報道され、凸凹社の株価は大きく下がりました**。
  * 犯行は内部の協力会社の人で、**データをぶっこ抜いて競合他社に売り渡し**ていました。**原因はお察し**。

## ならどうするか(理想論)

  * システム側だけではなく、全社的に**どの「組織(グループ)」がどの「業務(システム)」を執り行い、どのような権限を持つべき**なのか、**運用ポリシーを可視化**するしかないと思います。システムにしろフォルダにしろ、業務設計のマトリクスをベースにする等。
  * ユーザに移管するとカオスが広がるので、**可能な限り主管部門で運用した方が良い**です。
  * **棚卸ルールを定め、組織変更のタイミング等で捨てる、移動する処理も必要**です。

理想論の部分については、実現できている企業は見たことないです。自分でやってみたいとは思います。  
このあたりの設計は運用コスト削減のキモだと思うのですが、**AD屋は業務なんて知ったこっちゃない**ので**大抵は組織変更一発でカオス**です。セキュリティ事故も起こります。  
  
なんだか後半はデメリットばかりになってしまいましたが、こうした経年カオスによるデメリットを差し引いても、**ユーザ、権限、ポリシーを一括管理できるメリットはデカい**んですよねー。

## まとめ

  * ADは超便利な「ユーザ」「PC」「サーバー」管理ツールで、対象がたくさんあるほど大きくコスト削減になる。
  * 権限やグルーピングが企業の組織の構造と深く関わっているので、組織変更のたびにカオスが広がり、いずれセキュリティ事故になる。