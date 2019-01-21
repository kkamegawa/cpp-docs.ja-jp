---
title: CMapStringToOb クラス
ms.date: 11/04/2016
f1_keywords:
- CMapStringToOb
- AFXCOLL/CMapStringToOb
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
ms.assetid: 09653980-b885-4f3a-8594-0aeb7f94c601
ms.openlocfilehash: 75e9b49bca6b94595186e69a900a28fe5e38522c
ms.sourcegitcommit: 53f75afaf3c0b3ed481c5503357ed2b7b87aac6d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53657618"
---
# <a name="cmapstringtoob-class"></a>CMapStringToOb クラス

一意の `CString` オブジェクトを `CObject` へのポインターに割り当てる辞書コレクション クラスです。

## <a name="syntax"></a>構文

```
class CMapStringToOb : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMapStringToOb::CMapStringToOb](#cmapstringtoob)|コンストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMapStringToOb::GetCount](#getcount)|このマップ要素の数を返します。|
|[CMapStringToOb::GetHashTableSize](#gethashtablesize)|現在のハッシュ テーブル内の要素数を決定します。|
|[CMapStringToOb::GetNextAssoc](#getnextassoc)|反復処理するためには、次の要素を取得します。|
|[CMapStringToOb::GetSize](#getsize)|このマップ要素の数を返します。|
|[CMapStringToOb::GetStartPosition](#getstartposition)|最初の要素の位置を返します。|
|[CMapStringToOb::HashKey](#hashkey)|指定したキーのハッシュ値を計算します。|
|[CMapStringToOb::InitHashTable](#inithashtable)|ハッシュ テーブルを初期化します。|
|[CMapStringToOb::IsEmpty](#isempty)|マップが空の状態 (要素がない場合) をテストします。|
|[CMapStringToOb::Lookup](#lookup)|Void ポインター キーに基づく void ポインターを検索します。 エンティティではなく、ポインター値は、キーの比較に使用されます。|
|[CMapStringToOb::LookupKey](#lookupkey)|指定したキー値に関連付けられているキーへの参照を返します。|
|[CMapStringToOb::RemoveAll](#removeall)|このマップからすべての要素を削除します。|
|[CMapStringToOb::RemoveKey](#removekey)|キーで指定された要素を削除します。|
|[CMapStringToOb::SetAt](#setat)|マップに要素を挿入します。一致するキーが見つかった場合は、既存の要素を置き換えます。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CMapStringToOb::operator \[ \]](#operator_at)|マップに要素を挿入、演算子の代替の`SetAt`します。|

## <a name="remarks"></a>Remarks

挿入すると、 `CString` -  `CObject*`ペア (要素)、マップには、効率的に取得または、文字列を使用してペアを削除することができます、`CString`キーと値。 また、マップ内のすべての要素を反復処理することができます。

位置の型の変数は、すべての種類のマップで別のエントリのアクセスに使用されます。 エントリを「記憶」して、マップを反復処理する位置を使用することができます。 このイテレーションがキーの値にシーケンシャルであると思われる場合があります。そうじゃないです。 取得する要素の順序は不確定です。

`CMapStringToOb` には、`IMPLEMENT_SERIAL` マクロが組み込まれており、その要素のシリアル化とダンプがサポートされます。 各要素は、アーカイブ、オーバー ロードされた挿入のあるいずれかにマップが格納されている場合にシリアル化。 ( **<<**) 演算子、または、`Serialize`メンバー関数。

マップ内の個々 の要素の診断ダンプが必要なかどうか (、`CString`値と`CObject`内容)、ダンプ コンテキストの深さは 1 以上に設定する必要があります。

ときに、`CMapStringToOb`オブジェクトを削除すると、またはその要素が削除されます、`CString`オブジェクトと`CObject`ポインターを削除します。 によって参照されるオブジェクト、`CObject`ポインターは破棄されません。

マップ クラスの派生は、リストの派生に似ています。 記事をご覧ください[コレクション](../../mfc/collections.md)特殊なリスト クラスの派生の例についてはします。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToOb`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxcoll.h

##  <a name="cmapstringtoob"></a>  CMapStringToOb::CMapStringToOb

空の構築`CString`対`CObject*`マップします。

