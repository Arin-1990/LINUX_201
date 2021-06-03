**<span style="color: red; ">DNS</span>**

⭐️DNSサーバ
 - マスタサーバ
 - スレーブサーバ
  - named-compilezone コマンド：zoneファイルをバイナリ形式からテキスト形式に変更する

⭐️rndcコマンド

⭐️digコマンド

⭐️nslookupコマンド

⭐️hostsコマンド

⭐️BIND(dns服务器软件，域名解析)
 - /etc/named.confとゾーンファイルから構成される

⭐️zoneファイル
 - ディレクトリ：named.conf

 - ファイル名:zoneステートメント内
 - 種類
  1. hin情報
  2. 正引き
  3. 逆引き
 - 書式
  - 名前 「TTL値」 IN リソースレコードタイプ 値

⭐️リソースレコード(记录类型)
 - ゾーンの情報記述する
 - リソースレコードタイプ(7つある)

 | タイプ | 説明 | 書式 |
 | --- | --- | -- |
 | SOA |  |  |
 | NS |  |  |
 | MX |  |  |
 | A |  |  |
 | AAAA |  |  |
 | CNAME |  |  |
 | PTR |  |  |

⭐️DNSサーバのセキュリティ
 - ゾーン転送制限
 - DNS問い合わせ制限
 - バージョン番号隠蔽
 - chrootコマンド

⭐️DNSの仕組みを強化する仕組み
 - DNSSEC　(DNSサーバによる**DNS応答を保証する仕組み**) BINDバージョン9.3.0以降対応
  1. 電子署名
     - ZSK (ゾーン情報に電子署名)
     - KSK (ZSK情報に電子署名)
  2. DNSSECの設定方法
    - dnssec-signzoneコマンド
 - TSIG　(**ゾーン転送の安全性を向上させる仕組み**)
  1. dnssec-keygenコマンド

**<span style="color: red; ">Webサーバの設定</span>**

⭐️Apacheインストール
 - ディストリビューションから
 - ソースから(configure〜)

⭐️Apacheの設定
 - httpd.confファイル

⭐️Apacheの設定ファイル
- RedHat系
 - デーモンはhttpd
 - 設定ファイルは「/etc/httpd/conf/httpd.conf」
- Debian系
 - デーモンはapache2
 - 設定ファイルは「/etc/apache2/apache2.conf」

⭐️Apache2.4の主な**モジュール**
 ![avatar](/Users/yalinhe/Documents/Linux202/k30132.jpeg)

⭐️httpd.confの主な**サーバ処理関連のディレクティブ**
 ![avatar](/Users/yalinhe/Documents/Linux202/k30087.jpeg)

 ⭐️httpd.confの**外部設定ファイルに関するディレクティブ**
  ![avatar](/Users/yalinhe/Documents/Linux202/k30100.jpeg)

 ⭐️Requireディレクティブの主なエンティティ
  ![avatar](/Users/yalinhe/Documents/Linux202/k31674.jpeg)

⭐️Order、Allow、Denyディレクティブの使い方
 ![avatar](/Users/yalinhe/Documents/Linux202/k30125.jpeg)

⭐️外部設定ファイル
 - AccessFileNameディレクトリに指定
 - 許可するにはAllowOverrideディレクティブ

⭐️apache制御
 - SysVinitシステム： /etc/init.d/httpd start
 - systemdシステム：systemctl start httpd.service
 - apachectlコマンド

⭐️モジュールの利用
 - /usr/lib/httpd/modulesディレクトリ以下
 - apxsコマンド(モジュールを組み込む)

⭐️クライアントアクセス認証
 - **基本認証 (BASIC認証のユーザ管理)**
  - httpd.confにユーザー認証設定
  - htpasswdコマンド (ユーザー名とパスワード設定)
    - 書式：htpasswd [オプション] ファイル名 ユーザ名
    - オプション
      - -c パスワードファイル新規
      - -D ユーザ削除
  - Require vaild-user
 - **ダイジェスト認証**
  - AuthType,AuthNameの違い
  - htdigestコマンド
    - 書式: htdigest [-c] ファイル名 認可領域名 ユーザ名
 - **ホストベースによる認証**
  - Order,Allow,Denyディレクティブ
  - Requireディレクティブ

⭐️バーチャルホスト
 - 1台のサーバで複数のWebサイトを管理できる
 - 名前ベースバーチャル　(VirtualHost)
  - 稼働しているWebサーバにバーチャルホストを追加する場合、既存のホストも１つのバーチャル
  ホスト設定として設定する必要
 - IPベースバーチャル (VirtualHost)

