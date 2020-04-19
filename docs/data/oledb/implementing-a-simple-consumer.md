---
title: 単純なコンシューマーの実装
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumers, implementing
ms.assetid: 13828167-23a4-4e94-8b6c-878262fda464
ms.openlocfilehash: 67bce55a19a2aaaf3a8cbb62d7db228513e93c91
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707529"
---
# <a name="implementing-a-simple-consumer"></a>単純なコンシューマーの実装

::: moniker range="vs-2019"

ATL OLE DB コンシューマー ウィザードは、Visual Studio 2019 以降では使用できません。 ただし、この機能を手動で追加することは可能です。 詳細については、「[ウィザードを使用しないコンシューマーの作成](creating-a-consumer-without-using-a-wizard.md)」を参照してください。

::: moniker-end

::: moniker range="<=vs-2017"

次のトピックでは、**MFC アプリケーション ウィザード**と **ATL OLE DB コンシューマー ウィザード**によって作成されたファイルを編集し、単純なコンシューマーを作成する方法を説明します。 この例には次の項目があります。

- 「[コンシューマーによるデータの取得](#retrieve)」では、データベース テーブルからすべてのデータを 1 行ずつ読み取るコードをコンシューマーに実装する方法を説明します。

- 「[コンシューマーへのブックマーク サポートの追加](#bookmark)」では、コンシューマーにブックマークのサポートを追加する方法を説明します。

> [!NOTE]
> このセクションで説明されているコンシューマー アプリケーションを使用して、サンプル プロバイダー `MyProv` と `Provider` をテストできます。

> [!NOTE]
> コンシューマー アプリケーションを構築して `MyProv` (「[単純な読み取り専用プロバイダーの機能の拡張](../../data/oledb/enhancing-the-simple-read-only-provider.md)」で説明されているサンプル プロバイダー) をテストするには、「[コンシューマーへのブックマーク サポートの追加](#bookmark)」の説明に従ってブックマーク サポートを含める必要があります。

## <a name="retrieve" ></a> コンシューマーによるデータの取得

### <a name="to-modify-the-console-application-to-use-the-ole-db-consumer"></a>OLE DB コンシューマーを使用するようコンソール アプリケーションを変更するには

1. `MyCons.cpp` で、次のように太字のテキストを挿入してメインのコードを変更します。

    ```cpp
    // MyCons.cpp : Defines the entry point for the console application.
    //
    #include "stdafx.h"
    #include "Products.h"
    ...
    int main(int argc, char* argv[])
    {
       HRESULT hr = CoInitialize(NULL);   // Instantiate rowset
       CProducts rs;
       hr = rs.OpenAll();
       ATLASSERT(SUCCEEDED(hr ) );
       hr = rs.MoveFirst();   // Iterate through the rowset
       while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )   {      // Print out the column information for each row
         printf("Product ID: %d, Name: %s, Unit Price: %d, Quantity per Unit: %d, Units in Stock %d, Reorder Level %d\n",
           rs.m_ProductID, rs.m_ProductName, rs.m_UnitPrice, rs.m_QuantityPerUnit, rs.m_UnitsInStock, rs.m_ReorderLevel );
         hr = rs.MoveNext();   }
       rs.Close();
       rs.ReleaseCommand();
       CoUninitialize();

       return 0;
    }
    ```

## <a name="bookmark" ></a> コンシューマーへのブックマーク サポートの追加

ブックマークは、テーブル内の行を一意に識別する列です。 通常はキー列ですが、プロバイダーによってはそうでない場合もあります。 このセクションでは、ブックマーク サポートを追加する方法を説明します。 これを行うには、ユーザー レコード クラスで次の手順を実行する必要があります。

- ブックマークをインスタンス化します。 これらは [CBookmark](../../data/oledb/cbookmark-class.md) 型のオブジェクトです。

- `DBPROP_IRowsetLocate` プロパティを設定して、プロバイダーにブックマーク列を要求します。

- [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md) マクロを使用して、列マップにブックマーク エントリを追加します。

上の手順で、ブックマーク サポートと使用するブックマーク オブジェクトが得られました。 このコード例では、次の手順でブックマークの使用例を示します。

- 書き込み用にファイルを開きます。

- 行セットのデータを 1 行ずつファイルに出力します。

- [MoveToBookmark](../../data/oledb/crowset-movetobookmark.md) を呼び出して、行セットのカーソルをブックマークに移動します。

- ブックマークが設定された行を、ファイルの末尾に追加することで出力します。

> [!NOTE]
> このコンシューマー アプリケーションを使用して `Provider` サンプル プロバイダー アプリケーションをテストする場合、このセクションで説明されているブックマーク サポートは省略します。

### <a name="to-instantiate-the-bookmark"></a>ブックマークをインスタンス化するには

1. アクセサーで [CBookmark](../../data/oledb/cbookmark-class.md) 型のオブジェクトを保持する必要があります。 *nSize* パラメーターは、ブックマークのバッファーのサイズをバイト単位で指定します (通常、32 ビット プラットフォームの場合は 4、64 ビット プラットフォームの場合は 8 です)。 ユーザー レコード クラスの列データ メンバーに次の宣言を追加します。

    ```cpp
    //////////////////////////////////////////////////////////////////////
    // Products.h
    class CProductsAccessor
    {
    public:
       CBookmark<4> m_bookmark;   // Add bookmark declaration
       LONG m_ProductID;
       ...
    ```

### <a name="to-request-a-bookmark-column-from-the-provider"></a>プロバイダーにブックマーク列を要求するには

1. ユーザー レコード クラスの `GetRowsetProperties` メソッドに次のコードを追加します。

    ```cpp
    // Set the DBPROP_IRowsetLocate property.
    void GetRowsetProperties(CDBPropSet* pPropSet)
    {
       pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
       pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
       // Add DBPROP_IRowsetLocate property to support bookmarks   pPropSet->AddProperty(DBPROP_IRowsetLocate, true);
    }
    ```

### <a name="to-add-a-bookmark-entry-to-the-column-map"></a>列マップにブックマーク エントリを追加するには

1. ユーザー レコード クラスの列マップに次のエントリを追加します。

    ```cpp
    // Set a bookmark entry in the column map.
    BEGIN_COLUMN_MAP(CProductsAccessor)
       BOOKMARK_ENTRY(m_bookmark)   // Add bookmark entry
       COLUMN_ENTRY_LENGTH_STATUS(1, m_ProductID, m_dwProductIDLength, m_dwProductIDStatus)
       COLUMN_ENTRY_LENGTH_STATUS(2, m_ProductName, m_dwProductNameLength, m_dwProductNameStatus)
    ...
    END_COLUMN_MAP()
    ```

### <a name="to-use-a-bookmark-in-your-main-code"></a>メインのコードでブックマークを使用するには

1. 以前に作成したコンソール アプリケーションの `MyCons.cpp` ファイルで、次のようにメインのコードを変更します。 ブックマークを使用するには、メインのコードで独自のブックマーク オブジェクト (`myBookmark`) をインスタンス化する必要があります。これは、アクセサーのブックマーク (`m_bookmark`) とは別のものです。

    ```cpp
    ///////////////////////////////////////////////////////////////////////
    // MyCons.cpp : Defines the entry point for the console application.
    //

    #include "stdafx.h"
    #include "Products.h"
    #include <iostream>
    #include <fstream>
    using namespace std;

    int _tmain(int argc, _TCHAR* argv[])
    {
       HRESULT hr = CoInitialize(NULL);

       // Instantiate rowset
       CProducts rs;

       hr = rs.OpenAll();
       hr = rs.MoveFirst();

       // Cast CURRENCY m_UnitPrice to a long value
       LONGLONG lPrice = rs.m_UnitPrice.int64;

       // Open file output.txt for writing in overwrite mode
       ofstream outfile( "C:\\output.txt", ios::out );

       if (!outfile)      // Test for invalid file
          return -1;

       // Instantiate a bookmark object myBookmark for the main code
       CBookmark<4> myBookmark;
       int nCounter = 0;

       // Iterate through the rowset and output column data to output.txt row by row
       // In the file, mark the beginning of this set of data:
       outfile << "initial row dump" << endl;
       while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )
       {
          nCounter++;
          if(nCounter == 5 )
             myBookmark = rs.m_bookmark;
          // Output the column information for each row:
          outfile << rs.m_ProductID << rs.m_ProductName << lPrice << rs.m_QuantityPerUnit << rs.m_UnitsInStock << rs.m_ReorderLevel << endl;
          hr = rs.MoveNext();
       }

       // Move cursor to bookmark
       hr = rs.MoveToBookmark(myBookmark);

       // Iterate through the rowset and output column data to output.txt row by row
       // In the file, mark the beginning of this set of data:
       outfile << "row dump starting from bookmarked row" << endl;
       while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )
       {
          // Output the column information for each row
          outfile << rs.m_ProductID << rs.m_ProductName << lPrice << rs.m_QuantityPerUnit << rs.m_UnitsInStock << rs.m_ReorderLevel << endl;
          hr = rs.MoveNext();
       }

       rs.CloseAll();
       CoUninitialize();

       return 0;
    }
    ```

ブックマークの詳細については、「[ブックマークの使用](../../data/oledb/using-bookmarks.md)」を参照してください。 ブックマークの例は、「[行セットの更新](../../data/oledb/updating-rowsets.md)」にもあります。

::: moniker-end

## <a name="see-also"></a>関連項目

[ウィザードを使用した OLE DB コンシューマーの作成](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)
