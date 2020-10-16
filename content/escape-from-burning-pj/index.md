---
title: 泥船から決死の脱出
author: 田中(゜p゜)
type: page
date: 2020-09-07T10:49:26+00:00
og_img:
  - /wp-content/uploads/2020/10/image-15.png
change-canonical:
  - https://tmp-net.biz/page-1698/

---
<div class="wp-block-image">
  <figure class="aligncenter size-large"><img loading="lazy" width="180" height="180" src="/wp-content/uploads/2020/09/jiko_ansyou_noriageru_man.png" alt="" class="wp-image-338" srcset="https://tmp-net.biz/wp-content/uploads/2020/09/jiko_ansyou_noriageru_man.png 180w, https://tmp-net.biz/wp-content/uploads/2020/09/jiko_ansyou_noriageru_man-150x150.png 150w" sizes="(max-width: 180px) 100vw, 180px" /></figure>
</div>

田中(゜p゜)は、過去インフラ系のプロジェクトのPM、PMO、PL、メンバーとして20年、山ほど案件を担当してきました。

辛いことは何度もありましたが、みなそれなりにやり通してきたと自負しとるのです。  
  
<span style="background-color: #00ffff" class="background-color"><strong>が、この案件だけは唯一途中で逃げました。</strong></span>  
  
ちなみに会社は脱出したことありますけど、その時は案件はクローズしてから去ってます。  
どうして失敗したのか、どうすればよかったのか、今でもいろいろ考えますが、答は見つかりません。  
  
この失敗を胸に刻み、何かを掴みたいと思ってこの記事を書いてます。

## **案件内容**

モノがモノだけに少しぼかしてます。あと背景書かないと理解しづらい部分あると思うので、他の記事より少し細かく体制を書きます。

  * タイトル: 　某官公庁系 情報システム基盤総入れ替え(データセンター、ネットワーク、サーバー、PC)
  * 案件規模： 予算：数十億 期間：5年 メンバー100人 エンドユーザー2000人
  * 田中(゜p゜) ： PM支援兼技術支援リーダー。配下10名

複雑なんで、体制を絵にすると、田中のポジションはだいたい以下の通り。

<div class="wp-block-image">
  <figure class="aligncenter size-large is-resized"><img loading="lazy" src="/wp-content/uploads/2020/10/image-19.png" alt="" class="wp-image-1734" width="607" height="459" srcset="https://tmp-net.biz/wp-content/uploads/2020/10/image-19.png 760w, https://tmp-net.biz/wp-content/uploads/2020/10/image-19-300x227.png 300w" sizes="(max-width: 607px) 100vw, 607px" /></figure>
</div>

田中(゜p゜)のポジションは、某ビックベンダーの技術統括/プロジェクト統括グループのアンダーに自社のメンバーを複数人を入れ、その人達を管理するというもの。  
  
ちなみにこの統括チームは<span style="background-color: #00ffff" class="background-color"><strong>総勢15人ほどいましたが、10人が田中(゜p゜)チーム</strong></span>です。さらに管下メンバーにこういうデカい案件の経験は一切ない。  
これだけでも相当無理あると思うんですが、これは理由を後で述べます。  
  
ビッグベンダーはグループ企業を多数抱えているので、技術視点、プロジェクト視点で、技術部隊総勢100名をコントロールしていく、というのが統括のミッション。  
  
プロジェクトの成否を握るけっこう重要な役割で、PM、技術としての<span style="background-color: #00ffff" class="background-color"><strong>田中(゜p゜)の戦場スキルを最大に出していかなければならないハードなやつ。</strong></span>だと思った。  
  
あと、技術的には5年くらい前の枯れた技術使ってたんですけど、<span style="background-color: #00ffff" class="background-color"><strong>現行事業者が別ベンダー</strong></span>(これまたビッグ)というのもポイント。  
基本、客にはいい顔しつつ、協力どころかちくちく抵抗してくる位置づけ。  
  
まあ本来なら継続できてた案件を取りこぼしちゃったわけだから、多少なりとも嫌がらせしてくるのは想定の範囲内。  


## **経緯**

#### ビックベンダーと自社の関係性

そもそも田中(゜p゜)の所属する企業からすると、このビックベンダーとの直接取引は初でした。グループ企業経由しての取引はあったみたいだけど。

そういう意味で、田中(゜p゜)には案件拡大や、絶対逃げちゃダメ、みたいなプレッシャーもありました。自社には<span style="background-color: #00ffff" class="background-color"><strong>専属の営業いなかった</strong></span>んで、経営から直接言われてたんですけどね。  
  
