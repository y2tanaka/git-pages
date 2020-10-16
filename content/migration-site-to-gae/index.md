---
title: WordPressをGAE Standard に移行
author: 田中(゜p゜)
type: page
date: 2020-09-05T07:23:55+00:00
catchbox-sidebarlayout:
  - default

---
<div class="wp-block-image">
  <figure class="aligncenter size-large"><img loading="lazy" width="180" height="180" src="/wp-content/uploads/2020/09/computer_programming_man.png" alt="" class="wp-image-563" srcset="https://tmp-net.biz/wp-content/uploads/2020/09/computer_programming_man.png 180w, https://tmp-net.biz/wp-content/uploads/2020/09/computer_programming_man-150x150.png 150w" sizes="(max-width: 180px) 100vw, 180px" /></figure>
</div>

記事の流れで突然技術っぽくなってますが、過去の資産が尽きたので、新しいことやっとるのです。  
  
ちなみにこれは[投稿のエントリの][1]続きです。  
テストユースでは<a rel="noreferrer noopener" href="https://www.topgate.co.jp/gcp05-google-app-engine-run-application" target="_blank">Google App Engine(GAE)</a>を使ってWordPressを構築してみましたが、使い勝手が良くなったので**このサイト自体も移行しちゃいました**。  
  
GCEの無料枠でやってたんだけど、ロケーション米国で**管理がもっさりしてる**し、少し無茶するとすぐにOSごとやられてしまうのにイライラしてしまい。

## WordPress on GAEメリデメ

先進的なサービスであるGAEですが、レガシーなアプリであるWordPressを載せると様々な運用のデメリットが発生します。  
投稿のエントリにもありますが、田中(゜p゜)の認識をまとめます。

  * ○GAE Standardはインスタンスの費用が必要なく、**使った分だけお金を支払えばよい**。基本無料枠に収まるので安い。  
    ※ただしCloudSQLの費用は$9程度かかる。
  * ○￥1,000程度のレンタルサーバーでは考えられない**スケーラビリティとパワー**がある。しかも自動。
  * ○費用についてはこちらも参照のこと。  
    AWSからGAEに乗り換え  
    <https://yamavlog.com/gcp-gae-wordpress-running-cost-202006/>  
    レンタルサーバ  
    <https://webst8.com/blog/wordpress-recommend-rental-server/>
  * ○SSL化も証明書取得も自動でやってくれる。
  * ○**OSの運用は一切不要**。WordPressのコードをデプロイすれば終わり。
  * ×GAEは**ディスクに書き込めない**。具体的には以下が更新できない。  
    　プラグイン(設定は除く)  
    　テーマ(設定は除く)  
    　投稿・固定ページへの直接画像貼り付け(メディアライブラリからはOK)

メリットはとてつもなくあるんですが、**ディスクに書き込めないというのはWordPressさんにとって致命的**です。  
田中(゜p゜)はこの致命的な欠点を、以下のようにして工夫でカバーしてみました。

## 構成と運用の工夫

[構成自体は、テストでやった時の環境と大きく違わない][1]のですが、管理用のWordPressがローカルのPCからGCEになりました。

<div class="wp-block-image">
  <figure class="aligncenter size-large"><img loading="lazy" width="542" height="332" src="/wp-content/uploads/2020/09/image-43.png" alt="" class="wp-image-1206" srcset="https://tmp-net.biz/wp-content/uploads/2020/09/image-43.png 542w, https://tmp-net.biz/wp-content/uploads/2020/09/image-43-300x184.png 300w" sizes="(max-width: 542px) 100vw, 542px" /></figure>
</div>

つまり**GCEでサーバを立てて、そこで管理**します。  
ローカル管理との違いは以下です。

  * 使わないときには落としておく。
  * <a href="https://cloud.google.com/compute/docs/instances/preemptible?hl=ja" target="_blank" rel="noreferrer noopener">Preempt</a>で構築してタダ同然。Preemtは最大24時間で落ちるので、落とし忘れ対策にもなる。
  * CloudSQLとの距離が近いので、管理の操作がサクサクできる。
  * どこからでも更新できる。
  * バックアップが万全。

