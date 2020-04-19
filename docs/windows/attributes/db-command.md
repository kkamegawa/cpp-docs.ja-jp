---
title: db_command (C++ COM 属性)
ms.date: 07/10/2018
f1_keywords:
- vc-attr.db_command
helpviewer_keywords:
- db_command attribute
ms.assetid: 714c3e15-85d7-408b-9a7c-88505c3e5d24
ms.openlocfilehash: 136c82b2674f3c08f053de9676068c0fb4baac11
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148199"
---
# <a name="dbcommand"></a>db_command

OLE DB コマンドを作成します。

## <a name="syntax"></a>構文

```cpp
[ db_command(command, name, source_name, hresult, bindings, bulk_fetch)
]
```

### <a name="parameters"></a>パラメーター

*command*<br/>
OLE DB コマンドのテキストを含むコマンド文字列。 簡単な例を次に示します。

```cpp
[ db_command ( command = "Select * from Products" ) ]
```

*command* の構文は次のとおりです。

> バインディング パラメーター ブロック 1 &nbsp; &nbsp;OLE DB コマンド バインディング パラメーター ブロック 2 &nbsp; &nbsp;OLE DB コマンド バインディング パラメーター ブロック 3 の継続しています.

*binding parameter block* は次のように定義します。

> **(\[** *bindtype* **]** *szVar1* \[, *szVar2* \[, *nVar3* \[, ...]]] **)**

それぞれの文字について以下に説明します。

- **(** は、データ バインディング ブロックの開始を示します。

- **\[** *bindtype* **]** 以下の文字列の 1 つです。

  - **\[db_column]** 行セット内の列に各メンバー変数をバインドします。

  - **\[bindto]** (同じ **\[db_column]**)。

  - **\[in]** 入力パラメーターとしてメンバー変数をバインドします。

  - **\[out]** 出力パラメーターとしてメンバー変数をバインドします。

  - **\[in、out]** 入力/出力パラメーターとしてメンバー変数をバインドします。

- *szVarX*、 *nVarX*現在のスコープ内のメンバー変数に解決されます。

- **)** は、データ バインディング ブロックの終了を示します。

などのコマンド文字列に 1 つまたは複数の指定子が含まれている場合\[で]、 \[out]、または\[入力/出力]、 **db_command**はパラメーター マップを作成します。

などのコマンド文字列に 1 つまたは複数のパラメーターが含まれている場合\[db_column] や\[bindto]、 **db_command**行セットとこれらのバインドされた変数へのアクセサー マップを生成します。 詳しくは、「 [db_accessor](db-accessor.md) 」をご覧ください。

> [!NOTE]
> \[*bindtype*] 構文と*バインド*を使用する場合のパラメーターは無効な**db_command**クラス レベルでします。

バインディング パラメーター ブロックの例を次にいくつか示します。 次の例では、pubs データベースの authors テーブルの `m_au_fname` 列と `m_au_lname` 列に、それぞれ `au_fname` および `au_lname` データ メンバーをバインドします。

```cpp
TCHAR m_au_fname[21];
TCHAR m_au_lname[41];
TCHAR m_state[3] = 'CA';

[db_command (command = "SELECT au_fname([bindto]m_au_fname), au_lname([bindto]m_au_lname) " \
   "FROM dbo.authors " \
   "WHERE state = ?([in]m_state)")
]
```

*name*<br/>
(省略可能)行セットの操作に使用するためのハンドルの名前。 *name*を指定した場合、 **db_command** は指定された *name*のクラスを生成します。このクラスを使用して、行セットを走査したり、複数のアクション クエリを実行したりできます。 *name*を指定しないと、複数の結果行をユーザーに返すことはできません。

*source_name*<br/>
(省略可能)`CSession`変数またはを持つクラスのインスタンス、`db_source`コマンドが実行されることに適用される属性。 「 [db_source](db-source.md)」をご覧ください。

**db_command** は *source_name* に使用されている変数が有効であることを確認するので、指定する変数は関数スコープまたはグローバル スコープに存在する必要があります。

*hresult*<br/>
(省略可能)このデータベース コマンドの HRESULT を受け取る変数を識別します。 変数が存在しない場合は、属性によって自動的に挿入されます。

*バインド*<br/>
(省略可能)OLE DB コマンドからバインディング パラメーターを分離することができます。

値を指定する場合*バインド*、 **db_command**は関連付けられている値を解析し、解析しません、 \[ *bindtype*] パラメーターです。 これにより、OLE DB プロバイダーの構文を使用できます。 パラメーターをバインドせず、解析を無効にするには指定`Bindings=""`します。

値を指定しない場合*バインド*、 **db_command**を探して、バインディング パラメーター ブロックは解析 '**(**'、その後に **\[** _bindtype_**]** を 1 つ後に角かっこ、またはより以前に宣言されたC++メンバー変数、続けて '**)**'。 かっこで囲まれたすべてのテキストが最終的なコマンドから削除され、これらのパラメーターを使用してこのコマンドの列とパラメーターのバインディングが作成されます。

*bulk_fetch*<br/>
(省略可能)フェッチする行の数を指定する整数値。

既定値は 1 で、単一行のフェッチを指定します (行セットは [CRowset](../../data/oledb/crowset-class.md)型です)。

1 より大きい値は、バルク行フェッチを指定します。 バルク行フェッチとは、複数の行ハンドルをフェッチするバルク行セットの機能のことです (行セットは [CBulkRowset](../../data/oledb/cbulkrowset-class.md) 型であり、指定された行数で `SetRows` を呼び出します)。

*bulk_fetch* が 1 より小さい場合は、 `SetRows` は 0 を返します。

## <a name="remarks"></a>Remarks

OLE DB コンシューマーは、**db_command** によって作成された [CCommand](../../data/oledb/ccommand-class.md) オブジェクトを使用して、コマンドを実行します。

**db_command** はクラス スコープまたは関数スコープで使用できます。主な違いは、 `CCommand` オブジェクトのスコープです。 関数スコープでは、バインディングなどのデータは関数の終了時に終了します。 クラスと関数のスコープの使用法は、OLE DB コンシューマー テンプレート クラスを伴う`CCommand<>`、テンプレート引数は、関数およびクラスの場合の点が異なります。 関数の場合、バインドできるように、`Accessor`クラスの使用状況は推論中にローカル変数で構成する、 `CAccessor`-引数としてクラスを派生します。 クラス属性として使用すると、 **db_command** は **db_column**と共に動作します。

**db_command** を使用して、結果セットを返さないコマンドを実行できます。

コンパイラにクラスの名前は、コンシューマー属性プロバイダーでは、この属性をクラスに適用されます、ときに\_ *YourClassName*、アクセサーで*YourClassName*に付けた名前を指定します、クラス、さらに、コンパイラはというクラスを作成も*YourClassName*から派生した\_ *YourClassName*アクセサー。  クラス ビューでは、両方のクラスが表示されます。

## <a name="example"></a>例

この例では、テーブルから state 列が 'CA' と一致する姓と名を選択するコマンドを定義しています。 **db_command** は、ウィザードで生成される [OpenAll and CloseAll](../../data/oledb/consumer-wizard-generated-methods.md)などの関数および `CRowset` MoveNext [などの](../../data/oledb/crowset-movenext.md)メンバー関数を呼び出すことができる行セットを作成して読み取ります。

このコードでは、pubs データベースに接続する独自の接続文字列を指定する必要があることに注意してください。 開発環境でこれを行う方法については、次を参照してください。[方法。既存のオブジェクトの参照と、データベースに接続する](/sql/ssdt/how-to-connect-to-a-database-and-browse-existing-objects)と[新しい接続を追加](/visualstudio/data-tools/add-new-connections)します。

```cpp
// db_command.h
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

#pragma once

[  db_source(L"your connection string"), db_command(L" \
      SELECT au_lname, au_fname \
      FROM dbo.authors \
      WHERE state = 'CA'")  ]

struct CAuthors {
   // In order to fix several issues with some providers, the code below may bind
   // columns in a different order than reported by the provider

   DBSTATUS m_dwau_lnameStatus;
   DBSTATUS m_dwau_fnameStatus;
   DBLENGTH m_dwau_lnameLength;
   DBLENGTH m_dwau_fnameLength;

   [ db_column("au_lname", status="m_dwau_lnameStatus", length="m_dwau_lnameLength") ] TCHAR m_au_lname[41];
   [ db_column("au_fname", status="m_dwau_fnameStatus", length="m_dwau_fnameLength") ] TCHAR m_au_fname[21];

   [ db_param("7", paramtype="DBPARAMIO_INPUT") ] TCHAR m_state[3];

   void GetRowsetProperties(CDBPropSet* pPropSet) {
      pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
      pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   }
};
```

## <a name="example"></a>例

```cpp
// db_command.cpp
// compile with: /c
#include "db_command.h"

int main(int argc, _TCHAR* argv[]) {
   HRESULT hr = CoInitialize(NULL);

   // Instantiate rowset
   CAuthors rs;

   // Open rowset and move to first row
   strcpy_s(rs.m_state, sizeof(rs.m_state), _T("CA"));
   hr = rs.OpenAll();
   hr = rs.MoveFirst();

   // Iterate through the rowset
   while( SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET ) {
      // Print out the column information for each row
      printf("First Name: %s, Last Name: %s\n", rs.m_au_fname, rs.m_au_lname);
      hr = rs.MoveNext();
   }

   rs.CloseAll();
   CoUninitialize();
}
```

## <a name="example"></a>例

この例では、データ ソース クラス `db_source` で `CMySource`を使用し、コマンド クラス `db_command` と `CCommand1` で `CCommand2`を使用します。

```cpp
// db_command_2.cpp
// compile with: /c
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>
// class usage for both db_source and db_command

[  db_source(L"your connection string"), db_command(L" \
      SELECT au_lname, au_fname \
      FROM dbo.authors \
      WHERE state = 'CA'")  ]
struct CMySource {
   HRESULT OpenDataSource() {
      return S_OK;
   }
};

[db_command(command = "SELECT * FROM Products")]
class CCommand1 {};

[db_command(command = "SELECT FNAME, LNAME FROM Customers")]
class CCommand2 {};

int main() {
   CMySource s;
   HRESULT hr = s.OpenDataSource();
   if (SUCCEEDED(hr)) {
      CCommand1 c1;
      hr = c1.Open(s);

      CCommand2 c2;
      hr = c2.Open(s);
   }

   s.CloseDataSource();
}
```

## <a name="requirements"></a>要件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|**クラス**、**構造体**member、method、local|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|なし|

属性コンテキストの詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[OLE DB コンシューマー属性](ole-db-consumer-attributes.md)<br/>
[スタンドアロン属性](stand-alone-attributes.md)
