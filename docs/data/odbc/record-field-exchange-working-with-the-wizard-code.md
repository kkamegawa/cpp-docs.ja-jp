---
title: レコード フィールド エクスチェンジ:ウィザード コードの操作
ms.date: 05/09/2019
helpviewer_keywords:
- DoFieldExchange method, overriding
- Unicode, with database classes
- field data members, declaring
- RFX (ODBC), wizard code
- RFX (ODBC), implementing
- field data members
- ODBC, RFX
- m_nParams data member, initializing
- m_nFields data member
- m_nParams data member
- overriding, DoFieldExchange
- m_nFields data member, initializing
ms.assetid: f00d882a-ff1b-4a75-9717-98d8762bb237
ms.openlocfilehash: 81b26e61f64623d1e3da5ed207d0e8e43350229d
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707999"
---
# <a name="record-field-exchange-working-with-the-wizard-code"></a>レコード フィールド エクスチェンジ:ウィザード コードの操作

> [!NOTE] 
> MFC ODBC コンシューマー ウィザードは、Visual Studio 2019 以降では利用できません。 ただし、手動でコンシューマーを作成することはできます。

このトピックでは、RFX をサポートするために MFC アプリケーション ウィザードと (「[Adding an MFC ODBC Consumer](../../mfc/reference/adding-an-mfc-odbc-consumer.md)」 (MFC ODBC コンシューマーの追加) で説明した) **クラスの追加**で記述されるコードについて、およびこれらのコードを変更する方法について説明します。

> [!NOTE]
>  このトピックの内容は、バルク行フェッチが実装されていない `CRecordset` から派生したクラスを対象にしています。 バルク行フェッチを使用している場合は、バルク レコード フィールド エクスチェンジ (Bulk RFX) が実装されます。 Bulk RFX は、RFX に似ています。 相違点を理解するには、「[Recordset:Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)」 (レコードセット: レコードの一括フェッチ (ODBC)) を参照してください。

MFC アプリケーション ウィザードまたは**クラスの追加**を使用してレコードセット クラスを作成すると、ウィザードで選択したデータ ソース、テーブル、列に基づいて、ウィザードによって RFX に関連する次の要素が自動的に記述されます。

- レコードセット クラスでのレコードセット フィールド データ メンバーの宣言

- `CRecordset::DoFieldExchange` のオーバーライド

- レコードセット クラス コンストラクターでのレコードセット フィールド データ メンバーの初期化

##  <a name="_core_the_field_data_member_declarations"></a> フィールド データ メンバーの宣言

ウィザードによって、`CSections` クラスに対してレコード セット クラスの宣言が次のような .h ファイルに書き込まれます。

```cpp
class CSections : public CRecordset
{
public:
   CSections(CDatabase* pDatabase = NULL);
   DECLARE_DYNAMIC(CSections)

// Field/Param Data
   CString   m_strCourseID;
   CString   m_strInstructorID;
   CString   m_strRoomNo;
   CString   m_strSchedule;
   CString   m_strSectionNo;

// Overrides
   // Wizard generated virtual function overrides
   protected:
   virtual CString GetDefaultConnect();  // Default connection string
   virtual CString GetDefaultSQL();      // Default SQL for Recordset
   virtual void DoFieldExchange(CFieldExchange* pFX);  // RFX support

// Implementation
#ifdef _DEBUG
   virtual void AssertValid() const;
   virtual void Dump(CDumpContext& dc) const;
#endif

};
```

パラメーター データ メンバーまたは自分でバインドする新しいフィールド データ メンバーを追加する場合は、ウィザードで生成されたメンバーの後にそれらを追加します。

また、ウィザードによってクラス `CRecordset` のメンバー関数 `DoFieldExchange` がオーバーライドされることにも注意してください。

##  <a name="_core_the_dofieldexchange_override"></a> DoFieldExchange オーバーライド

