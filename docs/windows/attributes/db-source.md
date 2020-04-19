---
title: db_source (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_source
helpviewer_keywords:
- db_source attribute
ms.assetid: 0ec8bbf7-ade2-4899-bf4c-8608b92779bc
ms.openlocfilehash: 884cab78d64c20bef00958f0cc0319281fd69921
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148108"
---
# <a name="dbsource"></a>db_source

データ ソースへの接続を作成します。

## <a name="syntax"></a>構文

```cpp
[ db_source(db_source, name, hresult) ]
```

### <a name="parameters"></a>パラメーター

*db_source*<br/>
データ ソースに接続するために使用する接続文字列。 接続文字列の形式の場合、次を参照してください。[データ リンクの接続文字列と](/previous-versions/windows/desktop/ms718376(v=vs.85))で、Microsoft Data Access Components (MDAC) SDK。

*name*<br/>
(省略可能)使用すると**db_source**クラスで*名前*を持つデータ ソース オブジェクトのインスタンスです、 **db_source**属性 (例 1 を参照してください) を適用します。 使用すると**db_source**インライン メソッドの実装で*名前*データにアクセスするために使用される変数 (ローカル メソッド) は、ソース (例 2 を参照してください)。 これを渡す*名前*を*source_name*のパラメーター`db_command`にデータ ソースを関連付けるコマンド。

*hresult*<br/>
(省略可能)このデータベース コマンドの HRESULT を受け取る変数を識別します。 変数が存在しない場合は、属性によって自動的に挿入されます。

## <a name="remarks"></a>Remarks

**db_source**作成、 [CDataSource](../../data/oledb/cdatasource-class.md)と[CSession](../../data/oledb/csession-class.md)オブジェクトで、1 つと、OLE DB コンシューマーのデータ ソースの接続を表します。

使用すると**db_source**クラスで、`CSession`オブジェクト クラスのメンバーになります。

使用すると**db_source**メソッドのスコープ内で、挿入されたコードを実行メソッドでは、および`CSession`オブジェクトは、ローカル変数として作成されます。

**db_source**クラスまたはメソッド内では、データ ソースのプロパティを追加します。 組み合わせて使用されます`db_command`(受け取り、 *db_source* *名前*パラメーターとしてその*source_name*パラメーター)。

コンパイラにクラスの名前は、コンシューマー属性プロバイダーでは、この属性をクラスに適用されます、ときに\_ *YourClassName*、アクセサーで*YourClassName*に付けた名前を指定します、クラス、さらに、コンパイラはというクラスを作成も*YourClassName*から派生した\_ *YourClassName*アクセサー。  クラス ビューでは、両方のクラスが表示されます。

アプリケーションで使用されるこの属性の例では、サンプルを参照してください。 [AtlAgent](https://github.com/Microsoft/VCSamples)と[MultiRead](https://github.com/Microsoft/VCSamples)します。

## <a name="example"></a>例

このサンプルを呼び出す**db_source**データ ソースへの接続を作成するクラスの`ds`Northwind データベースを使用します。 `ds` 内部で使用できるデータ ソースのハンドル、`CMyCommand`クラス。

```cpp
// db_source_1.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[
  db_source(L"my_connection_string", name="ds"),
  db_command(L"select * from Products")
]
class CMyCommand {};
```

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|**クラス**、**構造体**member、method、local|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|なし|

属性コンテキストの詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[OLE DB コンシューマー属性](ole-db-consumer-attributes.md)
