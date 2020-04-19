---
title: STL/CLR コンテナー
ms.date: 09/18/2018
ms.topic: reference
helpviewer_keywords:
- STL/CLR, containers
- containers, STL/CLR
ms.assetid: 34ca8031-2041-46b9-aed9-29082d1972ea
ms.openlocfilehash: dc2e5ce3263c61839a1ba434ab0d2a39e6a9078f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384596"
---
# <a name="stlclr-containers"></a>STL/CLR コンテナー

同様にあるは、C++ 標準ライブラリですが .NET Framework の管理対象環境内で実行するコンテナーの STL/CLR ライブラリで構成されます。 実際、C++ 標準ライブラリの最新の状態が保持されないと、従来のサポートは維持されます。

このドキュメントでは、コンテナーの要素、要素をコンテナーに挿入することし、コンテナー内の要素と、所有権の問題の種類の要件など、STL/CLR のコンテナーの概要を示します。 必要に応じて、ネイティブの C++ 標準ライブラリと STL/CLR の相違点が示されています。

## <a name="requirements-for-container-elements"></a>コンテナー要素の要件

STL/CLR コンテナーに挿入されたすべての要素は、特定のガイドラインに従う必要があります。 詳細については、次を参照してください。 [STL/CLR コンテナー要素の要件](../dotnet/requirements-for-stl-clr-container-elements.md)します。

## <a name="valid-container-elements"></a>有効なコンテナー要素

STL/CLR コンテナーには、2 種類の要素のいずれかを保持できます。

- 参照型を処理します。

- 参照型。

- ボックス化解除された値の型。

ボックス化された値の型は、任意の STL/CLR コンテナーに挿入できません。

### <a name="handles-to-reference-types"></a>参照型へのハンドル

参照型を識別するハンドルを STL/CLR コンテナーに挿入できます。 CLR を対象とする C++ でのハンドルは、ネイティブ C++ でのポインターに似ています。 詳細については、次を参照してください。[オブジェクト演算子 (^) へのハンドル](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)します。

#### <a name="example"></a>例

次の例に、Employee オブジェクトを識別するハンドルを挿入する方法を示しています、 [cliext::set](../dotnet/set-stl-clr.md)します。

```
// cliext_container_valid_reference_handle.cpp
// compile with: /clr

#include <cliext/set>

using namespace cliext;
using namespace System;

ref class Employee
{
public:
    // STL/CLR containers might require a public constructor, so it
    // is a good idea to define one.
    Employee() :
        name(nullptr),
        employeeNumber(0) { }

    // All STL/CLR containers require a public copy constructor.
    Employee(const Employee% orig) :
        name(orig.name),
        employeeNumber(orig.employeeNumber) { }

    // All STL/CLR containers require a public assignment operator.
    Employee% operator=(const Employee% orig)
    {
        if (this != %orig)
        {
            name = orig.name;
            employeeNumber = orig.employeeNumber;
        }

        return *this;
    }

    // All STL/CLR containers require a public destructor.
    ~Employee() { }

    // Associative containers such as maps and sets
    // require a comparison operator to be defined
    // to determine proper ordering.
    bool operator<(const Employee^ rhs)
    {
        return (employeeNumber < rhs->employeeNumber);
    }

    // The employee's name.
    property String^ Name
    {
        String^ get() { return name; }
        void set(String^ value) { name = value; }
    }

    // The employee's employee number.
    property int EmployeeNumber
    {
        int get() { return employeeNumber; }
        void set(int value) { employeeNumber = value; }
    }

private:
    String^ name;
    int employeeNumber;
};

int main()
{
    // Create a new employee object.
    Employee^ empl1419 = gcnew Employee();
    empl1419->Name = L"Darin Lockert";
    empl1419->EmployeeNumber = 1419;

    // Add the employee to the set of all employees.
    set<Employee^>^ emplSet = gcnew set<Employee^>();
    emplSet->insert(empl1419);

    // List all employees of the company.
    for each (Employee^ empl in emplSet)
    {
        Console::WriteLine("Employee Number {0}: {1}",
            empl->EmployeeNumber, empl->Name);
    }

    return 0;
}
```

### <a name="reference-types"></a>参照型

STL/CLR コンテナーに参照型 (参照型を識別するハンドルではなく) を挿入することもできます。 主な違いは、参照型のコンテナーが削除されたときに、デストラクターは、コンテナー内のすべての要素に対して呼び出されます。 参照型へのハンドルのコンテナーでは、これらの要素のデストラクターを呼び出されませんが。

#### <a name="example"></a>例

次の例に、Employee オブジェクトを挿入する方法を示しています、`cliext::set`します。

