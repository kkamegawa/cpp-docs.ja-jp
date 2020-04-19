---
title: CMap クラス
ms.date: 11/04/2016
f1_keywords:
- CMap
- AFXTEMPL/CMap
- AFXTEMPL/CMap::CPair
- AFXTEMPL/CMap::CMap
- AFXTEMPL/CMap::GetCount
- AFXTEMPL/CMap::GetHashTableSize
- AFXTEMPL/CMap::GetNextAssoc
- AFXTEMPL/CMap::GetSize
- AFXTEMPL/CMap::GetStartPosition
- AFXTEMPL/CMap::InitHashTable
- AFXTEMPL/CMap::IsEmpty
- AFXTEMPL/CMap::Lookup
- AFXTEMPL/CMap::PGetFirstAssoc
- AFXTEMPL/CMap::PGetNextAssoc
- AFXTEMPL/CMap::PLookup
- AFXTEMPL/CMap::RemoveAll
- AFXTEMPL/CMap::RemoveKey
- AFXTEMPL/CMap::SetAt
helpviewer_keywords:
- CMap [MFC], CPair
- CMap [MFC], CMap
- CMap [MFC], GetCount
- CMap [MFC], GetHashTableSize
- CMap [MFC], GetNextAssoc
- CMap [MFC], GetSize
- CMap [MFC], GetStartPosition
- CMap [MFC], InitHashTable
- CMap [MFC], IsEmpty
- CMap [MFC], Lookup
- CMap [MFC], PGetFirstAssoc
- CMap [MFC], PGetNextAssoc
- CMap [MFC], PLookup
- CMap [MFC], RemoveAll
- CMap [MFC], RemoveKey
- CMap [MFC], SetAt
ms.assetid: 640a45ab-0993-4def-97ec-42cc78eb10b9
ms.openlocfilehash: 58f9efb19988be8487ec87ce0c63d90ee1a97911
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62296580"
---
# <a name="cmap-class"></a>CMap クラス

一意なキーを値に割り当てる辞書コレクション クラスです。

## <a name="syntax"></a>構文

```
template<class KEY, class ARG_KEY, class VALUE, class ARG_VALUE>class CMap : public CObject
```

#### <a name="parameters"></a>パラメーター

*KEY*<br/>
マップのキーとして使用されるオブジェクトのクラスです。

*ARG_KEY*<br/>
データ型*キー*引数。 通常は、への参照を*キー*します。

*値*<br/>
マップに格納されるオブジェクトのクラスです。

*ARG_VALUE*<br/>
データ型*値*引数。 通常は、への参照を*値*します。

## <a name="members"></a>メンバー

### <a name="public-structures"></a>パブリック構造体

