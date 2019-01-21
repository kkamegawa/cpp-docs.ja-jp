---
title: CMapStringToString クラス
ms.date: 11/04/2016
f1_keywords:
- CMapStringToString
- AFXCOLL/CMapStringToString
- AFXCOLL/CMapStringToString::CPair
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
- AFXCOLL/CMapStringToString::PGetFirstAssoc
- AFXCOLL/CMapStringToString::PGetNextAssoc
- AFXCOLL/CMapStringToString::PLookup
- AFXCOLL/CMapStringToOb::RemoveAll
- AFXCOLL/CMapStringToOb::RemoveKey
- AFXCOLL/CMapStringToOb::SetAt
helpviewer_keywords:
- CMapStringToString [MFC], CPair
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
- CMapStringToString [MFC], PGetFirstAssoc
- CMapStringToString [MFC], PGetNextAssoc
- CMapStringToString [MFC], PLookup
- CMapStringToOb [MFC], RemoveAll
- CMapStringToOb [MFC], RemoveKey
- CMapStringToOb [MFC], SetAt
ms.assetid: b45794c2-fe6b-4edb-a8ca-faa03b57b4a8
ms.openlocfilehash: 754232ea57a77b4eb37a72ff98a3150419d0a248
ms.sourcegitcommit: 53f75afaf3c0b3ed481c5503357ed2b7b87aac6d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53657371"
---
# <a name="cmapstringtostring-class"></a>CMapStringToString クラス

`CString` オブジェクトをキーとした `CString` オブジェクトのマップをサポートします。

## <a name="syntax"></a>構文

```
class CMapStringToString : public CObject
```

## <a name="members"></a>メンバー

メンバー関数は、`CMapStringToString`クラスのメンバー関数のような[CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md)します。 メンバー関数については `CMapStringToOb` クラスの説明を参照してください。 任意の場所を確認、`CObject`へのポインターにポインターの戻り値または「出力」パラメーターを関数として置き換えます**char**します。 任意の場所が表示、 `CObject` 「入力」関数パラメーターとしてのポインターへのポインターを置き換える**char**します。

`BOOL CMapStringToOb::Lookup(const char*<key>, CObject*&<rValue>) const;`

たとえば、次のように変換します。

`BOOL CMapStringToString::Lookup(LPCTSTR<key>, CString&<rValue>) const;`

### <a name="public-structures"></a>パブリック構造体

|名前|説明|
|----------|-----------------|
|[CMapStringToString::CPair](#cpair)|キーの値と関連付けられている文字列オブジェクトの値を含む入れ子になった構造体。|

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
|[CMapStringToString::PGetFirstAssoc](#pgetfirstassoc)|最初にポインターを取得します。`CString`マップにします。|
|[CMapStringToString::PGetNextAssoc](#pgetnextassoc)|次のポインターを取得`CString`の反復処理します。|
|[CMapStringToString::PLookup](#plookup)|ポインターを返します、`CString`値を持つ指定した値に一致します。|
|[CMapStringToOb::RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|このマップからすべての要素を削除します。|
|[CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|キーで指定された要素を削除します。|
|[CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|マップに要素を挿入します。一致するキーが見つかった場合は、既存の要素を置き換えます。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CMapStringToOb::operator \[ \]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|マップに要素を挿入、演算子の代替の`SetAt`します。|

## <a name="remarks"></a>Remarks

`CMapStringToString` には、`IMPLEMENT_SERIAL` マクロが組み込まれており、その要素のシリアル化とダンプがサポートされます。 各要素は、アーカイブ、オーバー ロードされた挿入のあるいずれかにマップが格納されている場合にシリアル化。 ( **<<**) 演算子、または、`Serialize`メンバー関数。

個別にダンプする必要がある場合`CString` -  `CString`要素、1 以上に、ダンプ コンテキストの深さを設定する必要があります。

ときに、`CMapStringToString`オブジェクトを削除すると、またはその要素が削除されます、`CString`オブジェクトは、必要に応じて削除されます。

詳細については`CMapStringToString`、記事をご覧ください[コレクション](../../mfc/collections.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToString`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxcoll.h

##  <a name="cpair"></a>  CMapStringToString::CPair

キー値と関連付けられている文字列オブジェクトの値が含まれています。

### <a name="remarks"></a>Remarks

これは、クラス内で入れ子になった構造[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)します。

構造体が 2 つのフィールドで構成されます。

- `key` キーの種類の実際の値。

- `value` 関連付けられたオブジェクトの値。

戻り値を格納するために[CMapStringToString::PLookup](#plookup)、 [CMapStringToString::PGetFirstAssoc](#pgetfirstassoc)、および[CMapStringToString::PGetNextAssoc](#pgetnextassoc)します。

### <a name="example"></a>例

  使用状況の例は、の例を参照してください。 [CMapStringToString::PLookup](#plookup)します。

##  <a name="pgetfirstassoc"></a>  CMapStringToString::PGetFirstAssoc

マップ オブジェクトの最初のエントリを返します。

```
const CPair* PGetFirstAssoc() const;

CPair* PGetFirstAssoc();
```

### <a name="return-value"></a>戻り値

マップ内の最初のエントリへのポインター参照してください[CMapStringToString::CPair](#cpair)します。 マップが空の場合、値は NULL です。

### <a name="remarks"></a>Remarks

この関数では、マップ オブジェクト内の最初の要素のポインターを返します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#73](../../mfc/codesnippet/cpp/cmapstringtostring-class_1.cpp)]

##  <a name="pgetnextassoc"></a>  CMapStringToString::PGetNextAssoc

によって示されるマップ要素を取得*pAssocRec*します。

```
const CPair *PGetNextAssoc(const CPair* pAssoc) const;

CPair *PGetNextAssoc(const CPair* pAssoc);
```

### <a name="parameters"></a>パラメーター

*pAssoc*<br/>
直前のマップ エントリが指す[PGetNextAssoc](#pgetnextassoc)または[PGetFirstAssoc](#pgetfirstassoc)呼び出します。

### <a name="return-value"></a>戻り値

マップ内の次のエントリへのポインター参照してください[CMapStringToString::CPair](#cpair)します。 要素がマップ内の最後の場合は、値は NULL です。

### <a name="remarks"></a>Remarks

マップ内のすべての要素を反復処理するには、このメソッドを呼び出します。 呼び出しの最初の要素を取得`PGetFirstAssoc`を連続する呼び出すと、マップを反復処理し、`PGetNextAssoc`します。

### <a name="example"></a>例

  例をご覧ください[CMapStringToString::PGetFirstAssoc](#pgetfirstassoc)します。

##  <a name="plookup"></a>  CMapStringToString::PLookup

指定されたキーにマップされている値を検索します。

```
const CPair* PLookup(LPCTSTR key) const;

CPair* PLookup(LPCTSTR key);
```

### <a name="parameters"></a>パラメーター

*key*<br/>
検索する要素のキーへのポインター。

### <a name="return-value"></a>戻り値

指定されたキーへのポインター。

### <a name="remarks"></a>Remarks

指定したキーと一致するキーを持つマップ要素を検索するには、このメソッドを呼び出します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#74](../../mfc/codesnippet/cpp/cmapstringtostring-class_2.cpp)]

## <a name="see-also"></a>関連項目

[MFC サンプルの収集](../../visual-cpp-samples.md)<br/>
[CObject クラス](../../mfc/reference/cobject-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)