```
CMapStringToOb(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>パラメーター

*nBlockSize*<br/>
マップを拡張するためのメモリ割り当ての粒度を指定します。

### <a name="remarks"></a>Remarks

単位でメモリが割り当てられているマップが拡大に合わせて*nBlockSize*エントリ。

次の表はその他のメンバー関数に似ている`CMapStringToOb:: CMapStringToOb`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**CMapPtrToPtr( INT_PTR** `nBlockSize` **= 10 );**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**CMapPtrToWord( INT_PTR** `nBlockSize` **= 10 );**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**CMapStringToPtr( INT_PTR** `nBlockSize` **= 10 );**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CMapStringToString( INT_PTR** `nBlockSize` **= 10 );**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CMapWordToOb( INT_PTR** `nBlockSize` **= 10 );**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**MapWordToPtr( INT_PTR** `nBlockSize` **= 10 );**|

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#63](../../mfc/codesnippet/cpp/cmapstringtoob-class_1.cpp)]

参照してください[使われて](../../mfc/reference/coblist-class.md#coblist)の一覧については、`CAge`コレクションのすべての例で使用されるクラス。

##  <a name="getcount"></a>  CMapStringToOb::GetCount

マップの要素の数が決まります。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>戻り値

このマップ内の要素の数。

### <a name="remarks"></a>Remarks

次の表はその他のメンバー関数に似ている`CMapStringToOb::GetCount`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Const; INT_PTR GetCount)**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Const; INT_PTR GetCount)**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Const; INT_PTR GetCount)**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Const; INT_PTR GetCount)**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**Const; INT_PTR GetCount)**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Const; INT_PTR GetCount)**|

### <a name="example"></a>例

参照してください[使われて](../../mfc/reference/coblist-class.md#coblist)の一覧については、`CAge`コレクションのすべての例で使用されるクラス。

[!code-cpp[NVC_MFCCollections#64](../../mfc/codesnippet/cpp/cmapstringtoob-class_2.cpp)]

##  <a name="gethashtablesize"></a>  CMapStringToOb::GetHashTableSize

現在のハッシュ テーブル内の要素数を決定します。

```
UINT GetHashTableSize() const;
```

### <a name="return-value"></a>戻り値

ハッシュ テーブル内の要素の数を返します。

### <a name="remarks"></a>Remarks

次の表はその他のメンバー関数に似ている`CMapStringToOb::GetHashTableSize`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Const; UINT GetHashTableSize)**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Const; UINT GetHashTableSize)**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Const; UINT GetHashTableSize)**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Const; UINT GetHashTableSize)**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**Const; UINT GetHashTableSize)**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Const; UINT GetHashTableSize)**|

##  <a name="getnextassoc"></a>  CMapStringToOb::GetNextAssoc

マップ要素を取得*rNextPosition*、し更新*rNextPosition*をマップに次の要素を参照してください。

```
void GetNextAssoc(
    POSITION& rNextPosition,
    CString& rKey,
    CObject*& rValue) const;
