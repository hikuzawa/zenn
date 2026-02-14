---
title: "201"
emoji: "📘"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: []
published: false
---
主題2.01：システムの起動とLinuxカーネル
2.01.1 ブートプロセスとGRUB
重要度	4
概要	ブートプロセス中およびリカバリモードのLinuxシステムを適切に操作する。関連するブートローダはGRUB バージョン2 である。BIOS と UEFI のシステム両方をカバーする。
詳細	
BIOS と UEFI
Master Boot Record (MBR)
EFI System Partition (ESP), efibootmgr, UEFI shell
ブートローダの標準的なオプションの変更とブートローダのシェル(コマンドライン)の使用。
ブートローダの開始とカーネルへの引継ぎ。
GRUB の起動メニューを生成する。
grub-mkconfig, grub2-mkconfig
カーネルローダブルモジュールのロード。
initrd, initramfs
ハードウェアの初期化と設定。
デバイス、モジュール
ファイルシステムのチェックとマウント。
デーモン / サービスの初期化と設定。
systemctl, systemd.unit
ハードディスクまたはリムーバルデバイスにおけるブートローダのインストール場所を知っている。
grub-install, grub2-install
/boot/, /boot/grub/,/boot/grub2/ および /boot/efi/ の内容

# 復習


---

2.01.2 システム起動のカスタマイズ
重要度	3
概要	さまざまなターゲットのシステムサービスの動作を照会および変更する。systemd と Linux のブートプロセスについての十分な理解が必要である。これには、systemd ターゲットの操作も含まれる。
詳細	
systemd
/usr/lib/systemd/, /etc/systemd/, /run/systemd/, systemctl, systemd-delta
systemctl status,systemctl list-units,systemctl start/stop,systemctl enable/disable,systemctl mask/unmask
systemd のrescue モードと emergency モード。

---

2.01.3 Linux カーネルの構成要素
重要度	2
概要	特定のハードウェア、ハードウェアドライバ、システムリソース、およびさまざまな要求に必要となるカーネルの構成要素を利用する。これには、異なる種類のカーネルイメージを実装すること、安定版および開発版のカーネルとパッチを区別すること、カーネルモジュールを利用することなども含まれる。
詳細	
Kernel の配布形式。
bzImage , xz データ圧縮
Kernelのモジュールとドキュメント。
/usr/src/linux/
/usr/src/linux/Documentation/

---

2.01.4 Linuxカーネルのコンパイル
重要度	2
概要	Linuxカーネルの特定の機能を必要に応じて取り込んだり無効化するために、カーネルを適切に構成できる。また、必要に応じてLinuxカーネルをコンパイルし、新しいカーネルに変更点を書き込み、initrdイメージを作成し、新しいカーネルをインストールできる。
詳細	
/usr/src/linux/
/usr/src/linux/.config
カーネルの Makefile
Kernel 2.6.x、3.x、4.x、5.x のmakeのターゲット。
all, config, xconfig, menuconfig, gconfig, oldconfig, mrproper, bzImage, modules, modules_install, rpm-pkg, binrpm-pkg, deb-pkg
カーネル構成をカスタマイズする。
新しいカーネルおよび適切なカーネルモジュールを構築する。
/lib/modules/kernel-version/, gzip, bzip2
新しいカーネルおよび必要なモジュールをインストールする。
module tools, depmod
ブートマネージャが新しいカーネルおよび関連付けられたファイルを探せるようにする。
モジュールの構成ファイル
DKMS を使用してカーネルのモジュールをコンパイルする。
dkms
initrd を構成する。
Dracut,mkinitrd, mkinitramfs
2.01.5 カーネル実行時における管理とトラブルシューティング

---

