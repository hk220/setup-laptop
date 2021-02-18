# ~~マイクの特性~~

~~HP Envy x360 ag0000の内蔵マイクは、広範囲の音を拾いハウリングを起こしてしまう。~~

~~Windows には、Bang & Olufsen Audio Controlというノイズ除去（ノイズ・エコーキャンセリング）や音を拾う方向の調整ができるソフトウェアを入れることができた。~~

~~しかし、Linux には Bang & Olufsen Audio Control がなく、標準のオーディオドライバに同等の機能がないため、マイクの音量を調整するなどして対処しなければならない。~~

~~一応、PulseAudio に module-echo-cancelling というノイズ・エコーキャンセリングを実現するモジュールがあるが、このマシンでうまく動かない。~~

~~結論としては、USB ヘッドセットなどのオーディオインタフェースを別途使うべきである。~~

# Linux でのオーディオの入出力

マイク・スピーカーともアナログ入出力を使うべし。

# その後気がついたこと

JBL E45BT ヘッドフォンを有線で接続して、マイクのボリュームを上げていったところ、同じ問題が発生した。

ヘッドフォンのため、スピーカー部分とマイク部分は離れているため、ハウリングが発生するとは考えにくい。

~~そのため、HP Envy x360 ag0000 のオーディオインタフェースを正しく Linux が扱えていない疑いが出てきた。~~

# その後原因の確定と対策

原因は、PulseAudio が一定以上のボリューム調整の時にブーストの値を上げていたため。

もともと ALSA は、入力が小さいマイクを大きく（ブースト）するための機能であるマイクブースト機能を持っている。

この機能を使うと、音割れが発生することがある[^1]。

以下のコマンドを実行＆再起動[^2]して、PulseAudio でマイクブーストの値を変更しないようにしたところ、現象がなくなった。

```bash
sudo cp -vR /usr/share/pulseaudio/alsa-mixer/paths /usr/share/pulseaudio/alsa-mixer/paths_backup
sudo perl -pi -0 -e 's/(\[[A-Za-z ]*Mic Boost\][A-Za-z._=\s-]+volume *= *)merge/\1zero/g;' /usr/share/pulseaudio/alsa-mixer/paths/*
sudo diff -r -C 5 /usr/share/pulseaudio/alsa-mixer/paths_backup /usr/share/pulseaudio/alsa-mixer/paths
```

また、再起動時に自動的に音量調整がされるとつらいので、`/etc/pulse/default.pa`の以下をコメントアウトする。

```bash
# load-module module-device-restore
# load-module module-stream-restore
# load-module module-card-restore
```

再起動して、alsamixerで音量を調整してalsaに保存する。

```bash
sudo alsamixer
sudo alsactl store
```

再起動して、ボリュームが保持されることを確認する。

[^1]: https://wiki.archlinux.jp/index.php/PulseAudio/%E3%83%88%E3%83%A9%E3%83%96%E3%83%AB%E3%82%B7%E3%83%A5%E3%83%BC%E3%83%86%E3%82%A3%E3%83%B3%E3%82%B0#.E9.9F.B3.E9.87.8F.E3.81.AE.E8.87.AA.E5.8B.95.E5.A4.89.E6.9B.B4.E3.81.AB.E3.82.88.E3.81.A3.E3.81.A6.E3.83.9E.E3.82.A4.E3.82.AF.E3.81.AE.E9.9F.B3.E3.81.8C.E3.81.8A.E3.81.8B.E3.81.97.E3.81.8F.E3.81.AA.E3.82.8B

[^2]: https://nzeid.net/pulseaudio-disable-auto-volume
