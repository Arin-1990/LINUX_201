**<span style="color: red; ">キャパシティプランニング 200</span>**

/etc/collectd.conf

⭐️SNMP　ネットワーク経由で機器を監視・制御するためのプロトコル、collectdやMRTGなどのツールが使用する

⭐️リソースの状態(システム)監視ツール
  - collectd　設定ファイル「/etc/collectd.conf」
  - Nagios  (サーバの死活監視など)
  - MRTG
  - Cacti  (MRTGの代替として使用される)
  - Icinga2  (Nagios互換の監視ツール)

⭐️tar
  - 「-z」gzip()
  - 「-j」bzip2(bz2)
  - 「-J」xz

⭐️ソースファイルがコンパイルからインストールの実行順序
 1. ./configure
 2. make
 3. su
 4. make install

⭐️initrd 形式の初期RAM ディスクイメージの中身参照
 1. gunzip コマンドで解凍
 2. mount で適切なファイルシステムとしてマウント

⭐️lsof　ファイルを開いているプロセス表示

⭐️iostat　CPUの利用状況およびディスクI/Oの状況など表示
 - 「avg-cpu:」行
 - 「Device:」行

⭐️free メモリやスワップ領域の使用状況表示
 - 「Mem」行
 - 「-/+ buffers/cache」行
 - 「Swap」行

⭐️mpstat マルチプロセッサシステムのCPUの使用状況表示
 - 「-P」 表示するCPUを番号（数値）で指定することがき
 - 「ALL」全てのCPUの状況表示

⭐️プロセスのPID表示
 - pstree -p
 - ps
 - top
 - lsof

⭐️sarコマンド各オプションの出力内容
 - b
 - r
 - d

⭐️crontabシステム(一定の時間間隔で実行)
 - sa1
   - sadcコマンド バイナリデータの統計情報生成
 - sa2
  - sarコマンド sa1が生成したバイナリデータからテキストデータ生成

⭐️mpstat (マルチプロセッサシステムのCPUの使用状況表示)
 - -P 表示するCPUを番号（数値）で指定する,-ALL 全てのCPUの状況を表示します

**<span style="color: red; ">Linuxカーネル(主題201)</span>**

modprobe -f は強制的に操作を行う

bzImage についての説明