|名前|説明|
|----------|-----------------|
|[CMap::CPair](#cpair)|キーの値と関連付けられているオブジェクトの値を含む入れ子になった構造体。|

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMap::CMap](#cmap)|キーを値にマップするコレクションを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMap::GetCount](#getcount)|このマップ要素の数を返します。|
|[CMap::GetHashTableSize](#gethashtablesize)|ハッシュ テーブル内の要素の数を返します。|
|[CMap::GetNextAssoc](#getnextassoc)|反復処理するためには、次の要素を取得します。|
|[CMap::GetSize](#getsize)|このマップ要素の数を返します。|
|[CMap::GetStartPosition](#getstartposition)|最初の要素の位置を返します。|
|[CMap::InitHashTable](#inithashtable)|ハッシュ テーブルを初期化し、そのサイズを指定します。|
|[CMap::IsEmpty](#isempty)|マップが空の状態 (要素がない場合) をテストします。|
|[CMap::Lookup](#lookup)|指定されたキーにマップされている値を検索します。|
|[CMap::PGetFirstAssoc](#pgetfirstassoc)|最初の要素へのポインターを返します。|
|[CMap::PGetNextAssoc](#pgetnextassoc)|次の要素に反復処理するためのポインターを取得します。|
|[CMap::PLookup](#plookup)|値が指定した値と一致するキーへのポインターを返します。|
|[CMap::RemoveAll](#removeall)|このマップからすべての要素を削除します。|
|[CMap::RemoveKey](#removekey)|キーで指定された要素を削除します。|
|[CMap::SetAt](#setat)|マップに要素を挿入します。一致するキーが見つかった場合は、既存の要素を置き換えます。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CMap::operator \[ \]](#operator_at)|マップに要素を挿入、演算子の代替の`SetAt`します。|

## <a name="remarks"></a>Remarks

マップにキー/値ペア (要素) を挿入すると効率的に取得またはへのアクセス キーを使用してペアを削除します。 また、マップ内のすべての要素を反復処理することができます。

位置の型の変数は、エントリに代替のアクセスに使用されます。 エントリを「記憶」して、マップを反復処理する位置を使用することができます。 このイテレーションがキーの値にシーケンシャルであると思われる場合があります。そうじゃないです。 取得する要素の順序は不確定です。

ほとんどの用途のグローバルなヘルパー関数をこのクラスの呼び出しの一部のメンバー関数をカスタマイズする必要があります、`CMap`クラス。 参照してください[コレクション クラスのヘルパー](../../mfc/reference/collection-class-helpers.md)のマクロとグローバルのセクションでは、 **MFC リファレンス**します。

`CMap` オーバーライド[cobject::serialize](../../mfc/reference/cobject-class.md#serialize)シリアル化とその要素のダンプをサポートするためにします。 アーカイブを使用して、マップが格納されている場合`Serialize`、各マップ要素が順番にシリアル化します。 既定の実装、`SerializeElements`ヘルパー関数はビットごとの書き込み。 派生したポインター コレクション項目のシリアル化に関する情報の`CObject`またはその他のユーザー定義型を参照してください[方法。タイプ セーフなコレクションの作成](../../mfc/how-to-make-a-type-safe-collection.md)です。

(キーと値) のマップ内の個々 の要素の診断ダンプが必要な場合は、1 以上にダンプ コンテキストの深さを設定する必要があります。

ときに、`CMap`オブジェクトを削除すると、またはその要素が削除されると、キーと値の両方が削除されます。

マップ クラスの派生は、リストの派生に似ています。 記事をご覧ください[コレクション](../../mfc/collections.md)特殊なリスト クラスの派生の例についてはします。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CMap`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxtempl.h

##  <a name="cmap"></a>  CMap::CMap

空のマップを構築します。

```
CMap(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>パラメーター

*nBlockSize*<br/>
マップを拡張するためのメモリ割り当ての粒度を指定します。

### <a name="remarks"></a>Remarks

単位でメモリが割り当てられているマップが拡大に合わせて*nBlockSize*エントリ。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#56](../../mfc/codesnippet/cpp/cmap-class_1.cpp)]

##  <a name="cpair"></a>  CMap::CPair

キー値と関連付けられているオブジェクトの値が含まれています。

### <a name="remarks"></a>Remarks

これは、クラス内で入れ子になった構造[CMap](../../mfc/reference/cmap-class.md)します。

構造体が 2 つのフィールドで構成されます。

- `key` キーの種類の実際の値。

- `value` 関連付けられたオブジェクトの値。

戻り値を格納するために[例](#plookup)、 [CMap::PGetFirstAssoc](#pgetfirstassoc)、および[CMap::PGetNextAssoc](#pgetnextassoc)します。

### <a name="example"></a>例

使用状況の例は、の例を参照してください。[例](#plookup)します。

##  <a name="getcount"></a>  CMap::GetCount

マップ内の要素の数を取得します。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>戻り値

要素の数。

### <a name="example"></a>例

例をご覧ください[CMap::Lookup](#lookup)します。

##  <a name="gethashtablesize"></a>  CMap::GetHashTableSize

マップのハッシュ テーブル内の要素の数を決定します。

```
UINT GetHashTableSize() const;
```

### <a name="return-value"></a>戻り値

ハッシュ テーブル内の要素の数。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#57](../../mfc/codesnippet/cpp/cmap-class_2.cpp)]

##  <a name="getnextassoc"></a>  CMap::GetNextAssoc

マップ要素を取得`rNextPosition`、し更新`rNextPosition`にマップの次の要素を参照してください。

```
void GetNextAssoc(
    POSITION& rNextPosition,
    KEY& rKey,
    VALUE& rValue) const;
```

### <a name="parameters"></a>パラメーター

*rNextPosition*<br/>
によって以前返される位置の値への参照を指定します`GetNextAssoc`または`GetStartPosition`呼び出します。

*KEY*<br/>
マップのキーの種類を指定するテンプレート パラメーター。

*rKey*<br/>
取得した要素の返されたキーを指定します。

*値*<br/>
マップの値の型を指定するテンプレート パラメーター。

*rValue*<br/>
取得した要素の戻り値を指定します。

### <a name="remarks"></a>Remarks

この関数のマップのすべての要素を反復処理する最も便利です。 位置の順序は必ずしもキー値のシーケンスと同じに注意してください。

場合は、取得した最後の要素をマップでは、次の新しい値*rNextPosition* NULL に設定されます。

### <a name="example"></a>例

例をご覧ください[CMap::SetAt](#setat)します。

##  <a name="getsize"></a>  CMap::GetSize

マップ要素の数を返します。

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>戻り値

マップ内のアイテムの数。

### <a name="remarks"></a>Remarks

マップ内の要素の数を取得するには、このメソッドを呼び出します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]

##  <a name="getstartposition"></a>  CMap::GetStartPosition

渡すことができる位置の値を返すことによって、マップの反復処理を開始、`GetNextAssoc`呼び出します。

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>戻り値

マップを反復処理するための開始位置を示す位置値または、マップが空の場合は NULL です。

### <a name="remarks"></a>Remarks

反復シーケンスが予測可能です。そのため、マップの最初の要素""では、特別な意味はありません。

### <a name="example"></a>例

例をご覧ください[CMap::SetAt](#setat)します。

##  <a name="inithashtable"></a>  CMap::InitHashTable

ハッシュ テーブルを初期化します。

```
void InitHashTable(UINT hashSize, BOOL  bAllocNow = TRUE);
```

### <a name="parameters"></a>パラメーター

*hashSize*<br/>
ハッシュ テーブル内のエントリの数。

*bAllocNow*<br/>
TRUE の場合は、初期化時にハッシュ テーブルを割り当てますそれ以外の場合、テーブルが必要なときに割り当てられます。

### <a name="remarks"></a>Remarks

最適なパフォーマンスは、素数の数がハッシュ テーブルのサイズにあります。 競合を最小限に抑えるには、サイズは約 20%、最大の予想されるデータ セットよりも大きい。

### <a name="example"></a>例

例をご覧ください[CMap::Lookup](#lookup)します。

##  <a name="isempty"></a>  CMap::IsEmpty

マップが空かどうかを判断します。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>戻り値

このマップに要素が含まれていない場合は 0 以外それ以外の場合 0 を返します。

### <a name="example"></a>例

例をご覧ください[CMap::RemoveAll](#removeall)します。

##  <a name="lookup"></a>  CMap::Lookup

指定されたキーにマップされている値を検索します。

```
BOOL Lookup(ARG_KEY key, VALUE& rValue) const;
```

### <a name="parameters"></a>パラメーター

*ARG_KEY*<br/>
テンプレートのパラメーターの型を指定する、*キー*値。

*key*<br/>
検索する要素を識別するキーを指定します。

*値*<br/>
検索する値の型を指定します。

*rValue*<br/>
検索する値を受け取ります。

### <a name="return-value"></a>戻り値

要素が見つかった場合は 0 以外それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

`Lookup` ハッシュ アルゴリズムを使用して、マップ要素に指定したキーに一致するキーをすばやく検索します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]

##  <a name="operator_at"></a>  CMap::operator [ ]

便利な代替、`SetAt`メンバー関数。

```
VALUE& operator[](arg_key key);
```

### <a name="parameters"></a>パラメーター

*値*<br/>
マップ値の型を指定するテンプレート パラメーター。

*ARG_KEY*<br/>
キーの値の型を指定するテンプレート パラメーター。

*key*<br/>
マップの値を取得するために使用するキー。

### <a name="remarks"></a>Remarks

そのため、代入ステートメント (左辺値) の左側にのみ使用できます。 指定したキーにマップ要素が存在しない、新しい要素が作成されます。

ありません「右側」(右辺値) この演算子と同じキーは、マップには存在しない可能性があるためです。 使用して、`Lookup`メンバー関数は要素を取得します。

### <a name="example"></a>例

例をご覧ください[CMap::Lookup](#lookup)します。

##  <a name="pgetfirstassoc"></a>  CMap::PGetFirstAssoc

マップ オブジェクトの最初のエントリを返します。

```
const CPair* PGetFirstAssoc() const;
CPair* PGetFirstAssoc();
```

### <a name="return-value"></a>戻り値

マップ内の最初のエントリへのポインター参照してください[CMap::CPair](#cpair)します。 マップにエントリが含まれていない場合、値は NULL です。

### <a name="remarks"></a>Remarks

この関数では、マップ オブジェクト内の最初の要素のポインターを返します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#59](../../mfc/codesnippet/cpp/cmap-class_4.cpp)]

##  <a name="pgetnextassoc"></a>  CMap::PGetNextAssoc

によって示されるマップ要素を取得*pAssocRec*します。

```
const CPair *PGetNextAssoc(const CPair* pAssocRet) const;

CPair *PGetNextAssoc(const CPair* pAssocRet);
```

### <a name="parameters"></a>パラメーター

*pAssocRet*<br/>
直前のマップ エントリが指す[PGetNextAssoc](#pgetnextassoc)または[CMap::PGetFirstAssoc](#pgetfirstassoc)呼び出します。

### <a name="return-value"></a>戻り値

マップ内の次のエントリへのポインター参照してください[CMap::CPair](#cpair)します。 要素がマップ内の最後の場合は、値は NULL です。

### <a name="remarks"></a>Remarks

マップ内のすべての要素を反復処理するには、このメソッドを呼び出します。 呼び出しの最初の要素を取得`PGetFirstAssoc`を連続する呼び出すと、マップを反復処理し、`PGetNextAssoc`します。

### <a name="example"></a>例

例をご覧ください[CMap::PGetFirstAssoc](#pgetfirstassoc)します。

##  <a name="plookup"></a>  CMap::PLookup

指定されたキーにマップされている値を検索します。

```
const CPair* PLookup(ARG_KEY key) const;
CPair* PLookup(ARG_KEY key);
```

### <a name="parameters"></a>パラメーター

*key*<br/>
検索する要素をキーします。

### <a name="return-value"></a>戻り値

キーの構造体へのポインター参照してください[CMap::CPair](#cpair)します。 一致が見つからない場合`CMap::PLookup`は NULL を返します。

### <a name="remarks"></a>Remarks

指定したキーと一致するキーを持つマップ要素を検索するには、このメソッドを呼び出します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#60](../../mfc/codesnippet/cpp/cmap-class_5.cpp)]

##  <a name="removeall"></a>  CMap::RemoveAll

グローバルなヘルパー関数を呼び出すことによってこのマップからすべての値を削除します。`DestructElements`します。

```
void RemoveAll();
```

### <a name="remarks"></a>Remarks

マップが空ではまだの場合、関数が正しく動作します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#61](../../mfc/codesnippet/cpp/cmap-class_6.cpp)]

##  <a name="removekey"></a>  CMap::RemoveKey

指定したキーに対応するマップ エントリを検索します。次に、キーが見つかった場合は、エントリを削除します。

```
BOOL RemoveKey(ARG_KEY key);
```

### <a name="parameters"></a>パラメーター

*ARG_KEY*<br/>
キーの型を指定するテンプレート パラメーター。

*key*<br/>
削除する要素をキーします。

### <a name="return-value"></a>戻り値

エントリが見つかり、正常に削除された場合は 0 以外それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

`DestructElements`ヘルパー関数を使用して、エントリを削除します。

### <a name="example"></a>例

例をご覧ください[CMap::SetAt](#setat)します。

##  <a name="setat"></a>  CMap::SetAt

プライマリは、マップ内の要素を挿入することです。

```
void SetAt(ARG_KEY key, ARG_VALUE newValue);
```

### <a name="parameters"></a>パラメーター

*ARG_KEY*<br/>
テンプレートのパラメーターの型を指定する、*キー*パラメーター。

*key*<br/>
新しい要素のキーを指定します。

*ARG_VALUE*<br/>
テンプレートのパラメーターの型を指定する、 *newValue*パラメーター。

*newValue*<br/>
新しい要素の値を指定します。

### <a name="remarks"></a>Remarks

最初に、キーを検索します。 対応する値が変更されました。 その後、キーが見つかった場合それ以外の場合、新しいキー/値ペアが作成されます。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#62](../../mfc/codesnippet/cpp/cmap-class_7.cpp)]

## <a name="see-also"></a>関連項目

[MFC サンプルの収集](../../overview/visual-cpp-samples.md)<br/>
[CObject クラス](../../mfc/reference/cobject-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)
