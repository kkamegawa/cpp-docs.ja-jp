---
title: リソース コンパイラの致命的なエラー RC1120
ms.date: 11/04/2016
f1_keywords:
- RC1120
helpviewer_keywords:
- RC1120
ms.assetid: 4e462931-e42e-42e3-8bfc-847677194286
ms.openlocfilehash: eff46ddee118c3355e548c73220b407db0561e36
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374256"
---
# <a name="resource-compiler-fatal-error-rc1120"></a>リソース コンパイラの致命的なエラー RC1120

メモリ不足に必要なバイト数です。

リソース コンパイラは、ストレージ、ヒープに格納されたアイテムの不足になりました。 通常、これは、シンボルが多すぎる場合の結果です。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>以下の可能性がある解決策を使って修正するには

1. Windows のスワップ ファイルの領域を増やします。 スワップ ファイルの領域を増やす方法の詳細については、Windows のヘルプ内の仮想メモリを参照してください。

1. 不要インクルード ファイル、特に不要な`#define`s と関数のプロトタイプ。

1. 2 つ以上のファイルに、現在のファイルに分割し、個別にコンパイルします。

1. 他のプログラムや、システムでは、大量のメモリを消費する可能性がありますで実行されているドライバーを削除します。