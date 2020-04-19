---
title: 行セットでの複数アクセサーの使用
ms.date: 10/24/2018
helpviewer_keywords:
- BEGIN_ACCESSOR macro
- BEGIN_ACCESSOR macro, multiple accessors
- rowsets [C++], multiple accessors
- accessors [C++], rowsets
ms.assetid: 80d4dc5d-4940-4a28-a4ee-d8602f71d2a6
ms.openlocfilehash: d1ab314edeebedef4cff14cd5364a7ca16c74769
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62216383"
---
# <a name="using-multiple-accessors-on-a-rowset"></a>行セットでの複数アクセサーの使用

複数のアクセサーを使用する必要がある 3 つの基本的なシナリオがあります。

- **複数の読み取り/書き込み行セット。** このシナリオでは、主キーを持つテーブルを作成します。 主キーを含め、行内のすべての列を読めるようにするには。 (主キー列を記述することはできません) ために、主キーを除くすべての列にデータを書き込むことができることもできます。 この場合、2 つのアクセサーを設定します。

  - 0 のアクセサーには、すべての列が含まれています。

  - アクセサーが 1 には、主キーを除くすべての列が含まれています。

- **パフォーマンス。** このシナリオでは、大量のデータ、たとえば、グラフィック、サウンド、ファイルまたはビデオ ファイルを 1 つまたは複数の列であります。 行に移動するたびに可能性がありますしない大きなデータ ファイルを列を取得するため、これは、アプリケーションのパフォーマンスが低下はので。

  最初のアクセサーに大きなデータは、1 つを除くすべての列が含まれていて、これらの列からデータを自動的に取得に別のアクセサーを設定することができます。最初のアクセサーは、自動アクセサーです。 2 番目のアクセサーは、大きなデータを保持している列のみを取得しますが、この列からデータを自動的に取得がありません。 その他のメソッドを更新またはオンデマンドで大規模なデータをフェッチすることができます。

  - アクセサー 0 は自動アクセサーです。大規模なデータを 1 つを除くすべての列を取得します。

  - アクセサーが 1 のない自動アクセサー。大きなデータ列を取得します。

  アクセサーが自動アクセサーであるかどうかを指定するのにには、自動引数を使用します。

- **複数の ISequentialStream 列。** このシナリオでは、複数の列の保持した`ISequentialStream`データ。 ただし、各アクセサーが 1 つに制限は`ISequentialStream`データ ストリーム。 この問題を解決するを設定する複数のアクセサーでは、それぞれが 1 つ`ISequentialStream`ポインター。

使用してアクセサーを作成する、 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)と[END_ACCESSOR](../../data/oledb/end-accessor.md)マクロ。 使用することも、 [db_accessor](../../windows/db-accessor.md)属性。 (アクセサーの詳細については[ユーザー レコード](../../data/oledb/user-records.md))。マクロまたは属性は、アクセサーが自動または非自動アクセサーがかどうかを指定します。

- 移動方法など、自動のアクセサーで`MoveFirst`、 `MoveLast`、 `MoveNext`、および`MovePrev`列を自動的に指定されたすべてのデータを取得します。 アクセサー 0 は、自動のアクセサーを指定する必要があります。

- 取得は、非自動アクセサーでなどのメソッドを明示的に呼び出したまで発生しません`Update`、 `Insert`、 `Fetch`、または`Delete`します。 前述のシナリオで移動するたびにすべての列を取得する可能性がありますされません。 別のアクセサーに 1 つまたは複数の列を配置でき、次に示すように、非自動アクセサーあることができます。

次の例では、複数のアクセサーを使用して SQL Server pubs データベースのジョブ テーブルを読み書きする複数のアクセサーを使用します。 この例は、複数のアクセサーの最も一般的な使用上記の「複数の読み取り/書き込み行セット」シナリオを参照してください。

ユーザー レコード クラスは次のとおりです。 2 つのアクセサーを設定します。 0 のアクセサーには、主キー列 (ID) のみが含まれています。 と 1 のアクセサーに他の列が含まれています。

