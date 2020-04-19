---
title: db_accessor (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_accessor
helpviewer_keywords:
- db_accessor attribute
ms.assetid: ec407a9f-24d7-4822-96d4-7cc6a0301815
ms.openlocfilehash: bfb287261fce4ebf189801c308f57513f2c9f113
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148251"
---
# <a name="dbaccessor"></a>db_accessor

グループ`db_column`に参加している属性`IAccessor`-ベースのバインド。

## <a name="syntax"></a>構文

```cpp
[ db_accessor(num, auto) ]
```

#### <a name="parameters"></a>パラメーター

*num*<br/>
アクセサーの数 (0 から始まる整数のインデックス) を指定します。 昇順にアクセサー番号が整数を使用して、注文や、定義された値を指定する必要があります。

*auto*<br/>
アクセサーが自動的に取得されます (TRUE) か (FALSE) を取得できないかどうかを指定するブール値。

## <a name="remarks"></a>Remarks

**db_accessor**の基になる OLE DB アクセサーを定義します。 後続`db_column`と`db_param`同じクラスまたは関数内の属性。 **db_accessor**はメンバーのレベルで使用可能なと使用をグループに`db_column`OLE DB に参加している属性`IAccessor`-ベースのバインド。 いずれかと組み合わせて使用されます、`db_table`または`db_command`属性。 この属性を呼び出すことは、呼び出しに似ています、 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)と[END_ACCESSOR](../../data/oledb/end-accessor.md)マクロ。

**db_accessor**行セットを生成し、対応するアクセサー マップにバインドします。 呼び出さない場合**db_accessor**アクセサー 0 が自動的に生成して、すべての列バインドはこのアクセサー ブロックにマップされます。

**db_accessor**グループ データベースの 1 つまたは複数のアクセサーに列のバインド。 複数のアクセサーを使用する必要があるシナリオの詳細については、次を参照してください。[行セットでの複数のアクセサーを使用して](../../data/oledb/using-multiple-accessors-on-a-rowset.md)します。 参照してください「ユーザー レコードのサポートの複数のアクセサー」[ユーザー レコード](../../data/oledb/user-records.md)します。

コンパイラにクラスの名前は、コンシューマー属性プロバイダーでは、この属性をクラスに適用されます、ときに\_ *YourClassName*、アクセサーで*YourClassName*に付けた名前を指定します、クラス、さらに、コンパイラはというクラスを作成も*YourClassName*から派生した\_ *YourClassName*アクセサー。  クラス ビューでは、両方のクラスが表示されます。

## <a name="example"></a>例

次の例では**db_accessor** Orders テーブルの 2 つのアクセサーに Northwind データベースからのグループ列にします。 アクセサー 0 は、自動のアクセサーと 1 のアクセサーはありません。

```cpp
// cpp_attr_ref_db_accessor.cpp
// compile with: /LD /link /OPT:NOREF
#define _ATL_ATTRIBUTES
#include <atlbase.h>
#include <atldbcli.h>

[ db_command(L"SELECT LastName, FirstName FROM Orders") ]
class CEmployees {
public:
   [ db_accessor(0, TRUE) ];
   [ db_column("1") ] LONG m_OrderID;
   [ db_column("2") ] TCHAR m_CustomerID[6];
   [ db_column("4") ] DBTIMESTAMP m_OrderDate;

   [ db_accessor(1, FALSE) ];
   [ db_column("8") ] CURRENCY m_Freight;
};
```

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|属性ブロック|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|なし|

属性コンテキストの詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[OLE DB コンシューマー属性](ole-db-consumer-attributes.md)