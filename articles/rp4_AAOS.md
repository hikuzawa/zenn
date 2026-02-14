---
title: "RasberyPi4でAndroid Automotive OSを構築する"
emoji: "⛳"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["ガジェット"]
published: false
---

## はじめに
自分はナビすら付いていない平成27年式のデミオ(DE3FS)に乗っており、普段はFMトランスミッターで
スマホとBluetooth接続し、ラジオの帯域でスマホから再生した音楽を車内で聞いていました。
なぜか冬の時期だけ車があったまるまではノイズのようなものが毎回うるさいので、
ノイズ解消がてらRasberyPiでナビが作れないかと思い、色々調べると、Android Automotiveが良さげだったので取り組むことにしました。

## メインPC構成
- CPC | Raizen9
- メモリ | DDR4 3200 16G×2
- OS   | Windows

## WSL(Ubuntu20.02)
- メモリスワップ 60G

## WSL環境を作る
### WSLインストール