重要度	3
概要	2.6.x、3.x、4.x、5.x カーネルとそのロード可能なモジュールについての管理や照会ができる。ブートおよび実行時の一般的な問題を特定および修正することができる。udevを使用したデバイスの検知と管理について理解する。これには、udevルールのトラブルシューティングが含まれる。
詳細	
コマンドラインユーティリティを使用して、現在実行中のカーネルおよびカーネルモジュールに関する情報を取得する。
depmod, modinfo
手作業でカーネルモジュールをロードおよびアンロードする。
modprobe, insmod, lsmod, rmmod
モジュールをアンロードできるタイミングを判断する。
モジュールが受け取るパラメータを判断する。
/etc/modprobe.d/
カーネルのバージョンを確認する。
uname
/lib/modules/kernel-version/modules.dep
モジュールをファイル名ではなく別の名前でロードできるようにシステムを設定する。
/proc ファイルシステム
/proc/sys/kernel/
/etc/sysctl.conf, /etc/sysctl.d/, /sbin/sysctl
/sys ファイルシステム (sysfs)
/bootおよび /lib/modules の内容
利用可能なハードウェアに関する情報を分析するツール
dmesg, lspci, lsdev, lsusb, journalctl
udevルール
udevmonitor, udevadm monitor, /etc/udev/
/etc内のモジュール設定ファイル
カーネルダンプを取得する。設定は含まない。
kdump, kexec
主題2.02：ファイルシステムとストレージ管理
2.02.1 ファイルシステムの設定とマウント

---

重要度	3
概要	標準的なLinuxファイルシステムの適切な設定と操作ができる。これには、各種ファイルシステムの設定およびマウントも含まれる。
詳細	
fstab設定の概念
/etc/fstab
ファイルシステムのマウントとアンマウント
mount, umount, /etc/mtab, /proc/mounts, systemd
マウントの順番
スワップパーティションおよびファイルを操作するツール
swapon, swapoff, mkswap
ファイルシステムを特定しマウントするための UUID の使用
blkid, lsblk
2.02.2 ファイルシステムの管理

---

重要度	4
概要	システムユーティリティを使用して、Linuxファイルシステムを適切に保守できる。これには、標準的なファイルシステムの操作およびSMARTデバイスの監視が含まれる。
詳細	
ファイルシステムを操作するツール
mkfs (mkfs.*), fsck (fsck.*)
ext4を操作するツール
tune2fs, dumpe2fs, dump, restore
XFS を操作するツール
xfs_info, xfs_check, xfs_repair, xfsdump, xfsrestore
subvolumes と snapshots を含む、 基本的な Btrfs を操作するツール
ext4 ファイルシステムをBtrfsに変換したり操作する。
btrfs, btrfs-convert
HDD, SSD の健康状態を監視できる。
smartd, smartctl
2.02.3 論理ボリュームマネージャの設定と管理

---

重要度	3
概要	論理ボリューム、ボリュームグループ、および物理ボリュームの作成および削除ができる。これには、スナップショットと論理ボリュームのサイズ変更が含まれる。
詳細	
LVM のツールと設定ファイル
lvm, lvm.conf
物理ボリュームの作成および削除方法
pv* コマンド
ボリュームグループの作成／削除、物理ボリュームの追加／削除、名前変更、有効化／無効化方法
vg* コマンド
論理ボリュームの作成／削除、サイズ変更、名前変更、有効化／無効化方法
lv* コマンド
主題2.03：ネットワーク構成
2.03.1 基本的なネットワーク構成

---

重要度	3
概要	ネットワークデバイスを設定し、有線または無線のローカルネットワークと広域ネットワークに接続できる。
詳細	
Ethernetネットワークインターフェイスを設定および操作する。デフォルトルートの設定を含む。
ip, ifconfig, route, arp, nmcli
無線ネットワークを構成する。
iw, iwconfig, iwlist
2.03.2 高度なネットワーク構成

---