それと、この仕組みのミソですが、いちいちSSHで入って実行が必要だった②のデプロイを、**スクリプト組んでwp-contentフォルダに更新があった時に勝手にデプロイするようにしてみました**。  
  
※スクリプトはダサいですが、このエントリにいちおう載せておきます。

## 構築方法(一部再掲)

  * まず、GCEでWordpressを建てます。ドメイン名もSSL証明書もいりません。面倒だったら、MarketPlaceの配布版が早いかもしれません。  
    <a rel="noreferrer noopener" href="https://cloud.google.com/compute/docs/instances/preemptible?hl=ja" target="_blank">https://cloud.google.com/compute/docs/instances/preemptible?hl=ja</a>  
    ちなみに建てとくだけで良くて、WordPressのセットアップは不要です。GCEインスタンスが建ったら、おもむろにSSHで作業開始して下さい。
  * **Googleのチュートリアル**参考に構築。「ローカル」を構築したGCEに合わせて読み替え。  
    <a rel="noreferrer noopener" href="https://cloud.google.com/community/tutorials/run-wordpress-on-appengine-standard?hl=ja" target="_blank">https://cloud.google.com/community/tutorials/run-wordpress-on-appengine-standard?hl=ja</a>
  * チュートリアルにミス。  
    ×php vendor/bin/wp-gae  
    ○php vendor/bin/wp-gae create
  * WP CLIのインストールは、チュートリアルじゃなくて公式のほうが良い。  
    <a rel="noreferrer noopener" href="https://wp-cli.org/ja/" target="_blank">https://wp-cli.org/ja/</a>
  * CloudSQLインストール前に、MySQL停止、無効化しておく。
  * CloudSQLの自動起動化。ちょっと面倒です…。  
    <a rel="noreferrer noopener" href="https://qiita.com/kumanoryo/items/ef3fbec70b4138ffe1c2" target="_blank">https://qiita.com/kumanoryo/items/ef3fbec70b4138ffe1c2</a>
  * デフォルトのapp.yamlは小規模サイトの運用に適しては居ないようなので、↓を参照して、インスタンス、エッジキャッシュの調整をしていくといいと思います。  
    <https://www.serversus.work/topics/p1uaj4jrv8b5x70hwe6p/>  
    <a rel="noreferrer noopener" href="https://koni.hateblo.jp/entry/2016/01/06/130613" target="_blank">https://koni.hateblo.jp/entry/2016/01/06/130613</a>  
    <a rel="noreferrer noopener" href="https://yamavlog.com/gae-edge-cache" target="_blank">https://yamavlog.com/gae-edge-cache</a>
  * サーチエンジン等SEO対策必要な場合は、app.yamlデフォルトのファイル形式にtxtやxml他、サイトに含まれるファイル形式の追加必要です。
  * wp-contentが更新された際に、GAEにデプロイが走るようにスクリプトを仕掛ける。田中(゜p゜)は以下のサンプルコードを適当な場所に置き、cronで5分毎に回してます。テストはした方が良いと思います。  
    田中(゜p゜)は本職じゃないので、やっつけコードがダサいのはまじ勘弁して下さい。WordPressへの貼り方もよく分かってない…。

<!-- wp:lis
</p>





























































-->

<pre class="wp-block-code"><code>-------------------------残念なスクリプトココから--------------------------
#!/bin/bash

####################################################################
特定ディレクトリで差分・更新が発生した場合、サービスの反映等の処理を実行させる
実行ユーザでgcloud diff treeがパスなし実行可能なこと。
####################################################################