⭐️ログファイル(/var/log/httpd)

 1. アクセスログファイル
  -  クライアントからのリクエスト記録
  -  フォーマット：httpd.conf内で設定(LogFormat,CustomLog)
 2. エラーログファイル
  -  エラー情報やサーバの挙動記録

⭐️プロキシサーバ
- プロキシ（Proxy）は英語で「代理」の意味。インターネットに直接接続できないコンピューターに代わり、インターネットに接続し、Webサイトへのアクセスなどを行うサーバーのことを指す。
1. Squid基本設定
 - squid.conf
2. アクセス制御の設定
 - acl ホストやプロトコルの集合にアクセスコントロールリスト名を付ける
 - http_access　アクセスコントロールリストに対しての制御設定する

⭐️Nginx
 - 高速で動作し負荷に強いWebサーバです
 - 一つのmaster processと複数のworker processから構成する
  1. worker process クライアントからのHttp要求を受付、処理する
  2. master process (worker process)を管理する
 - 設定ファイル(４つ)
 - 書式: ディレクティブ 値;

⭐️キープアライブの説明
 - ウェブサーバとクライアントの間でTCP接続をキープすること
 - リクエストごとにTCP接続を閉じるのではなく、同じ接続で複数のリクエストを処理する
 - KeepAliveディレクティブを使用して設定する

⭐️ApacheでSSL/TLSを利用する際の主な流れ
 1. 秘密鍵作成
 2.CSR（証明書の署名要求）作成

 (サーバ証明書を認証局に作成してもらう為、作成されるCSRには、秘密鍵の対となる公開鍵の情報が含まれる)
 3. 中間CA証明書とサーバ証明書が認証局より発行される
 4. 秘密鍵と中間CA証明書、サーバ証明書をサーバの所定の場所へ設置し、ApacheのSSL用の設定ファイル「ssl.conf」でそれぞれのファイルを指定する

⭐️ssl.confの主なディレクティブ
 ![avatar](/Users/yalinhe/Documents/Linux202/kk30137.jpeg)

⭐️Apacheの設定ファイルhttpd.confのセキュリティ設定
 ![avatar](/Users/yalinhe/Documents/Linux202/k30440.jpeg)

⭐️opensslコマンド (SSLの証明書や鍵作成)
 - サブコマンド
  - req :CSR(サーバ証明書発行要求)
    - 書式：openssl req -new -key 秘密鍵ファイル名 [-out 出力ファイル名]
  - genrsa :秘密鍵作成
  - ca :サーバ証明書作成
    - 書式：openssl ca [-out 出力ファイル名] -infiles CSRファイル名

**<span style="color: red; ">ファイル共有</span>**

⭐️Sambaの構成するプロセス(デーモン)
 - smbd :ファイル共有、認証
 - nmbd :ブラウズ機能、NetBIOS名前解決、WINSサーバなど
 - winbindd :winbind機能

⭐️Winbind機能
 - Winbind機能を提供するデーモンはwinbinddである
 - WindowsユーザのSIDを、LinuxユーザのUID・GIDにマッピングする
 - Samba側でWindowsドメインの既存のユーザ情報を利用する

⭐️smbcontrolコマンド
 - smbd、nmbd、winbinddにメッセージを送ることができるプログラムです。
 - 書式：smbcontrol [対象] [メッセージタイプ]
 - メッセージタイプ
  ![avatar](/Users/yalinhe/Documents/Linux202/kkk30549.jpeg)
 - 対象
  - all
  - PID
  - デーモン

⭐️smbclientコマンド
 - 他のSambaサーバやWindowsマシンの**共有リソースにアクセスする**
 - 書式：
  - smbclient [オプション] //ホスト名/共有名
  - smbclient //ホスト名/共有名 [オプション]
 ![avatar](/Users/yalinhe/Documents/Linux202/k29989.jpeg)


⭐️Sambaの設定ファイル
 - smb.conf(/etc/samba/smb.conf)
 - セクション
  1. global :変更した場合、Smaba再起動必要
  2. home :ホームディレクトリ一括して共有
  3. printers :共有プリント設定
 - 構文チェック
  - testparmコマンド
 - Sambaの**ユーザ管理する**コマンド
  - pdbedit　:Sambaユーザの追加(-a)、削除(-x)、一覧表示(-L)
  - smbpasswd :Sambaのパスワード変更。無効化(-d)、有効化(-e)、削除(-x)

