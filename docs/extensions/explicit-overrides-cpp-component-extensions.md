---
title: 明示的なオーバーライド (C++/CLI および C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- overriding, override [C++]
ms.assetid: 4ec3eaf5-163b-4df8-8f16-7a2ec04c3d0f
ms.openlocfilehash: 7d36793e4467f9454aca1eb207f3c3dfbd483bff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516677"
---
# <a name="explicit-overrides--ccli-and-ccx"></a>明示的なオーバーライド (C++/CLI および C++/CX)

このトピックでは、基底クラスまたはインターフェイスのメンバーを明示的にオーバーライドする方法について説明します。 名前付きの (明示的な) オーバーライドは、別の名前を持つ派生メソッドを使用してメソッドをオーバーライドするためにのみ使用する必要があります。

## <a name="all-runtimes"></a>すべてのランタイム

### <a name="syntax"></a>構文

```cpp
overriding-function-declarator = type::function [,type::function] { overriding-function-definition }
overriding-function-declarator = function { overriding-function-definition }
```

### <a name="parameters"></a>パラメーター

*overriding-function-declarator*<br/>
オーバーライドする関数の戻り値の型、名前、および引数リスト。  オーバーライドする関数に、オーバーライドされる関数と同じ名前があってはならないことに注意してください。

*type*<br/>
オーバーライドする関数を含む基本型。

*function*<br/>
オーバーライドする 1 つまたは複数の関数の名前のコンマ区切りのリスト。

*overriding-function-definition*<br/>
オーバーライドする関数を定義する関数の本体ステートメント。

### <a name="remarks"></a>解説

明示的なオーバーライドを使用して、メソッドのシグネチャのエイリアスを作成するか、同じシグネチャでメソッドの異なる実装を行います。

継承された型と継承された型のメンバーの動作を変更する方法の詳細については、「[オーバーライド指定子](override-specifiers-cpp-component-extensions.md)」を参照してください。

## <a name="windows-runtime"></a>Windows ランタイム

### <a name="requirements"></a>要件

コンパイラ オプション: `/ZW`

## <a name="common-language-runtime"></a>共通言語ランタイム

### <a name="remarks"></a>解説

ネイティブ コードまたは `/clr:oldSyntax` でコンパイルされたコードでの明示的なオーバーライドについては、「[明示的なオーバーライド](../cpp/explicit-overrides-cpp.md)」を参照してください。

### <a name="requirements"></a>要件

コンパイラ オプション: `/clr`

### <a name="examples"></a>使用例

次のコード例では、基本インターフェイスでの単純で暗黙的なオーバーライドとメンバーの実装を示します。ここでは明示的なオーバーライドは使用されていません。

```cpp
// explicit_override_1.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
};

ref class X : public I1 {
public:
   virtual void f() {
      System::Console::WriteLine("X::f override of I1::f");
   }
};

int main() {
   I1 ^ MyI = gcnew X;
   MyI -> f();
}
```

```Output
X::f override of I1::f
```

次のコード例では、明示的なオーバーライド構文を使用して、すべてのインターフェイス メンバーを一般的なシグネチャで実装する方法を示します。

```cpp
// explicit_override_2.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
};

interface struct I2 {
   virtual void f();
};

ref struct X : public I1, I2 {
   virtual void f() = I1::f, I2::f {
      System::Console::WriteLine("X::f override of I1::f and I2::f");
   }
};

int main() {
   I1 ^ MyI = gcnew X;
   I2 ^ MyI2 = gcnew X;
   MyI -> f();
   MyI2 -> f();
}
```

```Output
X::f override of I1::f and I2::f
X::f override of I1::f and I2::f
```

次のコード例では、関数のオーバーライドで、それが実装する関数とは異なる名前を持つ方法を示します。

```cpp
// explicit_override_3.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
};

ref class X : public I1 {
public:
   virtual void g() = I1::f {
      System::Console::WriteLine("X::g");
   }
};

int main() {
   I1 ^ a = gcnew X;
   a->f();
}
```

```Output
X::g
```

次のコード例では、タイプ セーフ コレクションを実装する明示的なインターフェイスの実装を示します。

```cpp
// explicit_override_4.cpp
// compile with: /clr /LD
using namespace System;
ref class R : ICloneable {
   int X;

   virtual Object^ C() sealed = ICloneable::Clone {
      return this->Clone();
   }

public:
   R() : X(0) {}
   R(int x) : X(x) {}

   virtual R^ Clone() {
      R^ r = gcnew R;
      r->X = this->X;
      return r;
   }
};
```

## <a name="see-also"></a>関連項目

[.NET および UWP でのコンポーネント拡張](component-extensions-for-runtime-platforms.md)