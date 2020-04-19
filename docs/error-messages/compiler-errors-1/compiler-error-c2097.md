---
title: コンパイラ エラー C2097
ms.date: 11/04/2016
f1_keywords:
- C2097
helpviewer_keywords:
- C2097
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
ms.openlocfilehash: 8b50221997dcf2fb60ee2b82ed630dd325a38145
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377008"
---
# <a name="compiler-error-c2097"></a>コンパイラ エラー C2097

初期化が正しくありません。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>次のような原因をチェックして問題を解決するには

1. 非定数の値を使用して変数の初期化。

1. 長いアドレスを使用して短いアドレスを初期化します。

1. ローカル構造体、共用体、または非定数の式をコンパイルするときに配列の初期化 **/Za**します。

1. コンマ演算子を含む式で初期化します。

1. 初期化式は定数もシンボルを定義します。