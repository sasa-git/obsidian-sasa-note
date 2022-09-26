$ lsblk
NAME        MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
nvme0n1     259:1    0   20G  0 disk
└─nvme0n1p1 259:2    0   20G  0 part /
nvme1n1     259:0    0  2.1T  0 disk /data

ディスクの容量は増えた。
パーティションは切ってないから、パーティションの拡張は必要ないっぽい？
$ lsblk
NAME        MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
nvme0n1     259:1    0  20G  0 disk
└─nvme0n1p1 259:2    0  20G  0 part /
nvme1n1     259:0    0   3T  0 disk /data

ファイルシステムの拡張はまだ
$ df -hT
ファイルシス   タイプ   サイズ  使用  残り 使用% マウント位置
/dev/nvme0n1p1 xfs         20G   11G  9.8G   52% /
devtmpfs       devtmpfs    16G     0   16G    0% /dev
tmpfs          tmpfs       16G     0   16G    0% /dev/shm
tmpfs          tmpfs       16G  488K   16G    1% /run
tmpfs          tmpfs       16G     0   16G    0% /sys/fs/cgroup
/dev/nvme1n1   xfs        2.1T  1.7T  449G   79% /data
tmpfs          tmpfs      3.1G     0  3.1G    0% /run/user/14545

指定したデバイスのパーティションテーブルを一覧表示する
$ sudo fdisk -l /dev/nvme1n1

Disk /dev/nvme1n1: 3328.6 GB, 3328599654400 bytes, 6501171200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O サイズ (最小 / 推奨): 512 バイト / 512 バイト

ファイルシステムの拡張を行う
$ sudo xfs_growfs /dev/nvme1n1
meta-data=/dev/nvme1n1           isize=512    agcount=11, agsize=52428800 blks
         =                       sectsz=512   attr=2, projid32bit=1
         =                       crc=1        finobt=0 spinodes=0
data     =                       bsize=4096   blocks=550502400, imaxpct=25
         =                       sunit=0      swidth=0 blks
naming   =version 2              bsize=4096   ascii-ci=0 ftype=1
log      =internal               bsize=4096   blocks=102400, version=2
         =                       sectsz=512   sunit=0 blks, lazy-count=1
realtime =none                   extsz=4096   blocks=0, rtextents=0
data blocks changed from 550502400 to 812646400
↑変わったっぽい

改めて確認。増えてる！
$ df -hT
ファイルシス   タイプ   サイズ  使用  残り 使用% マウント位置
/dev/nvme0n1p1 xfs         20G   11G  9.8G   52% /
devtmpfs       devtmpfs    16G     0   16G    0% /dev
tmpfs          tmpfs       16G     0   16G    0% /dev/shm
tmpfs          tmpfs       16G  488K   16G    1% /run
tmpfs          tmpfs       16G     0   16G    0% /sys/fs/cgroup
/dev/nvme1n1   xfs        3.1T  1.7T  1.5T   54% /data
tmpfs          tmpfs      3.1G     0  3.1G    0% /run/user/14545


$ sudo blkid
/dev/nvme1n1: UUID="a375bf9e-249e-4106-a9d0-fd39df47b270" TYPE="xfs"
/dev/nvme0n1p1: UUID="ef6ba050-6cdc-416a-9380-c14304d0d206" TYPE="xfs"
/dev/nvme0n1: PTTYPE="dos"
$ cat /etc/fstab

```/etc/fstab
#
# /etc/fstab
# Created by anaconda on Mon Feb 22 17:08:22 2016
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=ef6ba050-6cdc-416a-9380-c14304d0d206 /                       xfs     defaults,noatime        0 0
#/dev/nvme2n1       /data   xfs    defaults,noatime,nofail        0       2
# /dev/nvme1n1
UUID="a375bf9e-249e-4106-a9d0-fd39df47b270"       /data   xfs    defaults,noatime,nofail        0       2
```

↑は自動マウントの設定
https://qiita.com/suisuina/items/7b55a640fdd6b299aa46