⭐️Linuxカーネル4つのカテゴリ
 - prepatch (新機能が含まれておりテストが必要なリリース,開発版リリース,)
 - mainline (prepatchの後にリリースされる正式版)
 - stable (mainlineの後にリリースされる安定版)
 - longterm (stableの中から選ばれ,長い期間バグフィックスが行われます

⭐️安定版判定
 - 2.6 より前 :2.X.Y の X が奇数だと開発版、偶数だと安定版
 - 2.6 より後 :ハイフンや記号が付いていなければ安定版

⭐️/usr/src/linux 内のファイル・ディレクトリ
 - .config (カーネルのビルド設定)
 - Makefile　(make設定、カーネルバージョン)
 - kernel/ (カーネル本体ソース)
 - Documetation/ (ドキュメント類)

⭐️ソースから再構築の基本手順
 - 設定を初期化 make mrproper
 - 設定 make oldconfig,make config,make menuconfig,make xconfig,make modules (カーネル本体は含まれません)
 - ビルド make,make all(カーネル本体とモジュールのビルド、一時ファイル自動的削除)
 - システムにインストールする make modules_install(モジュール),make install(カーネル本体)

 ◆make install
  1. カーネルを /boot 以下配置
  2. 初期RAMディスク必要な場合作成(mkinitrd,mkinitramfs)
  3. ブートローダの設定ファイルに新しいカーネル用のエントリ追加 (/boot/grub2/grub.cfg)

⭐️カーネルのソースは展開する場所

　◆/usr/src/linux/

⭐️初期RAMディスク (メモリ上にRAMディスクを暫定なフルートァイルシステムとして作成、カーネル起動後本来の
ファイルシステムmount)
1. ディスクイメージの作成方法
 - mkinitrd
 - mkinitramfs (cpio アーカイブを利用した形式,出力先指定する際には -o オプションつけ)
 - dracut
2.initramfs 形式のイメージ
 - cpio アーカイブ
 - gzip 圧縮

⭐️カーネルパラメータを参照する方法
 - sysctlコマンド (オプション２つ：-w 変更,-a 一覧)
 - /proc/sys以下の仮想ファイル参照

⭐️カーネルパラメータ値変更方法
  - /proc/sys/kernel/　(システム再起動すると、元に戻る)
  - sysctlコマンド

⭐️カーネルパラメータ恒常的に設定するファイル
 - /etc/sysctl.conf
  - 形式：「パラメータ名＝値」
 - /etc/sysctl.d

⭐️カーネルモジュールの操作方法、設定ファイルの記述方法重要

✳︎sysctl -pコマンドより実行される

⭐️カーネルバージョン確認方法
 - uname -r
 - /proc/version
 - Makefile

⭐️uname(現在の環境の様々な情報を取得・表示する)
 - s (カーネル名前表示)
 - r (カーネルバージョン)
 - n (ホスト名)
 - p (CPUタイプ)
 - a (以上全て)

⭐️modinfo (カーネルモジュールの情報表示)
- -d, --description（モジュールの説明）
- -l, --license（モジュールのライセンス）
- -n, --filename（モジュールのファイル名（パス））
- -p, --parameters（モジュールがサポートしているパラメータ）


**<span style="color: red; ">システムの起動(主題202)</span>**

？initプロセスについての説明

？シンボリックリンク(/etc/init.d/),スクリプト(etc/rc[0-6].d)の関係

⭐️ブートローダの役割・使用法の説明
 - ランレベルを指定してシステムを起動させる
 - 起動オプションをカスタマイズしてシステムを起動させる
 - カーネルイメージを見つけ、ロードする


⭐️起動スクリプト(/etc/rc[0-6].d)
- init によりシステムの起動時・ランレベルの変更時に実行されるもの
- 各種サービスをランレベルに応じ自動的に起動・終了させるために用いられる

⭐️insserv コマンド
 - -r (サービス自動起動しない)

⭐️システム
 - SysVinit (システム起動時にサービスが**順次起動**する)
 - systemd (必要なサービスのみ起動することから、システム起動する)

⭐️サービス自動起動
 - 手動でリンク作成 (起動スクリプトのシンポリックリンク作成)
 - chkconfig
 - update-rc.d

⭐️起動時指定したパラメータの確認：/proc/cmdline

⭐️Linuxシステムのブートプロセス順
 - BIOS　(MBR 最初にアクセス)
 - ブートローダ
 - カーネル
 - init

⭐️Red Hat(7.0)以降、systemdプロセスの４つユニット
 - service (各種サービスの起動、停止)
 - mount (ファイルシステムmountする)
 - device (udevによって認識され)
 - target (ユニットをグループ化)

⭐️chkconfigコマンド (Red Hat（6.xまで）系ディストリビューションで使う)
- [--level| ランレベル] サービス (on|off|reset)
- --list[サービス]

⭐️udev(デバイスファイル動的作成する)
1. メイン設定ファイル
 - /etc/udev/udev.conf
2. デバイスファイルを動的に作成、削除する仕組み
 - /lib/udev/rules.d (カスタマイズされたudevルールファイル配置、変更可能)
 - /etc/udev/rules.d (デフォルトのudevルールファイル配置、編集不可)

⭐️SysV-initを採用したシステムで、デフォルトランレベル指定方法
 - /etc/inittab
 - GRUBの設定ファイル

⭐️UEFIの説明
 - GUIでマウス操作
 - ESPは「/boot/efi」にマウントされる
 - OS上から起動エントリを表示、設定できる

⭐️rdev カーネルイメージにルートファイルシステムの位置（ルートデバイス）書き込む
 - 書式：rdev カーネルイメージ ルートデバイス

⭐️ブートローダPXELINUX
 - pxelinux.0 (本体ファイル名)
 - pxelinux.cfg/ (設定ファイル格納)
 - DHCPサーバ,TFTPサーバ使用

⭐️ブートローダISOLINUX
 - isolinux.bin (本体ファイル)
 - isolinux.cfg (設定ファイル名)

⭐️ブートローダSYSLINUX
- FATファイルシステムからLinuxを起動する軽量のブートローダ
- 書式：syslinux -i|--install デバイス名

⭐️設定ファイル
 - /usr/lib/systemd/system (デフォルトのUnitファイル)
 - /etc/systemd/system (管理者がカスタマイズする(定制)Unitファイル、**起動時のデフォルトターゲット**)

⭐️GRUB2設定順序
  1. /etc/default/grub　
  2. grub-mkconfig コマンド
  3. grub.cfg ファイルが生成される

⭐️systemctl コメンド


**<span style="color: red; ">ファイルシステムとデバイス(主題203)</span>**

⭐️マウントオプション(デフォルト)
 - async, auto, exec, nouser, rw

⭐️スワップ領域として使用するファイル作成手順
 - dd (ファイル作成)
 - mkswap (ファイル初期化)
 - swapon (ファイル有効化)

⭐️ハードディスクを利用する手順
 - fdisk(パーティション切り)→ mkfs(フォーマット) → mount(マウント)

⭐️XFS
 - mkfs.xfs (作成)
 - xfs_check (チェック)
 - xfs_admin (設定)
 - xfs_info (情報表示)
 - xfsrestore (バックアップから復元)
 - xfsdump (バックアップ)

⭐️e2fsck　ext2/ext3/ext4 のチェックを行う
  - 「-b」指定したスーパーブロック復元
  - 「-c」不良ブロックチェック
  - 「-p」自動的に不良ブロック修復
  - 「-f」ファイルシステムの状態がcleanでもチェックする

⭐️Linuxファイルシステム暗号化の手順
  1. 暗号化マッピング作成(「/dev/mapper」ディレクトリに指定した名前で作成され)
  2. 暗号化マッピングにファイルシステム作成
  3. 暗号化ファイルシステムをマウントする

⭐️cryptsetup Linuxファイルシステム暗号化
 - 書式：[オプション] アクション 引数
 - ３つアクション
  1. create
  2. remove
  3. status

⭐️カーネルがサポートしているファイルシステムの確認方法
 - /proc/filesystems

⭐️<span style="color: red; ">sync :データ(ファイル)をまとめてディスクに書き込み</span>

⭐️スワップ
 - スワップ領域作成：mkswap
 - ファイルをスワップ領域として利用：dd

⭐️ファイルシステムにアクセスしているプロセス表示
 - fuser
 - lsof

⭐️uuid(デバイス固有の識別子、システムで一意の値)
 - blkid
 - /dev/disk/by-uuid

⭐️システム領域に汎用的に使用されるファイルシステム
 - ext2
 - ext4
 - XFS
 - btrfs

⭐️ファイルシステムの変換？

⭐️ブロック
 - データブロック
  1. 実際のファイル内容を保持している
  2. ブロックサイズはファイルシステム作成時に決められる
 - i ノードブロック
  1. ファイルのメタ情報を保持している
  2. ブロック内に複数の i ノードが含まれている
 - スーパーブロック
  1. ファイルシステム全体に関わる重要な情報（マウント回数、ブロックサイズなど）を保持している)

