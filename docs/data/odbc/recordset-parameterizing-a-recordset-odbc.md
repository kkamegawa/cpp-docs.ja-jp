---
title: レコードセット:レコードセットのパラメーター化 (ODBC)
ms.date: 05/09/2019
helpviewer_keywords:
- parameterizing recordsets
- ODBC recordsets, parameterizing
- recordsets, parameterizing
- passing parameters, to queries at runtime
ms.assetid: 7d1dfeb6-5ee0-45e2-aacc-63bc52a465cd
ms.openlocfilehash: 499741693009fb27df58f0ed3cde046d5e6b8c2d
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707789"
---
# <a name="recordset-parameterizing-a-recordset-odbc"></a>レコードセット:レコードセットのパラメーター化 (ODBC)

このトピックの内容は、MFC ODBC クラスに該当します。

計算したか、エンド ユーザーから入手した情報を利用し、実行時、レコードを選択できると便利なことがあります。 その目標を達成できるのがレコードセット パラメーターです。

このトピックでは、次の内容について説明します。

- [パラメーター化されたレコードセットの目的](#_core_parameterized_recordsets)。

- [レコードセットをパラメーター化できると便利な状況と理由](#_core_when_to_use_parameters)。

- [レコードセット クラスでパラメーター データ メンバーを宣言する方法](#_core_parameterizing_your_recordset_class)。

- [実行時にレコードセット オブジェクトにパラメーター情報を渡す方法](#_core_passing_parameter_values_at_run_time)。

##  <a name="_core_parameterized_recordsets"></a> パラメーター化されたレコードセット

レコードセットをパラメーター化すると、実行時にパラメーター情報を渡すことができます。 これには 2 つの重要な効果があります。

- 結果的に、実行速度が上がることがあります。

- ユーザーから入手したか、実行時に計算された情報など、デザイン時に利用できなかった情報に基づいて、実行時にクエリを構築できます。

`Open` を呼び出し、クエリを実行すると、レコードセットによりパラメーター情報が使用され、その **SQL SELECT** ステートメントが実行されます。 あらゆるレコードセットをパラメーター化できます。

##  <a name="_core_when_to_use_parameters"></a> パラメーターを使用する状況

パラメーターの典型的な用途:

- 事前定義されたクエリに実行時引数を渡します。

   ストアド プロシージャにパラメーターを渡すには、`Open` を呼び出すとき、パラメーター プレースホルダーを利用して完全なカスタム ODBC **CALL** ステートメントを指定し、レコードセットの既定の SQL ステートメントをオーバーライドする必要があります。 詳細については、*クラス ライブラリ リファレンス*の [CRecordset::Open](../../mfc/reference/crecordset-class.md#open)、「[SQL:レコードセットの SQL ステートメントのカスタマイズ (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)」、「[レコードセット:定義済みクエリのクラスの宣言 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)」を参照してください。

- さまざまなパラメーター情報を利用し、さまざまなクエリを効率的に実行します。

   たとえば、エンド ユーザーが学生登録データベースで特定の学生の情報を探すたびに、ユーザーから入手されるパラメーターとして、その学生の名前または ID を指定できます。 その後、レコードセットの `Requery` メンバー関数を呼び出すと、クリエによってその学生のレコードだけが選択されます。

   `m_strFilter` に保存されている、レコードセットのフィルター文字列は次のようになります。

    ```cpp
    "StudentID = ?"
    ```

   変数 `strInputID` で学生 ID を取得するとします。 パラメーターを `strInputID` に設定すると (たとえば、学生 ID が 100)、変数の値は、フィルター文字列の "?" で表されるパラメーター プレースホルダーにバインドされます。

   パラメーター値を次のように割り当てます。

    ```cpp
    strInputID = "100";
    ...
    m_strParam = strInputID;
    ```

   フィルター文字列を次のように設定することはないでしょう。

    ```cpp
    m_strFilter = "StudentID = 100";   // 100 is incorrectly quoted
                                       // for some drivers
    ```

   フィルター文字列に引用符を正しく使用する方法については、「[レコードセット:レコードのフィルター処理 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)」を参照してください。

   パラメーター値は、新しい学生 ID のレコードセットを再度問い合わせるたびに異なります。

   > [!TIP]
   > パラメーターの使用は、フィルターだけの場合より効率的です。 パラメーター化されたレコードセットについては、データベースで SQL **SELECT** ステートメントを 1 回だけ処理する必要があります。 パラメーターがなく、フィルタリングされたレコードセットについては、新しいフィルター値で `Requery` するたびに **SELECT** ステートメントを処理する必要があります。

フィルターの詳細については、「[レコードセット:レコードのフィルター処理 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)」を参照してください。

##  <a name="_core_parameterizing_your_recordset_class"></a> レコードセット クラスをパラメーター化する

> [!NOTE]
> このセクションの内容は、バルク行フェッチが実装されていない `CRecordset` の派生オブジェクトを対象にしています。 バルク行フェッチを使用している場合、パラメーターの実装は同じようなプロセスになります。 詳細については、「[レコードセット:レコードの一括フェッチ (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)」を参照してください。

レコードセット クラスを作成する前に、必要なパラメーター、そのデータの型、それらをレコードセットで使用する方法を決定します。

#### <a name="to-parameterize-a-recordset-class"></a>レコードセット クラスをパラメーター化するには

> [!NOTE] 
> MFC ODBC コンシューマー ウィザードは、Visual Studio 2019 以降はご利用いただけなくなります。 引き続きこの機能を手動で作成できます。

1. **[クラスの追加]** から [MFC ODBC コンシューマー ウィザード](../../mfc/reference/adding-an-mfc-odbc-consumer.md)を実行し、クラスを作成します。

1. レコードセットの列にフィールド データ メンバーを指定します。

1. ウィザードでプロジェクトのファイルにクラスが書き込まれたら、.h ファイルに移動し、1 つまたは複数のパラメーター データ メンバーを手動でクラス宣言に追加します。 この追加は次の例のようになります。この例は、"どの学生が上級クラスにいますか?" という問い合わせに答えるように設計されたスナップショット クラスの一部です。

    ```cpp
    class CStudentSet : public CRecordset
    {
    // Field/Param Data
        CString m_strFirstName;
        CString m_strLastName;
        CString m_strStudentID;
        CString m_strGradYear;

        CString m_strGradYrParam;
    };
    ```

   ウィザードで生成されたフィールド データ メンバーの後ろにパラメーター データ メンバーを追加します。 ユーザーが定義した各パラメーター名に "Param" という単語を付けるのが規則になっています。

1. .cpp ファイルの [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) メンバー関数定義を変更します。 クラスに追加した各パラメーター データ メンバーに RFX 関数呼び出しを追加します。 RFX 関数の記述方法については、「[レコード フィールド エクスチェンジ:RFX のしくみ](../../data/odbc/record-field-exchange-how-rfx-works.md)」を参照してください。 次の単一呼び出しの前にパラメーターの RFX 呼び出しを置きます。

    ```cpp
    pFX->SetFieldType( CFieldExchange::param );
    // RFX calls for parameter data members
    ```

1. レコードセット クラスのコンストラクターで、パラメーター `m_nParams` のカウントをインクリメントします。

   詳細については、「[レコード フィールド エクスチェンジ:ウィザード コードの使用](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md)」を参照してください。

1. このクラスのレコードセット オブジェクトを作成するコードを記述するとき、パラメーターを置換する SQL ステートメント文字列内の各場所に "?" (疑問符) 記号を置きます。

   実行時に、渡したパラメーター値が "?" プレースホルダーに順番に入ります。 [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) 呼び出し後の最初のパラメーター データ メンバーが SQL 文字列の最初の "?" に、2 番目のパラメーター データ メンバーが SQL 文字列の 2 番目の "?" に取って代わります。

> [!NOTE]
> パラメーターの順序が重要: `DoFieldExchange` 関数におけるパラメーターの RFX 呼び出しの順序は、SQL 文字列におけるパラメーター プレースホルダーの順序に一致する必要があります。

> [!TIP]
> 使用する可能性が最も高い文字列はクラスの [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) データ メンバーに指定する文字列ですが (あるとすれば)、一部の ODBC ドライバーでは他の SQL 句でパラメーターが許可されることがあります。

##  <a name="_core_passing_parameter_values_at_run_time"></a> 実行時にパラメーター値を渡す

`Open` (新しいレコードセット オブジェクトの場合) または `Requery` (既存のレコードセット オブジェクトの場合) を呼び出す前にパラメーター値を指定する必要があります。

#### <a name="to-pass-parameter-values-to-a-recordset-object-at-run-time"></a>実行時、レコードセット オブジェクトにパラメーター値を渡すには

1. レコードセット オブジェクトを構築します。

1. SQL ステートメントまたはその一部が含まれる、`m_strFilter` 文字列など、文字列を用意します。 パラメーター情報が入る場所にプレースホルダーの "?" を置きます。

1. オブジェクトの各パラメーター データ メンバーに実行時パラメーター値を割り当てます。

1. `Open` メンバー関数を呼び出します (既存のレコードセットの場合は `Requery`)。

たとえば、実行時に取得した情報を利用し、レコードセットにフィルター文字列を指定するとします。 以前にクラス `CStudentSet` のレコードセットを構築しており、その名前が `rsStudents` であるとします。これから、ある種類の学生情報を再度問い合わせます。

```cpp
// Set up a filter string with
// parameter placeholders
rsStudents.m_strFilter = "GradYear <= ?";

// Obtain or calculate parameter values
// to pass--simply assigned here
CString strGradYear = GetCurrentAcademicYear( );

// Assign the values to parameter data members
rsStudents.m_strGradYrParam = strGradYear;

// Run the query
if( !rsStudents.Requery( ) )
    return FALSE;
```

このレコードセットには、実行時パラメーターから構築されたフィルターによって指定された条件をレコードが満たす学生のレコードが含まれます。 この場合、レコードセットにはすべての上級生のレコードが含まれます。

> [!NOTE]
>  必要であれば、[SetParamNull](../../mfc/reference/crecordset-class.md#setparamnull) を使用し、パラメーター データ メンバーの値を null に設定できます。 同様に、[IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull) を使用し、パラメーター データ メンバーが null であるかどうかを確認できます。

## <a name="see-also"></a>関連項目

[レコードセット (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[レコードセット: レコードの追加、更新、削除 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)<br/>
[レコードセット: レコードセットでのレコード選択のしくみ (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)