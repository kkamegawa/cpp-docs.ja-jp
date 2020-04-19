---
title: CMapPtrToPtr クラス
ms.date: 11/04/2016
f1_keywords:
- CMapPtrToPtr
- AFXCOLL/CMapPtrToPtr
- AFXCOLL/CMapStringToOb::CMapStringToOb
- AFXCOLL/CMapStringToOb::GetCount
- AFXCOLL/CMapStringToOb::GetHashTableSize
- AFXCOLL/CMapStringToOb::GetNextAssoc
- AFXCOLL/CMapStringToOb::GetSize
- AFXCOLL/CMapStringToOb::GetStartPosition
- AFXCOLL/CMapStringToOb::HashKey
- AFXCOLL/CMapStringToOb::InitHashTable
- AFXCOLL/CMapStringToOb::IsEmpty
- AFXCOLL/CMapStringToOb::Lookup
- AFXCOLL/CMapStringToOb::LookupKey
- AFXCOLL/CMapStringToOb::RemoveAll
- AFXCOLL/CMapStringToOb::RemoveKey
- AFXCOLL/CMapStringToOb::SetAt
helpviewer_keywords:
- CMapStringToOb [MFC], CMapStringToOb
- CMapStringToOb [MFC], GetCount
- CMapStringToOb [MFC], GetHashTableSize
- CMapStringToOb [MFC], GetNextAssoc
- CMapStringToOb [MFC], GetSize
- CMapStringToOb [MFC], GetStartPosition
- CMapStringToOb [MFC], HashKey
- CMapStringToOb [MFC], InitHashTable
- CMapStringToOb [MFC], IsEmpty
- CMapStringToOb [MFC], Lookup
- CMapStringToOb [MFC], LookupKey
- CMapStringToOb [MFC], RemoveAll
- CMapStringToOb [MFC], RemoveKey
- CMapStringToOb [MFC], SetAt
ms.assetid: 23cbbaec-9d64-48f2-92ae-5e24fa64b926
ms.openlocfilehash: a44b9524324065581583bad13018b2c4479fc9f3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62237748"
---
# <a name="cmapptrtoptr-class"></a>CMapPtrToPtr クラス

void ポインターをキーとした void ポインターのマップをサポートします。

## <a name="syntax"></a>構文

```
class CMapPtrToPtr : public CObject
```

## <a name="members"></a>メンバー

メンバー関数は、`CMapPtrToPtr`クラスのメンバー関数のような[CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md)します。 メンバー関数については `CMapStringToOb` クラスの説明を参照してください。 任意の場所が表示、`CObject`関数パラメーターまたは戻り値としてのポインターへのポインターを置き換える**void**します。 任意の場所が表示、`CString`または**const**へのポインター **char**関数パラメーターまたは戻り値へのポインターを置き換える**void**します。

`BOOL CMapStringToOb::Lookup( const char* <key>, CObject*& <rValue> ) const;`

たとえば、次のように変換します。

`BOOL CMapPtrToPtr::Lookup( void* <key>, void*& <rValue> ) const;`

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMapStringToOb::CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|コンストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMapStringToOb::GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|このマップ要素の数を返します。|
|[CMapStringToOb::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|現在のハッシュ テーブル内の要素数を決定します。|
|[CMapStringToOb::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|反復処理するためには、次の要素を取得します。|
|[CMapStringToOb::GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|このマップ要素の数を返します。|
|[CMapStringToOb::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|最初の要素の位置を返します。|
|[CMapStringToOb::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|指定したキーのハッシュ値を計算します。|
|[CMapStringToOb::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|ハッシュ テーブルを初期化します。|
|[CMapStringToOb::IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|マップが空の状態 (要素がない場合) をテストします。|
|[CMapStringToOb::Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Void ポインター キーに基づく void ポインターを検索します。 エンティティではなく、ポインター値は、キーの比較に使用されます。|
|[CMapStringToOb::LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|指定したキー値に関連付けられているキーへの参照を返します。|
|[CMapStringToOb::RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|このマップからすべての要素を削除します。|
|[CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|キーで指定された要素を削除します。|
|[CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|マップに要素を挿入します。一致するキーが見つかった場合は、既存の要素を置き換えます。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CMapStringToOb::operator \[ \]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|マップに要素を挿入、演算子の代替の`SetAt`します。|

## <a name="remarks"></a>Remarks

`CMapPtrToPtr` 実行時の型へのアクセスとダンプをサポートするために IMPLEMENT_DYNAMIC マクロが組み込まれています、`CDumpContext`オブジェクト。 個々 のマップ要素 (ポインター値) のダンプが必要な場合は、1 以上にダンプ コンテキストの深さを設定する必要があります。

ポインターとポインターのマップは、シリアル化されません。

`CMapPtrToPtr` オブジェクトが削除されたとき、またはその要素が削除されたときは、ポインターだけが削除されます。ポインターが参照するエンティティは削除されません。

詳細については`CMapPtrToPtr`、記事をご覧ください[コレクション](../../mfc/collections.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CMapPtrToPtr`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxcoll.h

## <a name="see-also"></a>関連項目

[CObject クラス](../../mfc/reference/cobject-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)
