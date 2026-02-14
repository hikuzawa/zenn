---
title: "iOSアプリをwindows環境からリリースする手順まとめ"
emoji: "🌊"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["iOS", "Windows", "App Store"]
published: false
---

## はじめに

iOSアプリをWindows環境からリリースする手順をまとめました。

## 前提条件

- Apple Developer Programの登録済み
- FlutterでiOSアプリを開発している

## 1.Antigravityを使って開発
基本的にはAntigravityをwindows環境で使用し、FlutterでiOSアプリを開発します。
この時にiOSデバイスシュミレーターは使用できないので、Andorid端末かブラウザで動作の確認をします。
url: https://www.antigravity.com/ja/

## 2.実機テスト
ある程度シュミレータやブラウザでの動作が確認できたら、次は実機での確認をしていきます。
自分はiPhone端末しか持っていないので、iPhoneにインストールします。
自分の端末分のスクリーンショットは撮ることができますが、Andoroidであれば、Windows端末から、iOS向けなら後述するサービスを使えば撮影できるので、そちらでまとめて撮影した方が手っ取り早いかもしれません。

## 3.Macinecloud Portal
### windows環境で開発している方向けにクラウド上でMacを借りれるサービス
このサービスで借りたMacを使って、iOS端末のスクリーンショットの作成をします。
url: https://portal.macincloud.com/

## 