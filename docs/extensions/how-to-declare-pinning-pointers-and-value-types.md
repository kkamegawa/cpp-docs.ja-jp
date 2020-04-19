---
title: '方法: 固定ポインターと値型を宣言する'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- value types, declaring
- pinning pointers
ms.assetid: 57c5ec8a-f85a-48c4-ba8b-a81268bcede0
ms.openlocfilehash: 901980c76aac5dd364f2fa2fae0e007f5d25f3d8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515737"
---
# <a name="how-to-declare-pinning-pointers-and-value-types"></a>方法: 固定ポインターと値型を宣言する

値型を暗黙的にボックス化できます。 その後、値型オブジェクト自体への固定ポインターを宣言し、ボックス化された値型に対して **pin_ptr** を使用できます。

## <a name="example"></a>例

### <a name="code"></a>コード

```cpp
// pin_ptr_value.cpp
// compile with: /clr
value struct V {
   int i;
};

int main() {
   V ^ v = gcnew V;   // imnplicit boxing
   v->i=8;
   System::Console::WriteLine(v->i);
   pin_ptr<V> mv = &*v;
   mv->i = 7;
   System::Console::WriteLine(v->i);
   System::Console::WriteLine(mv->i);
}
```

```Output
8
7
7
```

## <a name="see-also"></a>関連項目

[pin_ptr (C++/CLI)](pin-ptr-cpp-cli.md)