```
// cliext_container_valid_reference.cpp
// compile with: /clr

#include <cliext/set>

using namespace cliext;
using namespace System;

ref class Employee
{
public:
    // STL/CLR containers might require a public constructor, so it
    // is a good idea to define one.
    Employee() :
        name(nullptr),
        employeeNumber(0) { }

    // All STL/CLR containers require a public copy constructor.
    Employee(const Employee% orig) :
        name(orig.name),
        employeeNumber(orig.employeeNumber) { }

    // All STL/CLR containers require a public assignment operator.
    Employee% operator=(const Employee% orig)
    {
        if (this != %orig)
        {
            name = orig.name;
            employeeNumber = orig.employeeNumber;
        }

        return *this;
    }

    // All STL/CLR containers require a public destructor.
    ~Employee() { }

    // Associative containers such as maps and sets
    // require a comparison operator to be defined
    // to determine proper ordering.
    bool operator<(const Employee^ rhs)
    {
        return (employeeNumber < rhs->employeeNumber);
    }

    // The employee's name.
    property String^ Name
    {
        String^ get() { return name; }
        void set(String^ value) { name = value; }
    }

    // The employee's employee number.
    property int EmployeeNumber
    {
        int get() { return employeeNumber; }
        void set(int value) { employeeNumber = value; }
    }

private:
    String^ name;
    int employeeNumber;
};

int main()
{
    // Create a new employee object.
    Employee empl1419;
    empl1419.Name = L"Darin Lockert";
    empl1419.EmployeeNumber = 1419;

    // Add the employee to the set of all employees.
    set<Employee>^ emplSet = gcnew set<Employee>();
    emplSet->insert(empl1419);

    // List all employees of the company.
    for each (Employee^ empl in emplSet)
    {
        Console::WriteLine("Employee Number {0}: {1}",
            empl->EmployeeNumber, empl->Name);
    }

    return 0;
}
```

### <a name="unboxed-value-types"></a>ボックス化解除された値の型

Unboxed 値型を STL/CLR コンテナーに挿入することもできます。 Unboxed 値型が値の型をまだ*手書き*参照型にします。

値型の要素がある標準の値の型のいずれかなど、 `int`、か、またはユーザー定義の値の型をなどあるできます、`value class`します。 詳細については、次を参照してください[クラスと構造体。](../extensions/classes-and-structs-cpp-component-extensions.md)

#### <a name="example"></a>例

次の例では、値の型をクラス、従業員のことで最初の例を変更します。 この値の型を挿入してから、`cliext::set`最初の例と同様です。

```
// cliext_container_valid_valuetype.cpp
// compile with: /clr

#include <cliext/set>

using namespace cliext;
using namespace System;

value class Employee
{
public:
    // Associative containers such as maps and sets
    // require a comparison operator to be defined
    // to determine proper ordering.
    bool operator<(const Employee^ rhs)
    {
        return (employeeNumber < rhs->employeeNumber);
    }

    // The employee's name.
    property String^ Name
    {
        String^ get() { return name; }
        void set(String^ value) { name = value; }
    }

    // The employee's employee number.
    property int EmployeeNumber
    {
        int get() { return employeeNumber; }
        void set(int value) { employeeNumber = value; }
    }

private:
    String^ name;
    int employeeNumber;
};

int main()
{
    // Create a new employee object.
    Employee empl1419;
    empl1419.Name = L"Darin Lockert";
    empl1419.EmployeeNumber = 1419;

    // Add the employee to the set of all employees.
    set<Employee>^ emplSet = gcnew set<Employee>();
    emplSet->insert(empl1419);

    // List all employees of the company.
    for each (Employee empl in emplSet)
    {
        Console::WriteLine("Employee Number {0}: {1}",
            empl.EmployeeNumber, empl.Name);
    }

    return 0;
}
```

値型へのハンドルをコンテナーに挿入しようとした場合[コンパイラ エラー C3225](../error-messages/compiler-errors-2/compiler-error-c3225.md)が生成されます。

### <a name="performance-and-memory-implications"></a>パフォーマンスとメモリへの影響

型または値型をコンテナー要素として参照するハンドルを使用するかどうかを決定するときに、いくつかの要因を考慮する必要があります。 値の型を使用する場合は、コンテナーに要素が挿入されるたびに要素のコピーが行われることに注意してください。 小さいオブジェクトは、挿入されるオブジェクトが大きい場合、パフォーマンスが低下する可能性がありますが、問題があります。 また、値の型を使用している場合は、各コンテナーは、要素のコピーを必要があるため、同時に複数のコンテナーで 1 つの要素を格納することはできません。

代わりに型を参照するハンドルを使用する場合は、コンテナーに挿入するときに、要素のコピーを作成するために必要ないため、パフォーマンスが向上します。 またとは異なり値型の場合は、同じ要素に存在できます複数のコンテナー。 ただし、ハンドルを使用する場合は、する必要があります注意するハンドルが有効であることを参照するオブジェクトが削除されていない他の場所で、プログラムのことを確認します。

## <a name="ownership-issues-with-containers"></a>コンテナーの所有権の問題

STL/CLR のコンテナーは、値のセマンティクスで動作します。 コンテナーに要素を挿入するたびにその要素のコピーが挿入されます。 参照のようなセマンティクスを取得する場合は、オブジェクト自体ではなく、オブジェクトを識別するハンドルを挿入できます。

クリア テキストの呼び出しまたはハンドル オブジェクトのコンテナーのメソッドを消去するときに、ハンドルが参照するオブジェクトはメモリから解放されません。 必要があります明示的にオブジェクトを削除または、これらのオブジェクトが、マネージ ヒープ上に存在しているので、オブジェクトが不要になった使用されていることを決定したら、メモリを解放するガベージ コレクターを許可します。

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ リファレンス](../standard-library/cpp-standard-library-reference.md)
