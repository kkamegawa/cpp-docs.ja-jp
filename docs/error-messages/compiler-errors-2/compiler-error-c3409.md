---
title: コンパイラ エラー C3409
ms.date: 11/06/2018
f1_keywords:
- C3409
helpviewer_keywords:
- C3409
ms.assetid: e372d9fa-230c-4b28-b6d3-6ad81ccf9dbb
ms.openlocfilehash: 24f107e0c1f74f95afc521c8a4c888a26a35c13a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173393"
---
# <a name="compiler-error-c3409"></a>コンパイラ エラー C3409

> 属性ブロックを空にすることはできません。

## <a name="remarks"></a>Remarks

角かっこ、コンパイラによってとして解釈されていましたが[属性](../../windows/attributes-alphabetical-reference.md)どの属性も、ブロックが見つかりました。

ラムダ式の定義の一部としての角かっこを使用すると、コンパイラはこのエラーを生成可能性があります。 このエラーは、コンパイラは角かっこまたは属性ブロック、ラムダ式の定義の一部であるかどうかを判断できないときに発生します。 ラムダ式について詳しくは、「[ラムダ式](../../cpp/lambda-expressions-in-cpp.md)」をご覧ください。

### <a name="to-correct-this-error"></a>このエラーを解決するには

1. 角かっこが属性ブロックの一部である場合。

   1. 属性ブロック内の 1 つまたは複数の属性を提供します。

   1. 属性ブロックを削除します。

1. 角かっこがラムダ式の一部である場合は、ラムダ式が有効な構文規則に従うことを確認します。

   ラムダ式の構文の詳細については、次を参照してください。[ラムダ式の構文](../../cpp/lambda-expression-syntax.md)します。

## <a name="example"></a>例

次の例では、C3409 を生成します。

```cpp
// C3409.cpp
// compile with: /c
#include <windows.h>
[]   // C3409
class a {};

// OK
[object, uuid("00000000-0000-0000-0000-000000000000")]
__interface x {};

[coclass, uuid("00000000-0000-0000-0000-000000000001")]
class b : public x {};
```

## <a name="example"></a>例

ラムダ式を使用するために次の例が c3409、`mutable`仕様では、パラメーター リストは提供されません。 コンパイラは、角かっこまたは属性ブロック、ラムダ式の定義の一部であるかどうかを判断できません。

```cpp
// C3409b.cpp

int main()
{
   [] mutable {}();
}
```

## <a name="see-also"></a>関連項目

[attribute](../../windows/attributes-alphabetical-reference.md)<br/>
[ラムダ式](../../cpp/lambda-expressions-in-cpp.md)<br/>
[ラムダ式の構文](../../cpp/lambda-expression-syntax.md)