⭐️SambaサーバをActive Directoryドメインに参加させる際に必要なsmb.confの設定
  ![avatar](/Users/yalinhe/Documents/Linux202/kkkkk31379.jpeg)

⭐️Sambaの管理コマンド
 - smbstatus :sambaサーバに接続されているクライアント、使用中の共有、ロックされているファイル表示
 - nmblookup :NetBIOS名問い合わせ
 - smbclient :共有ソース利用する

⭐️マスターブラウザ
- ブラウザリスト（Windowsネットワーク内にあるコンピュータのリスト）を管理するコンピュータのことです

⭐️nmblookupコマンド
- 「-M」オプション :マスターブラウザを調べる
- 「-A」オプション :IPアドレスからNetBIOS名やMACアドレスを調べる

⭐️NFSサーバ構築
 - RPC :リモートホストの機能を別のホストから使えるようにする仕組み
  - rpcinfoコマンドでRPCサービス状況確認する、一覧表示(-p)
 - /etc/exports エクスポートするディレクトリ記述する
  - exportfsコマンド　エクスポート状況表示、 /etc/exportsの変更反映
  - showmountコマンド　NFSサーバでエクスポートしているディレクトリ調べる
  - nfsstatコマンド　NFSの統計情報表示

**<span style="color: red; ">ネットワーククライアント管理</span>**

⭐️DHCP（动态主机配置协议）
 1. DHCPクライアントdhclient,pump,dhcpcd.
  - dhcpcd.confの設定
 2.DHCPリレエージェント(異なるネットワーク間で同一のDHCPサーバ利用したい場合を中継するプログラム)

⭐️PAM(Linux系统对不同用户以及系统中不同服务进行认证的安全机制)
 - 設定ファイル
  - /etc/pam.d
  - /etc/pam.conf
   - 書式：モジュールタイプ　コントロール　モジュールパス　引数
 - PAMのモジュールが格納されているディレクトリ
  - 32ビット版は「/lib/security」
  - 64ビット版は「/lib64/security」


⭐️LDAP(通讯协议,支持TCP/IP.一个为查询、浏览和搜索而优化的专业分布式数据库，呈树状结构组织数据,大多数是用来查询)
 1. LDIF(相当于JDBC)：树（dc=ljheee),分叉（ou=bei,ou=xi,ou= dong）,苹果（cn=redApple）
 2. LDAPサーバ設定
   - OpenLDAP
      - /etc/openldap/slapd.conf 設定ファイル
      - sladp デーモン
 4. LDAPサーバ管理のコマンド
   - slappasswd
   - slapcat
   - slapadd
   - slapindex
 5. クライアント利用のコマンド
   - ldapadd
   - ldapsearch
   - ldapdelete
   - ldapmodify
   - ldappasswd
 6. SSSD(守护进程。可以用来访问多种验证服务器(LDAP等)并提供授权。介于本地用户和数据存储之间的进程，本地客户端首先连接SSSD，再由SSSD联系远程服务器)
  - /etc/sssd/sssd.conf 設定ファイル

⭐️属性

![avatar](/Users/yalinhe/Documents/Linux202/kkk30335.jpeg)

⭐️「slapd.conf」ファイルのグローバルセクションに記述する主なディレクティブ
![avatar](/Users/yalinhe/Documents/Linux202/k30386.jpeg)

⭐️OpenLDAPの管理用コマンドの主な共通オプション
![avatar](/Users/yalinhe/Documents/Linux202/k30405.jpeg)

**<span style="color: red; ">メールサービス</span>**

⭐️SMTPサーバ構築

1.メール配送の仕組み(MTA,MDA,MUA)
- メールボックス形式(/var/mail)
 - mbox :１ユーザ１ファイル
 - Maildir :１メール１ファイル

2.Postfix(MTA)
- 設定(/etc/Postfix)
 - main.cf :MTAとしての基本設定ファイル
   - postconfコマンド :Postfix全体設定値表示される
 - master.cf :デーモンの設定ファイル
- 制御
 - postfixコマンド

3.メールエイリアスとメール転送(/etc/aliases,/etc/mail/aliases)
 - newaliasesコマンド :変更反映
 - 「/etc/aliases」ファイルの書式
  - アカウント名： 受け取りユーザ名[,受け取りユーザ名 ...]
  - 受け取りユーザ名
    -  /ファイルパス :メールのメッセージ追加
    - |コマンド :メールのメッセージを渡す
    - user@domain :メール転送
    - :include:/ファイルパス :別名で読み込む

