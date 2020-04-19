---
title: コンパイラ エラー C2002
ms.date: 11/04/2016
f1_keywords:
- C2002
helpviewer_keywords:
- C2002
ms.assetid: 91982314-203a-4de1-b884-94e39a623f61
ms.openlocfilehash: 30f472aa7a9475a19eea0e92fe5c2ea0d54e382b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209037"
---
# <a name="compiler-error-c2002"></a>コンパイラ エラー C2002

無効なワイド文字定数

マルチバイト文字定数が無効です。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>次のような原因をチェックして問題を解決するには

1. ワイド文字定数には、予想よりも多くのバイト数が含まれています。

1. 標準ヘッダー STDDEF.h は含まれません。

1. ワイド文字は、通常のリテラル文字列と連結ことはできません。

1. 文字 'L' はワイド文字定数を前する必要があります。

    ```
    L'mbconst'
    ```

1. Microsoft C では、プリプロセッサ ディレクティブのテキストの引数は ASCII である必要があります。 たとえば、次のようなディレクティブがあると、`#pragma message(L"string")`が無効です。