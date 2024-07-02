# discord-proxy

このプロジェクトは、Discord に接続するためのプロキシ アドレスを提供しません。これは、Discord がグローバル プロキシである必要があるという問題を解決するだけです。プロキシは個別に設定できます。

原則として、Discord.exe の起動時に version.dll がロードされ、コマンド ラインでプロキシ アドレス (http....) を読み取って保存し、Discord の updater.node モジュールの操作をインターセプトして環境変数を読み取ります。コマンドを変更する 行内のプロキシ アドレスが直接返されるため、システムの環境変数を変更する必要はありません。

このリポジトリは本家を翻訳して茨城高専のプロキシで動くことを確認したものです。

## 使用方法

### 方法1
プロジェクト [DiscordProxyStart](https://github.com/kazu-321/DiscordProxyStart) を使用して、version.dll を自動的にコピーし、Discord を起動します (**実験的**)

ダウンロード：[リリース](https://github.com/kazu-321/DiscordProxyStart/releases)

---

### 方法2
release.zip を手動でダウンロードし、version.dll を抽出します。

https://github.com/kazu-321/discord-proxy/releases

discord.exe が存在するディレクトリに version.dll を配置します (Discord が更新されている場合は、再度配置する必要がある場合があります)。
<p align="center" color="#6a737d">
<img src="./images/1.png" alt="discord-proxy">
</p>


次に、デスクトップ上のショートカットを複製します。
複製されたものを右クリックしてプロパティーを確認し最後に追加されたプロキシアドレスに従います (このショートカットは Discord のインストール時に自動的に作成されます。Discord.exe から自分で作成しないでください。詳細については下部を参照してください)。
<p align="center" color="#6a737d">
<img src="./images/2.png" alt="discord-proxy">
</p>

先頭にスペースがあることに注意してください。
```
 --a=--proxy-server=po.cc.ibaraki-ct.ac.jp:3128
```
これで設定は完了したので、デスクトップのショートカットから実行するだけです。


---

### **それでもアクセスできない場合は、こちらをご覧ください:**

#### **ショートカットが正しいかどうかを確認してください**
上記のデスクトップ ショートカットは、Discord.exe から作成されるのではなく、インストール中に自動的に作成されるショートカットです。変更後の完全なコマンド ラインの例は次のとおりです。
```
C:\Users\xxxxxx\AppData\Local\Discord\Update.exe --processStart Discord.exe --a=--proxy-server=po.cc.ibaraki-ct.ac.jp:3128
```

#### **プロキシ ルールに注意してください**
**クラッシュ プロキシ** を使用する場合は、プロキシ ルールに注意し、Discord 関連のドメイン名トラフィックがプロキシを通過するかどうかを確認してください。そのため、v2、ss、および ssr は指定されたポートの全世代を通過する必要がありません。他のことは何でもしてください。

#### **Socks プロキシはサポートされていません**
Socks プロキシは現在サポートされていません。どうしても必要な場合は、このプロジェクトを使用して Socks プロキシを http プロキシに変換できます: https://github.com/ginuerzh/gost
