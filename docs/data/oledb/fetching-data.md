---
title: データのフェッチ
ms.date: 10/19/2018
helpviewer_keywords:
- data [C++], fetching
- rowsets [C++], fetching
- fetching
- OLE DB consumer templates [C++], fetching data
ms.assetid: b07f747f-9855-4f27-a03d-b1d5b10fa284
ms.openlocfilehash: 441f036d1677806e81bc419ec6a45e810e63a34f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409060"
---
# <a name="fetching-data"></a>データのフェッチ

データ ソース、セッション、および行セット オブジェクトを開いた後は、データをフェッチできます。 、を使用するアクセサーの種類によっては、列をバインドする必要があります。

## <a name="to-fetch-data"></a>データをフェッチするには

1. 適切なを使用して行セットを開く**オープン**コマンド。

1. 使用している場合`CManualAccessor`、これをまだ完了していない場合は、出力列をバインドします。 次の例がから取得した、 [DBViewer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/dbviewer)サンプル。 列をバインドするには、呼び出す`GetColumnInfo`、し、次の例に示すように、バインドでアクセサーを作成します。

    ```cpp
    // From the DBViewer Sample CDBTreeView::OnQueryEdit
    // Get the column information
    ULONG ulColumns       = 0;
    DBCOLUMNINFO* pColumnInfo  = NULL;
    LPOLESTR pStrings      = NULL;
    if (rs.GetColumnInfo(&ulColumns, &pColumnInfo, &pStrings) != S_OK)
        ThrowMyOLEDBException(rs.m_pRowset, IID_IColumnsInfo);
    struct MYBIND* pBind = new MYBIND[ulColumns];
    rs.CreateAccessor(ulColumns, &pBind[0], sizeof(MYBIND)*ulColumns);
    for (ULONG l=0; l<ulColumns; l++)
    rs.AddBindEntry(l+1, DBTYPE_STR, sizeof(TCHAR)*40, &pBind[l].szValue, NULL, &pBind[l].dwStatus);
    rs.Bind();
    ```

1. 書き込みを**中**ループを使用してデータを取得します。 ループでは、呼び出す`MoveNext`カーソルを進めるし、次の例に示すように、S_OK に対して戻り値をテストします。

    ```cpp
    while (rs.MoveNext() == S_OK)
    {
        // Add code to fetch data here
        // If you are not using an auto accessor, call rs.GetData()
    }
    ```

1. 内で、**中**ループ、アクセサーの型に従ってデータをフェッチできます。

   - 使用する場合、 [CAccessor](../../data/oledb/caccessor-class.md)クラス、データ メンバーを含んでいるユーザー レコードが必要です。 次の例に示すようにそのデータ メンバーを使用してデータにアクセスすることができます。

        ```cpp
        while (rs.MoveNext() == S_OK)
        {
            // Use the data members directly. In this case, m_nFooID
            // is declared in a user record that derives from
            // CAccessor
            wsprintf_s("%d", rs.m_nFooID);
        }
        ```

   - 使用する場合、`CDynamicAccessor`または`CDynamicParameterAccessor`クラスにアクセスする関数を使用してデータをフェッチできます`GetValue`と`GetColumn`次の例のようにします。 使用するデータの種類を決定する場合を使用して、`GetType`します。

        ```cpp
        while (rs.MoveNext() == S_OK)
        {
            // Use the dynamic accessor functions to retrieve your data.

            ULONG ulColumns = rs.GetColumnCount();
            for (ULONG i=0; i<ulColumns; i++)
            {
                rs.GetValue(i);
            }
        }
        ```

   - 使用する場合`CManualAccessor`、独自のデータ メンバーを指定、自分でバインドおよび次の例に示すように、直接アクセスする必要があります。

        ```cpp
        while (rs.MoveNext() == S_OK)
        {
            // Use the data members you specified in the calls to
            // AddBindEntry.

            wsprintf_s("%s", szFoo);
        }
        ```

## <a name="see-also"></a>関連項目

[OLE DB コンシューマー テンプレートの操作](../../data/oledb/working-with-ole-db-consumer-templates.md)