### 環境に合わせて書き換えるパート
TARGET_DIR="/var/www/html/wp-content/"   # チェック対象ディレクトリ
#EXEC_COMMAND="echo `date "+%b %H%:M:%S"` Directory updated" # テスト
EXEC_COMMAND="gcloud app deploy --quiet /var/www/html/app.yaml  /var/www/html/cron.yaml " # 実行するコマンド
LOG_FILE="/var/log/gae_update"                    #ログファイルの場所

####シェル内部で使ってるファイルさん達
TMP_TREE_FILE1="/tmp/tmp_dir_tree1.txt"  #  実行前の状態
TMP_TREE_FILE2="/tmp/tmp_dir_tree2.txt"  #   今の状態

####################################################################

####フォルダ存在チェック
&#91; ! -e "$TARGET_DIR" ] && echo "Directory does not exist." && exit 1 >> $LOG_FILE

#####今の状態を確認 初回実行のため、FILE1作成
# treeにUNIX時間入れてタイムスタンプ確認する
tree $TARGET_DIR --timefmt +%s  > $TMP_TREE_FILE2   
touch $TMP_TREE_FILE1

#### 念のため、気持ち2秒待ってから実行
sleep 2

#### diffの結果が1行以上ある場合のみコマンド実行してログに書き込み
if &#91; `diff $TMP_TREE_FILE1 $TMP_TREE_FILE2 |wc -l` -ge 1 ]; then 

$EXEC_COMMAND >> $LOG_FILE                         #実行とログ書き込み
tree $TARGET_DIR --timefmt +%s > $TMP_TREE_FILE1   #次回実行のために、実行後のディレクトリ状態を記録

fi 
--------------------------------ココまで---------------------------------</code></pre>

このコードですが、Googleのデプロイのログがうまく出ないので、誰か改修してくれないかなぁ。  
田中(゜p゜)はこれにちょい加えてechoで、実行されたかどうかだけログに書き込んでます。

## 移行方法

以下は、既存サイトから移行したい場合の参考手順です。  
因みに田中(゜p゜)は <a href="https://ja.wordpress.org/plugins/all-in-one-wp-migration/" target="_blank" rel="noreferrer noopener">All in One Migration</a>を使いました。  
  
要は**移行用プラグインを**移行元と移行先に入れて、エクスポート→インポートするだけのはずですが、移行先のホスト名が<GCEの外部IP>なので、サイト内でのURL整合性が取れなくなります。  
  
**賢い移行ツールは、インポート先のホスト名を見て、DBなり設定ファイルなりを書き換えてしまう**のです。そのおかげで、見た目キレイに移行できるんですけどね…。  
  
田中(゜p゜)がこれを解決するためにやったのは、以下のような感じです。

  * 移行元サイトのリンクと画像の絶対パスを、可能な限り相対パスに書き換えておく。  
    <a href="https://www.will-hp.com/wpblog/wordpress/191/" target="_blank" rel="noreferrer noopener">https://www.will-hp.com/wpblog/wordpress/191/</a>  
    <a href="https://worpreya.com/change-to-image-link-relative-path/" target="_blank" rel="noreferrer noopener">https://worpreya.com/change-to-image-link-relative-path/</a>  
    移行先(GCE)にも同じ設定を実施する。
  * 固定ページとかのリンクは書き換えられないので、**手で頑張って下さい。**  
    ユーザの設定でビューをクラシックにして、HTMLをテキストエディタにコピペし、置換するのが早いと思います。※いいプラグインが有ればおしえて欲しいす…。
  * おもむろに移行ツールでエクスポート。  
    PHP設定でダウンロードできない場合は、実体ファイルが、<WordPressのルート>/wp-content/ai1wm-backups/」配下の「日付.wpress」というファイルになってます。
  * **管理用PCの**host等で移行先サイトのFQDNを、<GCEのIP>で解決できるようにしておく。
  * GCEのアップロードの上限設定を確認しておく。**だいたい上限が2MBでしにます。**これはPHP、WEBサーバ両方の設定があるので、適宜ググって変更して下さい。
  * GCEでスナップショットを取っておく。
  * おもむろに移行ツールでインポートし、**色々頑張って修正。**どうにもならなくなったらスナップショットから復元。
  * インポートが終わったらhostsは元に戻す。
  * 手動でもスクリプトでもよろしくGAEにデプロイ。

