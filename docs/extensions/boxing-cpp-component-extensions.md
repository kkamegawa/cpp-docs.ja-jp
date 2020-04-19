---
title: ボックス化 (C++/CLI および C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- boxing, C++
ms.assetid: b5fd2c98-c578-4f83-8257-6dd663478665
ms.openlocfilehash: 0b41cacba8c279447e1e944cc3214ca1ba607665
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516157"
---
# <a name="boxing--ccli-and-ccx"></a>ボックス化 (C++/CLI および C++/CX)

値型のオブジェクトへの変換を "*ボックス化*" と呼び、オブジェクトの値型への変換を "*ボックス化解除* " と呼びます。

## <a name="all-runtimes"></a>すべてのランタイム

(この言語機能にはランタイムに適用される特記事項がありません。)

## <a name="windows-runtime"></a>Windows ランタイム

C++/CX では、値型のボックス化と参照型のボックス化解除の短縮構文をサポートしています。 値型は `Object` 型の変数に代入されるときにボックス化されます。 `Object` 変数は値型の変数に代入されるときに、かっこ内にボックス化解除する型が指定される場合、つまり、オブジェクト変数が値型にキャストされるときに、ボックス化解除されます。

```cpp
  Platform::Object^
  object_variable  = value_variable;
value_variable = (value_type) object_variable;
```

### <a name="requirements"></a>要件

コンパイラ オプション: `/ZW`

### <a name="examples"></a>使用例

次のコード例では、`DateTime` 値をボックス化およびボックス化解除します。 最初に、この例では、現在の日付と時刻を表す `DateTime` 値を取得し、それを `DateTime` 変数に代入します。 次に、`DateTime` を `Object` 変数に代入することでボックス化します。 最後に、ボックス化された値を別の `DateTime` 変数に代入することでボックス化解除します。

この例をテストするには、`BlankApplication` プロジェクトを作成し、`BlankPage::OnNavigatedTo()` メソッドを置き換えた後、右かっこの位置と変数 `str1` への代入の位置にブレークポイントを指定します。 例で右かっこに到達したら、`str1` を確認します。

```cpp
void BlankPage::OnNavigatedTo(NavigationEventArgs^ e)
{
    using namespace Windows::Globalization::DateTimeFormatting;

    Windows::Foundation::DateTime dt, dtAnother;
    Platform::Object^ obj1;

    Windows::Globalization::Calendar^ c =
        ref new Windows::Globalization::Calendar;
    c->SetToNow();
    dt = c->GetDateTime();
    auto dtf = ref new DateTimeFormatter(
                           YearFormat::Full,
                           MonthFormat::Numeric,
                           DayFormat::Default,
                           DayOfWeekFormat::None);
    String^ str1 = dtf->Format(dt);
    OutputDebugString(str1->Data());
    OutputDebugString(L"\r\n");

    // Box the value type and assign to a reference type.
    obj1 = dt;
    // Unbox the reference type and assign to a value type.
    dtAnother = (Windows::Foundation::DateTime) obj1;

    // Format the DateTime for display.
    String^ str2 = dtf->Format(dtAnother);
    OutputDebugString(str2->Data());
}
```

詳細については、「[ボックス化 (C++/CX)](https://msdn.microsoft.com/library/windows/apps/hh969554.aspx)」を参照してください。

## <a name="common-language-runtime"></a>共通言語ランタイム

コンパイラは、値型を <xref:System.Object> にボックス化します。 これは、値型を <xref:System.Object> に変換するコンパイラで定義済みの変換により可能になりました。

ボックス化とボックス化解除を利用することで、値型をオブジェクトとして扱うことができます。 値型 (構造体型や int などの組み込み型を含む) を、<xref:System.Object> 型との間で相互に変換できます。

詳細については次を参照してください:

- [方法: 明示的にボックス化を要求する](../dotnet/how-to-explicitly-request-boxing.md)

- [方法: gcnew を使用して値型を作成し、暗黙的なボックス化を使用する](../dotnet/how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing.md)

- [方法: ボックス化を解除する](../dotnet/how-to-unbox.md)

- [標準変換と暗黙のボックス化](../dotnet/standard-conversions-and-implicit-boxing.md)

### <a name="requirements"></a>要件

コンパイラ オプション: `/clr`

### <a name="examples"></a>使用例

次の例では、暗黙的なボックス化の動作を示します。

```cpp
// vcmcppv2_explicit_boxing2.cpp
// compile with: /clr
using namespace System;

ref class A {
public:
   void func(System::Object^ o){Console::WriteLine("in A");}
};

value class V {};

interface struct IFace {
   void func();
};

value class V1 : public IFace {
public:
   virtual void func() {
      Console::WriteLine("Interface function");
   }
};

value struct V2 {
   // conversion operator to System::Object
   static operator System::Object^(V2 v2) {
      Console::WriteLine("operator System::Object^");
      return (V2^)v2;
   }
};

void func1(System::Object^){Console::WriteLine("in void func1(System::Object^)");}
void func1(V2^){Console::WriteLine("in func1(V2^)");}

void func2(System::ValueType^){Console::WriteLine("in func2(System::ValueType^)");}
void func2(System::Object^){Console::WriteLine("in func2(System::Object^)");}

int main() {
   // example 1 simple implicit boxing
   Int32^ bi = 1;
   Console::WriteLine(bi);

   // example 2 calling a member with implicit boxing
   Int32 n = 10;
   Console::WriteLine("xx = {0}", n.ToString());

   // example 3 implicit boxing for function calls
   A^ a = gcnew A;
   a->func(n);

   // example 4 implicit boxing for WriteLine function call
   V v;
   Console::WriteLine("Class {0} passed using implicit boxing", v);
   Console::WriteLine("Class {0} passed with forced boxing", (V^)(v));   // force boxing

   // example 5 casting to a base with implicit boxing
   V1 v1;
   IFace ^ iface = v1;
   iface->func();

   // example 6 user-defined conversion preferred over implicit boxing for function-call parameter matching
   V2 v2;
   func1(v2);   // user defined conversion from V2 to System::Object preferred over implicit boxing
                // Will call void func1(System::Object^);

   func2(v2);   // OK: Calls "static V2::operator System::Object^(V2 v2)"
   func2((V2^)v2);   // Using explicit boxing: calls func2(System::ValueType^)
}
```

```Output
1

xx = 10

in A

Class V passed using implicit boxing

Class V passed with forced boxing

Interface function

in func1(V2^)

in func2(System::ValueType^)

in func2(System::ValueType^)
```

## <a name="see-also"></a>関連項目

[.NET および UWP でのコンポーネント拡張](component-extensions-for-runtime-platforms.md)