重要なポジションではありましたが、新参者だったし、**<span style="background-color: #00ffff" class="background-color">ネーム的にも実質的にも権限はほぼ無かった</span>**と言って良いです。

#### 田中(゜p゜)の関与時期

田中(゜p゜)はこの案件の提案の後半段階から入ってました。その後、紆余曲折ありながらも、めでたく受注。

提案段階で2名だったのを、構築段階では要員足りないってんで人をあてがって、なんだかんだ10名まで増やしてもらったつう感じです。

#### 提案段階でのけぞったこと

原因分析は別項目あるんで、とりあえず入って提案でのけぞったことを書きます。

  * 提案書は**<span style="background-color: #00ffff" class="background-color">全部で2000ページオーバー</span>**。そのうち半分が補足資料。
  * こんなデカい会社にも関わらず、過去の事例の参照が難しい。アセット化どころではない。
  * 提案メンバーは40名。にも関わらず、日本語が壊滅的で、田中(゜p゜)はなぜか200ページくらい書いた。
  * 各グループは、<span style="background-color: #00ffff" class="background-color"><strong>コンペのためにコンテ(予備金)と原価をゴリゴリに削られてやる気ない。</strong></span>
  * **<span style="background-color: #00ffff" class="background-color">PMが社内調整をタテに何もしない。</span>**
  * 半年前から準備してんのに、<span style="background-color: #00ffff" class="background-color"><strong>WBSができたのが、提案書提出3日前</strong></span>だった。  
    ※金に関わる部分だったので、田中(゜p゜)がPMに強く依頼してた。

まあ官公庁系じゃなくても、よくある話なのかもしれませんが。

#### 提案後の田中(゜p゜)のアクション

「PM何もしない」「グループ会社は金削られてやる気ない」「現行事業者からの移行」ということで、<span style="background-color: #00ffff" class="background-color"><strong>ヤバすぎるのを認識した</strong></span>ので、取り急ぎ田中(゜p゜)は初動が大切だと思い、やべェアクションにかかりました。もちろん何もしないよりマシだろ、という自爆覚悟です。  
  
端的にいうと、PMの上司に対して、<span style="background-color: #00ffff" class="background-color"><strong>「このPMだと失敗するんで、田中(゜p゜)をPMにして下さい」</strong></span>という申し入れ。

もちろん、提案活動通して、ムチャクチャ下ネゴしたり、上役と信頼関係築いてからですよ？  
自惚れでも何でもなく、それが一番マシな選択肢だと思ったので、プロジェクトのためにそうしました。  
  
まあ予想はしてましたが**<span style="background-color: #00ffff" class="background-color">答は「No」。</span>** 社内の制度上できないので、PMを教育してなんとかする、というものでした。  
本音は何だコイツ、なのかもしれんですけどね。  
また、自社も出向要員にする抵抗もあり。  
  
ということで田中(゜p゜)に与えられたのは、当初の**<span style="background-color: #00ffff" class="background-color">技術統括にプラスしてPM補佐</span>**という、権限はないのに役割はたくさんあるという、なんとも生臭い肩書き。  
おかげで人増やせましたけど、↑の絵にあるような、クソほど苦労しそうなポジションに落ち着きました。

#### 構築期間中にのけぞったこと

同じく原因分析は後回しにして、構築期間中にのけぞったことを淡々と書きます。

  * WBSは当然EXCELで、担当者、作業工数、依存関係の記載がない。<span style="background-color: #00ffff" class="background-color"><strong>最初から顧客用と内部用の二重帳簿。</strong></span>
  * <span style="background-color: #00ffff" class="background-color"><strong>WBSを適正化しようとしたら、技術統括Aに怒られた。</strong></span>要するに「今までこれでやってきたんで！」とのこと。
  * **<span style="background-color: #00ffff" class="background-color">PM、技術統括Bは基本意思決定を何もしない</span>**コメンテーター。
  * ビッグベンダー側からの<span style="background-color: #00ffff" class="background-color"><strong>情報共有はほぼない。</strong></span>
  * 技術統括、PJ統括で課題管理表、WBSを更新するのは田中(゜p゜)だけ。
  * スコープが変わってるのにPMからの指示はなく、誰も課題管理表、WBSを更新しない。
  * PJ統括、技術統括は、**<span style="background-color: #00ffff" class="background-color">顧客向けの資料(構想含む)を一切作らない。</span>**
  * 内部会議は基本2時間以上。アジェンダ、議事メモがないので、前回のコミットをみんな忘れてる。
  * 各Gリーダーが、「それは担当外なんでー」とすぐさま言う。<span style="background-color: #00ffff" class="background-color"><strong>つうかやる気ない。</strong></span>

