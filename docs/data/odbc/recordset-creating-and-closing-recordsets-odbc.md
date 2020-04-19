---
title: レコードセット:レコードセットの作成と破棄 (ODBC)
ms.date: 05/09/2019
helpviewer_keywords:
- ODBC recordsets, creating
- recordsets, creating
- recordsets, opening
- recordsets, closing
- ODBC recordsets, closing
- ODBC recordsets, opening
ms.assetid: 8d2aac23-4396-4ce2-8c60-5ecf1b360d3d
ms.openlocfilehash: b4896dff711d87db05334afc0345c15da2fa23e6
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707992"
---
# <a name="recordset-creating-and-closing-recordsets-odbc"></a>レコードセット:レコードセットの作成と破棄 (ODBC)

> [!NOTE] 
> MFC ODBC コンシューマー ウィザードは、Visual Studio 2019 以降では利用できません。 ただし、手動でコンシューマーを作成することはできます。

このトピックの内容は、MFC ODBC クラスに該当します。

レコードセットを使用するには、レコードセット オブジェクトを構築してから、そのメンバー関数 `Open` を呼び出して、レコードセットのクエリを実行し、レコードを選択します。 レコードセットを使用し終えたら、オブジェクトを閉じて破棄します。

このトピックでは、次の内容について説明します。