4.SMTPサーバの運用と管理
 - 格納場所
   - /var/spool/postfix
   - /var/spool/mqueue
 - メールキュー表示するコマンド
   - mailq
   - postqueue -p
 - メールキューのメールを削除するコマンド
   - postsuper -d

5.POPとIMAP(プロトコル)
- 提供するソフトウェア
  - Dovecot(MDA)
  - Courier IMAP
- Dovecotの利用(/etc/dovecot.conf)
  - dovecotコマンド :dovecotの設定内容出力
    - -nオプション：デフォルト値以外出力
    - -cオプション：設定ファイル指定
  - doveadmコマンド :Dovecotの管理用
- Dovecotの設定
  - mechanisms :認証方式の指定
  - listen :接続を待ち受けるアドレスの指定
  - mail_location :メールの格納方法および格納場所の指定
  - protocols :プロトコル指定
  -
- メール関連のポート番号
  - IMAP：143
  - POP3:110
  - SMTP：25
  - IMAPS：993
  - POP3S:995

⭐️RBL（Real-time Blackhole List）
- 迷惑メール（スパム）やウィルス等の送信を行う、問題のあるメールの送信元を登録したブラックリストです。MTAはクライアントからの接続を受け付ける際にRBLを照会し、ブラックリストに載ったIPアドレスからの接続は拒否するようになっています。



**<span style="color: red; ">システムセキュリティ</span>**

⭐️パケットフィルタリング

1.テーブル
  - filter
  - nat
  - mangle

2.コマンド
- 書式
  - ポリシーを設定する：**iptables [-t テーブル名] –P チェイン ターゲット**
  - ルールを追加する：**iptables [-t テーブル名] –A チェイン ルール**
- iptables :パケットフィルタリング設定する
- iptables-restore :iptablesの設定が保存されているファイルから設定を復元する

3.ポート転送(使用するルール)
  - -p
  - -dport
  - -i
  - -d

⭐️ルータの構成

1.ルーティングテーブル
  - 表示するコマンド
    - route
    - netstat -r
  - パケット転送許可設定
    - /proc/sys/net/ipv4/ip_forward
    - /proc/sys/net/ipv6/conf/all/forwarding
    - /etc/sysctl.conf(恒久的)
    - /etc/sysconfig/network(恒久的)

2.ipマスカレード(masquerade)
  - SNAT:指在数据包从网卡发送出去时，把数据包中的源地址部分替换为指定的IP，这样，接收方就认为数据包的来源是被替换的那个IP的主机
  - MASQUERADE:指用发送数据的网卡上的IP来替换源IP，适用于IP不固定的场合
  - DNAT:指数据包从网卡发送出去时，修改数据包中的目的IP，表现为如果你想访问A可是因为网关做了DNAT，把所有访问A的数据包的目的IP全部修改为B，那么实际上访问的是B

⭐️FTPサーバのセキュリティ

1.FTPサーバ種類
  - wu-ftpd
  - ProFTPD
  - vxftpd
  - Pure-FTPD

2.アクセス制御
 - /etc/ftpusers :ログイン許可しないユーザ指定する
 - chroot機能 :特定ディレクトリー以外のディレクトリーへ移動禁止

3.パッシブモード(被动模式传送)
- Port模式：是客户端C在本地打开一个端口N等服务端S去连接建立数据连接
- Pasv模式：是服务端S打开一个端口M等待客户端C去建立一个数据连接

⭐️OpenSSH

1.SSHの設定
 - /etc/ssh/sshd_config (服务端配置文件)

2.

3.公開鍵認証
 - ssh-keygenコマンド:ユーザーの公開鍵と秘密鍵のペア作成する(生成公钥)

4.公钥加密过程

![avatar](/Users/yalinhe/Documents/Linux202/1430251-20180916095223643-1252382453.png)
 - （1）远程主机收到用户的登录请求，把自己的公钥发给用户。

 - （2）用户使用这个公钥，将登录密码加密后，发送回来。

 - （3）远程主机用自己的私钥，解密登录密码，如果密码正确，就同意用户登录。
 - 当远程主机的公钥被接受以后，它就会被保存在文件~.ssh/known_hosts之中。下次再连接这台主机，系统就会认出它的公钥已经保存在本地了，从而跳过警告部分，直接提示输入密码。

⭐️攻撃回避の対策
- SYN flood攻撃: echo 1 > /proc/sys/net/ipv4/tcp_syncookies
- Smurf攻撃: echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts
