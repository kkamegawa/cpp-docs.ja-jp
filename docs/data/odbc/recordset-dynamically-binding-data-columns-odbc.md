---
title: 'レコードセット: データ列の動的なバインド (ODBC)'
ms.date: 05/09/2019
helpviewer_keywords:
- ODBC recordsets [C++], binding columns dynamically
- data binding [C++], recordset columns
- recordsets [C++], binding data
- data binding [C++], columns in recordsets
- columns [C++], binding to recordsets
ms.assetid: bff67254-d953-4ae4-9716-91c348cb840b
ms.openlocfilehash: bde61348bbfb33eef42e36bd75830c23e5b2a5f5
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707930"
---
# <a name="recordset-dynamically-binding-data-columns-odbc"></a>レコードセット: データ列の動的なバインド (ODBC)

このトピックの内容は、MFC ODBC クラスに該当します。

設計時に指定したテーブル列のバインドはレコードセットによって管理されますが、設計時に不明であった列を自分でバインドしたい場合があります。 このトピックでは、次の内容について説明します。

- [どのようなときにレコードセットに列を動的にバインドするか](#_core_when_you_might_bind_columns_dynamically)。

- [実行時に列を動的にバインドする方法](#_core_how_to_bind_columns_dynamically)。

> [!NOTE]
>  このトピックの内容は、バルク行フェッチが実装されていない `CRecordset` の派生オブジェクトを対象にしています。 バルク行フェッチを使っている場合、説明する手法は一般に推奨されません。 バルク行フェッチの詳細については、「[Recordset: Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)」 (レコードセット: レコードの一括フェッチ (ODBC)) を参照してください。

##  <a name="_core_when_you_might_bind_columns_dynamically"></a> どのようなときに列を動的にバインドするか

> [!NOTE] 
> MFC ODBC コンシューマー ウィザードは、Visual Studio 2019 以降では利用できません。 ただし、手動でコンシューマーを作成することはできます。

設計時には、MFC アプリケーション ウィザードまたは [MFC ODBC コンシューマー ウィザード](../../mfc/reference/adding-an-mfc-odbc-consumer.md) (**[クラスの追加]** から) により、データ ソースでわかっているテーブルと列に基づいて、レコードセット クラスが作成されます。 データベースは、設計した時点から、後で実行時にアプリケーションでそれらのテーブルや列が使われるまでの間に、変更されている場合があります。 自分や他のユーザーが、アプリケーションのレコードセットが依存しているテーブルやテーブルの列を、追加または削除する可能性があります。 これはおそらくすべてのデータアクセス アプリケーションに対する問題ではないでしょうが、もし自分がその立場になったら、再設計や再コンパイル以外でデータベース スキーマの変更に対応するには、どうすればよいでしょうか。 このトピックの目的は、その質問に答えることです。

このトピックでは、動的に列をバインドする可能性がある最も一般的なケースについて説明します。つまり、既知のデータベース スキーマに基づいてレコードセットを開始した後、実行時に追加の列を処理する必要がある場合です。 さらに、追加の列は最も一般的な `CString` フィールド データ メンバーにマップしているものとしますが、他のデータ型の管理に役立つ推奨事項を提供します。

コードを少し追加することで、次のことができます。

- [実行時に、使用可能な列を特定します](#_core_how_to_bind_columns_dynamically)。

- [実行時に、追加の列をレコードセットに動的にバインドします](#_core_adding_the_columns)。

レコードセットには、設計時にわかっていた列のデータ メンバーも含まれています。 また、ターゲット テーブルに新しい列が追加されているかどうかを動的に判別し、そうである場合はこれらの新しい列を (レコード セットのデータ メンバーではなく) 動的に割り当てられた記憶域にバインドする、少量の追加コードも含まれます。

このトピックでは、削除されたテーブルや列など、他の動的なバインドの場合については説明しません。 それらのケースについては、さらに直接的に ODBC API の呼び出しを使う必要があります。 詳細については、MSDN ライブラリ CD に収録されている ODBC SDK の*プログラマーズ リファレンス*を参照してください。

##  <a name="_core_how_to_bind_columns_dynamically"></a> 列を動的にバインドする方法

列を動的にバインドするには、追加する列の名前がわかっている (または特定できる) 必要があります。 また、追加するフィールド データ メンバー用の記憶域を割り当て、それらの名前と型を指定し、追加する列の数を指定する必要もあります。

次の説明では、2 つの異なるレコードセットを取り上げます。 1 つ目は、ターゲット テーブルからレコードを選択するメイン レコードセットです。 2 つ目は、ターゲット テーブル内の列に関する情報を取得するために使われる特殊な列レコードセットです。

###  <a name="_core_the_general_process"></a> 一般的なプロセス

最も一般的なレベルでは、次のような手順で行います。

1. メイン レコードセット オブジェクトを構築します。

   必要に応じて、開いている `CDatabase` オブジェクトへのポインターを渡すか、または何らかの方法で列レコードセットへの接続情報を提供できます。

1. 列を動的に追加する手順を実行します。

   後の「列の追加」で説明されているプロセスを参照してください。

1. メイン レコードセットを開きます。

   レコードセットでレコードが選択され、レコード フィールド エクスチェンジ (RFX) を使って静的な列 (レコードセットのフィールド データ メンバーにマップされるもの) と動的な列 (ユーザーが割り当てた追加記憶域にマップされるもの) の両方がバインドされます。

###  <a name="_core_adding_the_columns"></a> 列の追加

追加された列を実行時に動的にバインドするには、次の手順が必要です。

1. 実行時に、ターゲット テーブルにある列を特定します。 その情報から、レコードセット クラスが設計された後でテーブルに追加された列の一覧を抽出します。

   データ ソースでターゲット テーブルの列の情報 (列の名前やデータ型など) に関するクエリを行うように設計されている列レコードセット クラスを使うのがよい方法です。

1. 新しいフィールド データ メンバー用の記憶域を提供します。 メイン レコードセット クラスには不明な列に対するフィールド データ メンバーがないため、名前、結果の値、および必要に応じてデータ型の情報 (列が異なるデータ型の場合) を格納する場所を提供する必要があります。

   1 つの方法は、動的なリストを 1 つ以上作成することです。1 つ目のリストは新しい列の名前用、2 つ目は結果の値用、3 つ目はデータ型用 (必要な場合) です。 これらのリスト (特に値リスト) で、バインドのための情報と必要な記憶域を提供します。 次の図はリストの作成を示したものです。

   ![動的にバインドする列のリストの作成](../../data/odbc/media/vc37w61.gif "動的にバインドする列のリストの作成")<br/>
   動的に結び付ける列のリストを生成する方法

1. メイン レコードセットの `DoFieldExchange` 関数で、追加する列ごとに RFX 関数の呼び出しを追加します。 これらの RFX の呼び出しでは、レコードをフェッチし、追加の列を組み込み、レコードセットのデータ メンバーまたは追加列用に動的に提供した記憶域に、列をバインドします。

   1 つの方法としては、メイン レコードセットの `DoFieldExchange` 関数にループを追加し、その中で、新しい列のリストをループ処理して、リスト内の各列に対して適切な RFX 関数を呼び出します。 各 RFX の呼び出しでは、列名リストからの列名と、結果値リストの対応するメンバーの記憶域の場所を渡します。

###  <a name="_core_lists_of_columns"></a> 列のリスト

処理する必要がある 4 つのリストを次の表に示します。

|||
|-|-|
|**Current-Table-Columns**| (図のリスト 1) データ ソースのテーブルに現在存在する列のリスト。 このリストは、レコードセットで現在バインドされている列のリストと一致する場合があります。|
|**Bound-Recordset-Columns**| (図のリスト 2) レコードセットでバインドされている列のリスト。 `DoFieldExchange` 関数にはこれらの列の RFX ステートメントが既にあります。|
|**Columns-To-Bind-Dynamically**| (図のリスト 3) テーブルにはあるがレコードセットにはない列のリスト。 これらは動的にバインドする列です。|
|**Dynamic-Column-Values**| (図のリスト 4) 動的にバインドする列から取得された値のための記憶域が含まれるリスト。 このリストの要素は、Columns-to-Bind-Dynamically の要素と一対一に対応します。|

###  <a name="_core_building_your_lists"></a> リストの構築

一般的な戦略を念頭に置いて、詳細に取りかかることができます。 このトピックの残りの部分では、「[列のリスト](#_core_lists_of_columns)」で示したリストを作成する方法を示します。 以下の手順について説明します。

- [レコードセットにない列の名前を特定します](#_core_determining_which_table_columns_are_not_in_your_recordset)。

- [テーブルに新しく追加する列用の動的な記憶域を提供します](#_core_providing_storage_for_the_new_columns)。

- [新しい列の RFX 呼び出しを動的に追加します](#_core_adding_rfx_calls_to_bind_the_columns)。

###  <a name="_core_determining_which_table_columns_are_not_in_your_recordset"></a> レコードセットに存在しないテーブル列の特定

メイン レコードセットで既にバインドされている列の一覧を含むリスト (Bound-Recordset-Columns、図のリスト 2) を作成します。 次に、データ ソースのテーブルにはあるがメイン レコードセットにはない列名を含むリスト (Columns-to-Bind-Dynamically、Current-Table-Columns と Bound-Recordset-Columns から派生) を作成します。

##### <a name="to-determine-the-names-of-columns-not-in-the-recordset-columns-to-bind-dynamically"></a>レコードセットにない列の名前を特定するには (Columns-to-Bind-Dynamically)

1. メイン レコードセットで既にバインドされている列のリスト (Bound-Recordset-Columns) を作成します。

   1 つの方法としては、設計時に Bound-Recordset-Columns を作成します。 レコードセットの `DoFieldExchange` 関数内で RFX 関数の呼び出しを目で見て調べて、これらの名前を取得できます。 次に、その名前で初期化された配列としてリストを設定します。

   たとえば、図で示されている Bound-Recordset-Columns (リスト 2) には 3 つの要素があります。 Bound-Recordset-Columns には、Current-Table-Columns (リスト 1) で示されている Phone 列がありません。

1. Current-Table-Columns と Bound-Recordset-Columns を比較して、メイン レコードセットでまだバインドされていない列のリスト (Columns-to-Bind-Dynamically) を作成します。

   1 つの方法は、実行時のテーブルの列のリスト (Current-Table-Columns) とレコードセットで既にバインドされている列のリスト (Bound-Recordset-Columns) を、並列にループ処理することです。 Current-Table-Columns に含まれる列のうち、Bound-Recordset-Columns に含まれないものの名前を、Columns-to-Bind-Dynamically に設定します。

   たとえば、図の Columns-to-Bind-Dynamically (リスト 3) に含まれる 1 つの要素 Phone 列は、Current-Table-Columns (リスト 1) では見つかりますが、Bound-Recordset-Columns (リスト 2) では見つかりません。

1. 動的にバインドする列のリスト (Columns-to-Bind-Dynamically) に格納されている各列名に対応するデータ値を格納するために、Dynamic-Column-Values のリスト (図のリスト 4) を作成します。

   このリストの要素は、新しいレコードセット フィールド データ メンバーの役割を果たします。 それらは、動的な列がバインドされる記憶域の場所です。 リストの説明については、「[列のリスト](#_core_lists_of_columns)」をご覧ください。

###  <a name="_core_providing_storage_for_the_new_columns"></a> 新しい列のための記憶域の提供

次に、動的にバインドする列に対する記憶域の場所を設定します。 考え方としては、各列の値を格納するリスト要素を提供します。 これらの記憶域の場所は、通常にバインドされた列が格納されるレコードセット メンバー変数と並列になっています。

#### <a name="to-provide-dynamic-storage-for-new-columns-dynamic-column-values"></a>新しい列の動的な記憶域を提供するには (Dynamic-Column-Values)

1. 各列のデータの値を格納する Dynamic-Column-Values (Columns-to-Bind-Dynamically と並列) を作成します。

   たとえば、図で示されている Dynamic-Column-Values (リスト 4) の 1 つの要素である `CString` オブジェクトには、現在のレコードの実際の電話番号が格納されます: "555-1212"。

   最も一般的なケースでは、Dynamic-Column-Values には `CString` 型の要素が含まれます。 さまざまなデータ型の列を扱っている場合は、さまざまな型の要素を含むことのできるリストが必要です。

上記の手順の結果は、2 つの主なリストです。つまり、列の名前が含まれる Columns-to-Bind-Dynamically と、現在のレコードに対する列の値が含まれる Dynamic-Column-Values です。

> [!TIP]
> 新しい列がすべて同じデータ型ではない場合は、列リストの各対応要素の型を何らかの方法で定義している項目が含まれる追加の並列リストが必要な場合があります。 (必要な場合は、AFX_RFX_BOOL、AFX_RFX_BYTE などの値をこれに使用できます。 これらの定数は、AFXDB.H で定義されています。)列のデータ型を表す方法に基づいて、リストの型を選択します。

###  <a name="_core_adding_rfx_calls_to_bind_the_columns"></a> 列をバインドするための RFX 呼び出しの追加

最後に、`DoFieldExchange` 関数内に新しい列の RFX 呼び出しを配置することによって、動的なバインドが行われるようにします。

##### <a name="to-dynamically-add-rfx-calls-for-new-columns"></a>新しい列の RFX 呼び出しを動的に追加するには

1. メイン レコードセットの `DoFieldExchange` メンバー関数で、新しい列のリスト (Columns-to-Bind-Dynamically) をループ処理するコードを追加します。 各ループでは、Columns-to-Bind-Dynamically から列の名前を、Dynamic-Column-Values から列の結果の値を抽出します。 これらの項目を、列のデータ型に適した RFX 関数の呼び出しに渡します。 リストの説明については、「[列のリスト](#_core_lists_of_columns)」をご覧ください。

一般的なケースでは、`RFX_Text` 関数の呼び出しの中で、次のコード行のように、リストから `CString` オブジェクトを抽出します。ここで、Columns-to-Bind-Dynamically は `m_listName` という名前の `CStringList` であり、Dynamic-Column-Values は `CStringList` という名前の `m_listValue` です。

```cpp
RFX_Text( pFX,
            m_listName.GetNext( posName ),
            m_listValue.GetNext( posValue ));
```

RFX 関数の詳細については、"*クラス ライブラリ リファレンス*" の「[Macros and Globals](../../mfc/reference/mfc-macros-and-globals.md)」 (マクロとグローバル) を参照してください。

> [!TIP]
> 新しい列が異なるデータ型の場合は、ループで switch ステートメントを使って、各型の適切な RFX 関数を呼び出します。

フレームワークで `Open` プロセスの間に `DoFieldExchange` を呼び出して列をレコードセットにバインドすると、静的列に対する RFX の呼び出しによってそれらの列がバインドされます。 その後、ループで動的な列の RFX 関数を繰り返し呼び出します。

## <a name="see-also"></a>関連項目

[レコードセット (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[レコードセット: 大きいデータ項目の処理 (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)