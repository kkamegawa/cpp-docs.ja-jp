---
title: 致命的なエラー C1047
ms.date: 11/04/2016
f1_keywords:
- C1047
helpviewer_keywords:
- C1047
ms.assetid: e1bbbc6b-a5bc-4c23-8203-488120a0ec78
ms.openlocfilehash: 053c4d828b3583d0e16ab8f4fe03a4b0bbed96f9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62243760"
---
# <a name="fatal-error-c1047"></a>致命的なエラー C1047

オブジェクトまたはライブラリ ファイル 'file' は、他のオブジェクトよりも古いコンパイラで作成されました。古いオブジェクトおよびライブラリをリビルドしてください

C1047 は、 **/LTCG** を指定してビルドされたオブジェクト ファイルまたはライブラリがリンクされるときに、それらのオブジェクト ファイルまたはライブラリが、異なるバージョンの Visual C++ ツールセットでビルドされている場合に発生します。

これは、新しいバージョンのコンパイラの使用を開始するときに、既存のオブジェクト ファイルまたはライブラリをクリーンにリビルドしない場合に発生することがあります。

C1047 を解決するには、オブジェクト ファイルまたはライブラリをすべてリビルドします。