- [レコードセット オブジェクトを作成するタイミングと方法](#_core_creating_recordsets_at_run_time)。

- [レコードセットの動作を、パラメーター化、フィルター処理、並べ替え、またはロックすることで、絞り込むタイミングと方法](#_core_setting_recordset_options)。

- [レコードセット オブジェクトを閉じるタイミングと方法](#_core_closing_a_recordset)。

##  <a name="_core_creating_recordsets_at_run_time"></a> 実行時にレコードセットを作成する

プログラムでレコードセット オブジェクトを作成するには、通常、事前にアプリケーション固有のレコードセット クラスを記述します。 この準備手順の詳細については、「[Adding an MFC ODBC Consumer](../../mfc/reference/adding-an-mfc-odbc-consumer.md)」 (MFC ODBC コンシューマーの追加) を参照してください。

データ ソースからレコードを選択する必要がある場合は、ダイナセットまたはスナップショット オブジェクトを開きます。 作成するオブジェクトの種類は、アプリケーションでデータを使って行う必要があることと、ご利用の ODBC ドライバーでサポートされていることによって異なります。 詳細については、「[ダイナセット](../../data/odbc/dynaset.md)」と「[スナップショット](../../data/odbc/snapshot.md)」を参照してください。

#### <a name="to-open-a-recordset"></a>レコードセットを開くには

1. `CRecordset` 派生クラスのオブジェクトを構築します。

   オブジェクトは、ヒープまたは関数のスタック フレーム オブジェクト上に構築できます。

1. 必要に応じてレコードセットの既定の動作を変更します。 使用可能なオプションについては、「[レコードセットのオプションを設定する](#_core_setting_recordset_options)」を参照してください。

1. オブジェクトのメンバー関数 [Open](../../mfc/reference/crecordset-class.md#open) を呼び出します。

コンストラクターで、ポインターを `CDatabase` オブジェクトに渡すか、NULL を渡して、フレームワークによって構築され、メンバー関数 [GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect) によって返される接続文字列に基づいて開かれる一時的なデータベース オブジェクトを使用します。 `CDatabase` オブジェクトは、データ ソースに既に接続されている場合があります。

`Open` への呼び出しでは、SQL を使用してデータ ソースからレコードが選択されます。 選択された最初のレコード (ある場合) が現在のレコードです。 このレコードのフィールドの値は、レコードセット オブジェクトのフィールド データ メンバーに格納されます。 いずれかのレコードが選択されていた場合は、`IsBOF` と `IsEOF` の両方のメンバー関数が 0 を返します。

[Open](../../mfc/reference/crecordset-class.md#open) 呼び出しでは、次のことができます。

- レコードセットがダイナセットかスナップショットかを指定します。 レコードセットは、既定でスナップショットとして開かれます。 または、一度に 1 レコードずつの前方スクロールのみを許可する順方向専用のレコードセットを指定することもできます。

   既定では、レコードセットでは `CRecordset` データ メンバー `m_nDefaultType` に格納されている既定の種類が使用されます。 ウィザードによって `m_nDefaultType` を初期化するコードが、ウィザードで選択したレコードセットの種類に書き込まれます。 この既定を受け入れるのではなく、別のレコードセットの種類に置き換えることもできます。

- レコードセットによって構築される既定の SQL **SELECT** ステートメントを置換する文字列を指定します。

- レコードセットを読み取り専用、または追加専用にするかどうかを指定します。 レコードセットでは既定ですべての更新が許可されていますが、それを新しいレコードの追加のみに制限したり、すべての更新プログラムを許可しないようにすることもできます。

次の例では、クラス `CStudentSet` (アプリケーション固有のクラス) の読み取り専用スナップショット オブジェクトを開く方法を示しています。

```cpp
// Construct the snapshot object
CStudentSet rsStudent( NULL );
// Set options if desired, then open the recordset
if(!rsStudent.Open(CRecordset::snapshot, NULL, CRecordset::readOnly))
    return FALSE;
// Use the snapshot to operate on its records...
```

`Open` を呼び出した後、オブジェクトのメンバー関数とデータ メンバーを使用してレコードを処理します。 場合によっては、データ ソースで発生した変更を含めるために、クエリを再実行またはレコードセットを更新することをお勧めします。 詳細については、「[Recordset: Requerying a Recordset (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)」 (レコードセット: クエリの再実行 (ODBC)) を参照してください。

> [!TIP]
>  開発時に使用する接続文字列は、最終的にユーザーが必要とする接続文字列とは異なる場合があります。 これに関するアプリケーションの汎用化については、「[Data Source:Managing Connections (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)」 (データ ソース:接続の管理 (ODBC)) を参照してください。

##  <a name="_core_setting_recordset_options"></a> レコードセットのオプションを設定する

レコードセット オブジェクトを構築してから、`Open` を呼び出してレコードを選択する前に、レコードセットの動作を制御するためのオプションをいくつか設定することができます。 すべてのレコードセットに対して、次の操作を実行できます。

- [フィルター](../../data/odbc/recordset-filtering-records-odbc.md)を指定して、レコードの選択を制限する。

- レコードの[並べ替え](../../data/odbc/recordset-sorting-records-odbc.md)順序を指定する。

- 実行時に取得または計算した情報を使用してレコードを選択できるように、[パラメーター](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)を指定する。

条件が整っている場合は、次のオプションを設定することもできます。

- レコードセットが更新可能でロック オプションがサポートされている場合は、更新に使用する[ロック](../../data/odbc/recordset-locking-records-odbc.md)方法を指定します。

> [!NOTE]
>  レコードの選択に影響を及ぼすには、メンバー関数 `Open` を呼び出す前にこれらのオプションを設定する必要があります。

##  <a name="_core_closing_a_recordset"></a> レコードセットを閉じる

レコードセットを使用し終えたら、それを破棄してそのメモリの割り当てを解除する必要があります。

#### <a name="to-close-a-recordset"></a>レコードセットを閉じるには

1. そのメンバー関数 [Close](../../mfc/reference/crecordset-class.md#close) を呼び出します。

1. レコードセット オブジェクトを破棄します。

   関数のスタック フレームで宣言した場合は、オブジェクトがスコープから外れたときに、オブジェクトが自動的に破棄されます。 それ以外の場合は、**delete** 演算子を使用します。

`Close` によってレコードセットの `HSTMT` ハンドルが解放されます。 C++ オブジェクトは破棄されません。

## <a name="see-also"></a>関連項目

[レコードセット (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[レコードセット: スクロール (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)<br/>
[レコードセット: レコードの追加、更新、削除 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)