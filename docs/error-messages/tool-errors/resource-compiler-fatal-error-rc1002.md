---
title: リソース コンパイラの致命的なエラー RC1002
ms.date: 11/04/2016
f1_keywords:
- RC1002
helpviewer_keywords:
- RC1002
ms.assetid: b43dfece-0dc3-4d0b-9d8f-509699b9ae80
ms.openlocfilehash: 0804e7db92355c023e4f9f1dbef8d9194caa3718
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297742"
---
# <a name="resource-compiler-fatal-error-rc1002"></a>リソース コンパイラの致命的なエラー RC1002

ヒープ スペースがありません。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>以下の可能性がある解決策を使って修正するには

1. Windows のスワップ ファイルの領域を増やします。 スワップ ファイルの領域を増やす方法の詳細については、Windows のヘルプ内の仮想メモリを参照してください。

1. 小さなファイルに、現在のファイルに分割し、個別にコンパイルします。

1. その他のプログラムまたはシステムで実行されているドライバーを削除します。