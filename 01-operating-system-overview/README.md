# システム起動順序

https://milestone-of-se.nesuke.com/sv-basic/architecture/mbr-gpt/

1. コンピュータの電源を入れる
2. mother board の SPI flash に格納された Legacy BIOS ( or UEFI) がメモリ上に展開される。
3. Legacy BIOS や UEFI などの firmware が起動して hardware を初期化する
4. Legacy BIOS から MBR を読み取り、もしくは UEFI から MBR もしくは GPT を読み取り
5. HDD/SSD の boot sector から GRUB や Windows Boot Manager などの boot loader をメモリに展開する。
6. boot loader が OS kernel を起動する。ここでは Linux Kernel とする。
7. Linux kernel が init process を起動する。
8. init process が 子プロセスを起動し... tree structure を作成する。

# MBR

4. Legacy BIOS から MBR を読み取り、もしくは UEFI から MBR もしくは GPT を読み取り

- MBR の中にある一次 boot loader がメモリに読み込まれ、起動可能 flag のあるパーティションの先頭セクタ (PBR: Partition Boot Recorder) を読み込む
- PBR が 2 次 boot loader である GRUB や Windows Boot Manager などを呼び出し、そこから OS を起動する。

5. GRUB や Windows Boot Manager などの boot loader を起動する。

- ESP (EFI System Partition) は FAT でフォーマットされたファイルシステムであり、その中に GRUB や Windows Boot Manager、各種 OS ブート素材が含まれている。
- UEFI から GPT が読み込まれると、ESP が検索され、見つけた ESP から boot loader を実行し、OS を起動する。