⭐️oracleが使用するファイルシステムで、btrfsが参考としたファイルシステムはZFS

**<span style="color: red; ">高度なストレージ管理(主題204)</span>**

⭐️RAID構成の最低台数、利用可能容量

| レベル | 最低台数 | 利用容量 |説明|
| :--- | :---: | :---: |:---: |
| RAID0 | 2 | 全ディスク合計 |直列化、ストライピング、大きく高速なディスク領域確保|
| RAID1 | 2 | １台分 |並列化、ミラーリング、冗長性高い|
| RAID5 | 3 | 合計から１台引く |直列化、冗長性あり|

⭐️RAID構築するコマンド
 - mdadm

⭐️RAID動作状態
 - /proc/mdstat (格納場所)
 - mdadm --detail --scan/mdadm --detail RAID デバイス名　(表示するコマンド)

⭐️hdparm ハードディスクに関するパラメータを取得・設定する
 - オプション指定ない場合
 - -i

⭐️RAID デバイス
 - MD（Multiple Device） デバイスと呼ばれる /dev/md0, /dev/md1 等を使います

⭐️インテルが策定した規格
 - AHCI (ホストのストレージとメモリ間のデータ交換)
 - SSD ()
 - NVMe (PCI Express バスから SSD に接続するための規格)
 - Trim ()