```

### <a name="parameters"></a>パラメーター

*rNextPosition*<br/>
によって以前返される位置の値への参照を指定します`GetNextAssoc`または`GetStartPosition`呼び出します。

*rKey*<br/>
取得される要素 (文字列) の返されたキーを指定します。

*rValue*<br/>
取得した要素の返された値を指定します (、`CObject`ポインター)。 このパラメーターの詳細については、「解説」を参照してください。

### <a name="remarks"></a>Remarks

この関数のマップのすべての要素を反復処理する最も便利です。 位置の順序は必ずしもキー値のシーケンスと同じに注意してください。

場合は、取得した最後の要素をマップでは、次の新しい値*rNextPosition* NULL に設定されます。

*右辺値*パラメーターに、オブジェクト型をキャストすることを確認する**CObject\*&**、これは、コンパイラによってどのような要求を次の例に示すように。

[!code-cpp[NVC_MFCCollections#65](../../mfc/codesnippet/cpp/cmapstringtoob-class_3.cpp)]

これには当てはまりません`GetNextAssoc`テンプレートに基づくマップの。

次の表はその他のメンバー関数に似ている`CMapStringToOb::GetNextAssoc`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, void\*&** *rKey* **, void\*&** *rValue* **) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, void\*&** *rKey* **, WORD&** *rValue* **) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, CString&** *rKey* **, void\*&** *rValue* **) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, CString&** *rKey* **, CString&** *rValue* **) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, WORD&** *rKey* **, CObject\*&** *rValue* **) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, WORD&** *rKey* **, void\*&** *rValue* **) const;**|

### <a name="example"></a>例

参照してください[使われて](../../mfc/reference/coblist-class.md#coblist)の一覧については、`CAge`コレクションのすべての例で使用されるクラス。

[!code-cpp[NVC_MFCCollections#66](../../mfc/codesnippet/cpp/cmapstringtoob-class_4.cpp)]

このプログラムからの結果は次のとおりです。

```Output
Lisa : a CAge at $4724 11
Marge : a CAge at $47A8 35
Homer : a CAge at $4766 36
Bart : a CAge at $45D4 13
```

##  <a name="getsize"></a>  CMapStringToOb::GetSize

マップ要素の数を返します。

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>戻り値

マップ内のアイテムの数。

### <a name="remarks"></a>Remarks

マップ内の要素の数を取得するには、このメソッドを呼び出します。

次の表はその他のメンバー関数に似ている`CMapStringToOb::GetSize`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Const; INT_PTR GetSize)**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Const; INT_PTR GetSize)**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Const; INT_PTR GetSize)**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Const; INT_PTR GetSize)**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**Const; INT_PTR GetSize)**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Const; INT_PTR GetSize)**|

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#67](../../mfc/codesnippet/cpp/cmapstringtoob-class_5.cpp)]

##  <a name="getstartposition"></a>  CMapStringToOb::GetStartPosition

渡すことができる位置の値を返すことによって、マップの反復処理を開始、`GetNextAssoc`呼び出します。

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>戻り値

マップを反復処理するための開始位置を示す位置値または、マップが空の場合は NULL です。

### <a name="remarks"></a>Remarks

反復シーケンスが予測可能です。そのため、マップの最初の要素""では、特別な意味はありません。

次の表はその他のメンバー関数に似ている`CMapStringToOb::GetStartPosition`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**POSITION GetStartPosition( ) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**POSITION GetStartPosition( ) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**POSITION GetStartPosition( ) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**POSITION GetStartPosition( ) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**POSITION GetStartPosition( ) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**POSITION GetStartPosition( ) const;**|

### <a name="example"></a>例

例をご覧ください[CMapStringToOb::GetNextAssoc](#getnextassoc)します。

##  <a name="hashkey"></a>  CMapStringToOb::HashKey

指定したキーのハッシュ値を計算します。

```
UINT HashKey(LPCTSTR key) const;
```

### <a name="parameters"></a>パラメーター

*key*<br/>
ハッシュ値が計算されるキー。

### <a name="return-value"></a>戻り値

キーのハッシュ値

### <a name="remarks"></a>Remarks

次の表はその他のメンバー関数に似ている`CMapStringToOb::HashKey`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT HashKey (void** <strong>\*</strong> `key` **) const です。**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT HashKey (void** <strong>\*</strong> `key` **) const です。**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT HashKey (LPCTSTR** `key` **) const です。**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT HashKey (LPCTSTR** `key` **) const です。**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT HashKey (WORD** `key` **) const です。**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT HashKey (WORD** `key` **) const です。**|

##  <a name="inithashtable"></a>  CMapStringToOb::InitHashTable

ハッシュ テーブルを初期化します。

```
void InitHashTable(
    UINT hashSize,
    BOOL bAllocNow = TRUE);
```

### <a name="parameters"></a>パラメーター

*hashSize*<br/>
ハッシュ テーブル内のエントリの数。

*bAllocNow*<br/>
TRUE の場合は、初期化時にハッシュ テーブルを割り当てますそれ以外の場合、テーブルが必要なときに割り当てられます。

### <a name="remarks"></a>Remarks

最適なパフォーマンスは、素数の数がハッシュ テーブルのサイズにあります。 競合を最小限に抑えるには、サイズは約 20%、最大の予想されるデータ セットよりも大きい。

次の表はその他のメンバー関数に似ている`CMapStringToOb::InitHashTable`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE );**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE );**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE );**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE );**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE );**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE );**|

##  <a name="isempty"></a>  CMapStringToOb::IsEmpty

マップが空かどうかを判断します。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>戻り値

このマップに要素が含まれていない場合は 0 以外それ以外の場合 0 を返します。

### <a name="example"></a>例

例をご覧ください[RemoveAll](#removeall)します。

### <a name="remarks"></a>Remarks

次の表はその他のメンバー関数に似ている**CMapStringToOb:。IsEmpty**します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Const; BOOL IsEmpty)**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Const; BOOL IsEmpty)**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Const; BOOL IsEmpty)**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Const; BOOL IsEmpty)**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**Const; BOOL IsEmpty)**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Const; BOOL IsEmpty)**|

##  <a name="lookup"></a>  CMapStringToOb::Lookup

返します、`CObject`ポインターに基づいて、`CString`値。

```
BOOL Lookup(
    LPCTSTR key,
    CObject*& rValue) const;
