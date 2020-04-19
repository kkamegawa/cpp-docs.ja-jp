---
title: nullptr
ms.date: 11/04/2016
f1_keywords:
- nullptr_cpp
helpviewer_keywords:
- nullptr keyword [C++]
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
ms.openlocfilehash: 57be8d71f1dac4f347ea6567c02a385719bb7306
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403491"
---
# <a name="nullptr"></a>nullptr

任意の生ポインター型に変換可能な `std::nullptr_t` 型の null ポインター定数を指定します。  キーワードを使用できますが、 **nullptr**コードは、型を使用する場合、ヘッダーを含めず`std::nullptr_t`、ヘッダーを含めることで定義する必要がありますし、`<cstddef>`します。

> [!NOTE]
>  **Nullptr**キーワードが c++ も定義されている/cli 用の CLI は、マネージ コード アプリケーションと、ISO 標準の C++ キーワードと互換性がありません。 場合を使用して、コードをコンパイルする場合があります、 [/clr](../build/reference/clr-common-language-runtime-compilation.md)マネージ コードを対象とするコンパイラ オプションを使用し、`__nullptr`で任意の行のコードは、コンパイラはネイティブな C++ 解釈を使用することを保証する必要があります。 詳細については、次を参照してください。 [nullptr](../extensions/nullptr-cpp-component-extensions.md)します。

## <a name="remarks"></a>Remarks

NULL または 0 を使用しないでください (`0`) として null ポインター定数です。**nullptr**悪用に対する脆弱性が減少し、ほとんどの状況でパフォーマンスが優れています。  たとえば、`func(std::pair<const char *, double>)` が指定されている場合に、`func(std::make_pair(NULL, 3.14))` を呼び出すとコンパイラ エラーが発生します。  NULL マクロは `0` に展開します。したがって、`std::make_pair(0, 3.14)` の呼び出しでは、func() の `std::pair<int, double>` パラメーター型に変換可能ではない `std::pair<const char *, double>` が返されます。  `func(std::make_pair(nullptr, 3.14))` は `std::make_pair(nullptr, 3.14)` に変換可能な `std::pair<std::nullptr_t, double>` を返すので、`std::pair<const char *, double>` の呼び出しは正常にコンパイルされます。

## <a name="see-also"></a>関連項目

[キーワード](../cpp/keywords-cpp.md)<br/>
[nullptr](../extensions/nullptr-cpp-component-extensions.md)(C +/cli CLI)