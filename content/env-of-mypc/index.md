---
title: 田中(゜p゜)のPC環境
author: 田中(゜p゜)
type: page
date: 2020-09-05T10:49:02+00:00
catchbox-sidebarlayout:
  - default

---
昔々、自作PCを手がけてたので、PCの詳しさはそれなりです。  
今はこだわりは特にないので、「安さ」「動きの軽さ」「丈夫さ」の質実剛健さを重視。デスクトップ置くスペースがもったいないのでもっぱらノートです。

## 起動スピード

この環境の最大のウリ(笑) 10秒ちょいで起動。パパパパァーん。という感じで小気味良い。  
※だらしない格好と、パッキン外れてるのは気にしないで。<figure class="wp-block-video"><video controls muted src="/wp-content/uploads/2020/09/VID\_20200914\_152352.mov" playsinline></video></figure> 

## ハードウェア

ヤフオクで3万以下で売られてたDellのノートPC。  
SSD256GBに換装。メモリ8GBに増強。  
企業向けのリース上がり品だと思うけど、素性は不明。Windows7 Proのライセンス付きをWindows10にアップグレード。  
  
スペックは以下の通りみたい。<figure class="wp-block-image size-large">

<img loading="lazy" width="870" height="373" src="/wp-content/uploads/2020/09/2020-09-14-150547_1366x768_scrot.png" alt="" class="wp-image-783" srcset="https://tmp-net.biz/wp-content/uploads/2020/09/2020-09-14-150547_1366x768_scrot.png 870w, https://tmp-net.biz/wp-content/uploads/2020/09/2020-09-14-150547_1366x768_scrot-300x129.png 300w, https://tmp-net.biz/wp-content/uploads/2020/09/2020-09-14-150547_1366x768_scrot-768x329.png 768w" sizes="(max-width: 870px) 100vw, 870px" /> </figure> 

## ソフトウェア

画像だけ見ても意味が分からんと思うので少し解説。

OS： Lubuntu 16.04  
ブラウザ： Chromium  
他： VMPlayer12入れてWindows10動かしてる。やむを得ないOffice利用時に。  
あと英会話用のskype。Linuxなのに動くんすよ。<figure class="wp-block-image size-large">

<img loading="lazy" width="1024" height="576" src="/wp-content/uploads/2020/09/2020-09-14-151301_1366x768_scrot-1024x576.png" alt="" class="wp-image-784" srcset="https://tmp-net.biz/wp-content/uploads/2020/09/2020-09-14-151301_1366x768_scrot-1024x576.png 1024w, https://tmp-net.biz/wp-content/uploads/2020/09/2020-09-14-151301_1366x768_scrot-300x169.png 300w, https://tmp-net.biz/wp-content/uploads/2020/09/2020-09-14-151301_1366x768_scrot-768x432.png 768w, https://tmp-net.biz/wp-content/uploads/2020/09/2020-09-14-151301_1366x768_scrot.png 1366w" sizes="(max-width: 1024px) 100vw, 1024px" /> </figure> 

## 2020年時の所感

4年くらい前に入れた気がするが、パフォーマンス的には未だ何も困っていないし、ブラウザで実施する作業はChromiumで何も問題ない。Wordpressもこれで更新してる。  
EclipseとかVScodeとか開発ツールも微妙に入ってるけど、最近は使ってない。  
  
正直、Chromiumで動かないサイトが微妙にあるのと、ブログ始めてPowerPointとペイントツールでお絵かきするのと、リモートワーク増えてきてOffice利用が増えており、Windows10に乗り換えようか検討中。  
でもなぁ。細かいカスタマイズとGUIがなぁ。  
  
このVMの中にあるWindows10をそのままハードに移したいんだけと、やり方が分からんのです。

## おまけ

Google CloudのGCSに一発でバックアップできるスクリプト作って、安く、快適にバックアップしとりますのでご参考まで。リカバリの実績もあり。「tanaka」「homepc003」は自分の環境に置き換えて下さい。

<blockquote class="wp-block-quote">
  <p>
    umount /media/gs_tanaka/<br />umount /media/gs_system/<br /><br />gcsfuse tanaka_local /media/gs_tanaka/<br />gcsfuse tanaka_system /media/gs_system/<br /><br />rsync -auv &#8211;include=&#8221;<em>/&#8221; &#8211;exclude=&#8221;</em>&#8221; &#8211;exclude=&#8221;.*&#8221; /home/tanaka/ /media/gs_tanaka/<br />gsutil -m rsync -r /home/tanaka/books/ gs://tanaka_local/books/<br />gsutil -m rsync -r /home/tanaka/download/ gs://tanaka_local/download/<br />gsutil -m rsync -r /home/tanaka/img/ gs://tanaka_local/img/<br />gsutil -m rsync -r /home/tanaka/info/ gs://tanaka_local/info/<br />gsutil -m rsync -r /home/tanaka/learning/ gs://tanaka_local/learning/<br />gsutil -m rsync -r /home/tanaka/picture/ gs://tanaka_local/picture/<br />gsutil -m rsync -r /home/vmware/ gs://tanaka_system/vmware/<br />tar -X backup_exclude_list -zcpvf /root/homepc003_system.tgz /*<br />gsutil -m mv /root/homepc003_system.tgz gs://tanaka_system<br /><br />umount /media/gs_tanaka/<br />umount /media/gs_system/
  </p>
</blockquote>

あれ？gsutilsサポート切れかな？  
あと、HDD容量たくさん食ってて、回線細い人には向いてないかも。