今まで酷いプロジェクトはいくつも担当しましたけどね、<span style="background-color: #00ffff" class="background-color"><strong>限度あるだろ</strong>、と。</span>  
あ、そういえば、こういう状況に対して危機意識ある人、田中(゜p゜)とPM上司以外にいなかったっぽい。

#### 構築期間中の田中(゜p゜)のアクション

まあとにかくクダグダなんで、地味なのもエモいのも含めて、過去の経験フル動員して、いろいろ活動しました。

  * 技術統括Aの**<span style="background-color: #00ffff" class="background-color">目を盗んで</span>**WBS、課題管理表の適正化。
  * PM上司にホットライン作って、PJの本当の状況を伝える。
  * 自社、PM上司に増援要請。自社は5人増員、PM上司側は叶わず。
  * PJ統括、技術統括で朝会30分開催して情報共有。内部のコミットぶれないようハンドリング。
  * 自社メンバーに指示して、内部会議のアジェンダ、時間管理、議事メモを作成するように依頼。
  * 顧客との会議資料作成、現行事業者、各Gとの調整ハンドリングを引き受け。  
    現行事業者にはとにかく下手に下手に。
  * 話を聞かない技術統括Aをなだめられる人をつけ、影響を緩和する。
  * 各Gリーダーと密に会話して、共感を引き出した上で、生臭い課題の洗い出し。
  * PM上司を説き伏せ、各Gに大元のコンテ(予備金)分け与える旨をアナウンス。
  * PJが2ヶ月ビハインドしてるので、止めて練り直すのが最善策であることを、自社の偉い人含めてPM＆PM上司にエスカレ。  
    →契約上、納期絶対で止められないとの回答。  
    →<span style="background-color: #00ffff" class="background-color"><strong>要するに「ガンバル/ガンバレ」との回答。</strong></span>

なんか他にやれることあったかな？  
**当然土日含めてフル稼働してました**よ。他のメンバーはのうのうとしてたようですけど。

## **失敗の内容**(結果)

この項はアッサリしてますね。タイトルにも書いてありますし。

#### 田中(゜p゜)の結果

プロジェクト開始後、3ヶ月ほどして眠れない状況が続き、**<span style="background-color: #00ffff" class="background-color">6ヶ月目にリタイヤ。自社も退職。</span>**  
他に2人ほど自社メンバーがリタイヤしてましたし、各グループのリーダーも頻繁に入れ替わってたかな。  
  
心療内科行って、しばらくこんなおくすり貰って飲んでました。

<div class="wp-block-image">
  <figure class="aligncenter size-large"><img loading="lazy" width="524" height="290" src="/wp-content/uploads/2020/10/image-17.png" alt="" class="wp-image-1714" srcset="https://tmp-net.biz/wp-content/uploads/2020/10/image-17.png 524w, https://tmp-net.biz/wp-content/uploads/2020/10/image-17-300x166.png 300w" sizes="(max-width: 524px) 100vw, 524px" /></figure>
</div>

田中(゜p゜)はふだん薬飲まんので、けっこうだるくなったり眠くなったり副作用あるんだなぁ。  
  
ま、適応障害もうつ病も該当しない、ってお医者さんに言われてたけど、ベンチャーで失敗こいた時も、不眠の後に帯状疱疹が出たんでいちおう。  
  
退職のダシにもなるし、<span style="background-color: #00ffff" class="background-color"><strong>しばらく</strong></span>**<span style="background-color: #00ffff" class="background-color">調子の悪いフリしてました。</span>**  
マジで調子悪い日もあったけどね。  
  
自社からはなだめたり脅したりで退職を引き止められましたけど、「**じゃあアナタ方が田中(゜p゜)の健康と家庭に責任を持ってくれるんですか**」と言い放って断ち切りました。  
労働基準法の基礎知識さえあれば、大抵はこれで押し切れます。  
  
診断書あれば、傷病手当も貰えたかも知れないけど、まあ症状も軽いし、色々面倒だし。

#### プロジェクトの結果

正直、最低限の引き継ぎだけして逃げて、あと連絡最小限にしてたんで、**どうなったのかは知らん**のです。  
これで納期通りにサービスインできたなら、**スコープか品質大きく削る交渉を顧客とせなならんはず**ですけど、そういう力量があるメンバーは、プロジェクト内にはいなかったと思う。  
  
