---
title: レコードセット:アーキテクチャ (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets, data members
- field data members, recordset architecture
- field data members
- m_nParams data member, recordsets
- recordsets, architecture
- parameter data members in recordsets
- m_nFields data member
- ODBC recordsets, architecture
- m_nParams data member
- m_nFields data member, recordsets
ms.assetid: 47555ddb-11be-4b9e-9b9a-f2931764d298
ms.openlocfilehash: 0edde640e0eebaf21216fc9ef37a8e31e2c1a210
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707974"
---
# <a name="recordset-architecture-odbc"></a>レコードセット:アーキテクチャ (ODBC)

このトピックの内容は、MFC ODBC クラスに該当します。

このトピックでは、レコードセット オブジェクトのアーキテクチャを構成するデータ メンバーについて説明します。

- [フィールド データ メンバー](#_core_field_data_members)

- [パラメーター データ メンバー](#_core_parameter_data_members)

- [m_nFields と m_nParams データ メンバーの使用](#_core_using_m_nfields_and_m_nparams)

> [!NOTE]
>  このトピックの内容は、バルク行フェッチが実装されていない `CRecordset` の派生オブジェクトを対象にしています。 バルク行フェッチが実装されている場合も、アーキテクチャはほぼ同じです。 相違点を理解するには、「[Recordset:Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)」 (レコードセット: レコードの一括フェッチ (ODBC)) を参照してください。

##  <a name="_core_a_sample_class"></a> サンプル クラス

> [!NOTE] 
> MFC ODBC コンシューマー ウィザードは、Visual Studio 2019 以降では利用できません。 ただし、手動でコンシューマーを作成することはできます。

**クラス追加**ウィザードから [MFC ODBC コンシューマー ウィザード](../../mfc/reference/adding-an-mfc-odbc-consumer.md)を使用して、`CRecordset` から派生したレコードセット クラスを宣言すると、結果として得られるクラスは、次の単純なクラスで示される一般的な構造クラスを持ちます。

```cpp
class CCourse : public CRecordset
{
public:
   CCourse(CDatabase* pDatabase = NULL);
   ...
   CString m_strCourseID;
   CString m_strCourseTitle;
   CString m_strIDParam;
};
```

クラスの先頭には、ウィザードによって一連の[フィールド データ メンバー](#_core_field_data_members)が書き込まれます。 クラスを作成するときに、1 つまたは複数のフィールド データ メンバーを指定する必要があります。 サンプル クラスのようにクラスが (データ メンバー `m_strIDParam` で) パラメーター化されている場合は、[パラメーター データ メンバー](#_core_parameter_data_members)を手動で追加する必要があります。 ウィザードでは、クラスへのパラメーターの追加はサポートされていません。

##  <a name="_core_field_data_members"></a> フィールド データ メンバー

レコードセット クラスの最も重要なメンバーは、フィールド データ メンバーです。 データ ソースから選択する各列のクラスには、その列に適したデータ型のデータ メンバーが含まれています。 たとえば、このトピックの冒頭で示した[サンプル クラス](#_core_a_sample_class)には、`m_strCourseID` および `m_strCourseTitle` と呼ばれる 2 つのフィールド データ メンバーがあり、どちらの型も `CString` です。

レコードセットで一連のレコードが選択されるときに、フレームワークによって現在のレコード (`Open` を呼び出した後の、最初のレコードが現在のレコード) の列がオブジェクトのフィールド データ メンバーに自動的にバインドされます。 つまり、フレームワークでは適切なフィールド データ メンバーが、レコード列の内容を格納するバッファーとして使用されます。

ユーザーが新しいレコードまでスクロールすると、フレームワークはフィールド データ メンバーを使用して現在のレコードを表します。 フレームワークによって前のレコードの値が置換され、フィールド データ メンバーが更新されます。 フィールド データ メンバーは、現在のレコードの更新と新しいレコードの追加にも使用されます。 レコードの更新プロセスの一環として、該当するフィールド データ メンバーまたはメンバーに値を直接割り当てて、更新値を指定します。

##  <a name="_core_parameter_data_members"></a> パラメーター データ メンバー

クラスがパラメーター化されると、1 つ以上のパラメーター データ メンバーを持ちます。 パラメーター化されたクラスを使用すると、実行時に取得または計算した情報に基づいてレコードセットのクエリを実行できます。

通常、パラメーターは、次の例のように、選択範囲を絞り込むのに役立ちます。 このトピックの冒頭の[サンプル クラス](#_core_a_sample_class)に基づいて、レコードセット オブジェクトが次の SQL ステートメントを実行できます。

```sql
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = ?
```

"?" は実行時に指定するパラメーター値のプレースホルダーです。 レコードセットを構築してその `m_strIDParam` データ メンバーを MATH101 に設定すると、レコードセットの有効な SQL ステートメントは次のようになります。

```sql
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = MATH101
```

パラメーター データ メンバーを定義することで、SQL 文字列内のパラメーターについてフレームワークに指示します。 フレームワークによってパラメーターがバインドされます。これにより ODBC にプレースホルダーを置き換える値を取得する場所を知らせることができます。 例では、結果のレコード セットには、Course テーブルから CourseID 列の値が MATH101 のレコードのみが含まれます。 このレコードのすべての指定した列が選択されます。 パラメーター (とプレースホルダー) は必要なだけ指定することができます。

> [!NOTE]
>  MFC 自体はパラメーターに対して何も行いません。具体的には、テキストの置換は実行されません。 代わりに、MFC は ODBC にパラメーターを取得する場所を伝え、ODBC がデータを取得して、必要なパラメーター化を実行します。

> [!NOTE]
>  パラメーターの順序は重要です。 これに関する情報とパラメーターの詳細については、「[Recordset:Parameterizing a Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)」 (レコードセット: レコードセットのパラメーター化 (ODBC)) を参照してください。

##  <a name="_core_using_m_nfields_and_m_nparams"></a> m_nFields と m_nParams の使用

ウィザードによってコンストラクターが自動的に書き込まれるときに、クラス内の [field data members](#_core_field_data_members) の数を指定する [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) データ メンバーの初期化も行われます。 任意の[パラメーター](#_core_parameter_data_members)をクラスに追加する場合は、パラメーター データ メンバーの数を指定する [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams) データ メンバーの初期化も追加する必要があります。 フレームワークではデータ メンバーを使用するためにこれらの値が使用されます。

詳細と例については、「[Record Field Exchange:Using RFX](../../data/odbc/record-field-exchange-using-rfx.md)」 (レコード フィールド エクスチェンジ: RFX の使用) を参照してください。

## <a name="see-also"></a>関連項目

[レコードセット (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[レコードセット: テーブル用のクラスの宣言 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[レコード フィールド エクスチェンジ (RFX)](../../data/odbc/record-field-exchange-rfx.md)