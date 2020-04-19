---
title: ADO.NET によるデータ アクセス (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- ADO.NET [C++]
- .NET Framework [C++], data access
- databases [C++], accessing in C++
- data access [C++], ADO.NET
- data [C++], ADO.NET
- native strings [C++]
- ADO.NET [C++], marshaling ANSI strings
- strings [C++], ADO.NET
- BSTRs, strings
- ADO.NET [C++], marshaling BSTR strings
- strings [C++], marshaling BSTR strings
- ADO.NET [C++], marshaling Unicode strings
- Unicode [C++], strings
- strings [C++], Unicode
- VARIANT, marshaling
- ADO.NET [C++], marshaling VARIANT types
- VARIANT
- SAFEARRAY, marshaling
- ADO.NET [C++], marshaling SAFEARRAY types
ms.assetid: b0cd987d-1ea7-4f76-ba01-cbd52503d06d
ms.openlocfilehash: b258e574b912b1c32e5ffae7ba29cfc5f9903685
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209093"
---
# <a name="data-access-using-adonet-ccli"></a>ADO.NET によるデータ アクセス (C++/CLI)

ADO.NET はデータ アクセス用の .NET Framework API であり、電源と前のデータ アクセス ソリューションでは味わえない使いやすさを提供します。 このセクションでは、いくつかのネイティブ型のマーシャ リングなど、Visual C のユーザーに固有の ADO.NET に関連する問題について説明します。

ADO.NET では、共通言語ランタイム (CLR) 下で実行されます。 このため、ADO.NET と対話するすべてのアプリケーションでは、CLR がターゲットもする必要があります。 ただし、わけネイティブ アプリケーションが ADO.NET を使用できません。 これらの例では、ネイティブ コードから ADO.NET データベースと対話する方法を示します。

## <a name="marshal_ansi"></a> ADO.NET の ANSI 文字列をマーシャ リングする.

ネイティブの文字列を追加する方法を示します (`char *`) をマーシャ リングする方法、およびデータベースを<xref:System.String?displayProperty=fullName>ネイティブの文字列にデータベースからです。

### <a name="example"></a>例

この例で、クラス DatabaseClass が作成される ADO.NET と対話する<xref:System.Data.DataTable>オブジェクト。 このクラスは、ネイティブ C++ `class` (と比較する`ref class`または`value class`)。 これは、機能は、ネイティブ コードからこのクラスを使用して、マネージ型をネイティブ コードで使用することはできませんので必要です。 このクラスは、CLR を対象にコンパイルされる、`#pragma managed`クラス宣言の前のディレクティブ。 このディレクティブの詳細については、次を参照してください。[マネージ、アンマネージ](../preprocessor/managed-unmanaged.md)します。

DatabaseClass クラスのプライベート メンバーに注意してください:`gcroot<DataTable ^> table`します。 ネイティブ型は、管理対象の型を含めることはできませんので、`gcroot`キーワードが必要です。 詳細については`gcroot`を参照してください[方法。ネイティブ型のハンドルを宣言](../dotnet/how-to-declare-handles-in-native-types.md)します。

この例では、コードの残りの部分はネイティブの C++ コードで示される、`#pragma unmanaged`ディレクティブの前`main`します。 この例では DatabaseClass の新しいインスタンスを作成していますテーブルを作成し、テーブルのいくつかの行を設定するには、そのメソッドの呼び出し。 ネイティブ C++ 文字列 StringCol データベース列の値として渡されることに注意してください。 DatabaseClass、内でこれらの文字列がマーシャ リングの機能を使用して管理対象の文字列をマーシャ リング、<xref:System.Runtime.InteropServices?displayProperty=fullName>名前空間。 メソッドでは具体的には、<xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A>マーシャ リングするために使用、`char *`を<xref:System.String>、およびメソッド<xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A>マーシャ リングするために使用、<xref:System.String>を`char *`。

> [!NOTE]
>  によって割り当てられたメモリ<xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A>いずれかを呼び出して解放する必要があります<xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A>または`GlobalFree`します。

```cpp
// adonet_marshal_string_native.cpp
// compile with: /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll
#include <comdef.h>
#include <gcroot.h>
#include <iostream>
using namespace std;

#using <System.Data.dll>
using namespace System;
using namespace System::Data;
using namespace System::Runtime::InteropServices;

#define MAXCOLS 100

#pragma managed
class DatabaseClass
{
public:
    DatabaseClass() : table(nullptr) { }

    void AddRow(char *stringColValue)
    {
        // Add a row to the table.
        DataRow ^row = table->NewRow();
        row["StringCol"] = Marshal::PtrToStringAnsi(
            (IntPtr)stringColValue);
        table->Rows->Add(row);
    }

    void CreateAndPopulateTable()
    {
        // Create a simple DataTable.
        table = gcnew DataTable("SampleTable");

        // Add a column of type String to the table.
        DataColumn ^column1 = gcnew DataColumn("StringCol",
            Type::GetType("System.String"));
        table->Columns->Add(column1);
    }

    int GetValuesForColumn(char *dataColumn, char **values,
        int valuesLength)
    {
        // Marshal the name of the column to a managed
        // String.
        String ^columnStr = Marshal::PtrToStringAnsi(
                (IntPtr)dataColumn);

        // Get all rows in the table.
        array<DataRow ^> ^rows = table->Select();
        int len = rows->Length;
        len = (len > valuesLength) ? valuesLength : len;
        for (int i = 0; i < len; i++)
        {
            // Marshal each column value from a managed string
            // to a char *.
            values[i] = (char *)Marshal::StringToHGlobalAnsi(
                (String ^)rows[i][columnStr]).ToPointer();
        }

        return len;
    }

private:
    // Using gcroot, you can use a managed type in
    // a native class.
    gcroot<DataTable ^> table;
};

#pragma unmanaged
int main()
{
    // Create a table and add a few rows to it.
    DatabaseClass *db = new DatabaseClass();
    db->CreateAndPopulateTable();
    db->AddRow("This is string 1.");
    db->AddRow("This is string 2.");

    // Now retrieve the rows and display their contents.
    char *values[MAXCOLS];
    int len = db->GetValuesForColumn(
        "StringCol", values, MAXCOLS);
    for (int i = 0; i < len; i++)
    {
        cout << "StringCol: " << values[i] << endl;

        // Deallocate the memory allocated using
        // Marshal::StringToHGlobalAnsi.
        GlobalFree(values[i]);
    }

    delete db;

    return 0;
}
```

```Output
StringCol: This is string 1.
StringCol: This is string 2.
```

### <a name="compiling-the-code"></a>コードのコンパイル

- コマンドラインからコードをコンパイルするには、adonet_marshal_string_native.cpp という名前のファイルのコード例を保存し、次のステートメントを入力します。

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp
    ```

## <a name="marshal_bstr"></a> ADO.NET の BSTR 文字列をマーシャ リングする.

COM 文字列を追加する方法を示します (`BSTR`) をマーシャ リングする方法、およびデータベースを<xref:System.String?displayProperty=fullName>へのデータベースから、`BSTR`します。

### <a name="example"></a>例

この例で、クラス DatabaseClass が作成される ADO.NET と対話する<xref:System.Data.DataTable>オブジェクト。 このクラスは、ネイティブ C++ `class` (と比較する`ref class`または`value class`)。 これは、機能は、ネイティブ コードからこのクラスを使用して、マネージ型をネイティブ コードで使用することはできませんので必要です。 このクラスは、CLR を対象にコンパイルされる、`#pragma managed`クラス宣言の前のディレクティブ。 このディレクティブの詳細については、次を参照してください。[マネージ、アンマネージ](../preprocessor/managed-unmanaged.md)します。

DatabaseClass クラスのプライベート メンバーに注意してください:`gcroot<DataTable ^> table`します。 ネイティブ型は、管理対象の型を含めることはできませんので、`gcroot`キーワードが必要です。 詳細については`gcroot`を参照してください[方法。ネイティブ型のハンドルを宣言](../dotnet/how-to-declare-handles-in-native-types.md)します。

この例では、コードの残りの部分はネイティブの C++ コードで示される、`#pragma unmanaged`ディレクティブの前`main`します。 この例では DatabaseClass の新しいインスタンスを作成していますテーブルを作成し、テーブルのいくつかの行を設定するには、そのメソッドの呼び出し。 COM 文字列 StringCol データベース列の値として渡されることに注意してください。 DatabaseClass、内でこれらの文字列がマーシャ リングの機能を使用して管理対象の文字列をマーシャ リング、<xref:System.Runtime.InteropServices?displayProperty=fullName>名前空間。 メソッドでは具体的には、<xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A>マーシャ リングするために使用、`BSTR`を<xref:System.String>、およびメソッド<xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A>マーシャ リングするために使用、<xref:System.String>を`BSTR`。

> [!NOTE]
>  によって割り当てられたメモリ<xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A>いずれかを呼び出して解放する必要があります<xref:System.Runtime.InteropServices.Marshal.FreeBSTR%2A>または`SysFreeString`します。

``` cpp
// adonet_marshal_string_bstr.cpp
// compile with: /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll
#include <comdef.h>
#include <gcroot.h>
#include <iostream>
using namespace std;

#using <System.Data.dll>
using namespace System;
using namespace System::Data;
using namespace System::Runtime::InteropServices;

#define MAXCOLS 100

#pragma managed
class DatabaseClass
{
public:
    DatabaseClass() : table(nullptr) { }

    void AddRow(BSTR stringColValue)
    {
        // Add a row to the table.
        DataRow ^row = table->NewRow();
        row["StringCol"] = Marshal::PtrToStringBSTR(
            (IntPtr)stringColValue);
        table->Rows->Add(row);
    }

    void CreateAndPopulateTable()
    {
        // Create a simple DataTable.
        table = gcnew DataTable("SampleTable");

        // Add a column of type String to the table.
        DataColumn ^column1 = gcnew DataColumn("StringCol",
            Type::GetType("System.String"));
        table->Columns->Add(column1);
    }

    int GetValuesForColumn(BSTR dataColumn, BSTR *values,
        int valuesLength)
    {
        // Marshal the name of the column to a managed
        // String.
        String ^columnStr = Marshal::PtrToStringBSTR(
                (IntPtr)dataColumn);

        // Get all rows in the table.
        array<DataRow ^> ^rows = table->Select();
        int len = rows->Length;
        len = (len > valuesLength) ? valuesLength : len;
        for (int i = 0; i < len; i++)
        {
            // Marshal each column value from a managed string
            // to a BSTR.
            values[i] = (BSTR)Marshal::StringToBSTR(
                (String ^)rows[i][columnStr]).ToPointer();
        }

        return len;
    }

private:
    // Using gcroot, you can use a managed type in
    // a native class.
    gcroot<DataTable ^> table;
};

#pragma unmanaged
int main()
{
    // Create a table and add a few rows to it.
    DatabaseClass *db = new DatabaseClass();
    db->CreateAndPopulateTable();

    BSTR str1 = SysAllocString(L"This is string 1.");
    db->AddRow(str1);

    BSTR str2 = SysAllocString(L"This is string 2.");
    db->AddRow(str2);

    // Now retrieve the rows and display their contents.
    BSTR values[MAXCOLS];
    BSTR str3 = SysAllocString(L"StringCol");
    int len = db->GetValuesForColumn(
        str3, values, MAXCOLS);
    for (int i = 0; i < len; i++)
    {
        wcout << "StringCol: " << values[i] << endl;

        // Deallocate the memory allocated using
        // Marshal::StringToBSTR.
        SysFreeString(values[i]);
    }

    SysFreeString(str1);
    SysFreeString(str2);
    SysFreeString(str3);
    delete db;

    return 0;
}
```

```Output
StringCol: This is string 1.
StringCol: This is string 2.
```

### <a name="compiling-the-code"></a>コードのコンパイル

- コマンドラインからコードをコンパイルするには、adonet_marshal_string_native.cpp という名前のファイルのコード例を保存し、次のステートメントを入力します。

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp
    ```

## <a name="marshal_unicode"></a> ADO.NET の Unicode 文字列をマーシャ リングする.

ネイティブの Unicode 文字列を追加する方法を示します (`wchar_t *`) をマーシャ リングする方法、およびデータベースを<xref:System.String?displayProperty=fullName>ネイティブの Unicode 文字列にデータベースからです。

### <a name="example"></a>例

この例で、クラス DatabaseClass が作成される ADO.NET と対話する<xref:System.Data.DataTable>オブジェクト。 このクラスは、ネイティブ C++ `class` (と比較する`ref class`または`value class`)。 これは、機能は、ネイティブ コードからこのクラスを使用して、マネージ型をネイティブ コードで使用することはできませんので必要です。 このクラスは、CLR を対象にコンパイルされる、`#pragma managed`クラス宣言の前のディレクティブ。 このディレクティブの詳細については、次を参照してください。[マネージ、アンマネージ](../preprocessor/managed-unmanaged.md)します。

DatabaseClass クラスのプライベート メンバーに注意してください:`gcroot<DataTable ^> table`します。 ネイティブ型は、管理対象の型を含めることはできませんので、`gcroot`キーワードが必要です。 詳細については`gcroot`を参照してください[方法。ネイティブ型のハンドルを宣言](../dotnet/how-to-declare-handles-in-native-types.md)します。

この例では、コードの残りの部分はネイティブの C++ コードで示される、`#pragma unmanaged`ディレクティブの前`main`します。 この例では DatabaseClass の新しいインスタンスを作成していますテーブルを作成し、テーブルのいくつかの行を設定するには、そのメソッドの呼び出し。 C++ の Unicode 文字列 StringCol データベース列の値として渡されることに注意してください。 DatabaseClass、内でこれらの文字列がマーシャ リングの機能を使用して管理対象の文字列をマーシャ リング、<xref:System.Runtime.InteropServices?displayProperty=fullName>名前空間。 メソッドでは具体的には、<xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A>マーシャ リングするために使用、`wchar_t *`を<xref:System.String>、およびメソッド<xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A>マーシャ リングするために使用、<xref:System.String>を`wchar_t *`。

> [!NOTE]
>  によって割り当てられたメモリ<xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A>いずれかを呼び出して解放する必要があります<xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A>または`GlobalFree`します。

```cpp
// adonet_marshal_string_wide.cpp
// compile with: /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll
#include <comdef.h>
#include <gcroot.h>
#include <iostream>
using namespace std;

#using <System.Data.dll>
using namespace System;
using namespace System::Data;
using namespace System::Runtime::InteropServices;

#define MAXCOLS 100

#pragma managed
class DatabaseClass
{
public:
    DatabaseClass() : table(nullptr) { }

    void AddRow(wchar_t *stringColValue)
    {
        // Add a row to the table.
        DataRow ^row = table->NewRow();
        row["StringCol"] = Marshal::PtrToStringUni(
            (IntPtr)stringColValue);
        table->Rows->Add(row);
    }

    void CreateAndPopulateTable()
    {
        // Create a simple DataTable.
        table = gcnew DataTable("SampleTable");

        // Add a column of type String to the table.
        DataColumn ^column1 = gcnew DataColumn("StringCol",
            Type::GetType("System.String"));
        table->Columns->Add(column1);
    }

    int GetValuesForColumn(wchar_t *dataColumn, wchar_t **values,
        int valuesLength)
    {
        // Marshal the name of the column to a managed
        // String.
        String ^columnStr = Marshal::PtrToStringUni(
                (IntPtr)dataColumn);

        // Get all rows in the table.
        array<DataRow ^> ^rows = table->Select();
        int len = rows->Length;
        len = (len > valuesLength) ? valuesLength : len;
        for (int i = 0; i < len; i++)
        {
            // Marshal each column value from a managed string
            // to a wchar_t *.
            values[i] = (wchar_t *)Marshal::StringToHGlobalUni(
                (String ^)rows[i][columnStr]).ToPointer();
        }

        return len;
    }

private:
    // Using gcroot, you can use a managed type in
    // a native class.
    gcroot<DataTable ^> table;
};

#pragma unmanaged
int main()
{
    // Create a table and add a few rows to it.
    DatabaseClass *db = new DatabaseClass();
    db->CreateAndPopulateTable();
    db->AddRow(L"This is string 1.");
    db->AddRow(L"This is string 2.");

    // Now retrieve the rows and display their contents.
    wchar_t *values[MAXCOLS];
    int len = db->GetValuesForColumn(
        L"StringCol", values, MAXCOLS);
    for (int i = 0; i < len; i++)
    {
        wcout << "StringCol: " << values[i] << endl;

        // Deallocate the memory allocated using
        // Marshal::StringToHGlobalUni.
        GlobalFree(values[i]);
    }

    delete db;

    return 0;
}
```

```Output
StringCol: This is string 1.
StringCol: This is string 2.
```

### <a name="compiling-the-code"></a>コードのコンパイル

- コマンドラインからコードをコンパイルするには、adonet_marshal_string_wide.cpp という名前のファイルのコード例を保存し、次のステートメントを入力します。

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_wide.cpp
    ```

## <a name="marshal_variant"></a> ADO.NET の VARIANT をマーシャ リングします。

ネイティブを追加する方法を示します`VARIANT`をマーシャ リングする方法、およびデータベースを<xref:System.Object?displayProperty=fullName>をネイティブのデータベースから`VARIANT`します。

### <a name="example"></a>例

この例で、クラス DatabaseClass が作成される ADO.NET と対話する<xref:System.Data.DataTable>オブジェクト。 このクラスは、ネイティブ C++ `class` (と比較する`ref class`または`value class`)。 これは、機能は、ネイティブ コードからこのクラスを使用して、マネージ型をネイティブ コードで使用することはできませんので必要です。 このクラスは、CLR を対象にコンパイルされる、`#pragma managed`クラス宣言の前のディレクティブ。 このディレクティブの詳細については、次を参照してください。[マネージ、アンマネージ](../preprocessor/managed-unmanaged.md)します。

DatabaseClass クラスのプライベート メンバーに注意してください:`gcroot<DataTable ^> table`します。 ネイティブ型は、管理対象の型を含めることはできませんので、`gcroot`キーワードが必要です。 詳細については`gcroot`を参照してください[方法。ネイティブ型のハンドルを宣言](../dotnet/how-to-declare-handles-in-native-types.md)します。

この例では、コードの残りの部分はネイティブの C++ コードで示される、`#pragma unmanaged`ディレクティブの前`main`します。 この例では DatabaseClass の新しいインスタンスを作成していますテーブルを作成し、テーブルのいくつかの行を設定するには、そのメソッドの呼び出し。 ネイティブに注意してください`VARIANT`ObjectCol データベース列の値として渡される型。 DatabaseClass、内でこれら`VARIANT`型があるマーシャ リングの機能を使用してマネージ オブジェクトにマーシャ リング、<xref:System.Runtime.InteropServices?displayProperty=fullName>名前空間。 メソッドでは具体的には、<xref:System.Runtime.InteropServices.Marshal.GetObjectForNativeVariant%2A>マーシャ リングするために使用、`VARIANT`を<xref:System.Object>、およびメソッド<xref:System.Runtime.InteropServices.Marshal.GetNativeVariantForObject%2A>マーシャ リングするために使用、<xref:System.Object>を`VARIANT`します。

```cpp
// adonet_marshal_variant.cpp
// compile with: /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll
#include <comdef.h>
#include <gcroot.h>
#include <iostream>
using namespace std;

#using <System.Data.dll>
using namespace System;
using namespace System::Data;
using namespace System::Runtime::InteropServices;

#define MAXCOLS 100

#pragma managed
class DatabaseClass
{
public:
    DatabaseClass() : table(nullptr) { }

    void AddRow(VARIANT *objectColValue)
    {
        // Add a row to the table.
        DataRow ^row = table->NewRow();
        row["ObjectCol"] = Marshal::GetObjectForNativeVariant(
            IntPtr(objectColValue));
        table->Rows->Add(row);
    }

    void CreateAndPopulateTable()
    {
        // Create a simple DataTable.
        table = gcnew DataTable("SampleTable");

        // Add a column of type String to the table.
        DataColumn ^column1 = gcnew DataColumn("ObjectCol",
            Type::GetType("System.Object"));
        table->Columns->Add(column1);
    }

    int GetValuesForColumn(wchar_t *dataColumn, VARIANT *values,
        int valuesLength)
    {
        // Marshal the name of the column to a managed
        // String.
        String ^columnStr = Marshal::PtrToStringUni(
                (IntPtr)dataColumn);

        // Get all rows in the table.
        array<DataRow ^> ^rows = table->Select();
        int len = rows->Length;
        len = (len > valuesLength) ? valuesLength : len;
        for (int i = 0; i < len; i++)
        {
            // Marshal each column value from a managed object
            // to a VARIANT.
            Marshal::GetNativeVariantForObject(
                rows[i][columnStr], IntPtr(&values[i]));
        }

        return len;
    }

private:
    // Using gcroot, you can use a managed type in
    // a native class.
    gcroot<DataTable ^> table;
};

#pragma unmanaged
int main()
{
    // Create a table and add a few rows to it.
    DatabaseClass *db = new DatabaseClass();
    db->CreateAndPopulateTable();

    BSTR bstr1 = SysAllocString(L"This is a BSTR in a VARIANT.");
    VARIANT v1;
    v1.vt = VT_BSTR;
    v1.bstrVal = bstr1;
    db->AddRow(&v1);

    int i = 42;
    VARIANT v2;
    v2.vt = VT_I4;
    v2.lVal = i;
    db->AddRow(&v2);

    // Now retrieve the rows and display their contents.
    VARIANT values[MAXCOLS];
    int len = db->GetValuesForColumn(
        L"ObjectCol", values, MAXCOLS);
    for (int i = 0; i < len; i++)
    {
        switch (values[i].vt)
        {
            case VT_BSTR:
                wcout << L"ObjectCol: " << values[i].bstrVal << endl;
                break;
            case VT_I4:
                cout << "ObjectCol: " << values[i].lVal << endl;
                break;
            default:
                break;
        }

    }

    SysFreeString(bstr1);
    delete db;

    return 0;
}
```

```Output
ObjectCol: This is a BSTR in a VARIANT.
ObjectCol: 42
```

### <a name="compiling-the-code"></a>コードのコンパイル

- コマンドラインからコードをコンパイルするには、adonet_marshal_variant.cpp という名前のファイルのコード例を保存し、次のステートメントを入力します。

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_variant.cpp
    ```

## <a name="marshal_safearray"></a> ADO.NET の SAFEARRAY をマーシャ リングします。

ネイティブを追加する方法を示します`SAFEARRAY`データベースからをネイティブのマネージ配列をマーシャ リングする方法、およびデータベースに`SAFEARRAY`します。

### <a name="example"></a>例

この例で、クラス DatabaseClass が作成される ADO.NET と対話する<xref:System.Data.DataTable>オブジェクト。 このクラスは、ネイティブ C++ `class` (と比較する`ref class`または`value class`)。 これは、機能は、ネイティブ コードからこのクラスを使用して、マネージ型をネイティブ コードで使用することはできませんので必要です。 このクラスは、CLR を対象にコンパイルされる、`#pragma managed`クラス宣言の前のディレクティブ。 このディレクティブの詳細については、次を参照してください。[マネージ、アンマネージ](../preprocessor/managed-unmanaged.md)します。

DatabaseClass クラスのプライベート メンバーに注意してください:`gcroot<DataTable ^> table`します。 ネイティブ型は、管理対象の型を含めることはできませんので、`gcroot`キーワードが必要です。 詳細については`gcroot`を参照してください[方法。ネイティブ型のハンドルを宣言](../dotnet/how-to-declare-handles-in-native-types.md)します。

この例では、コードの残りの部分はネイティブの C++ コードで示される、`#pragma unmanaged`ディレクティブの前`main`します。 この例では DatabaseClass の新しいインスタンスを作成していますテーブルを作成し、テーブルのいくつかの行を設定するには、そのメソッドの呼び出し。 ネイティブに注意してください`SAFEARRAY`ArrayIntsCol データベース列の値として渡される型。 DatabaseClass、内でこれら`SAFEARRAY`型があるマーシャ リングの機能を使用してマネージ オブジェクトにマーシャ リング、<xref:System.Runtime.InteropServices?displayProperty=fullName>名前空間。 メソッドでは具体的には、<xref:System.Runtime.InteropServices.Marshal.Copy%2A>マーシャ リングするために使用、`SAFEARRAY`メソッドや整数のマネージ配列に<xref:System.Runtime.InteropServices.Marshal.Copy%2A>する整数のマネージ配列をマーシャ リングするために使用、`SAFEARRAY`します。

```cpp
// adonet_marshal_safearray.cpp
// compile with: /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll
#include <comdef.h>
#include <gcroot.h>
#include <iostream>
using namespace std;

#using <System.Data.dll>
using namespace System;
using namespace System::Data;
using namespace System::Runtime::InteropServices;

#define MAXCOLS 100

#pragma managed
class DatabaseClass
{
public:
    DatabaseClass() : table(nullptr) { }

    void AddRow(SAFEARRAY *arrayIntsColValue)
    {
        // Add a row to the table.
        DataRow ^row = table->NewRow();
        int len = arrayIntsColValue->rgsabound[0].cElements;
        array<int> ^arr = gcnew array<int>(len);

        int *pData;
        SafeArrayAccessData(arrayIntsColValue, (void **)&pData);
        Marshal::Copy(IntPtr(pData), arr, 0, len);
        SafeArrayUnaccessData(arrayIntsColValue);

        row["ArrayIntsCol"] = arr;
        table->Rows->Add(row);
    }

    void CreateAndPopulateTable()
    {
        // Create a simple DataTable.
        table = gcnew DataTable("SampleTable");

        // Add a column of type String to the table.
        DataColumn ^column1 = gcnew DataColumn("ArrayIntsCol",
            Type::GetType("System.Int32[]"));
        table->Columns->Add(column1);
    }

    int GetValuesForColumn(wchar_t *dataColumn, SAFEARRAY **values,
        int valuesLength)
    {
        // Marshal the name of the column to a managed
        // String.
        String ^columnStr = Marshal::PtrToStringUni(
                (IntPtr)dataColumn);

        // Get all rows in the table.
        array<DataRow ^> ^rows = table->Select();
        int len = rows->Length;
        len = (len > valuesLength) ? valuesLength : len;
        for (int i = 0; i < len; i++)
        {
            // Marshal each column value from a managed array
            // of Int32s to a SAFEARRAY of type VT_I4.
            values[i] = SafeArrayCreateVector(VT_I4, 0, 10);
            int *pData;
            SafeArrayAccessData(values[i], (void **)&pData);
            Marshal::Copy((array<int> ^)rows[i][columnStr], 0,
                IntPtr(pData), 10);
            SafeArrayUnaccessData(values[i]);
        }

        return len;
    }

private:
    // Using gcroot, you can use a managed type in
    // a native class.
    gcroot<DataTable ^> table;
};

#pragma unmanaged
int main()
{
    // Create a table and add a few rows to it.
    DatabaseClass *db = new DatabaseClass();
    db->CreateAndPopulateTable();

    // Create a standard array.
    int originalArray[] = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };

    // Create a SAFEARRAY.
    SAFEARRAY *psa;
    psa = SafeArrayCreateVector(VT_I4, 0, 10);

    // Copy the data from the original array to the SAFEARRAY.
    int *pData;
    HRESULT hr = SafeArrayAccessData(psa, (void **)&pData);
    memcpy(pData, &originalArray, 40);
    SafeArrayUnaccessData(psa);
    db->AddRow(psa);

    // Now retrieve the rows and display their contents.
    SAFEARRAY *values[MAXCOLS];
    int len = db->GetValuesForColumn(
        L"ArrayIntsCol", values, MAXCOLS);
    for (int i = 0; i < len; i++)
    {
        int *pData;
        SafeArrayAccessData(values[i], (void **)&pData);
        for (int j = 0; j < 10; j++)
        {
            cout << pData[j] << " ";
        }
        cout << endl;
        SafeArrayUnaccessData(values[i]);

        // Deallocate the memory allocated using
        // SafeArrayCreateVector.
        SafeArrayDestroy(values[i]);
    }

    SafeArrayDestroy(psa);
    delete db;

    return 0;
}
```

```Output
0 1 2 3 4 5 6 7 8 9
```

### <a name="compiling-the-code"></a>コードのコンパイル

- コマンドラインからコードをコンパイルするには、adonet_marshal_safearray.cpp という名前のファイルのコード例を保存し、次のステートメントを入力します。

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_safearray.cpp
    ```

## <a name="net-framework-security"></a>.NET Framework セキュリティ

ADO.NET に関連するセキュリティ問題については、次を参照してください。 [ADO.NET アプリケーションのセキュリティで保護する](/dotnet/framework/data/adonet/securing-ado-net-applications)します。

## <a name="related-sections"></a>関連項目

|セクション|説明|
|-------------|-----------------|
|[ADO.NET](/dotnet/framework/data/adonet/index)|ADO.NET では、一連の .NET プログラマにデータ アクセス サービスを公開するクラスの概要を示します。|

## <a name="see-also"></a>関連項目

[C++/CLI (Visual C++) による .NET プログラミング](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

[ネイティブと .NET の相互運用性](../dotnet/native-and-dotnet-interoperability.md)

<xref:System.Runtime.InteropServices>

[相互運用性](/dotnet/framework/interop/index)