重要度	3
概要	
複数のサブネットへの経路設定ができる。これにはルータ機能の設定も含まれる。
ネットワークの状態を監視できる。
ネットワークのデバイス、通信状態などを分析できる。
詳細	
ルーティングテーブルを操作するユーティリティ
ip, route
IPフォワードを設定してルータ機能を実装する。
/etc/sysctl.conf, sysctl
ネットワークデバイスの状態を分析するユーティリティ
ip, ifconfig
TCP/IPの通信状態やトラフィックを監視および分析するユーティリティ
ping, ping6, netcat(nc, ncat), tcpdump, nmap, ss, netstat
2.03.3 ネットワークの問題解決

---

重要度	3
概要	一般的なネットワーク設定に関する問題を特定して解決できる。これには、基本的な設定ファイルの位置とコマンドに関する知識も含まれる。
詳細	
ネットワークの設定に関する情報を取得する。
hostname, /etc/hostname, /etc/hosts, /etc/resolv.conf, nmcli, ip
ネットワークの通信経路の問題を特定して解決する。
traceroute, traceroute6, ip, route, mtr
ハードウェアの認識と利用に関する情報を取得する。
dmesg, /var/log/syslogおよび/var/log/messagesなどのシステムのログファイルおよび systemd のジャーナル
システムの初期化ファイルとその内容（systemd）
NetworkManagerおよびそれがネットワーク設定に及ぼす影響について知っている。
/etc/network/, /etc/sysconfig/network-scripts/
主題2.04：システムの保守と運用管理
2.04.1 makeによるソースコードからのビルドとインストール

---

重要度	3
概要	ソースコードから実行プログラムをビルドしてインストールできる。これには、ソースファイルの展開も含まれる。
詳細	
gitを使ってソースコードを入手する。
git clone, git tag -l, git checkout
一般的な圧縮およびアーカイブユーティリティを使用して、ソースコードを展開する。
gzip, gunzip, bzip2, xz, tar, unzip
ソースコードにパッチを適用する。
patch
configureスクリプトにパラメータを適用する。
configure
プログラムをビルドするmakeの実行について基本を理解する。
make, make install
2.04.2 バックアップとリストア

---

重要度	3
概要	
重要なシステムデータをバックアップするシステムツールを使用できる。
Linuxシステムのバックアップ計画を立てられる。
詳細	
バックアップに含める必要があるディレクトリについて決定できる。
Amanda、Bacula、Bareos、BackupPCなどのネットワークバックアップソリューションについて知っている。
バックアップ対象として、ファイル、ブロック、イメージを使い分けられる。
テープ、ハードディスク、光メディアまたはその他のバックアップメディアを選択できる。
容量、保存期間、ライトワンス、シーケンシャル/ランダムアクセス
完全バックアップ、差分バックアップ、増分バックアップを使い分けられる。
バックアップファイルの整合性を確認する。
バックアップを部分的または完全に復元する。
dd, tar, /dev/st*, /dev/nst*, mt, rsync
2.04.3 ユーザへの通知

---

重要度	1
概要	現在発生しているシステム関連の問題についてユーザに通知できる。
詳細	
ログオンメッセージを使用してユーザへの通知を自動的に行う。
/etc/issue, /etc/issue.net, /etc/motd
アクティブなユーザにシステムの保守を通知する。
wall, shutdown, systemctl
2.04.4 リソース使用状況の把握

---

重要度	3
概要	ハードウェアリソースとネットワーク帯域幅の使用率を測定でき、リソースの問題を解決できる。
詳細	
CPU使用率を測定する。
top, htop, ps, sar
メモリ使用量を測定する。
vmstat, free, sar
ディスクI/Oを測定する。
iostat, iotop, sar
I/O 待ちのプロセス, blocks in, blocks out
ネットワークI/Oを測定する。
netstat, iftop, ss, sar
システムがオープンしているファイルやポートを表示する。
lsof
ファイアウォール機能とルーティングスループットを測定する。
クライアントの帯域幅使用率をマップする。
ネットワーキングを含むシステムにおいてスループットを推定し、ボトルネックを見つけ出す。
iptraf
2.04.5 死活監視、リソース監視、運用監視ツール

