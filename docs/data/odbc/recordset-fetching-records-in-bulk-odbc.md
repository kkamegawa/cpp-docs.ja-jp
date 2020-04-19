---
title: レコード セット:方法 (ODBC) 内のレコードをフェッチしています
ms.date: 11/04/2016
helpviewer_keywords:
- bulk row fetching, implementing
- ODBC recordsets, bulk row fetching
- bulk record field exchange
- bulk row fetching
- bulk RFX functions
- recordsets, bulk row fetching
- DoBulkFieldExchange method
- fetching ODBC records in bulk
- RFX (ODBC), bulk
- rowsets, bulk row fetching
- RFX (ODBC), bulk row fetching
ms.assetid: 20d10fe9-c58a-414a-b675-cdf9aa283e4f
ms.openlocfilehash: 2fdcbf18fcb0d97ba7b2a39aa9bbbd79e65a4112
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397849"
---
# <a name="recordset-fetching-records-in-bulk-odbc"></a>レコード セット:方法 (ODBC) 内のレコードをフェッチしています

このトピックの内容は、MFC ODBC クラスに該当します。

クラス`CRecordset`バルク行フェッチ、つまり、複数のレコード取得できることを一度に取得する 1 つのレコードではなく、1 回のフェッチ中に、時に、データ ソースからサポートを提供します。 派生でのみバルク行フェッチを実装する`CRecordset`クラス。 レコード セット オブジェクトにデータ ソースからデータを転送するプロセスは、バルク レコード フィールド エクス チェンジ (Bulk RFX) と呼ばれます。 バルク行フェッチを使用しない場合、 `CRecordset`-データの派生クラスは、レコード フィールド エクス (チェンジ RFX) 経由で転送します。 詳細については、次を参照してください。[レコード フィールド エクス チェンジ (RFX)](../../data/odbc/record-field-exchange-rfx.md)します。

このトピックでは、次の内容について説明します。

