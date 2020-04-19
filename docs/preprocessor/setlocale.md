---
title: setlocale プラグマ
ms.date: 08/29/2019
f1_keywords:
- setlocale_CPP
- vc-pragma.setlocale
helpviewer_keywords:
- pragmas, setlocale
- setlocale pragma
ms.assetid: e60b43d9-fbdf-4c4e-ac85-805523a13b86
ms.openlocfilehash: 219354595e5c63b2f13211d43bfa517d97413251
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218176"
---
# <a name="setlocale-pragma"></a>setlocale プラグマ

ワイド文字定数とリテラル文字列を変換するときに使用する*ロケール*、国、地域、および言語を定義します。

## <a name="syntax"></a>構文

> **#pragma setlocale ("** [ *locale-string* ] **")**

## <a name="remarks"></a>Remarks

マルチバイト文字をワイド文字に変換するためのアルゴリズムはロケールによって異なる場合があります。また、コンパイルは実行可能ファイルを実行する別のロケールで実行される可能性があるため、このプラグマを使用すると、コンパイル時にターゲットロケールを指定することができます。 これは、ワイド文字列が正しい形式で格納されることを保証します。

既定の*ロケール文字列*は "" です。

"C" ロケールでは、文字列内の各文字が**wchar_t**として値にマップされます。 の`setlocale`その他の有効な値は、[[言語文字列](../c-runtime-library/language-strings.md)] ボックスの一覧にあるエントリです。 たとえば、次のように指定できます。

```cpp
#pragma setlocale("dutch")
```

言語文字列を指定する機能は、お使いのコンピューターのコードページと言語 ID のサポートによって異なります。

## <a name="see-also"></a>関連項目

[プラグマディレクティブと __ プラグマキーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
