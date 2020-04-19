---
title: コンパイラ エラー C3366
ms.date: 11/04/2016
f1_keywords:
- C3366
helpviewer_keywords:
- C3366
ms.assetid: efc55bcf-c16d-43c1-a36f-87a6165fa2a8
ms.openlocfilehash: 5173b1c0df7de6a4e8d9993e680b961a82bb10a7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738467"
---
# <a name="compiler-error-c3366"></a>コンパイラ エラー C3366

' variable ': マネージ型または WinRTtypes の静的データメンバーは、クラス定義内で定義されなければなりません

WinRT または .NET のクラスまたはインターフェイスの静的メンバーをそのクラスまたはインターフェイスの定義外で参照しようとしました。

コンパイラは、(1 回のパスの後に、メタデータを出力するために) クラスの完全定義を認識する必要があり、静的データ メンバーをクラス内で初期化する必要があります。

たとえば、次の例では、C3366 を生成し、その修正方法を示しています。

```cpp
// C3366.cpp
// compile with: /clr /c
ref class X {
   public:
   static int i;   // initialize i here to avoid C3366
};

int X::i = 5;      // C3366
```
