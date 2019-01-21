---
title: ABI の境界での移植性 (Modern C++)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: abbd405e-3038-427c-8c24-e00598f0936a
ms.openlocfilehash: 3f72bc32e436c2f7a2f76ed6bbb9553b5e5be6b8
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220310"
---
# <a name="portability-at-abi-boundaries-modern-c"></a>ABI の境界での移植性 (Modern C++)

バイナリ インターフェイス境界で十分に移植可能な型と規則を使用します。 「移植可能な型」は、C の組み込み型または C の組み込み型のみを含む構造体です。 クラス型は、呼び出し元と呼び出し先、呼び出し規則などのレイアウト、同意。 場合にのみ使用できます。これは、両方のコンパイラ設定と同じコンパイラでコンパイル時にのみ可能です。

## <a name="how-to-flatten-a-class-for-c-portability"></a>C の移植性のためのクラスをフラット化する方法

呼び出し元が別のコンパイラ/言語でコンパイルすることがあり、に「フラット化」、 **extern"C"** 特定の呼び出し規約を使用した API:

```cpp
// class widget {
//   widget();
//   ~widget();
//   double method( int, gadget& );
// };
extern "C" {        // functions using explicit "this"
   struct widget;   // opaque type (forward declaration only)
   widget* STDCALL widget_create();      // constructor creates new "this"
   void STDCALL widget_destroy(widget*); // destructor consumes "this"
   double STDCALL widget_method(widget*, int, gadget*); // method uses "this"
}
```

## <a name="see-also"></a>関連項目

[C++ へようこそ (Modern C++)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 言語リファレンス](../cpp/cpp-language-reference.md)<br/>
[.NET 標準ライブラリ](../standard-library/cpp-standard-library-reference.md)