```cpp
class CJobs
{
public:
    enum {
        sizeOfDescription = 51
    };

    short nID;
    char szDescription[ sizeOfDescription ];
    short nMinLvl;
    short nMaxLvl;

    DWORD dwID;
    DWORD dwDescription;
    DWORD dwMinLvl;
    DWORD dwMaxLvl;

BEGIN_ACCESSOR_MAP(CJobs, 2)
    // Accessor 0 is the automatic accessor
    BEGIN_ACCESSOR(0, true)
        COLUMN_ENTRY_STATUS(1, nID, dwID)
    END_ACCESSOR()
    // Accessor 1 is the non-automatic accessor
    BEGIN_ACCESSOR(1, true)
        COLUMN_ENTRY_STATUS(2, szDescription, dwDescription)
        COLUMN_ENTRY_STATUS(3, nMinLvl, dwMinLvl)
        COLUMN_ENTRY_STATUS(4, nMaxLvl, dwMaxLvl)
    END_ACCESSOR()
END_ACCESSOR_MAP()
};
```

メインのコードは次のとおりです。 呼び出す`MoveNext`アクセサー 0 を使用して主キー列の ID から自動的にデータを取得します。 注方法、`Insert`主キー列への書き込みを回避するために使用アクセサー 1 近くメソッド。

```cpp
int main(int argc, char* argv[])
{
    // Initialize COM
    ::CoInitialize(NULL);

    // Create instances of the data source and session
    CDataSource source;
    CSession session;
    HRESULT hr = S_OK;

    // Set initialization properties
    CDBPropSet dbinit(DBPROPSET_DBINIT);
    dbinit.AddProperty(DBPROP_AUTH_USERID, OLESTR("my_user_id"));
    dbinit.AddProperty(DBPROP_INIT_CATALOG, OLESTR("pubs"));
    dbinit.AddProperty(DBPROP_INIT_DATASOURCE, OLESTR("(local)"));

    hr = source.Open("SQLOLEDB.1", &dbinit);
    if (hr == S_OK)
    {
        hr = session.Open(source);
        if (hr == S_OK)
        {
            // Ready to fetch/access data
            CTable<CAccessor<CJobs>> jobs;

            // Set properties for making the rowset a read/write cursor
            CDBPropSet dbRowset(DBPROPSET_ROWSET);
            dbRowset.AddProperty(DBPROP_CANFETCHBACKWARDS, true);
            dbRowset.AddProperty(DBPROP_CANSCROLLBACKWARDS, true);
            dbRowset.AddProperty(DBPROP_IRowsetChange, true);
            dbRowset.AddProperty(DBPROP_UPDATABILITY,
                DBPROPVAL_UP_INSERT | DBPROPVAL_UP_CHANGE |
                DBPROPVAL_UP_DELETE);

            hr = jobs.Open(session, "jobs", &dbRowset);
            if (hr == S_OK)
            {
                // Calling MoveNext automatically retrieves ID
                // (using accessor 0)
                while(jobs.MoveNext() == S_OK)
                   printf_s("Description = %s\n", jobs.szDescription);

                hr = jobs.MoveFirst();
                if (hr == S_OK)
                {
                    jobs.nID = 25;
                    strcpy_s(&jobs.szDescription[0],
                             jobs.sizeOfDescription,
                             "Developer");
                    jobs.nMinLvl = 10;
                    jobs.nMaxLvl = 20;

                    jobs.dwDescription = DBSTATUS_S_OK;
                    jobs.dwID = DBSTATUS_S_OK;
                    jobs.dwMaxLvl = DBSTATUS_S_OK;
                    jobs.dwMinLvl = DBSTATUS_S_OK;

                    // Insert method uses accessor 1
                    // (to avoid writing to the primary key column)
                    hr = jobs.Insert(1);
                }
                jobs.Close();
            }
            session.Close();
        }
        source.Close();
    }

    // Uninitialize COM
    ::CoUninitialize();
    return 0;
}
```

## <a name="see-also"></a>関連項目

[アクセサーの使用](../../data/oledb/using-accessors.md)<br/>
[ユーザー レコード](../../data/oledb/user-records.md)