- [CRecordset がバルク行フェッチをサポートするどの](#_core_how_crecordset_supports_bulk_row_fetching)します。

- [いくつか特別な考慮事項を使用する場合はバルク行フェッチ](#_core_special_considerations)します。

- [バルク レコード フィールド エクス チェンジの実装方法](#_core_how_to_implement_bulk_record_field_exchange)します。

##  <a name="_core_how_crecordset_supports_bulk_row_fetching"></a> CRecordset がバルク行フェッチをサポートする方法

レコード セット オブジェクトを開く前に、行セットのサイズを定義できます、`SetRowsetSize`メンバー関数。 行セットのサイズは、1 回のフェッチ中に取得するレコードの数を指定します。 バルク行フェッチが実装された場合、既定の行セットのサイズは 25 です。 バルク行フェッチが実装されていない場合、行セットのサイズは 1 に固定されたままです。

行セットのサイズを初期化した後、[オープン](../../mfc/reference/crecordset-class.md#open)メンバー関数。 ここで指定する必要があります、`CRecordset::useMultiRowFetch`のオプション、 *dwOptions*バルク行フェッチを実装するパラメーター。 さらに設定することができます、`CRecordset::userAllocMultiRowBuffers`オプション。 バルク レコード フィールドの交換機構は、複数の行のフェッチ中に取得されるデータを格納するのに配列を使用します。 これらのストレージ バッファーは、フレームワークによって自動的に割り当てることや、手動で割り当てることができます。 指定する、`CRecordset::userAllocMultiRowBuffers`オプションは、割り当てを行うことを意味します。

次の表に、メンバー関数によって提供される`CRecordset`バルク行フェッチをサポートするためにします。

|メンバー関数|説明|
|---------------------|-----------------|
|[CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)|フェッチ中に発生するエラーを処理する仮想関数。|
|[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)|実装は一括レコード フィールド エクス チェンジです。 自動的に呼び出されます転送を複数行のデータをレコード セット オブジェクトにデータ ソースからです。|
|[GetRowsetSize](../../mfc/reference/crecordset-class.md#getrowsetsize)|行セットのサイズの現在の設定を取得します。|
|[GetRowsFetched](../../mfc/reference/crecordset-class.md#getrowsfetched)|行の数は指定されたフェッチ後に実際に取得されたように指示します。 ほとんどの場合、これは、行セット サイズしない限り、不完全な行セットがフェッチされました。|
|[GetRowStatus](../../mfc/reference/crecordset-class.md#getrowstatus)|行セット内の特定の行のフェッチの状態を返します。|
|[RefreshRowset](../../mfc/reference/crecordset-class.md#refreshrowset)|データと、行セット内の特定の行の状態を更新します。|
|[SetRowsetCursorPosition](../../mfc/reference/crecordset-class.md#setrowsetcursorposition)|行セット内の特定の行にカーソルを移動します。|
|[SetRowsetSize](../../mfc/reference/crecordset-class.md#setrowsetsize)|指定した値に行セット サイズの設定を変更する仮想関数。|

##  <a name="_core_special_considerations"></a> 特別な考慮事項

バルク行フェッチはパフォーマンスの向上が、特定の機能が異なる方法で動作します。 バルク行フェッチを実装する前に、次を検討してください。

- フレームワークが自動的に呼び出し、`DoBulkFieldExchange`メンバー関数は、データ ソースからデータをレコード セット オブジェクトを転送します。 ただし、データ ソース、データは、レコード セットからに転送されません。 呼び出す、 `AddNew`、 `Edit`、 `Delete`、または`Update`失敗したアサーション内のメンバー関数の結果。 `CRecordset`現在メカニズムが用意されていないデータの一括行を更新するには、ODBC API 関数を使用して、独自の関数を記述することができます`SQLSetPos`します。 詳細については`SQLSetPos`を参照してください、 *ODBC SDK プログラマー リファレンス*MSDN ドキュメント。

- メンバー関数は、 `IsDeleted`、 `IsFieldDirty`、 `IsFieldNull`、 `IsFieldNullable`、 `SetFieldDirty`、および`SetFieldNull`バルク行フェッチを実装したレコード セットでは使用できません。 ただし、呼び出す`GetRowStatus`の代わりに`IsDeleted`、および`GetODBCFieldInfo`の代わりに`IsFieldNullable`します。

- `Move`操作は、行セットによって、レコード セットを再配置されます。 たとえば、100 個のレコードの最初の行セット サイズは 10 を含むレコード セットを開くとします。 `Open` 1 行に配置されている 1 ~ 10 の現在のレコードでの行をフェッチします。 呼び出し`MoveNext`次へ の 次の行ではなく行セットをフェッチします。 11 行目に配置されている行 11 ~ 20 の現在のレコードに、この行セットで構成されます。 なお`MoveNext`と`Move( 1 )`はバルク行フェッチが実装された場合とは異なります。 `Move( 1 )` 現在のレコードから 1 行で始まる行セットをフェッチします。 この例では、呼び出す`Move( 1 )`呼び出した後`Open`行 2 に配置されている現在のレコードに 2 ~ 11、行で構成される行セットをフェッチします。 詳細については、次を参照してください。、[移動](../../mfc/reference/crecordset-class.md#move)メンバー関数。

- レコード フィールド エクス チェンジとは異なり、ウィザードには、バルク レコード フィールド エクス チェンジがサポートされません。 つまり、手動でフィールド データ メンバーを宣言し、手動でオーバーライドする必要があります`DoBulkFieldExchange`バルク RFX 関数の呼び出しを記述しています。 詳細については、次を参照してください。[レコード フィールド エクス チェンジ関数](../../mfc/reference/record-field-exchange-functions.md)で、*クラス ライブラリ リファレンス*します。

##  <a name="_core_how_to_implement_bulk_record_field_exchange"></a> バルク レコード フィールド エクス チェンジを実装する方法

バルク レコード フィールド エクス チェンジでは、レコード セット オブジェクトをデータ ソースからデータの行セットを転送します。 バルク RFX 関数は、行セットの各データ項目の長さを格納する配列と同様にこのデータを格納する配列を使用します。 クラスの定義には、データの配列にアクセスするへのポインターとしてフィールド データ メンバーを定義する必要があります。 さらに、長さの配列にアクセスするへのポインターのセットを定義する必要があります。 パラメーター データ メンバーは、ポインターとして宣言してはなりませんバルク レコード フィールド エクス チェンジを使用する場合は、パラメーター データ メンバーを宣言すると、レコード フィールド エクス チェンジを使用する場合、そのファイルを宣言することと同じです。 次のコードは、単純な例を示しています。

```cpp
class MultiRowSet : public CRecordset
{
public:
   // Field/Param Data
      // field data members
      long* m_rgID;
      LPSTR m_rgName;

      // pointers for the lengths
      // of the field data
      long* m_rgIDLengths;
      long* m_rgNameLengths;

      // input parameter data member
      CString m_strNameParam;

   .
   .
   .
}
```

これらのストレージ バッファーを手動で割り当てるか、framework が、割り当てを実行します。 自分でバッファーを割り当て、指定する必要があります、`CRecordset::userAllocMultiRowBuffers`のオプション、 *dwOptions*パラメーター、`Open`メンバー関数。 行セット サイズ値以上の配列のサイズを設定することを確認します。 Framework が、割り当てを実行する場合は、NULL へのポインターを初期化する必要があります。 これは通常、レコード セット オブジェクトのコンス トラクターで行われます。

```cpp
MultiRowSet::MultiRowSet( CDatabase* pDB )
   : CRecordset( pDB )
{
   m_rgID = NULL;
   m_rgName = NULL;
   m_rgIDLengths = NULL;
   m_rgNameLengths = NULL;
   m_strNameParam = "";

   m_nFields = 2;
   m_nParams = 1;

   .
   .
   .
}
```

最後に、オーバーライドする必要があります、`DoBulkFieldExchange`メンバー関数。 フィールド データ メンバーの場合、バルク RFX 関数を呼び出すパラメーター データ メンバー、RFX 関数を呼び出します。 SQL ステートメントまたはストアド プロシージャに渡すことによって、レコード セットを開いた場合`Open`、レコード セット内の列順序 Bulk rfx 関数の呼び出しを行う順序に対応する必要があります同様に、、RFX の注文の問い合わせについては、パラメーターは、対応する必要があります。SQL ステートメントまたはストアド プロシージャのパラメーター順序。

```cpp
void MultiRowSet::DoBulkFieldExchange( CFieldExchange* pFX )
{
   // call the Bulk RFX functions
   // for field data members
   pFX->SetFieldType( CFieldExchange::outputColumn );
   RFX_Long_Bulk( pFX, _T( "[colRecID]" ),
                  &m_rgID, &m_rgIDLengths );
   RFX_Text_Bulk( pFX, _T( "[colName]" ),
                  &m_rgName, &m_rgNameLengths, 30 );

   // call the RFX functions for
   // for parameter data members
   pFX->SetFieldType( CFieldExchange::inputParam );
   RFX_Text( pFX, "NameParam", m_strNameParam );
}
```

> [!NOTE]
>  呼び出す必要があります、`Close`メンバー関数は、派生する前に`CRecordset`クラスがスコープ外になります。 これにより、フレームワークによって割り当てられたメモリが解放されます。 常に明示的に呼び出すことをお勧め`Close`バルク行フェッチを実装するかどうかに関係なく、します。

レコード フィールド エクス チェンジ (RFX) の詳細については、次を参照してください。[レコード フィールド エクス チェンジ。RFX のしくみ](../../data/odbc/record-field-exchange-how-rfx-works.md)します。 詳細については、パラメーターを使用して、次を参照してください。[つ](../../mfc/reference/cfieldexchange-class.md#setfieldtype)と[レコード セット。レコード セット (ODBC) をパラメーター化](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)します。

## <a name="see-also"></a>関連項目

[レコードセット (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset::m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)<br/>
[CRecordset::m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)

