---
title: 動的アクセサーの使用
ms.date: 10/18/2018
helpviewer_keywords:
- accessors [C++], dynamic
- dynamic accessors
ms.assetid: e5d5bfa6-2b1d-49d0-8ced-914666422431
ms.openlocfilehash: 4539247894c3980464e744c76cea450324372382
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403062"
---
# <a name="using-dynamic-accessors"></a>動的アクセサーの使用

動的アクセサーを使用すると、データベース スキーマ (構造体の基になる) の知識があるない場合にデータ ソースにアクセスできます。 OLE DB テンプレート ライブラリに役立ついくつかのクラスを提供します。

[DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer)サンプル動的アクセサー クラスを使用して、列の情報を取得し、動的にアクセサーを作成する方法を示しています。

## <a name="using-cdynamicaccessor"></a>CDynamicAccessor を使用します。

[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)データベース スキーマ (データベースの基になる構造) の知識があるない場合にデータ ソースにアクセスすることができます。 `CDynamicAccessor` メソッドは、列名、数、およびデータ型などの列情報を取得します。 実行時に動的にアクセサーを作成するのにには、この列の情報を使用します。 列情報が作成され、このクラスで管理されるバッファーに格納されます。 使用してバッファーからデータを取得、 [GetValue](../../data/oledb/cdynamicaccessor-getvalue.md)メソッド。

## <a name="example"></a>例

```cpp
// Using_Dynamic_Accessors.cpp
// compile with: /c /EHsc
#include <stdio.h>
#include <objbase.h>
#include <atldbcli.h>

int main(int argc, char* argv[] )
{
    HRESULT hr = CoInitialize(NULL );

    CDataSource ds;
    CSession ss;

    CTable<CDynamicAccessor> rs;

    // The following is an example initialization string:
    hr = ds.OpenFromInitializationString(L"Provider=SQLOLEDB.1;"
      L"Integrated Security=SSPI;Persist Security Info=False;"
      L"Initial Catalog=Loginname;Data Source=your_data_source;"
      L"Use Procedure for Prepare=1;Auto Translate=True;"
      L"Packet Size=4096;Workstation ID=LOGINNAME01;"
      L"Use Encryption for Data=False;"
      L"Tag with column collation when possible=False");

    hr = ss.Open(ds );
    hr = rs.Open(ss, "Shippers" );

    hr = rs.MoveFirst();
    while(SUCCEEDED(hr ) && hr != DB_S_ENDOFROWSET )
    {
        for(size_t i = 1; i <= rs.GetColumnCount(); i++ )
        {
            DBTYPE type;
            rs.GetColumnType(i, &type );
            printf_s( "Column %d [%S] is of type %d\n",
                      i, rs.GetColumnName(i ), type );

            switch(type )
            {
                case DBTYPE_WSTR:
                    printf_s( "value is %S\n",
                              (WCHAR*)rs.GetValue(i ) );
                break;
                case DBTYPE_STR:
                    printf_s( "value is %s\n",
                              (CHAR*)rs.GetValue(i ) );
                default:
                    printf_s( "value is %d\n",
                              *(long*)rs.GetValue(i ) );
            }
        }
        hr = rs.MoveNext();
    }

    rs.Close();
    ss.Close();
    ds.Close();
    CoUninitialize();

    return 0;
}
```

## <a name="using-cdynamicstringaccessor"></a>CDynamicStringAccessor を使用します。

[CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md)と同様に動作[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)、1 つの重要な点を除きます。 中に`CDynamicAccessor`、プロバイダーによって報告されたネイティブ形式でデータを要求`CDynamicStringAccessor`要求プロバイダーが文字列データとしてデータ ストアからすべてのデータをフェッチします。 プロセスは単純なタスクを表示またはデータ ストアの内容を印刷するなど、データ ストア内の値の計算を必要としない場合に特に役立ちます。

使用`CDynamicStringAccessor`列情報を取得するメソッド。 実行時に動的にアクセサーを作成するのにには、この列の情報を使用します。 列の情報は、このクラスによって作成および管理のバッファーに格納されます。 使用してバッファーからデータを取得[cdynamicstringaccessor::getstring](../../data/oledb/cdynamicstringaccessor-getstring.md)を使用して、バッファーに格納または[cdynamicstringaccessor::setstring](../../data/oledb/cdynamicstringaccessor-setstring.md)します。

## <a name="example"></a>例

```cpp
// Using_Dynamic_Accessors_b.cpp
// compile with: /c /EHsc
#include <stdio.h>
#include <objbase.h>
#include <atldbcli.h>

int main(int argc, char* argv[] )
{
    HRESULT hr = CoInitialize(NULL );
    if (hr != S_OK)
    {
        exit (-1);
    }

    CDataSource ds;
    CSession ss;

    CTable<CDynamicStringAccessor> rs;

    // The following is an example initialization string:
    hr = ds.OpenFromInitializationString(L"Provider=SQLOLEDB.1;"
      L"Integrated Security=SSPI;Persist Security Info=False;"
      L"Initial Catalog=Loginname;Data Source=your_data_source;"
      L"Use Procedure for Prepare=1;Auto Translate=True;"
      L"Packet Size=4096;Workstation ID=LOGINNAME01;"
      L"Use Encryption for Data=False;"
      L"Tag with column collation when possible=False");

    hr = ss.Open(ds );
    hr = rs.Open(ss, "Shippers" );

    hr = rs.MoveFirst();
    while(SUCCEEDED(hr ) && hr != DB_S_ENDOFROWSET )
    {
        for(size_t i = 1; i <= rs.GetColumnCount(); i++ )
        {
            printf_s( "column %d value is %s\n",
                      i, rs.GetString(i ) );
        }
        hr = rs.MoveNext();
    }

    rs.Close();
    ss.Close();
    ds.Close();
    CoUninitialize();

   return 0;
}
```

## <a name="using-cdynamicparameteraccessor"></a>Using CDynamicParameterAccessor

[CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)のような[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)ことを除いて、`CDynamicParameterAccessor`呼び出すことによって設定されるパラメーター情報を取得、 [ICommandWithParameters](/sql/relational-databases/native-client-ole-db-interfaces/icommandwithparameters)インターフェイス。 コンシューマーがこのクラスを使用するには、プロバイダーで `ICommandWithParameters` がサポートされている必要があります。

パラメーター情報は、このクラスによって作成および管理されるバッファーに格納されます。 使用して、バッファーからパラメーター データを取得[cdynamicparameteraccessor::getparam](../../data/oledb/cdynamicparameteraccessor-getparam.md)と[Cdynamicparameteraccessor:getparamtype](../../data/oledb/cdynamicparameteraccessor-getparamtype.md)します。

このクラスを使用して、SQL Server のストアド プロシージャを実行し、出力パラメーターの値を取得する方法を示す例では、次を参照してください、 [DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer)サンプル コード、 [Microsoft VCSamples](https://github.com/Microsoft/VCSamples) 。GitHub のリポジトリ。

## <a name="see-also"></a>関連項目

[アクセサーの使用](../../data/oledb/using-accessors.md)<br/>
[CDynamicAccessor クラス](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessor クラス](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
[CDynamicParameterAccessor クラス](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[DynamicConsumer サンプル](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer)
