---
title: 入出力の代替手段
ms.date: 05/07/2019
helpviewer_keywords:
- I/O [C++], alternatives
ms.assetid: 9f8401c7-d90d-4285-8918-63573df74a80
ms.openlocfilehash: b46ff242fc263be5069eb691dd0ea9e8fb00b0f9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455291"
---
# <a name="inputoutput-alternatives"></a>入出力の代替手段

Microsoft C++コンパイラでは、i/o プログラミングにいくつかの代替手段が用意されています。

- C ランタイム ライブラリの直接的なバッファーされない入出力。

- ANSI C ランタイム ライブラリのストリーム入出力。

- コンソールおよびポートの直接入出力。

- Microsoft Foundation Class ライブラリ。

- Microsoft C++ 標準ライブラリ。

iostream クラスは、バッファーされた書式設定テキストの入出力に役立ちます。 C++ プログラミング インターフェイスが必要であり、Microsoft Foundation Class (MFC) ライブラリを使用しない場合のバッファーされていない入出力またはバイナリ入出力にも役立ちます。 iostream クラスは、C ランタイム関数のオブジェクト指向の入出力の代替手段です。

iostream クラスは、Microsoft Windows オペレーティング システムで使用できます。 文字列とファイルのストリームは制限なしで動作しますが、文字モード ストリーム オブジェクト `cin`、`cout`、`cerr`、および `clog` には Windows グラフィカル ユーザー インターフェイスとの一貫性がありません。 また、Windows 環境と直接やり取りするカスタム ストリーム クラスを派生させることもできます。

## <a name="see-also"></a>関連項目

[ストリームとは何か](../standard-library/what-a-stream-is.md)
