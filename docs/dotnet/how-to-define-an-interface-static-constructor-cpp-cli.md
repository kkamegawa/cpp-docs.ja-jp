---
title: '方法: インターフェイス静的コンス トラクターの定義 (C +/cli CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- constructors [C++]
- static constructors, interface
- interface static constructor
ms.assetid: 1f031cb2-e94f-43dc-819b-44cf2faaaa49
ms.openlocfilehash: 326b315e1e6c4defbef3ab6e487c78635e0aa50f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378980"
---
# <a name="how-to-define-an-interface-static-constructor-ccli"></a>方法: インターフェイス静的コンス トラクターの定義 (C +/cli CLI)

インターフェイス静的コンス トラクター、静的データ メンバーを初期化するために使用することができます。  静的コンス トラクターは、最大で 1 回呼び出されが初めての静的なインターフェイス メンバーにアクセスする前に呼び出されます。

## <a name="example"></a>例

```
// mcppv2_interface_class2.cpp
// compile with: /clr
using namespace System;

interface struct MyInterface {
   static int i;
   static void Test() {
      Console::WriteLine(i);
   }

   static MyInterface() {
      Console::WriteLine("in MyInterface static constructor");
      i = 99;
   }
};

ref class MyClass : public MyInterface {};

int main() {
   MyInterface::Test();
   MyClass::MyInterface::Test();

   MyInterface ^ mi = gcnew MyClass;
   mi->Test();
}
```

```Output
in MyInterface static constructor
99
99
99
```

## <a name="see-also"></a>関連項目

[interface クラス](../extensions/interface-class-cpp-component-extensions.md)
