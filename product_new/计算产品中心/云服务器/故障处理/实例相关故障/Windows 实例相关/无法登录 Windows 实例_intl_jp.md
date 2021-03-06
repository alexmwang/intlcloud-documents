本文書は、Windowsインスタンスに接続できない場合のトラブルシューティング方法、及びWindowsインスタンスに接続できないことを引き起こす可能性のある主な原因について説明し、問題のトラブルシューティング、特定及び解決を指導します。

## 可能性のある原因
Windows インスタンスにログインできない主な原因は下記を含んでいます。
- [パスワード問題によりログインできない](#CryptographicProblem)
- [帯域幅利用率が高すぎる](#BandwidthUtilization)
- [サーバーのハイロード](#HighServerLoad)
- [リモートポートのコンフィギュレーション異常](#RemotePortConfiguration)
- [セキュリティグループ規則の不具合](#SafetyGroupRule)
- [ファイアウォール又はセキュリティソフトによるログイン異常](#LoginSecuritySoftware)
- [リモートデスクトップの接続に身分検証エラーが発生した](#AuthenticationError)

## セルフ診断ツールの利用

Tencent Cloudはセルフ診断ツールを提供し、帯域幅、ファイアウォールやセキュリティグループ設定等よく見られている問題により Windows インスタンスに接続できないかを判断することに貢献しています。70%の障害はツールで問題を特定できます。顧客は検出された原因により、ログインできないことを引き起こす可能性のある障害を特定することが可能です。
1.  [セルフ診断](https://console.cloud.tencent.com/workorder/check)をクリックし、セルフ診断ツールを開きます。
2. 診断しようとするCVM instance-idを入力し、【診断開始】をクリックします。

トラブル診断ツールで問題を検出できない場合は、 [ VNC方法によりCVMにログイン](#VNC) し障害をトラブルシューティングすることをお薦めします。

<span id="TroubleshootingIdeas"></span>
## 障害処置

<span id="VNC"></span>
### VNC 方法によるログイン

RDP又はリモートログインソフトでWindowsインスタンスにログインできない場合は、Tencent Cloud VNCを介してログインし、障害原因を特定することができます。
1.  [Tencent Cloudコンソール](https://console.cloud.tencent.com/cvm/index)にログインします。
2. インスタンスの管理ページで、ログインしようとするインスタンスを選択し、【ログイン】をクリックします。下図の通りです。
![](https://main.qcloudimg.com/raw/038fce530c6c6827796e51d896306a93.png)
3. ポップアップした 「Windowsインスタンスへのログイン」ウィンドーで、【ほかの方法（VNC）】を選択し、【すぐにログインする】をクリックします。
> ログインする時に、パスワードを忘れた場合は、コンソールで当該インスタンスのパスワードをリセットすることができます。具体的な操作は [インスタンスパスワードのリセット](https://intl.cloud.tencent.com/document/product/213/16566)をご参照ください。
>
4. ポップアップしたログインウィンドーで、左上の「リモートコマンドの送信」を選択し、 Ctrl-Alt-Delete をクリックすると、システムログイン画面に入ります。下図の通りです。
![](https://main.qcloudimg.com/raw/2dec43fa6ddb5e442da59c75f7a34b0f.png)

<span id="CryptographicProblem"></span>
### パスワード問題によるログイン不能

**障害の現象**：パスワード入力間違い、パスワード忘れ又はパスワードのリセット失敗によるログイン失敗です。
**解決方法**： [Tencent Cloudコンソール](https://console.cloud.tencent.com/cvm/index) で当該インスタンスのパスワードをリセットしてから、インスタンスを再起動します。
**処置ステップ**：インスタンスパスワードリセットの方法は [インスタンスパスワードのリセット](https://intl.cloud.tencent.com/document/product/213/16566)をご参照ください。

<span id="BandwidthUtilization"></span>
### 帯域幅の利用率が高すぎる

**障害の現象**：セルフ診断ツールにより診断された問題は帯域幅利用率が高すぎることです。
**処置ステップ**：
1.  [VNC ログイン](#VNC) を介してインスタンスにログインします。
2.  [帯域幅の高い利用率によるログイン不能](https://cloud.tencent.com/document/product/213/10334#.E9.92.88.E5.AF.B9-windows-.E6.9C.8D.E5.8A.A1.E5.99.A8)を参考にし、インスタンスの帯域幅利用状況及び障害処置を調べます。

<span id="HighServerLoad"></span>
### サーバーのハイロード

**障害の現象**：セルフ診断ツール又はクラウド監視により、サーバーのCPU負荷が高いためシステムがリモート接続をできないか、或いはアクセスできないことが判明しました。
**可能な原因**：ウィルスやトロイの木馬、サードパーティーアンチウィルスソフト、アプリケーションの異常、ドライバーの異常又はソフトウェアバックグラウンドの自動更新により、CPU利用率が高くなり、CVMにログインできなかったり、アクセス速度が遅くなったりすることが発生しました。
**処置ステップ**：
1.  [VNC ログイン](#VNC) を介してインスタンスにログインします。
2.  [Windows インスタンス：CPU とメモリの高い利用率によるログイン不能](https://cloud.tencent.com/document/product/213/10233)を参考にし、「タスクマネージャー」でハイロードプロセスを特定します。

<span id="RemotePortConfiguration"></span>
### リモートポートのコンフィギュレーション異常

**障害の現象**：リモートに接続できない、リモートアクセスポートがデフォルトポートでなく、修正されたか、或いは3389ポートが有効になっていません。
**問題特定の考え**：インスタンスのパブリックIPへのpingを実行できるかどうか、また、telnetコマンドでポートが有効になっているかどうかをチェックします。
**処置ステップ**：具体的な操作は [ポート問題によるリモートログイン不能](https://cloud.tencent.com/document/product/213/10232)をご参照ください。

<span id="SafetyGroupRule"></span>
### セキュリティグループ規則の不具合

**障害の現象**：セルフ診断ツールで検査した結果、セキュリティグループの規則設定の不具合によりログインできなくなったことが判明しました。
**処置ステップ**： [セキュリティグループ（ポート）検証ツール](https://console.cloud.tencent.com/vpc/helper) で検査を行います。
> リモートログインの Windows インスタンスは3389ポートをインターネットにオープンする必要があります。
> 

セキュリティグループポート設定の問題だと確定した場合は、【オーペンアール】機能でポートをオーペンすることが可能です。

セキュリティグループ規則をカスタマイズしたい場合は、 [セキュリティグループ操作](https://intl.cloud.tencent.com/document/product/213/18197) を参考にし、セキュリティグループの規則をコンフィギュレーションしなおしてください。


<span id="LoginSecuritySoftware"></span>
### ファイアウォール又はセキュリティソフトによるログイン異常

**障害の現象**：CVMのファイアウォールのコンフィギュレーション、又はセキュリティソフトによりログイン異常が起こりました。
**問題特定の考え**： VNC ログイン方法により Windows インスタンスにログインし、サーバーにファイアウォールがオンにされているか、360やセキュリティドッグ等のセキュリティソフトがインストールされているかをチェックします。
> この操作はCVMのファイアウォールをシャットダウンすることにかかわっているため、ご自身にはこの操作を行う権限があるかどうかを確認する必要があります。
>
**処置ステップ**：ファイアウォール又はセキュリティソフトをオフにし、リモート接続をリトライし、成功にリモートログインできるかを確認します。下記の操作は Windows Server 2016 インスタンスのファイアウォールのオフを例とします。
1.  [VNCログイン](#VNC)を介してインスタンスにログインします。
2. OS画面で、 <img src="https://main.qcloudimg.com/raw/6e36af2ceb4604b81de13cb42f30e859.png" style="margin: 0;">をクリックし、【コントロールパネル】を選択し、コントロールパネルウィンドーを開きます。
3. 【Windows ファイアウォール】をクリックすると、「Windows ファイアウォール」 画面に入ります。
4. 左側の【 Windows ファイアウォールをオン/オフにする】をクリックすると、「カスタマイズ設定」画面に入ります。
5. 【専用ネットワーク設定】と【パブリックネットワーク設定】を【 Windows ファイアウォールをオフにする】に設定し、【OK】をクリックします。
6. インスタンスを再起動し、リモート接続をリトライし、リモートログインができるかを確認します。

<span id="AuthenticationError"></span>
### リモートデスクトップの接続に身分検証エラーが発生した

**障害の現象**：リモートデスクトップ経由でWindows インスタンスにログインする時に、「身分検証エラーです。関数に提供されたマークが無効です。」或いは 「身分検証エラーです。リクエストされた関数がサポートされていません」 というエラーメッセージが表示されました。
**問題の原因**：Microsoftは2018年3月にセキュリティ更新をリリースしました。当該更新は証明書セキュリティサポートプロトコル（CredSSP）の身分検証プロセスにおける検証リクエスト方法を修正したことにより、 CredSSPにおける遠隔実行コードの脆弱性を修復しています。クライアントもサーバーもこの更新をインストールする必要があります。そうしないと、上記の問題が発生する可能性があります。
**処置ステップ**：セキュリティ更新をインストールすることにより解決することをお薦めします。具体的には[Windows インスタンス：身分検証エラーが発生しました](https://cloud.tencent.com/document/product/213/30813)をご参照ください。

## その他ソリューション
上記トラブルシューティングをした後、 それでもWindows インスタンスに接続できない場合は、セルフ診断の結果を保存し、[作業依頼書を提出する](https://console.cloud.tencent.com/workorder/category) でフィードバックしてください。
