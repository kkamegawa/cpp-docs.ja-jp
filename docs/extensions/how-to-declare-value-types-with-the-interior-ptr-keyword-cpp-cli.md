---
title: '方法: interior_ptr キーワードを含む値型を宣言する (C++/CLI)'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- _ptr keyword
- value types, declaring
ms.assetid: 49eea66e-eeba-49bd-95b0-ba297be436e3
ms.openlocfilehash: 2b75f6c4763ddd7d3fd2d802371e21c40d506b16
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515757"
---
# <a name="how-to-declare-value-types-with-the-interiorptr-keyword-ccli"></a>方法: interior_ptr キーワードを含む値型を宣言する (C++/CLI)

値型で **Interior_ptr** を使用できます。

> [!IMPORTANT]
> この言語機能は、`/clr` コンパイラ オプションではサポートされていますが、`/ZW` コンパイラ オプションではサポートされていません。

## <a name="example"></a>例

### <a name="description"></a>説明

次の C++/CLI の例では、値型で **interior_ptr** を使用する方法を示します。

### <a name="code"></a>コード

```cpp
// interior_ptr_value_types.cpp
// compile with: /clr
value struct V {
   V(int i) : data(i){}
   int data;
};

int main() {
   V v(1);
   System::Console::WriteLine(v.data);

   // pointing to a value type
   interior_ptr<V> pv = &v;
   pv->data = 2;

   System::Console::WriteLine(v.data);
   System::Console::WriteLine(pv->data);

   // pointing into a value type
   interior_ptr<int> pi = &v.data;
   *pi = 3;
   System::Console::WriteLine(*pi);
   System::Console::WriteLine(v.data);
   System::Console::WriteLine(pv->data);
}
```

```Output
1
2
2
3
3
3
```

## <a name="example"></a>例

### <a name="description"></a>説明

値型で、**this** ポインターが interior_ptr と評価されます。

値型 `V` の非静的メンバー関数の本文で、**this** は `interior_ptr<V>` 型の式であり、その値が関数によって呼び出されるオブジェクトのアドレスになります。

### <a name="code"></a>コード

```cpp
// interior_ptr_value_types_this.cpp
// compile with: /clr /LD
value struct V {
   int data;
   void f() {
      interior_ptr<V> pv1 = this;
      // V* pv2 = this;   error
   }
};
```

## <a name="example"></a>例

### <a name="description"></a>説明

次の例では、静的メンバーを持つ address-of 演算子を使用する方法を示します。

静的な Visual C++ 型のメンバーのアドレスは、ネイティブ ポインターを生成します。  静的な値型のメンバーのアドレスは、値型のメンバーがランタイム ヒープに割り当てられ、ガベージ コレクターによって移動される可能性があるため、マネージ ポインターになります。

### <a name="code"></a>コード

```cpp
// interior_ptr_value_static.cpp
// compile with: /clr
using namespace System;
value struct V { int i; };

ref struct G {
   static V v = {22};
   static int i = 23;
   static String^ pS = "hello";
};

int main() {
   interior_ptr<int> p1 = &G::v.i;
   Console::WriteLine(*p1);

   interior_ptr<int> p2 = &G::i;
   Console::WriteLine(*p2);

   interior_ptr<String^> p3 = &G::pS;
   Console::WriteLine(*p3);
}
```

```Output
22
23
hello
```

## <a name="see-also"></a>関連項目

[interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md)