⭐️lvcreateのオプション
 - -L (サイズ指定)
 - -s (スナップショット)
 - -n (論理ボリューム名指定)

⭐️仮想的なデバイス名
 - /dev/dm-1
 - /dev/VG/LV
 - /dev/mapper/VG-LV

⭐️デーモン
 - iscsidデーモン (**サーバ**をiSCSIイニシエータとして動作させる)
 - iscsiデーモン (ローカルデータベースに登録済みのiSCSIターゲットに**自動的にログインする**)

⭐️SCSI（Small Computer System Interface）とは
 - PCやサーバに直接接続されたハードディスクなどの周辺機器を制御し、データ転送を行うための規格の一つです
 - このSCSIの機能をTCP/IPネットワーク上で利用できるようにしたものがiSCSI（Internet Small Computer System Interface）という規格です。

⭐️iscsi_idとscsi_idの違い


⭐️SCSI（iSCSI）(ホスト側=イニシエータ、デバイス側=ターゲット)
 - iscsiadm (iSCSIイニシエータからiSCSIターゲットへアクセスし、**デバイスとして使用可能にする**)

**<span style="color: red; ">ネットワーク構成(主題205)</span>**

⭐️ARP キャッシュ(IP アドレスと MAC アドレスの対応関係) オプション６つ

  - -i (インタフェース指定)
  - -a (ホスト名指定)
  - -d (削除)
  - -n (名前解決せず)
  - -s (IPとMACの対応をキャッシュに追加)
  - -f (ファイル指定して、キャッシュに追加)✳︎ファイル名省略した場合/etc/ethersが使用される)

⭐️iw(無線デバイスや無線インターフェイス設定)
 - 書式: iw オブジェクト コマンド
 - 主なオブジェクト
|オブジェクト|コマンド |
| :-- |--- |
| dev |<span style="color: red; ">link(無線の接続状況)</span><br>scan<br>connect/disconnect(ESSID指定して接続・切断)<br><span style="color: red; ">station dump(統計情報確認)</span>|
| phy |interface add/del<br>info(デバイス使用可能な情報表示)|

⭐️ウェルノウンポート
 - 20，21 FTP (データ用、制御用)
 - 22 SSH (リモートログイン暗号化あり)
 - 53 DNS (名前解決)
 - 80 HTTP (HTMLファイル転送)

⭐️netstat,ss同様なオプション
 - -a (全てのソケット表示)
 - -l (接続待ちのソケット表示)
 - -n (名前解決せず)
 - -t (TCPソケット)
 - -u (UDPソケット)
 - -t
 -l (接続まち状態のTCPポート表示)

⭐️ netstat (ネットワークの状態に関する情報を表示)
- 「-s」プロトコル毎にパケットの送受信に関する情報表示
- 「-i」ネットワークインターフェースの状態表示
- 「-r」ルーティングテーブル表示
- 「-n」名前解決せず
- 「-a」全てのソケット表示
- 「-l」待ち受け状態ソケット表示
- 「-c」回数

⭐️IPアドレスとホスト名の変換
 - nslookup
 - dig　(nslookupより詳細、DNS得られた応答出力)

⭐️nmap
説明：ネットワーク上のオープンしているポート調べて状態表示、詳細が不明なネットワークの構造調査、**スキャン**
 - ３つスキャンタイプ
  1. -sT (TCP、デフォルト)
  2. -sU (UDP、root権限必要)
  3. <span style="color: red; ">-sP (Ping、ICMP)</span>
 - ３つオプション
  1. <span style="color: red; ">-p (ポート指定)</span>
  2. -F (高速スキャン)
  3. -O (OS検出)
  4. -T (遅延時間設定、数字が大きほど遅延時間を短く設定するので実行速度あげる)