```

### <a name="parameters"></a>パラメーター

*key*<br/>
検索する要素を識別する文字列キーを指定します。

*rValue*<br/>
検索する要素から返される値を指定します。

### <a name="return-value"></a>戻り値

要素が見つかった場合は 0 以外それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

`Lookup` ハッシュ アルゴリズムを使用してすばやく正確に一致するキーを使用して、マップの要素を検索 (`CString`値)。

次の表はその他のメンバー関数に似ている`CMapStringToOb::LookUp`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL ルックアップ (void** <strong>\*</strong> `key` **, void\* &**  `rValue` **) const です。**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL ルックアップ (void** <strong>\*</strong> `key` **、WORD &** `rValue` **) const です。**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL ルックアップ (LPCTSTR** `key` **, void\* &**  `rValue` **) const です。**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL ルックアップ (LPCTSTR** `key` **、CString &** `rValue` **) const です。**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL ルックアップ (WORD** `key` **、CObject\* &**  `rValue` **) const です。**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL ルックアップ (WORD** `key` **, void\* &**  `rValue` **) const です。**|

### <a name="example"></a>例

参照してください[使われて](../../mfc/reference/coblist-class.md#coblist)の一覧については、`CAge`コレクションのすべての例で使用されるクラス。

[!code-cpp[NVC_MFCCollections#68](../../mfc/codesnippet/cpp/cmapstringtoob-class_6.cpp)]

##  <a name="lookupkey"></a>  CMapStringToOb::LookupKey

指定したキー値に関連付けられているキーへの参照を返します。

```
BOOL LookupKey(
    LPCTSTR key,
    LPCTSTR& rKey) const;
```

### <a name="parameters"></a>パラメーター

*key*<br/>
検索する要素を識別する文字列キーを指定します。

*rKey*<br/>
関連付けられているキーへの参照。

### <a name="return-value"></a>戻り値

キーが見つかった場合は 0 以外それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

関連付けられている要素は、マップから削除された後に使用されている場合、またはマップの破棄後に、キーへの参照を使用しても安全です。

次の表はその他のメンバー関数に似ている`CMapStringToOb:: LookupKey`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL LookupKey (LPCTSTR** `key` **、LPCTSTR &** `rKey` **) const です。**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL LookupKey (LPCTSTR** `key` **、LPCTSTR &** `rKey` **) const です。**|

##  <a name="operator_at"></a>  CMapStringToOb::operator [ ]

便利な代替、`SetAt`メンバー関数。

```
CObject*& operator[ ](lpctstr key);
```

### <a name="return-value"></a>戻り値

ポインターへの参照を`CObject`オブジェクトまたはマップが空の場合は NULL または*キー*が範囲外です。

### <a name="remarks"></a>Remarks

そのため、代入ステートメント (左辺値) の左側にのみ使用できます。 指定したキーにマップ要素が存在しない、新しい要素が作成されます。

ありません「右側」(右辺値) この演算子と同じキーは、マップには存在しない可能性があるためです。 使用して、`Lookup`メンバー関数は要素を取得します。

次の表はその他のメンバー関数に似ている`CMapStringToOb::operator []`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|<strong>void\*& 演算子\[] (void \*</strong>  `key`  **\);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**WORD & 演算子\[] (void** <strong>\*</strong> `key`  **\);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void\*& 演算子\[] (lpctstr** `key`  **\);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CString & 演算子\[] (lpctstr** `key`  **\);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CObject\*& 演算子\[] (word** `key`  **\);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void\*& 演算子\[] (word** `key`  **\);**|

### <a name="example"></a>例

参照してください[使われて](../../mfc/reference/coblist-class.md#coblist)の一覧については、`CAge`コレクションのすべての例で使用されるクラス。

[!code-cpp[NVC_MFCCollections#72](../../mfc/codesnippet/cpp/cmapstringtoob-class_7.cpp)]

このプログラムからの結果は次のとおりです。

```Output
Operator [] example: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $4A02 11
[Bart] = a CAge at $497E 13
```

##  <a name="removeall"></a>  CMapStringToOb::RemoveAll

このマップからすべての要素を削除し、破棄、`CString`オブジェクトのキーします。

```
void RemoveAll();
```

### <a name="remarks"></a>Remarks

`CObject`各キーによって参照されるオブジェクトは破棄されません。 `RemoveAll`ことは保証されませんが、参照されている場合、関数はメモリ リークを起こすことができます`CObject`オブジェクトが破棄されます。

マップが空ではまだの場合、関数が正しく動作します。

次の表はその他のメンバー関数に似ている`CMapStringToOb::RemoveAll`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void RemoveAll( );**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void RemoveAll( );**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void RemoveAll( );**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void RemoveAll( );**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void RemoveAll( );**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void RemoveAll( );**|

### <a name="example"></a>例

参照してください[使われて](../../mfc/reference/coblist-class.md#coblist)の一覧については、`CAge`コレクションのすべての例で使用されるクラス。

[!code-cpp[NVC_MFCCollections#69](../../mfc/codesnippet/cpp/cmapstringtoob-class_8.cpp)]

##  <a name="removekey"></a>  CMapStringToOb::RemoveKey

指定したキーに対応するマップ エントリを検索します。次に、キーが見つかった場合は、エントリを削除します。

```
BOOL RemoveKey(LPCTSTR key);
```

### <a name="parameters"></a>パラメーター

*key*<br/>
マップの検索に使用する文字列を指定します。

### <a name="return-value"></a>戻り値

エントリが見つかり、正常に削除された場合は 0 以外それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

メモリ リークを起こすこれには、場合、`CObject`オブジェクトは別の場所には削除されません。

次の表はその他のメンバー関数に似ている`CMapStringToOb::RemoveKey`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**ブール値には (void** <strong>\*</strong> `key` **)。**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**ブール値には (void** <strong>\*</strong> `key` **)。**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**ブール値には (LPCTSTR** `key` **)。**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**ブール値には (LPCTSTR** `key` **)。**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**ブール値には (WORD** `key` **)。**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**ブール値には (WORD** `key` **)。**|

### <a name="example"></a>例

参照してください[使われて](../../mfc/reference/coblist-class.md#coblist)の一覧については、`CAge`コレクションのすべての例で使用されるクラス。

[!code-cpp[NVC_MFCCollections#70](../../mfc/codesnippet/cpp/cmapstringtoob-class_9.cpp)]

このプログラムからの結果は次のとおりです。

```Output
RemoveKey example: A CMapStringToOb with 3 elements
[Marge] = a CAge at $49A0 35
[Homer] = a CAge at $495E 36
[Bart] = a CAge at $4634 13
```

##  <a name="setat"></a>  CMapStringToOb::SetAt

プライマリは、マップ内の要素を挿入することです。

```
void SetAt(
    LPCTSTR key,
    CObject* newValue);