[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) は RFX の中心部です。 フレームワークでデータ ソースからレコードセットに、またはレコードセットからデータ ソースにデータを移動する必要がある場合にはいつでも `DoFieldExchange` が呼び出されます。 `DoFieldExchange` では、メンバー関数 [IsFieldDirty](../../mfc/reference/crecordset-class.md#isfielddirty) と [IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull) を使用したフィールド データ メンバーに関する情報の入手もサポートされています。

次の `DoFieldExchange` オーバーライドは、`CSections` クラス用です。 ウィザードによって関数がレコードセット クラスの .cpp ファイルに書き込まれます。

```cpp
void CSections::DoFieldExchange(CFieldExchange* pFX)
{
   pFX->SetFieldType(CFieldExchange::outputColumn);
   RFX_Text(pFX, "CourseID", m_strCourseID);
   RFX_Text(pFX, "InstructorID", m_strInstructorID);
   RFX_Text(pFX, "RoomNo", m_strRoomNo);
   RFX_Text(pFX, "Schedule", m_strSchedule);
   RFX_Text(pFX, "SectionNo", m_strSectionNo);
}
```

関数の次の主要機能に注目してください。

- 関数のこのセクションは、フィールド マップと呼ばれます。

- `pFX` ポインターを使用した `CFieldExchange::SetFieldType` への呼び出し。 この呼び出しによって、`DoFieldExchange` の末尾までのすべての RFX 関数呼び出し、または次の `SetFieldType` への呼び出しが出力列であることが指定されます。 詳細については、「[CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)」を参照してください。

- グローバル関数 `RFX_Text` への複数の呼び出し (フィールド データ メンバーごとに 1 つ、この例ではすべて `CString` 変数)。 これらの呼び出しでは、データ ソースの列名とフィールド データ メンバー間のリレーションシップが指定されます。 RFX 関数では、実際のデータ転送が行われます。 クラス ライブラリによって、一般的なすべてのデータ型の RFX 関数が提供されます。 RFX 関数の詳細については、「[Record Field Exchange:Using the RFX Functions](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)」 (レコード フィールド エクスチェンジ: RFX 関数の使い方) を参照してください。

    > [!NOTE]
    >  結果セットの列の順序は、`DoFieldExchange` での RFX 関数の呼び出しの順序と一致している必要があります。

- フレームワークが `DoFieldExchange` を呼び出すときに渡す [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) オブジェクトへの `pFX` ポインター。 `CFieldExchange` オブジェクトは、`DoFieldExchange` によって実行される操作、転送の方向、およびその他のコンテキスト情報を指定します。

##  <a name="_core_the_recordset_constructor"></a> レコードセット コンストラクター

ウィザードによって記述されるレコードセット コンストラクターには、RFX に関連する次の 2 つが含まれています。

- 各フィールド データ メンバーの初期化

- [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) データ メンバーの初期化。これにはフィールド データ メンバーの数が含まれます。

`CSections` レコードセットのコンストラクターの例は次のようになります。

```cpp
CSections::CSections(CDatabase* pdb)
   : CRecordset(pdb)
{
   m_strCourseID = "";
   m_strInstructorID = "";
   m_strRoomNo = "";
   m_strSchedule = "";
   m_strSectionNo = "";
   m_nFields = 5;
}
```

> [!NOTE]
>  新しい列を動的にバインドするなど、任意のフィールド データ メンバーを手動で追加した場合、`m_nFields` をインクリメントする必要があります。 これを行うには、次のような別のコード行を追加します。

```cpp
m_nFields += 3;
```

これは、3 つの新しいフィールドを追加するコードです。 任意のパラメーター データ メンバーを追加する場合は、パラメーター データ メンバーの数が含まれている [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)データ メンバーを初期化する必要があります。 `m_nParams` の初期化はかっこの外側に配置します。

## <a name="see-also"></a>関連項目

[レコード フィールド エクスチェンジ (RFX)](../../data/odbc/record-field-exchange-rfx.md)