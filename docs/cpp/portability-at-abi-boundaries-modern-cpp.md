---
title: ABI の境界での移植性
description: バイナリC++インターフェイスの境界で、C の呼び出し規約にインターフェイスを平坦化します。
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: abbd405e-3038-427c-8c24-e00598f0936a
ms.openlocfilehash: b3b2b217739ff5900c8ef0329ff3e8909a3fe036
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303317"
---
# <a name="portability-at-abi-boundaries"></a>ABI の境界での移植性

バイナリインターフェイスの境界では、十分に移植可能な型と規約を使用します。 "移植可能な型" は、C の組み込み型、または C の組み込み型のみを含む構造体です。 クラス型は、呼び出し元と呼び出し先がレイアウト、呼び出し規約などに同意する場合にのみ使用できます。これは、両方が同じコンパイラとコンパイラの設定でコンパイルされている場合にのみ可能です。

## <a name="how-to-flatten-a-class-for-c-portability"></a>C の移植性のためにクラスを平坦化する方法

呼び出し元が別のコンパイラ/言語でコンパイルされる場合は、特定の呼び出し規約で**extern "C"** API を "平坦化" します。

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

## <a name="see-also"></a>参照

[に戻るC++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 言語リファレンス](../cpp/cpp-language-reference.md)<br/>
[C++ 標準ライブラリ](../standard-library/cpp-standard-library-reference.md)