```

### <a name="parameters"></a>パラメーター

*key*<br/>
新しい要素のキーである文字列を指定します。

*newValue*<br/>
指定します、`CObject`新しい要素の値を示すポインター。

### <a name="remarks"></a>Remarks

最初に、キーを検索します。 対応する値が変更されました。 その後、キーが見つかった場合それ以外の場合、新しいキーと値の要素が作成されます。

次の表はその他のメンバー関数に似ている`CMapStringToOb::SetAt`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**setat メソッドを無効にする (void** <strong>\*</strong> `key` **, void** <strong>\*</strong> `newValue` **)。**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**setat メソッドを無効にする (void** <strong>\*</strong> `key` **、WORD** `newValue` **)。**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**setat メソッドを void (LPCTSTR** `key` **, void** <strong>\*</strong> `newValue` **)。**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void SetAt( LPCTSTR** `key` **, LPCTSTR** `newValue` **);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**setat メソッドを void (WORD** `key` **、CObject** <strong>\*</strong> `newValue` **)。**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**setat メソッドを void (WORD** `key` **, void** <strong>\*</strong> `newValue` **)。**|

### <a name="example"></a>例

参照してください[使われて](../../mfc/reference/coblist-class.md#coblist)の一覧については、`CAge`コレクションのすべての例で使用されるクラス。

[!code-cpp[NVC_MFCCollections#71](../../mfc/codesnippet/cpp/cmapstringtoob-class_10.cpp)]

このプログラムからの結果は次のとおりです。

```Output
before Lisa's birthday: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $493C 11
[Bart] = a CAge at $4654 13
after Lisa's birthday: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $49C0 12
[Bart] = a CAge at $4654 13
```

## <a name="see-also"></a>関連項目

[CObject クラス](../../mfc/reference/cobject-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CMapPtrToPtr クラス](../../mfc/reference/cmapptrtoptr-class.md)<br/>
[CMapPtrToWord クラス](../../mfc/reference/cmapptrtoword-class.md)<br/>
[CMapStringToPtr クラス](../../mfc/reference/cmapstringtoptr-class.md)<br/>
[CMapStringToString クラス](../../mfc/reference/cmapstringtostring-class.md)<br/>
[CMapWordToOb クラス](../../mfc/reference/cmapwordtoob-class.md)<br/>
[CMapWordToPtr クラス](../../mfc/reference/cmapwordtoptr-class.md)
