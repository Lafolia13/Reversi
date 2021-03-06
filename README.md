# Reverci

## Build

`docker-compose up -d`

## Description

Web 上で動作するリバーシプログラムです。
フロントエンドに Vue.js を、バックエンドに golang を使用しています。 <br>
また、CPU プログラムは C++ で記述し、実行ファイルを golang 内で実行しています。

## pure_vue

CSS フレームワークを使用せず、Vue.js のみで描画しています。

build と同時に動作します。

## var_bootstrap

BootstrapVue を使用しています。

実用上の利便性のため、build ではコンテナのみ立ち上がり、サーバは起動されません。

## Background

このアプリケーションは、高専プロコン競技部門の解法プログラムの開発について習熟するため作成されました。

競技部門では、与えられた問題の解法プログラムと (非本質ではありますが) 問題についてのビジュアライザが求められます。 <br>
解法プログラムは場合によっては並列に動作させることが考えられ、結果的に以下の 3 つの要素が必要になります。

1. 描画部

1. 計算部

1. 集計部

本アプリケーションは、描画部を Vue.js、計算部を C++、集計部を golang でそれぞれ独立に実装し、
描画部から計算に使用するプログラムを選択し集計部に送信、
集計部で受信された計算プログラムをサブプロセスとして実行し、計算結果を反映させ、描画部に返しています。