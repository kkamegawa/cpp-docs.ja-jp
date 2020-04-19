---
title: 致命的なエラー C1308
ms.date: 11/04/2016
f1_keywords:
- C1308
helpviewer_keywords:
- C1308
ms.assetid: 46177997-069e-433a-8e20-93c846d78ffd
ms.openlocfilehash: 95e13a6914b5e02441f95dd2256532dbd1d718e5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747021"
---
# <a name="fatal-error-c1308"></a>致命的なエラー C1308

アセンブリのリンクはサポートされていません

.Netmodule はリンカーへの入力として許可されていますが、アセンブリが指定されていません。 このエラーは、`/clr:safe`でコンパイルしたアセンブリをリンクしようとしたときに生成されます。

詳細については、「 [リンカー入力としての .netmodule ファイル](../../build/reference/netmodule-files-as-linker-input.md)」を参照してください。

次の例では、C1308 が生成されます。

```cpp
// C1308.cpp
// compile with: /clr:safe /LD
public ref class MyClass {
public:
   int i;
};
```

それから

```cpp
// C1308b.cpp
// compile with: /clr /link C1308b.obj C1308.dll
// C1308 expected
#using "C1308.dll"
int main() {
   MyClass ^ my = gcnew MyClass();
}
```
