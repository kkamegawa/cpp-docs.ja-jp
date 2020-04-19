---
title: コンパイラ エラー C3293
ms.date: 07/21/2017
f1_keywords:
- C3293
helpviewer_keywords:
- C3293
ms.assetid: b772cf98-52e0-4e24-be23-1f5d87d999ac
ms.openlocfilehash: 1713632d21ef401fb1177350c81a4a64ed0503ec
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760115"
---
# <a name="compiler-error-c3293"></a>コンパイラ エラー C3293

'accessor': クラス'type' の既定のプロパティ (インデクサー) にアクセスするには 'default' を使用してください

インデックス付きプロパティへのアクセスが正しくありません。  詳細については、「[方法:/cli でC++プロパティを使用する](../../dotnet/how-to-use-properties-in-cpp-cli.md)」を参照してください。

**Visual studio 2017 以降**: visual studio 2015 以前では、コンパイラは既定のインデクサーとして既定のプロパティを誤っ場合がありました。 識別子 "default" を使用してプロパティにアクセスすることで、この問題を回避できました。 C++11 で default がキーワードとして導入された後は、この回避策自体が問題になりました。 そのため、Visual Studio 2017 では、この回避策を必要とするバグが修正され、クラスの既定のプロパティにアクセスするために "default" が使用された場合は、コンパイラがエラーを発生させるようになりました。

## <a name="example"></a>使用例

次の例では、Visual Studio 2015 以前で C3293 が生成されます。

```cpp
// C3293.cpp
// compile with: /clr /c
using namespace System;
ref class IndexerClass {
public:
   // default indexer
   property int default[int] {
      int get(int index) { return 0; }
      void set(int index, int value) {}
   }
};

int main() {
   IndexerClass ^ ic = gcnew IndexerClass;
   ic->Item[0] = 21;   // C3293 in VS2015 OK in VS2017
   ic->default[0] = 21;   // OK in VS2015 and earlier

   String ^s = "Hello";
   wchar_t wc = s->Chars[0];   // C3293 in VS2015 OK in VS2017
   wchar_t wc2 = s->default[0];   // OK in VS2015 and earlier
   Console::WriteLine(wc2);
}
```