ま、いつか結果聞けたら追記します。  
そもそもかの会社にとっては、失敗の定義が他社より大幅にゆるい気がするし。

## **原因**

#### 体制

これで全部終わっちゃうっちゃあ、終わっちゃうんですけど。  
今回のPJメンバーってのは、言わば<span style="background-color: #00ffff" class="background-color"><strong>ビッグベンダーの中で</strong></span>**<span style="background-color: #00ffff" class="background-color">の3軍</span>**です。ビッグベンダーもこの案件だけやってるわけではないので。  
たぶん田中(゜p゜)の認識だと、

**　政府共通案件 ＞ 中央官庁案件 ＞ 外郭団体**

という感じで、明確に割り当てられるメンバーの優先順位、質が決まってます。

つまりこの案件は当初からあまり質のよろしくないメンバーが割り当てられていた、と。PMと技術統括Bにやる気なかったり、技術統括Aにクセがありまくりだったりのはこうした事情でしょう。  
  
その中で、田中(゜p゜)の会社の経験ないメンバーがフォローしていくっていう、**<span style="background-color: #00ffff" class="background-color">ちょっとしにたい状態</span>**だった、ということです。

#### 見積もり

メンバーもメンバーだったので、各グループが出してくる作業工数に対して明確な妥当性なんて評価できるわけないんです。  
<span style="background-color: #00ffff" class="background-color"><strong>そもそもWBSをベースにしてない時点で終わっとる。</strong></span>  
  
トドメを刺しちゃったのが、原価削減するのに、各Gのコンテ(予備金)と工数を削ったこと。  
後々分かったんですが、**<span style="background-color: #00ffff" class="background-color">本当に</span><span style="background-color: #00ffff" class="background-color">必要な工数もガッツリ削られてて、調整に泣きそう</span>**になった。なんか削る代わりに本体側のコンテ使うよー、みたいなこと言われてたらしいですが、そんな約束守られるわけもなく。  
  
そら各Gともスコープに厳しくなるし、やる気もなくなるわ。

#### キーマン？

あまり個人を標的にしたくないんですけど、それでも言わざるを得ないです。  
明らかに状況を引っ掻き回してたのは**技術統括A**。下の図の赤字のポジションの人で、技術統括と運用グループのリーダー兼任でやってた。  


<div class="wp-block-image">
  <figure class="aligncenter size-large is-resized"><img loading="lazy" src="/wp-content/uploads/2020/10/image-18.png" alt="" class="wp-image-1722" width="516" height="390" srcset="https://tmp-net.biz/wp-content/uploads/2020/10/image-18.png 760w, https://tmp-net.biz/wp-content/uploads/2020/10/image-18-300x227.png 300w" sizes="(max-width: 516px) 100vw, 516px" /></figure>
</div>

50歳前半のオジサンで、やたら声が大きい人。それと運用一筋でやってきて、それなり官公庁系の案件の実績もある。  
ただ、面倒なのは、グループの実績も背負っているので、運用に都合の良いように物事を誘導していくのです。  
  
このオジサンが、**<span style="background-color: #00ffff" class="background-color">「運用ガー」「運用ガー」言う度にスコープ増える</span>**んすよね。  
あとたぶんこのオジサンはプライムのPM経験ないので、プロジェクト全体のQCDのバランスという観点がない。顧客との交渉も、運用に関わる部分しかしないし、したとしても構築にしわ寄せが来る。  
  
そして、何もしないPM/コメンテーター技術統括B/やる気ないグループリーダーが合わさり、嫌な感じの化学反応で運用のタスクだけ山のように積み上がっていって、スケジュールがカオスになっていきました。  
6ヶ月経過した時点で2ヶ月はビハインドしてたはずだけど、半分くらいはこの人が原因かなぁ。  
  
トドメにこのオジサンは<span style="background-color: #00ffff" class="background-color"><strong>WBS意味ない説を唱え、打ち合わせは手ぶらで乗り込んで、自分の興味を根掘り葉掘り聞く派</strong></span>です。  
しにたい。

#### PMの真摯さ

上の方でもPMに能力がないことは書きましたが、能力がないのはいくらでもカバーします。  
いやウソ。限度はあるかもしんないけど。  
  
ただ、どうしてもこれはダメだな、と思うのは、**<span style="background-color: #00ffff" class="background-color">プロジェクトに対して真摯に向き合う気持ちのなさ</span>**です。  
そもそも**<span style="background-color: #00ffff" class="background-color">WBSの二重帳簿を黙認してる</span>**のもそうだし、WBS適当に書いた上でコスト削ってグループ苦しめてるのもそうだし、QCD引っ掻き回している管下要員に何もアクションしないのもそう。  
  
