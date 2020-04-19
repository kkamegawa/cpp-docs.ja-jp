---
title: リンカー ツールの警告 LNK4248
ms.date: 11/04/2016
f1_keywords:
- LNK4248
helpviewer_keywords:
- LNK4248
ms.assetid: e40523ff-e3cb-4ba6-ab79-23f0f339f6cf
ms.openlocfilehash: 4ba05ef067c539dc9c0aca6dc2a395748fd217a2
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988102"
---
# <a name="linker-tools-warning-lnk4248"></a>リンカー ツールの警告 LNK4248

' type ' の未解決の typeref トークン (トークン) です。イメージは実行されない可能性があります

型には、MSIL メタデータの定義がありません。

LNK4248 は、msil モジュール ( **/clr**でコンパイルされた) 内の型に対して、型が msil モジュールで参照され、その型の定義を持つネイティブモジュールに msil モジュールがリンクされている場合に発生する可能性があります。

この場合、リンカーは MSIL メタデータにネイティブ型定義を提供します。これにより、正しい動作が提供される可能性があります。

ただし、前方型宣言が CLR 型である場合、リンカーのネイティブ型定義が正しくない可能性があります。

詳細については、「[/clr (共通言語ランタイムのコンパイル)](../../build/reference/clr-common-language-runtime-compilation.md)」を参照してください。

### <a name="to-correct-this-error"></a>このエラーを解決するには

1. MSIL モジュールで型定義を指定します。

## <a name="example"></a>使用例

次の例では、LNK4248 が生成されます。 解決する構造体を定義します。

```cpp
// LNK4248.cpp
// compile with: /clr /W1
// LNK4248 expected
struct A;
void Test(A*){}

int main() {
   Test(0);
}
```

## <a name="example"></a>使用例

次の例には、型の事前定義が含まれています。

```cpp
// LNK4248_2.cpp
// compile with: /clr /c
class A;   // provide a definition for A here to resolve
A * newA();
int valueA(A * a);

int main() {
   A * a = newA();
   return valueA(a);
}
```

## <a name="example"></a>使用例

次の例では、LNK4248 が生成されます。

```cpp
// LNK4248_3.cpp
// compile with: /c
// post-build command: link LNK4248_2.obj LNK4248_3.obj
class A {
public:
   int b;
};

A* newA() {
   return new A;
}

int valueA(A * a) {
   return (int)a;
}
```
