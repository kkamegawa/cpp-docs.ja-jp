---
title: sealed (C++/CLI および C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- sealed_cpp
- sealed
helpviewer_keywords:
- sealed keyword [C++]
ms.assetid: 3d0d688a-41aa-45f5-a25a-65c44206521e
ms.openlocfilehash: 493f6597d146480714848b37154cc8bacd37113a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516007"
---
# <a name="sealed--ccli-and-ccx"></a>sealed (C++/CLI および C++/CX)

**sealed** は ref クラスの状況依存キーワードであり、仮想メンバーがオーバーライドできないこと、または型を基底型として使用できないことを示します。

> [!NOTE]
> ISO C++11 標準言語に [final](../cpp/final-specifier.md) キーワードが導入されました。 標準クラスでは **final** を、ref クラスでは **sealed** を使用してください。

## <a name="all-runtimes"></a>すべてのランタイム

## <a name="syntax"></a>構文

```cpp
ref class identifier sealed {...};
virtual return-type identifier() sealed {...};
```

### <a name="parameters"></a>パラメーター

*identifier*<br/>
関数またはクラスの名前。

*return-type*<br/>
関数によって返される型。

## <a name="remarks"></a>解説

最初の構文例ではクラスがシールされます。 2 番目の例では仮想関数がシールされます。

**sealed** キーワードは、ref クラスとそれらの仮想メンバー関数で使用します。 詳細については、[指定子とネイティブ コンパイルのオーバーライド](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)に関する記事を参照してください。

`__is_sealed(type)` 型の特徴を使用することで、型がシールされているかどうかをコンパイル時に判断することができます。 詳細については、「[型の特徴のコンパイラ サポート](compiler-support-for-type-traits-cpp-component-extensions.md)」を参照してください。

**sealed** は状況依存キーワードです。  詳細については、「[状況依存キーワード](context-sensitive-keywords-cpp-component-extensions.md)」を参照してください。

## <a name="windows-runtime"></a>Windows ランタイム

「[Ref クラスと構造体](../cppcx/ref-classes-and-structs-c-cx.md)」を参照してください。

### <a name="requirements"></a>要件

コンパイラ オプション: `/ZW`

## <a name="common-language-runtime"></a>共通言語ランタイム

(この言語機能には共通言語ランタイムのみに適用される特記事項がありません。)

### <a name="requirements"></a>要件

コンパイラ オプション: `/clr`

### <a name="examples"></a>使用例

次のコード例では、仮想メンバーに対する **sealed** の効果を示します。

```cpp
// sealed_keyword.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
   virtual void g();
};

ref class X : I1 {
public:
   virtual void f() {
      System::Console::WriteLine("X::f override of I1::f");
   }

   virtual void g() sealed {
      System::Console::WriteLine("X::f override of I1::g");
   }
};

ref class Y : public X {
public:
   virtual void f() override {
      System::Console::WriteLine("Y::f override of I1::f");
   }

   /*
   // the following override generates a compiler error
   virtual void g() override {
      System::Console::WriteLine("Y::g override of I1::g");
   }
   */
};

int main() {
   I1 ^ MyI = gcnew X;
   MyI -> f();
   MyI -> g();

   I1 ^ MyI2 = gcnew Y;
   MyI2 -> f();
}
```

```Output
X::f override of I1::f
X::f override of I1::g
Y::f override of I1::f
```

次のコード例では、シール済みというマークをクラスに付ける方法を示します。

```cpp
// sealed_keyword_2.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
};

ref class X sealed : I1 {
public:
   virtual void f() override {}
};

ref class Y : public X {   // C3246 base class X is sealed
public:
   virtual void f() override {}
};
```

## <a name="see-also"></a>関連項目

[.NET および UWP でのコンポーネント拡張](component-extensions-for-runtime-platforms.md)