⭐️ホストテストするコマンド
 - telnet
 - nc

⭐️アクセス設定Wrapperファイル
 - /etc/hosts.deny , /etc/hosts.allow　(どちらも記載されてないホスト許可する)
 - サービス実行中に変更しても内容反映される
 - Wrapperデーモン

  1. tcpd (inetd経由で、起動だれるサーバに対するアクセス制御だげ)
  2. libwrap (libwrapにリンクしたサーバで利用できる)

⭐️リモートファイルシステム
 - cifsiostat
 - nfsstat
 - nfsiostat


⭐️tcpdump (ネットワークのトラフィックモニター、パケットキャプチャ、パケット監視)
 - -i (インタフェース指定)
 - -n (名前解決せず)
 - -X (16進数とASCIIの表でパケット内容表示)

⭐️ネットワーク関連ファイル
 - /etc/hosts (ホスト名とIPアドレスとの対応)書式：IPアドレス ホスト名 [ホスト名...]
 - /etc/hostname　(ホスト名)
 - /etc/networks　(ネットワーク名とネットワークアドレスとの対応)
 - /etc/sysconfig/network (ネットワーク機能の使用・不使用、ホスト名、デフォルトゲートウェイアドレスの設定)
 - /etc/sysconfig/network-scripts (ネットワークデバイスの設定ファイル配置)
 - /etc/network/interfaces (Debian系ディストリビューションで使用)
 - /etc/resolv.conf (DNSサーバやドメイン名の設定)

⭐️ネットワーク問題解決方法

 1. pingコマンドによる疎通確認
 2. /etc/resolv.conf (名前解決確認)
 3. route (デフォルトゲートウェイ確認)
 4. tracerouteコマンドによる経路確認,mtrにも使える
 5. ifconfigやnetstatコマンド (ネットワーク確認)

⭐️hostname
 - -a (エリアス)
 - -f (完全修飾ドメイン名 (FQDN))
 - -i (IPアドレス)
 - -d (ドメイン)

⭐️fdisk　ハードディスクのパーティション設定を行う

**<span style="color: red; ">システムの保守(主題206)</span>**

⭐️バックアップ
 - ローカルバックアップ
 1. tar
 2. cpio
 3. dd
 4. dump
 5. restore
 6. mt
 - ネットワーク経由
  - rsync

⭐️GNUmake(指示ファイル検索)
 - GNUmakefile、makefile、Makefileの順

⭐️Makefileに含まれるターゲット(makeビルドツール)
 - clean：ビルド時に作成されたファイルの削除
 - install：ビルドしたプログラム、ライブラリの指定場所へのコピーやパーミッション設定
 - uninstall：インストールしたプログラム、ライブラリの削除

⭐️ mt (テープドライブ制御) 書式：mt -f テープデバイス 操作
  - デバイス
    1. /dev/st0 テープが自動的に巻き戻されます
    2. /dev/nst0 複数のファイルを読み書きしたい場合などは巻き戻ししない
  - コマンド
    1. fsf テープ進める
    2. dsf テープ戻す

⭐️rsync(ネットワーク経由でファイルコピー)
 - <span style="color: red; ">構文：rsync [オプション] 送信元 送信先</span>
 - <span style="color: red; ">送信先（送信元）の指定：[ユーザ名@][ホスト:]ディレクトリ</span>
 - オプション
  - -a (属性保持したままコピー)
  - -e (転送方式指定)

⭐️tar(ファイルのアーカイブ)
 - -c (アーカイブ作成)
 - -x (アーカイブからファイル展開)
 - -t (アーカイブ内容表示)

⭐️メッセージ
 - /etc/issue ログイン画面に表示される内容を設定する
 - /etc/motd ログイン直後に表示される内容を設定する

⭐️patch コマンドの書式
 - patch [オプション] <span style="color: red; "><</span> パッチファイル
