---
title: リソース コンパイラの致命的なエラー RC1015
ms.date: 11/04/2016
f1_keywords:
- RC1015
helpviewer_keywords:
- RC1015
ms.assetid: 23f187e1-5538-40b5-9042-edd2888f55c2
ms.openlocfilehash: f20101c2edc4da132c89dcda451c71af2304a13d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297659"
---
# <a name="resource-compiler-fatal-error-rc1015"></a>リソース コンパイラの致命的なエラー RC1015

インクルード ファイル 'filename' を開くことはできません。

指定したインクルード ファイルが存在しないかを開けませんでしたが見つかりませんでした。

環境設定が有効であることと、ファイルの正しいパスを指定していることを確認してください。 十分なファイル ハンドルがリソース コンパイラを使用できることを確認します。 ファイルがネットワーク ドライブ上にある場合は、ファイルを開く権限があることを確認します。

-> リソースの構成のプロパティで追加のインクルード ディレクトリとして指定されたディレクトリのインクルード ファイルが存在する場合でも、RC1015 が発生することが [全般] プロパティ ページ ->インクルード ファイルへの完全パスを指定します。
