---
title: db_column (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_column
helpviewer_keywords:
- db_column attribute
ms.assetid: 58da4afc-f69c-4ae6-af9a-3f9515f56081
ms.openlocfilehash: e0e2c873452884275e97663ae2d9d6df2f790ffd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148184"
---
# <a name="db_column"></a>db_column

指定された列を行セット内の変数にバインドします。

## <a name="syntax"></a>構文

```cpp
[ db_column(ordinal, dbtype, precision, scale, status, length) ]
```

#### <a name="parameters"></a>パラメーター

*序数*<br/>
列の序数 (`DBCOLUMNINFO`序数) またはデータをバインドする行セット内のフィールドに対応する列の名前 (ANSI または Unicode 文字列)。 番号を使用する場合は、連続する序数を省略できます (例。1, 2, 3, 5). 使用する OLE DB プロバイダーでサポートされている場合、名前はスペースを含めることがあります。 たとえば、次の形式のいずれかを使用できます。

```cpp
[db_column("2")] TCHAR szCity[30];
[db_column(L"city_name")] TCHAR szCity[30];
```

*dbtype*<br/>
(省略可能)OLE DB[型インジケーター](/previous-versions/windows/desktop/ms711251(v=vs.85))列エントリにします。

*precision*<br/>
(省略可能)列のエントリに使用する有効桁数です。 詳細については、説明を参照してください、`bPrecision`の要素、 [DBBINDING 構造体](/previous-versions/windows/desktop/ms716845(v=vs.85))

*scale*<br/>
(省略可能)列のエントリに使用する小数点以下桁数。 詳細については、説明を参照してください`bScale`の要素、 [DBBINDING 構造体。](/previous-versions/windows/desktop/ms716845(v=vs.85))

*status*<br/>
(省略可能)この列の状態を保持するために使用するメンバー変数です。 状態は、列の値がデータ値や NULL など、他のいくつかの値であるかどうかを示します。 使用可能な値は、次を参照してください。[状態](/previous-versions/windows/desktop/ms722617(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

*length*<br/>
(省略可能)メンバー変数 (バイト単位)、列のサイズを保持するために使用します。

## <a name="remarks"></a>Remarks

**db_column**行セット内の変数に指定したテーブル列をバインドします。 OLE DB に参加できるメンバー データを区切る`IAccessor`-ベースのバインド。 この属性は、通常 OLE DB コンシューマーのマクロを使用して定義されている列のマップを設定[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)、 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)、および[COLUMN_ENTRY](../../data/oledb/column-entry.md)します。 これらの操作、OLE DB [DBBINDING 構造体](/previous-versions/windows/desktop/ms716845(v=vs.85))指定された列にバインドします。 各メンバーをマークする、 **db_column**属性は、列のエントリの形式で列のマップで 1 つのエントリを占有します。 したがって、コピー先の場所は列のマップは、コマンドまたはテーブル クラスでこの属性を呼び出します。

使用**db_column**いずれかと組み合わせて、 [db_table](db-table.md)または[db_command](db-command.md)属性。

コンパイラにクラスの名前は、コンシューマー属性プロバイダーでは、この属性をクラスに適用されます、ときに\_ *YourClassName*、アクセサーで*YourClassName*に付けた名前を指定します、クラス、さらに、コンパイラはというクラスを作成も*YourClassName*から派生した\_ *YourClassName*アクセサー。  クラス ビューでは、両方のクラスが表示されます。

アプリケーションで使用されるこの属性の例については、サンプル[AtlAgent](https://github.com/Microsoft/VCSamples)、および[MultiRead](https://github.com/Microsoft/VCSamples)します。

## <a name="example"></a>例

このサンプルでは、列をバインドするテーブルで、**long**データ メンバーをステータスや長さのフィールドを指定します。

```cpp
// db_column_1.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_command(L"Select * from Products") ]
class CProducts {
   DBSTATUS m_dwProductIDStatus;
   DBLENGTH m_dwProductIDLength;

   [ db_column("1", status="m_dwProductIDStatus", length="m_dwProductIDLength") ] LONG m_ProductID;
};
```

## <a name="example"></a>例

このサンプルを 4 つの列をバインドする、**long**、文字の文字列、タイムスタンプ、および`DB_NUMERIC`をこの順序で、整数。

```cpp
// db_column_2.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_command(L"Select * from Products") ]
class CProducts {
   [db_column("1")] LONG m_OrderID;
   [db_column("2")] TCHAR m_CustomerID[6];
   [db_column("4")] DB_NUMERIC m_OrderDate;
   [db_column("7", dbtype="DBTYPE_NUMERIC")] DB_NUMERIC m_ShipVia;
};
```

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|**クラス**、**構造体**メンバー、メソッド|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|なし|

属性コンテキストの詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[OLE DB コンシューマー属性](ole-db-consumer-attributes.md)<br/>
[クラス属性](class-attributes.md)
