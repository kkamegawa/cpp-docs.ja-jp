---
title: new (vtable の新しいスロット) (C++/CLI および C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 1a9a5704-f02f-46ae-ad65-f0f2b6dbabc3
ms.openlocfilehash: c5446e5e84491ff7d736ce3b3af49dacd471c010
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515647"
---
# <a name="new-new-slot-in-vtable--ccli-and-ccx"></a>new (vtable の新しいスロット) (C++/CLI および C++/CX)

**new** キーワードは、仮想メンバーが vtable の新しいスロットを取得することを示します。

## <a name="all-runtimes"></a>すべてのランタイム

(この言語機能にはランタイムに適用される特記事項がありません。)

## <a name="windows-runtime"></a>Windows ランタイム

Windows ランタイムではサポートされません。

## <a name="common-language-runtime"></a>共通言語ランタイム

### <a name="remarks"></a>解説

`/clr` のコンパイルでは、**new** は、仮想メンバーが vtable の新しいスロットを取得することを示します。つまり、関数で基底クラスのメソッドをオーバーライドしません。

**new** を指定すると、関数の IL に newslot 修飾子が追加されます。  newslot の詳細については、次のトピックを参照してください。

- <xref:System.Reflection.MethodInfo.GetBaseDefinition?displayProperty=nameWithType>

- <xref:System.Reflection.MethodAttributes?displayProperty=nameWithType>

### <a name="requirements"></a>要件

コンパイラ オプション: `/clr`

### <a name="examples"></a>使用例

**new** の効果の例を次に示します。

```cpp
// newslot.cpp
// compile with: /clr
ref class C {
public:
   virtual void f() {
      System::Console::WriteLine("C::f() called");
   }

   virtual void g() {
      System::Console::WriteLine("C::g() called");
   }
};

ref class D : public C {
public:
   virtual void f() new {
      System::Console::WriteLine("D::f() called");
   }

   virtual void g() override {
      System::Console::WriteLine("D::g() called");
   }
};

ref class E : public D {
public:
   virtual void f() override {
      System::Console::WriteLine("E::f() called");
   }
};

int main() {
   D^ d = gcnew D;
   C^ c = gcnew D;

   c->f();   // calls C::f
   d->f();   // calls D::f

   c->g();   // calls D::g
   d->g();   // calls D::g

   D ^ e = gcnew E;
   e->f();   // calls E::f
}
```

```Output
C::f() called

D::f() called

D::g() called

D::g() called

E::f() called
```

## <a name="see-also"></a>関連項目

[.NET および UWP でのコンポーネント拡張](component-extensions-for-runtime-platforms.md)<br/>

[オーバーライド指定子](override-specifiers-cpp-component-extensions.md)