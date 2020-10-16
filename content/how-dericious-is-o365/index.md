---
title: Office365(とAzure)って美味しいの？
author: 田中(゜p゜)
type: page
date: 2020-09-05T00:49:57+00:00
catchbox-sidebarlayout:
  - default
og_img:
  - /wp-content/uploads/2020/09/Azure-office365-1024x346.png

---
<figure class="wp-block-image size-large"><img loading="lazy" width="1024" height="346" src="/wp-content/uploads/2020/09/Azure-office365-1024x346.png" alt="" class="wp-image-507" srcset="https://tmp-net.biz/wp-content/uploads/2020/09/Azure-office365-1024x346.png 1024w, https://tmp-net.biz/wp-content/uploads/2020/09/Azure-office365-300x101.png 300w, https://tmp-net.biz/wp-content/uploads/2020/09/Azure-office365-768x259.png 768w, https://tmp-net.biz/wp-content/uploads/2020/09/Azure-office365.png 1347w" sizes="(max-width: 1024px) 100vw, 1024px" /></figure> 

美味しいの？ シリーズ第四弾。  
田中(゜p゜)がなまくら刀で今アツい？ Office365に切り込んでいきます。  
  
いつものように最初に結論から。  
Office365(とAzure)って、ITインフラエンジニアにとって美味しいの？ ということですが、

**Microsoftは明らかにOffice365(とAzure)にサービス寄せたがってるし、やっといて損はないんじゃね？**

と田中(゜p゜)は思ってます。

## O365について

コレですが、オンラインでライセンス確認、ソフトウェアのアップデートができるという点が、明らかにMicrosft側にも企業側にもメリットがあります。  
安っぽい言葉で言えば **Win-Winの関係**？  
  
企業側にとって必要悪であった**ライセンスの棚卸しと、ソフトウェアのアップデートの問題が解決**し、Microsoftからしても、**違法ライセンスの排除が図れる**というイカしたしくみ。  
しかもMicrosoftにとっても、企業にとってもの主力商品であるOfficeですから、  
  
正直、田中(゜p゜)はオンライン上の機能とかにはあんまり着目してねーのですが、ライセンスのランクによっては、**容量無制限になる**ので、ファイルサーバの代わりに使えば、**ファイルサーバの維持コストが大きく削減できる可能性**があります。  
  
ファイルサーバって、容量たくさん必要なので、ハードウェアとしてのストレージたくさん必要で、お金かかるんですよね。  
  
ただ、これは**AD同等の権限をO365側に持ってくるのが今はまだ難しく**、そこを補完するミドルウェアがたくさん出てるような状況です。  
これがキレイにO365側に統合されるようなことになれば、**更に優位性が向上**するんじゃないかな、と思います。

## Azureについて

正直、田中(゜p゜)はパブリッククラウド**単体のサービスで見た時のAzureはあんま好きじゃないです**。安定性は増してきたけど、遅いし、ユーザビリティも良くないし、PowerShellで管理できる範囲も限られてるし。(REST APIまでは見てないけど、もっと色々なことができるのかな？)  
  
それと、O365を最初にいじってみた時は、なんでAzureADなんかを噛ませなきゃいけないんだろうな、と思ってましたが、最近なんとなくMicrosoftの意図が分かりはじめました。  
Office365っつうコアなサービスをわざわざAzureADに紐付けようとしてるのは、理由があるんじゃないか、と田中(゜p゜)は思ったのです。

## Azure ADって何？

<div class="wp-block-image">
  <figure class="aligncenter size-large"><img loading="lazy" width="409" height="123" src="/wp-content/uploads/2020/09/azure_ad.png" alt="" class="wp-image-516" srcset="https://tmp-net.biz/wp-content/uploads/2020/09/azure_ad.png 409w, https://tmp-net.biz/wp-content/uploads/2020/09/azure_ad-300x90.png 300w" sizes="(max-width: 409px) 100vw, 409px" /></figure>
</div>

**ADとAzureADは全くの別物**です。**前者はLAN前提＋NTLM認証のサービス**なのに対し、後者は**インターネット＋SAMLベース**のサービスです。どっちかというとADというよりADFSのインターネットサービス版、みたいな。  
AzureADでWindows10の認証を通しておけば、SAML連携しているインターネット上のサーバ達にもシングルサインオンできる仕組み。  
  
つまるところMicrosoftは今までのLAN前提のインフラ構成を、**インターネットベースにしようとしてんだ**な、と。  
  
そうなると、認証はSAMLでいいとしても、**ADの強みの一つであったポリシー管理はどうなるのか**な、と思いましたが、やはり[Microsoft Intune ][1]つうのを用意してやがりました。  
  
サラッといじってみたところ、**現段階ではADのポリシーのようなきめ細やかな制御は難しい**ようですが、カスタムしてレジストリもいじれるようになってるし、インターフェイスとして組み込まれるのも時間の問題かな、という気がします。  
  
あとちょっと気軽に使うにはコストが高い気がしますが、**ADとファイルサーバとLANを廃して、浮いたコストをIntuneのライセンス費に当てれば**、余裕でペイできそうな気がします。  
  
うーん。  
**この提案、やってみたい。**  
  
**[企業のネットワークアクセスパターン][2]**でも書いたように田中(゜p゜)は**クラウド使うためにLANに入らなければいけないのはナンセンス**だと思ってて、**End To Endの認証が基本**だと思ってるんですが、**AzureADとIntuneの組み合わせ**であれば**認証もPCのポリシー管理もいけちゃう**よね、などと思ってます。  
  
とは言いつつも、Azure ADの権限管理も、Intuneのポリシー管理も、**まだまだADに追いついてない**ようなので、**既にADの資産を山ほど築いてる企業に取っては移行の敷居が高い**のだとは思いますが、ワクワクするようなソリューションだな、とは思いました。

## まとめ

  * Office365の利点は、企業のライセンス管理コスト、アップグレードコストを削減できること。
  * MicrosoftはAzure AD(＋Intune？)を、インターネット上のADとして展開するつもり
  * Azure ADがキレイに実装されれば、ユーザはLANの呪縛から開放される。かもしれない。

 [1]: https://www.microsoft.com/ja-jp/microsoft-365/enterprise-mobility-security/microsoft-intune
 [2]: /article/nw-pattern-of-enterprise/