内部定例もアジェンダの棒読みなんすよね。  
この課題はこうしたいああしたい、このプロジェクトではこうすべきだ！ みたいな意思がない。  
  
細かいですけど、顧客のサービスにインパクト与えるようなネットワークの切替が休日にあっても現場に出てこない。  
あまりに現場に申し訳なかったんで、田中(゜p゜)は関係無かったけど、何かあったときのために立ち会いました。  
  
なんというか、**<span style="background-color: #00ffff" class="background-color">なんとしてでもこのプロジェクトを成功させるのだ、という熱意がPMに一切感じられなかった</span>**です。  
田中(゜p゜)は「真摯さ」と表現していますが。  
  
これ、人を動かす上で一番重要なことなんじゃないですかね・・・。

#### 人間関係

「体制」「適正な金払われてない」「運用のみ優位」「PMやる気なし」 というような事象が積み重なった結果、プロジェクトは**<span style="background-color: #00ffff" class="background-color">リスクを取らず、言われたことだけやるロボットのような人間が増加</span>**していきました。

最終的には田中(゜p゜)もそうなってたかもしれない。  
どんなに主体的に活動しても無駄なら、**<span style="background-color: #00ffff" class="background-color">心を殺して黙々と働くしかない</span>**んじゃないかな。　

プロジェクト開始後4ヶ月後、増員で来たメンバーに「**<span style="background-color: #00ffff" class="background-color">なんかこのプロジェクト雰囲気悪いっすね</span>**」って言われたのが印象的。

まあその頃には田中(゜p゜)も、何やっても無駄だな、と考え始めてましたけど、改めて言われてみるとプロジェクトに飲まれて死んだ魚の眼をしてたかもしれない。  
  
沈むことが分かってる泥舟に黙って乗ってるくらいなら脱出したほうがいいな、と田中(゜p゜)考え始めたのもこの頃からです。  
グループのリーダや、田中(゜p゜)の管下メンバーからも、脱出する人がチラホラ。  
  
正直、過去田中(゜p゜)が立て直した、立て直ってきた炎上案件とは全く違う。  
過去の炎上案件は、プロジェクトのQCDはヤバくても中の人間には活気があって「絶対なんとかするんだ」というようなベースがあり、<span style="background-color: #00ffff" class="background-color"><strong>コアメンバーが役割意識持って主体的に動いてた。</strong></span>  
  
大変だけど楽しかったし、無力感なんてのはもちろんなかったと思う。

## **反省点**

田中(゜p゜)個人で言えば、「このプロジェクトを何とかしたい」という思いが強すぎましたね。また、、<span style="background-color: #00ffff" class="background-color"><strong>自</strong></span>**<span style="background-color: #00ffff" class="background-color">分の能力や、置かれた環境に対して、できることの見積もりの過信がすぎた</span>**。  
  
過去の炎上立て直しの経験から、一人でも熱意をもってぶつかれば状況を変えられると信じたのがそもそもの間違いで、どうにもならんもんはどうにもならん。  
結婚して子供もいたし、独身の時とは使える時間も、背負ってるものも違う。  
  
提案が終わった段階でこうなることはある程度見えてたんで、手持ちのリソース見て、そこで**<span style="background-color: #00ffff" class="background-color">断るかサービスの範囲を定義しちゃえば楽になれたかも</span>**知れないですね。  
  
また、残されたメンバーには悪いとは思いますが、去る前から「このプロジェクトはこういう部分がヘンだよ、田中(゜p゜)はこれこれこういうことやったけどダメだった。田中(゜p゜)はたぶん逃げるけど、耐えられなくなったら逃げてね」とは伝えてきました。  
ま、<span style="background-color: #00ffff" class="background-color"><strong>田中(゜p゜)の前にも何人か逃げてた</strong></span>しね。  
  
あとはどうしても技術統括Aと仲良くできなかったけど、これはもう少し田中(゜p゜)が上手くハンドリングできたかなー、と思う部分ではあります。  
  
いずれにせよ、田中(゜p゜)が初めて逃げた案件ではあるので、この経験を活かして、次につなげたいとは思います。  
本来田中(゜p゜)は、転んでも砂を掴んで相手の目に投げつけて、状況を優位に運ぶたくましい子のはずです。  
  
さしあたって田中(゜p゜)のキャパ的には家庭と仕事の両立は難しいっぽいので、<span style="background-color: #00ffff" class="background-color"><strong>仕事側をてきとうにハンドリングしていきたい</strong></span>と考えてます。