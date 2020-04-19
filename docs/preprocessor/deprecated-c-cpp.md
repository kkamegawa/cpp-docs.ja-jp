---
title: 非推奨のプラグマ
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.deprecated
- deprecated_CPP
helpviewer_keywords:
- deprecated pragma
- pragmas, deprecated
ms.assetid: 9c046f12-7875-499a-8d5d-12f8642fed2d
ms.openlocfilehash: 2e76d1c53cb900c108e2839a9aad17b330143a5d
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222406"
---
# <a name="deprecated-pragma"></a>非推奨のプラグマ

**deprecated**プラグマを使用すると、関数、型、またはその他の識別子が将来のリリースでサポートされなくなる可能性があるか、使用できなくなることを示すことができます。

> [!NOTE]
> C++ 14 `[[deprecated]]`属性の詳細と、Microsoft `__declspec(deprecated)`修飾子または**非推奨**のプラグマではなくこの属性を使用する場合のガイダンスについては、「 [」のC++「属性](../cpp/attributes.md)」を参照してください。

## <a name="syntax"></a>構文

> **#pragma 非推奨 (** *identifier1* [ **,** *identifier2* ...] **)**

## <a name="remarks"></a>Remarks

コンパイラがで指定された識別子を検出した場合、**deprecated**プラグマ、コンパイラの警告を発行[C4995](../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md)します。

マクロ名の使用を避けることができます。 マクロ名を引用符で囲んで配置します。そうしないと、マクロ展開が発生します。

**deprecated**プラグマは、すべての一致する識別子で機能し、アカウントに署名を受け取らない、オーバー ロードされた関数の特定のバージョンを非推奨の最適なオプションではありません。 スコープ内にある一致する関数名は、警告をトリガーします。

C++ 14 を使用することをお勧めします。`[[deprecated]]`属性は、可能であれば、の代わりに、**deprecated**プラグマ。 Microsoft 固有[__declspec(deprecated)](../cpp/deprecated-cpp.md)宣言修飾子はより多くの場合の方が適切でも、**deprecated**プラグマ。 `[[deprecated]]`属性と`__declspec(deprecated)`修飾子を使用すると、オーバー ロードされた関数の特定のフォームの非推奨のステータスを指定できます。 診断の警告のみに表示されます、特定のオーバー ロードされた関数への参照属性または修飾子に適用されます。

## <a name="example"></a>例

```cpp
// pragma_directive_deprecated.cpp
// compile with: /W3
#include <stdio.h>
void func1(void) {
}

void func2(void) {
}

int main() {
   func1();
   func2();
   #pragma deprecated(func1, func2)
   func1();   // C4995
   func2();   // C4995
}
```

次のサンプルでは、クラスの使用を避ける方法を示します。

```cpp
// pragma_directive_deprecated2.cpp
// compile with: /W3
#pragma deprecated(X)
class X {  // C4995
public:
   void f(){}
};

int main() {
   X x;   // C4995
}
```

## <a name="see-also"></a>関連項目

[プラグマディレクティブと __ プラグマキーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
