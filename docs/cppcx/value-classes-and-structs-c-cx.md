---
title: 値クラスと構造体 (C++/CX)
ms.date: 12/30/2016
helpviewer_keywords:
- value struct
- value class
ms.assetid: 262a0992-9721-4c02-8297-efc07d90e5a4
ms.openlocfilehash: 3340c5e387dc58ddcb5348cdc041a58840463995
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740933"
---
# <a name="value-classes-and-structs-ccx"></a>値クラスと構造体 (C++/CX)

*値構造体*または*値クラス*は、WINDOWS ランタイム互換性のあるポッド ("plain old data structure") です。 これは、サイズが固定され、フィールドだけで構成されています。ref クラスとは異なり、プロパティはありません。

次の例で、値構造体の宣言および初期化の方法について説明します。

```

// in mainpage.xaml.h:
    value struct TestStruct
    {
        Platform::String^ str;
        int i;
    };

    value struct TestStruct2
    {
        TestStruct ts;
        Platform::String^ str;
        int i;
    };

// in mainpage.cpp:
    // Initialize a value struct with an int and String
    TestStruct ts = {"I am a TestStruct", 1};

    // Initialize a value struct that contains
    // another value struct, an int and a String
    TestStruct2 ts2 = {{"I am a TestStruct", 1}, "I am a TestStruct2", 2};

    // Initialize value struct members individually.
    TestStruct ts3;
    ts3.i = 108;
    ts3.str = "Another way to init a value struct.";
```

値型の変数を別の変数に代入すると、2 つの変数がそれぞれ独自にデータのコピーを持つように値がコピーされます。 *値構造体* は、パブリック データ フィールドのみを格納し、 `value struct` キーワードを使用して宣言された固定サイズの構造体です。

*値クラス* は `value struct` と基本的には同じですが、フィールドにパブリック アクセシビリティを明示的に指定する必要がある点が異なります。 これは `value class` キーワードを使用して宣言されます。

値の構造体または値クラスには、フィールドとしてのみ、基本的`Platform::String^`な数値型、列挙型クラス、、または[Platform:: ibox \<T > ^](../cppcx/platform-ibox-interface.md)を含めることができます。ここで、T は数値型、列挙型クラス、または値クラスまたは構造体です。 `IBox<T>^` フィールドは `nullptr`という値を持つことができます。C++ はこの方法で、 *null 許容値型*という概念を実装します。

`Platform::String^` 型または `IBox<T>^` 型をメンバーとして含む値クラスまたは値構造体は、 `memcpy`可能ではありません。

`value class` または `value struct` のメンバーはすべて public であり、メタデータに出力されるので、標準 C++ 型はメンバーとして許可されていません。 `private` または `internal` の標準 C++ 型を含むことができる ref クラスとは異なります。

次のコードは、 `Coordinates` 型と `City` 型を値構造体として宣言します。 `City` データ メンバーの 1 つが `GeoCoordinates` 型であることに注意してください。 `value struct` には、メンバーとして他の値構造体を含めることができます。

[!code-cpp[cx_classes#07](../cppcx/codesnippet/CPP/classesstructs/class1.h#07)]

## <a name="parameter-passing-for-value-types"></a>値型のパラメーターの引き渡し

値の型を関数パラメーターまたはメソッド パラメーターとして持っている場合、通常、値によって渡されます。 大きなオブジェクトの場合、パフォーマンスの問題が生じる可能性があります。 Visual Studio2013 以前では、C++/CX の値の型は値によって渡されていました。 Visual Studio 2015 以降では、参照または値によって値の型を渡すことができます。

値によって値の型を渡すパラメーターを宣言するには、次のようなコードを使用します。

```
void Method1(MyValueType obj);
```

参照によって値の型を渡すパラメーターを宣言するには、次のように、参照のシンボル (&) を使用します。

```
void Method2(MyValueType& obj);
```

Method2 内の型は MyValueType への参照であり、標準 C++ の参照型と同じように機能します。

Method1 を別の言語 (C# など) から呼び出す場合、 `ref` または `out` キーワードを使用する必要はありません。 Method2 を呼び出す場合、 `ref` キーワードを使用します。

```
Method2(ref obj);
```

ポインターのシンボル (*) を使用して、参照によって値の型を渡すこともできます。 その他の言語での呼び出し元に関する動作は同じですが (C# の呼び出し元は `ref` キーワードを使用する)、メソッドにおける型は値の型へのポインターです。

## <a name="nullable-value-types"></a>null 許容値型

前述のように、値クラスまたは値構造体には、 [Platform:: ibox\<T > ^](../cppcx/platform-ibox-interface.md)型のフィールドを指定`IBox<int>^`できます (例:)。 このようなフィールドは、 `int` 型として有効である任意の数値型の値を持つことができます。または `nullptr`という値を持つこともできます。 オプションとして宣言されたパラメーターを持つメソッドに対する引数として、またはどこか他の場所にあり値を持つことが必須ではない値型に対して、null 許容フィールドを渡すことができます。

null 許容フィールドを持つ構造体を初期化する方法の例を次に示します。

```
public value struct Student
{
    Platform::String^ Name;
    int EnrollmentYear;
    Platform::IBox<int>^ GraduationYear; // Null if not yet graduated.
};
//To create a Student struct, one must populate the nullable type.
MainPage::MainPage()
{
    InitializeComponent();

    Student A;
    A.Name = "Alice";
    A.EnrollmentYear = 2008;
    A.GraduationYear = ref new Platform::Box<int>(2012);

    Student B;
    B.Name = "Bob";
    B.EnrollmentYear = 2011;
    B.GraduationYear = nullptr;

    IsCurrentlyEnrolled(A);
    IsCurrentlyEnrolled(B);
}
bool MainPage::IsCurrentlyEnrolled(Student s)
{
    if (s.GraduationYear == nullptr)
    {
        return true;
    }
    return false;
}
```

次に示すように、同じ方法で値の構造体自体を null 許容にすることもできます。

```

public value struct MyStruct
{
public:
    int i;
    Platform::String^ s;
};

public ref class MyClass sealed
{
public:
    property Platform::IBox<MyStruct>^ myNullableStruct;
};
```

## <a name="see-also"></a>関連項目

[型システム (C++/CX)](../cppcx/type-system-c-cx.md)<br/>
[C++/CX 言語リファレンス](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[名前空間参照](../cppcx/namespaces-reference-c-cx.md)<br/>
[Ref クラスと構造体 (C++/CX)](../cppcx/ref-classes-and-structs-c-cx.md)
