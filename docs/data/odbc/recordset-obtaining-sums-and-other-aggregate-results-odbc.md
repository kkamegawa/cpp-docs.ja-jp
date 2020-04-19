---
title: 'レコードセット: 合計とその他の集計結果 (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- SQL, retrieving aggregate values from recordsets
- recordsets, retrieving SQL aggregate values
- retrieving SQL aggregate values from recordsets
- ODBC recordsets, retrieving SQL aggregate values
- SQL aggregate values
- SQL Server projects, retrieving aggregate values from recordsets
- SQL aggregate values, retrieving from recordsets
ms.assetid: 94500662-22a4-443e-82d7-acbe6eca447b
ms.openlocfilehash: 29906366e6e9a5a852fcf40d9e7ecc8593d1b0b0
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707842"
---
# <a name="recordset-obtaining-sums-and-other-aggregate-results-odbc"></a>レコードセット: 合計とその他の集計結果 (ODBC)

> [!NOTE] 
> MFC ODBC コンシューマー ウィザードは、Visual Studio 2019 以降はご利用いただけなくなります。 引き続き、コンシューマーを手動で作成することはできます。

このトピックの内容は、MFC ODBC クラスに該当します。

このトピックでは、次の [SQL](../../data/odbc/sql.md) キーワードを使用して集計の結果を取得する方法について説明します。

- **SUM** では、数値データ型の列において値の合計を計算します。

- **MIN** では、数値データ型の列において最小値を抽出します。

- **MAX** では、数値データ型の列において最大値を抽出します。

- **AVG** では、数値データ型の列において、すべての値の平均値を計算します。

- **COUNT** では、任意のデータ型の列においてレコードの数をカウントします。

これらの SQL 関数は、データ ソースからレコードを抽出するためではなく、データ ソース内のレコードに関する統計情報を取得するために使用します。 作成されるレコードセットは通常、1 つの値を含む 1 つのレコードで構成されます (すべての列が集計列である場合)。 (**GROUP BY** 句を使用した場合は、複数のレコードがある可能性があります。)この値は SQL 関数によって実行された計算または抽出の結果です。

> [!TIP]
>  SQL **GROUP BY** 句 (および場合によって **HAVING** 句) を SQL ステートメントに追加するには、`m_strFilter`の末尾に追加します。 次に例を示します。

```
m_strFilter = "sales > 10 GROUP BY SALESPERSON_ID";
```

列をフィルターおよび並べ替えすることによって、集計結果を得るために使用するレコードの数を制限できます。

> [!CAUTION]
>  一部の集計演算子では、集計される列とは異なるデータ型が返されます。

- **SUM** および **AVG** では、次に大きいデータ型が返される場合があります (たとえば、`int` を使用した呼び出しで **LONG** や **double** が返されます)。

- **COUNT** では通常、ターゲット列の型に関係なく **LONG** が返されます。

- **MAX** および **MIN** では、計算する列と同じデータ型が返されます。

     たとえば、**クラスの追加**ウィザードでは、Sales 列に対応する `long` `m_lSales` が作成されますが、集計結果を対応するためには、これを `double m_dblSumSales` データ メンバーに置き換える必要があります。 次の例を参照してください。

#### <a name="to-obtain-an-aggregate-result-for-a-recordset"></a>レコードセットの集計結果を取得するには

1. 「[MFC ODBC コンシューマーの追加](../../mfc/reference/adding-an-mfc-odbc-consumer.md)」の説明に従って、集計結果を取得する基になる列を含むレコードセットを作成します。

1. レコードセットの [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) 関数を変更します。 列名を表す文字列 ([RFX](../../data/odbc/record-field-exchange-using-rfx.md) 関数呼び出しの 2 番目の引数) を、列の集計関数を表す文字列に置き換えます。 たとえば、次を置き換えるとします。

    ```
    RFX_Long(pFX, "Sales", m_lSales);
    ```

     次の内容に置き換えます。

    ```
    RFX_Double(pFX, "Sum(Sales)", m_dblSumSales)
    ```

1. レコードセットを開きます。 集計操作の結果は `m_dblSumSales` に残されています。

> [!NOTE]
>  ウィザードでは、実際にはハンガリアン記法の接頭辞を付けずにデータ メンバー名が割り当てられます。 たとえば、ウィザードによって Sales 列に対して生成されるのは、先ほどの説明に使用した `m_lSales` 名ではなく、`m_Sales` です。

データを表示するために [CRecordView](../../mfc/reference/crecordview-class.md) クラスを使用している場合は、新しいデータ メンバー値を表示するように DDX 関数呼び出しを変更する必要があります。この場合、以下を変更します。

```
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_lSales, m_pSet);
```

移動先:

```
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_dblSumSales, m_pSet);
```

## <a name="see-also"></a>関連項目

[レコードセット (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[レコードセット: レコードセットでのレコード選択のしくみ (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)