hostsをゴニョゴニョし、絶対リンクをなんとかすれば、**賢い移行ツールさんは自分がFQDNのサイトにいるのだと勘違い**してくれます。  
  
あ、忘れてましたが、DNSの移行は省いてます。**<a rel="noreferrer noopener" href="https://cloud.google.com/dns?hl=ja" target="_blank">Cloud DNS</a>**ならシームレスに移行できますが、そうでない場合はドメイン所有権の確認のために、DNSにTXTレコードの追加が必要で、少しタイムラグあるかもしれません。↓  
<a rel="noreferrer noopener" href="https://blog.apar.jp/web/8281/" target="_blank">https://blog.apar.jp/web/8281/ (外部サイト)</a>

## 運用上の注意点

運用していて気づく注意点について、いくつか記載します。今後も増えていくかもしれません。

  * テーマやプラグインで、WP cron等で動的にファイルを作成ものは軒並みGAE上でアウト。WP Super Cacheとか。田中(゜p゜)の使ってるテーマLuxeritasもアウト(っぽい)。
  * テーマの中でも、jsやcssの圧縮、効率化のためにファイルを生成するものは注意。ホスト名を勝手に埋め込んでるので、管理画面が本番と同じアドレスじゃないとダメなケースがある。
  * GAEは(簡易)CDNがついているので、デザイン等jsやcssがキャッシュされてると変更がすぐに反映されず、切り分けが面倒なことになる。キャッシュの時間は長いので、app.yaml等で短くして更新するのが良いかもしれない。ChromeのF12での切り分けが必要。
  * 似たようなサイトが2つあるので混乱する。とくに、テーマの都合等でhostsでGCE側に本番のFQDNを振ってる場合に顕著。管理画面で「ファイルが書き込めません」と出ているのはGAE。
  * ホスト名問題について、GAEのサービス名(appspot〜)で確認するというのもワークアラウンドとしてあり。
  * GCE側でデザインのテストだけしたい場合は、一時的にCron止めて、GAEに他のサービス名でアップロードする等の工夫が必要。

やっぱり性能とコストに引き換えにするものはある感じですね。  
何も分からないユーザに渡すには不安があるな。

## 使ってみてどうか

米国の無料枠に比べたら、**サービスも管理もとにかく速い**です。  
距離も近いし、DBが外出しだというのも大きい。生産性のために、千円払っとくか、というのが移行のキッカケです。  
本番の挙動にOSが関係ないのも嬉しい。  
  
ただ、**意外とデプロイに時間がかかるなあ**、という印象です。手動で回したときも、更新でトリガーされてからGAEのデプロイに5分ぐらいかかる印象。なんで、すぐ反映されないことに対して理解は必要かもですね。  
  
更新トリガーのcronを5分毎にしてるけど、大した処理じゃないし、1分毎でもいいかもしれない。  
イライラする人はSSHで繋いで、ログをtail -fしてればいいんだと思うよ。 **※田中(゜p゜)です。**  
  
あとこの構成のウリはスケーラビリティです。  
どんな規模のトラフィック来ても、サーバ増設は必要ないから費用は抑えられるし、SQLの負荷を気にしとけばいいだけ。  
**どんなに田中(゜p゜)のサイトがバズっちゃっても問題ないよ？**  
  
ただ、実運用で大規模サイト運用したことないから分からないけど、マルチテナントだと、フォルダごとにWordPress立てて、GAE側はサービスかプロジェクトでで切り分けていく感じになるのかな？  
  
ま、**趣味でやってる分には何の関係も無いんですけど**ね。

<p class="has-text-align-right">
  2020/09/29
</p>

 [1]: /blog/post-1091/