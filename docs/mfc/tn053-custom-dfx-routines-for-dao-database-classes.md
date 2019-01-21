---
title: 'テクニカル ノート 53: DAO データベース クラス用カスタム DFX ルーチン'
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.dfx
helpviewer_keywords:
- MFC, DAO and
- database classes [MFC], DAO
- DAO [MFC], MFC
- DFX (DAO record field exchange) [MFC], custom routines
- TN053
- DAO [MFC], classes
- DFX (DAO record field exchange) [MFC]
- custom DFX routines [MFC]
ms.assetid: fdcf3c51-4fa8-4517-9222-58aaa4f25cac
ms.openlocfilehash: 81529dd1e34d06dd3e5d541d39dbe91bb5eda1b7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517768"
---
# <a name="tn053-custom-dfx-routines-for-dao-database-classes"></a>テクニカル ノート 53: DAO データベース クラス用カスタム DFX ルーチン

> [!NOTE]
>  Visual C 環境とウィザードは、(DAO クラスが含まれていますし、それらを使用することもできます) が DAO をサポートしています。 使用することをお勧めします。 [OLE DB テンプレート](../data/oledb/ole-db-templates.md)または[ODBC と MFC](../data/odbc/odbc-and-mfc.md)の新しいプロジェクト。 DAO は、既存のアプリケーションを維持するためにのみ使用する必要があります。

このテクニカル ノートには、DAO レコード フィールド エクス (チェンジ DFX) メカニズムについて説明します。 DFX ルーチンの動作の理解に役立つ、`DFX_Text`関数は、例として詳細に説明されます。 このテクニカル ノートの情報の追加のソースとして、他のコードの確認する個々 の DFX 関数。 おそらく必要はありませんカスタム DFX ルーチン頻度カスタム RFX ルーチン (ODBC データベース クラスで使用) する必要があります。

このテクニカル ノートが含まれます。

- DFX の概要

