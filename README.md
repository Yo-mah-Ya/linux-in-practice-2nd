# linux-in-practice-2nd

「Linux のしくみ 増補改訂版」の実験コードです

# 実験プログラム実行環境の作成

お手元の Ubuntu 20.04 環境で本書の実験プログラムを実行する際は、以下のコマンドを実行して必要パッケージのインストールおよびユーザ設定をしてください。

```console
$ sudo apt update && sudo apt install binutils build-essential golang sysstat python3-matplotlib python3-pil fonts-takao fio qemu-kvm virt-manager libvirt-clients virtinst jq docker.io containerd libvirt-daemon-system
$ sudo adduser `id -un` libvirt
$ sudo adduser `id -un` libvirt-qemu
$ sudo adduser `id -un` kvm
```

# その他参考資料

https://learning.lpi.org/ja/learning-materials/learning-materials/