---

重要度	2
概要	
システム監視の重要性を理解している。
監視対象に応じて適切な監視手法を選択できる。
運用監視ツールの導入メリットと種類を理解し、適切にシステムを監視できる。
詳細	
システムの障害と予兆についての関連性を知っている。
リソースの枯渇、過負荷、異常停止、結果異常、OOMKiller
システムの死活、サービスの死活
死活監視の対象と手法
レスポンス、ログ監視（サーバー、サービス、プロセス、ネットワーク）
リソース監視の対象と手法
ログ監視、使用率監視（CPU、メモリ、ストレージ、通信量）、 SNMP
運用監視ツールによる監視作業の標準化と自動化
標準管理項目、標準のしきい値、標準のアラート方式
監視方式のパッケージ化、複数台の監視
主要な監視ツールを知っている。
Icinga2、Nagios、collectd、MRTG、Cacti、Zabbix
2.04.6 システム構成ツール

---

重要度	4
概要	
システム構成ツールの必要性を理解している。
システム構成ツールを使って、対象ホストの設定が行える。
詳細	
システム構成ツールの機能、メリットを知っている。
自動化の標準化, 効率化, スケール可能, 冪等性
Ansible の構成要素を理解している。
インベントリ、モジュール、Playbook
システムの構成変更を自動化する。
仮想サーバー・コンテナの払い出し
アプリケーションのリリース
ネットワーク機器のステータス取得・設定変更
自動化のためのファイルとツール
Playbook, YAML
ansible, ansible-playbook
主題2.05：仮想化サーバー
2.05.1 仮想マシンの仕組みとKVM

---

重要度	3
概要	基本的な仮想マシンの仕組みについて理解し、KVMを導入して仮想マシンの実行環境を構築できる。
詳細	
仮想マシンの基本について知っている。
ホスト型とハイパーバイザー型（KVM, VirtualBox, Xen）
コンピューターリソース（CPU、メモリ、ストレージ、ネットワーク）の仮想化
KVMを導入し、仮想マシンが稼働するための環境構築および設定ができる。
QEMU
仮想化支援技術（vmxとsvm）
/proc/cpuinfo, lscpu
KVMモジュール（kvm-intelとkvm-amd）
libvirtd
virt-manager
ネットワークの構成（bridge-utils）
2.05.2 仮想マシンの作成と管理

---

重要度	3
概要	各種ツールを使って、仮想マシンを作成し、起動や停止ができる。
詳細	
仮想マシンを作成し、OSをインストールする。
virt-manager, virt-install, 完全仮想化と準仮想化（virtio）
仮想マシンを起動、停止する。
virt-manager, virsh
パフォーマンスを監視する。
virt-manager
主題2.06：コンテナ
2.06.1 コンテナの仕組み

---

重要度	2
概要	基本的なコンテナの仕組みについて理解している。
詳細	
物理マシン、仮想マシン、コンテナの特徴と違いを理解している。
コンテナのファイルシステムとイメージの関係を知っている。
コンテナを実現する技術の概念を知っている。
名前空間, cgroups
2.06.2 Dockerコンテナとコンテナイメージの管理

---

重要度	3
概要	
Dockerを導入してコンテナ実行環境を構築できる。
Dockerコンテナを実行できる。
コンテナイメージを管理できる。
詳細	
Dockerを導入して、ネットワークを構成する。
ポート変換, フラットL2ネットワーク
Dockerコンテナを実行して、停止する。
docker ps/stats, docker run/create/restart, docker pause/unpause, docker stop/kill, docker rm
Dockerコンテナに接続してプロセスを実行する。
docker attach, docker exec
コンテナイメージを管理する。
Dockerレジストリ: docker images, docker pull, docker rmi, docker import
Dockerfile: docker build, docker commit
