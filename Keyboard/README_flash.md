# Keyboard
自作キーボードのコード管理リポジトリ
【QMKコンパイル・フラッシュ手順書】


元の手順書はこちら
https://docs.qmk.fm/#/ja/newbs

QMK MSYSをインストールしたらqmk setup

これ以下ではサリチル酸さん作のnafudaを例にする。

元々用意されているキーマップなどは
C:\Users\[ホームディレクトリ]\qmk_firmware\keyboards\salicylic_acid3\nafuda\keymaps\default
などに入っている。変更を加えるにはこのdefaultディレクトリを複製して開発すれば良い。

defaultをコピーするとディレクトリ内にkeymap.cがあるのでそれに変更を加える。
同変更すればいいかわからないときは他のキーボードのdefaultソースコードを参考にできる。

変更を加えたらキーマップをコンパイルする。
qmk_firmwareディレクトリに移動して
qmk compile -kb salicylic_acid3/nafuda -km custom(defaultを変更したディレクトリ)
ちなみに
-kb keyboardsフォルダ
-km keymapフォルダ
をそれぞれ意味する。

コンパイルすると
qmk_firmware直下に.hexファイルが出力される。これがキー配列を決定する実体。
defaultをコピーしたcustomディレクトリをいじった今回の例では
C:\Users\[ホームディレクトリ]\qmk_firmware\salicylic_acid3_nafuda_custom.hex
が生成された。

このファイルをqmktool boxでopen-->flashする。

フラッシュに必要なqmk toolはこちら
https://github.com/qmk/qmk_toolbox/releases/tag/0.1.1

qmk toolsはショートさせてからちょっとしてから5秒間だけフラッシュできる。
ショートのさせ方は各種マイコンの仕様書を見てほしい。Pro Microの場合はGNDとRSTを金属などでつなげばよい。
フラッシュボタンを押せない場合は再起動などを試してみる。

キーコード(マウスコードやLEDコードなど)
https://docs.qmk.fm/#/ja/keycodes

LEDの色選択について
https://docs.qmk.fm/#/ja/feature_rgblight?id=lighting-layers