- [例](#_mfcnotes_tn053_examples)DAO レコード フィールド エクス チェンジと動的なバインドを使用して

- [DFX のしくみ](#_mfcnotes_tn053_how_dfx_works)

- [カスタム DFX ルーチンの動作](#_mfcnotes_tn053_what_your_custom_dfx_routine_does)

- [DFX_Text の詳細](#_mfcnotes_tn053_details_of_dfx_text)

**DFX の概要**

DAO レコード フィールド エクス機構 (DFX) の使用を取得して、データの更新を使用する場合の手順を簡略化、`CDaoRecordset`クラス。 データ メンバーを使用して、プロセスが簡素化、`CDaoRecordset`クラス。 派生することによって`CDaoRecordset`、テーブルまたはクエリ内の各フィールドを表す、派生クラスにデータ メンバーを追加することができます。 この「静的バインド」メカニズム単純ですが、すべてのアプリケーションの任意のデータのフェッチまたは更新方法ができない可能性があります。 DFX は、現在のレコードが変更されるたびにすべての束縛のフィールドを取得します。 通貨が変更されたときに、すべてのフィールドをフェッチしていますが不要なパフォーマンスが重要なアプリケーションを開発している場合「動的バインド」を使用して`CDaoRecordset::GetFieldValue`と`CDaoRecordset::SetFieldValue`任意のデータ アクセス方法があります。

> [!NOTE]
>  DFX と動的なバインドは静的および動的なバインドのハイブリッドの使用を使用できるように、相互に排他的されません。

## <a name="_mfcnotes_tn053_examples"></a> DAO レコード フィールド エクスのみの使用例 1:

(想定`CDaoRecordset`-クラスを派生`CMySet`既に開かれている)

```
// Add a new record to the customers table
myset.AddNew();

myset.m_strCustID = _T("MSFT");

myset.m_strCustName = _T("Microsoft");

myset.Update();
```

**動的バインディングのみの使用例 2:**

(使用を前提と`CDaoRecordset`クラス、`rs`が既に開かれている)

```
// Add a new record to the customers table
COleVariant  varFieldValue1 (_T("MSFT"),
    VT_BSTRT);

//Note: VT_BSTRT flags string type as ANSI,
    instead of UNICODE default
COleVariant  varFieldValue2  (_T("Microsoft"),
    VT_BSTRT);

rs.AddNew();

rs.SetFieldValue(_T("Customer_ID"),
    varFieldValue1);

rs.SetFieldValue(_T("Customer_Name"),
    varFieldValue2);

rs.Update();
```

**例 3 — DAO レコード フィールド エクスの使用と動的バインディング**

(参照の従業員データを前提としています`CDaoRecordset`-クラスを派生`emp`)

```
// Get the employee's data so that it can be displayed
emp.MoveNext();

// If user wants to see employee's photograph,
// fetch it
COleVariant varPhoto;
if (bSeePicture)
    emp.GetFieldValue(_T("photo"),
    varPhoto);

// Display the data
PopUpEmployeeData(emp.m_strFirstName,
    emp.m_strLastName,
    varPhoto);
```

## <a name="_mfcnotes_tn053_how_dfx_works"></a> DFX のしくみ

DFX メカニズムは、MFC ODBC クラスで使用されるレコード フィールド エクス (チェンジ RFX) メカニズムと同様の方法で機能します。 DFX と RFX の原則は同じですが多数の内部の違いがあります。 DFX 関数の設計は、個々 の DFX ルーチンによってほぼすべてのコードを共有できるようにしました。 最上位の DFX だけでは、いくつかの点。

- DFX は、SQL を構築します**選択**句と SQL**パラメーター**句が必要な場合。

- DFX は、DAO ので使用されるバインディングの構造を構築`GetRows`関数 (詳細後述)。

- DFX (ダブル バッファリングを使用している) 場合は、ダーティであるフィールドを検出するために使用するデータ バッファーを管理します。

- DFX は、管理、 **NULL**と**DIRTY**状態配列および更新プログラムに必要な場合に値を設定します。

メカニズムには、DFX の中核、`CDaoRecordset`派生クラスの`DoFieldExchange`関数。 この関数は、適切な操作の種類の個々 の DFX 関数への呼び出しをディスパッチします。 呼び出しの前に`DoFieldExchange`内部 MFC 関数は、操作の種類を設定します。 さまざまな操作の種類と簡単な説明を次に示します。

|操作|説明|
|---------------|-----------------|
|`AddToParameterList`|ビルド パラメーター句|
|`AddToSelectList`|ビルドの SELECT 句|
|`BindField`|バインド構造体を設定します。|
|`BindParam`|パラメーター値を設定します。|
|`Fixup`|NULL 状態を設定します。|
|`AllocCache`|変更されているキャッシュを割り当てます|
|`StoreField`|現在のレコードをキャッシュに保存します|
|`LoadField`|メンバーの値に復元キャッシュ|
|`FreeCache`|キャッシュを解放します。|
|`SetFieldNull`|フィールドの状態と値を NULL に設定|
|`MarkForAddNew`|記号フィールドがダーティかどうか擬似 NULL|
|`MarkForEdit`|記号フィールド ダーティの場合はキャッシュに一致しません。|
|`SetDirtyField`|フィールド ダーティとマークされている値の設定|

次のセクションで各操作については説明のさらに詳しく`DFX_Text`します。

DAO レコード フィールド交換プロセスの詳細を理解する最も重要な機能が使用される、`GetRows`の関数、`CDaoRecordset`オブジェクト。 DAO`GetRows`関数がいくつかの方法で作業できます。 このテクニカル ノートは簡単に説明が`GetRows`このテクニカル ノートの範囲外です。

DAO`GetRows`いくつかの方法で作業できます。

- 複数のレコードと複数のデータ フィールドを一度に取得できます。 これにより、複雑な大規模なデータ構造と、各フィールドに、適切なオフセットの処理を高速データ アクセスと、構造内のデータの各レコードについて。 MFC には、複数レコードのフェッチ機構の利点はなりません。

- 別の方法として`GetRows`できる作業は、プログラマが 1 つのレコード データの各フィールドの取得したデータのバインド アドレスを指定できるようにします。

- 「コールバック」可変長列の呼び出し元にメモリを割り当て、呼び出し元を許可するには、DAO は、します。 この 2 つ目の機能がクラスのメンバーへのデータの格納を許可するほかのデータのコピーの数を最小限に抑えることの利点は、(、`CDaoRecordset`派生クラス)。 この 2 つ目のメカニズムは、MFC で使用するデータ メンバーにバインドする方法を`CDaoRecordset`クラスを派生します。

##  <a name="_mfcnotes_tn053_what_your_custom_dfx_routine_does"></a> カスタム DFX ルーチンの動作

DFX 関数で実装される最も重要な操作が正常に呼び出すに必要なデータ構造を設定することをする必要があるの説明からは`GetRows`します。 DFX 関数をサポートする必要がありますも、その他の操作が、重要なまたは正しくに備えるように複雑なとして none のいくつか、`GetRows`呼び出します。

DFX の使用は、オンライン ドキュメントで説明します。 基本的には、2 つの要件があります。 最初に、メンバーを追加する必要があります、`CDaoRecordset`各束縛のフィールドとパラメーターのクラスを派生します。 次のこの`CDaoRecordset::DoFieldExchange`オーバーライドする必要があります。 メンバーのデータ型が重要なことに注意してください。 データベースのフィールドからのデータと一致または以上では、その型に変換可能であること必要があります。 たとえば、長整数などのデータベース内の数値フィールドは、常にテキストに変換して'CString'メンバーにバインドできますが、データベース内のテキストフィールドは必ずしも数値表現に変換されるとは限りません。長整数などの長整数メンバーにバインドされています。 DAO および Microsoft Jet データベース エンジンは、変換 (なく MFC) を行います。

##  <a name="_mfcnotes_tn053_details_of_dfx_text"></a> DFX_Text の詳細

前述のように、DFX のしくみを説明する最善の方法は、例を操作するは。 この目的の内部を通過`DFX_Text`少なくとも DFX の基本的な理解を確保するためにかなりうまく機能する必要があります。

- `AddToParameterList`

   この操作は、SQL をビルド**パラメーター**句 ("`Parameters <param name>, <param type> ... ;`") Jet で必要です。 各パラメーターがという名前し、(rfx 関数の呼び出しで指定) として型指定します。 関数を参照してください。`CDaoFieldExchange::AppendParamType`の個々 の型の名前を表示する関数。 場合に`DFX_Text`、使用される種類は**テキスト**します。

- `AddToSelectList`

   SQL をビルド**選択**句。 これは、DFX の呼び出しで指定された列名は単にとても簡単に追加されます ("`SELECT <column name>, ...`")。

- `BindField`

   操作の最も複雑なは。 これで、DAO バインド構造体が使用されるは、以前説明したように`GetRows`設定します。 内のコードからわかるように`DFX_Text`構造情報の種類は、DAO の型を含める (**DAO_CHAR**または**DAO_WCHAR**の場合に`DFX_Text`)。 さらに、に使用されるバインディングの種類も設定されます。 前のセクションで`GetRows`ごく短時間しか」で説明したが、MFC で使用されるバインドの種類は、直接アドレスのバインドでは常に説明する十分でしたが (**DAOBINDING_DIRECT**)。 さらに可変長列のバインドの (など`DFX_Text`) MFC をメモリの割り当てを制御し、正しい長さのアドレスを指定するためのコールバックのバインディングが使用されます。 これにより、MFC が常に把握 DAO メンバー変数に直接バインドできます。 つまり、データを格納する"where"。 メモリ割り当てのコールバック関数と、(列名でバインド) 列のバインドの種類のアドレスなど、バインド構造体の残りの部分が入力されます。

- `BindParam`

   これは、単純な操作を呼び出す`SetParamValue`メンバーで指定されたパラメーターの値。

- `Fixup`

   入力、 **NULL**各フィールドの状態。

- `SetFieldNull`

   この操作は各フィールドの状態をマークするだけ**NULL**メンバー変数の値を設定および**PSEUDO_** します。

- `SetDirtyField`

   呼び出し`SetFieldValue`各フィールドをダーティとマークします。

残りのすべての操作のみ、データ キャッシュを使用してを対処します。 データ キャッシュは、特定のものを簡素化するために使用する現在のレコード内のデータの余分なバッファーです。 たとえば、「ダーティ」フィールドを自動的に検出することができます。 オンライン ドキュメントの説明に従って完全にまたは、フィールド レベルで無効にできます。 バッファーの実装では、マップで使用します。 このマップが動的に割り当てられたデータのコピー「バインド」フィールドのアドレスを一致させる (または`CDaoRecordset`データ メンバーの派生)。

- `AllocCache`

   動的にキャッシュされているフィールドの値を割り当てるし、マップに追加します。

- `FreeCache`

   キャッシュされたフィールドの値を削除し、マップから削除されます。

- `StoreField`

   データ キャッシュには、現在のフィールドの値をコピーします。

- `LoadField`

   フィールドのメンバーには、キャッシュされた値をコピーします。

- `MarkForAddNew`

   現在のフィールド値が以外**NULL**し、必要に応じてダーティ マークします。

- `MarkForEdit`

   データ キャッシュを使用して現在のフィールド値を比較し、必要な場合は、ダーティのマークを付けます。

> [!TIP]
> 標準のデータ型の既存の DFX ルーチンのカスタム DFX ルーチン モデルです。

## <a name="see-also"></a>関連項目

[番号順テクニカル ノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカル ノート](../mfc/technical-notes-by-category.md)

