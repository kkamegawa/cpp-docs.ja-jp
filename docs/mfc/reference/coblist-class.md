---
title: CObList クラス
ms.date: 11/04/2016
f1_keywords:
- CObList
- AFXCOLL/CObList
- AFXCOLL/CObList::CObList
- AFXCOLL/CObList::AddHead
- AFXCOLL/CObList::AddTail
- AFXCOLL/CObList::Find
- AFXCOLL/CObList::FindIndex
- AFXCOLL/CObList::GetAt
- AFXCOLL/CObList::GetCount
- AFXCOLL/CObList::GetHead
- AFXCOLL/CObList::GetHeadPosition
- AFXCOLL/CObList::GetNext
- AFXCOLL/CObList::GetPrev
- AFXCOLL/CObList::GetSize
- AFXCOLL/CObList::GetTail
- AFXCOLL/CObList::GetTailPosition
- AFXCOLL/CObList::InsertAfter
- AFXCOLL/CObList::InsertBefore
- AFXCOLL/CObList::IsEmpty
- AFXCOLL/CObList::RemoveAll
- AFXCOLL/CObList::RemoveAt
- AFXCOLL/CObList::RemoveHead
- AFXCOLL/CObList::RemoveTail
- AFXCOLL/CObList::SetAt
helpviewer_keywords:
- CObList [MFC], CObList
- CObList [MFC], AddHead
- CObList [MFC], AddTail
- CObList [MFC], Find
- CObList [MFC], FindIndex
- CObList [MFC], GetAt
- CObList [MFC], GetCount
- CObList [MFC], GetHead
- CObList [MFC], GetHeadPosition
- CObList [MFC], GetNext
- CObList [MFC], GetPrev
- CObList [MFC], GetSize
- CObList [MFC], GetTail
- CObList [MFC], GetTailPosition
- CObList [MFC], InsertAfter
- CObList [MFC], InsertBefore
- CObList [MFC], IsEmpty
- CObList [MFC], RemoveAll
- CObList [MFC], RemoveAt
- CObList [MFC], RemoveHead
- CObList [MFC], RemoveTail
- CObList [MFC], SetAt
ms.assetid: 80699c93-33d8-4f8b-b8cf-7b58aeab64ca
ms.openlocfilehash: 2fc3a3643c675394de555f1411030e278bcee775
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388242"
---
# <a name="coblist-class"></a>CObList クラス

一意の順序付きリスト fSupports`CObject`値順番に、またはポインターによってアクセス可能なポインター。

## <a name="syntax"></a>構文

```
class CObList : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CObList::CObList](#coblist)|空のリストを構築します`CObject`ポインター。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CObList::AddHead](#addhead)|(新しい head は、) リストの先頭に要素 (または別のリストのすべての要素) を追加します。|
|[CObList::AddTail](#addtail)|(新しい末尾になります)、リストの末尾に要素 (または別のリストのすべての要素) を追加します。|
|[CObList::Find](#find)|ポインター値で指定された要素の位置を取得します。|
|[CObList::FindIndex](#findindex)|0 から始まるインデックスで指定した要素の位置を取得します。|
|[CObList::GetAt](#getat)|指定された位置に要素を取得します。|
|[CObList::GetCount](#getcount)|この一覧には、要素の数を返します。|
|[CObList::GetHead](#gethead)|(空にすることはできません) の一覧の先頭の要素を返します。|
|[CObList::GetHeadPosition](#getheadposition)|リストの先頭の要素の位置を返します。|
|[CObList::GetNext](#getnext)|反復処理するためには、次の要素を取得します。|
|[CObList::GetPrev](#getprev)|反復処理するためには、直前の要素を取得します。|
|[CObList::GetSize](#getsize)|この一覧には、要素の数を返します。|
|[CObList::GetTail](#gettail)|(空にすることはできません)、リストの末尾の要素を返します。|
|[CObList::GetTailPosition](#gettailposition)|リストの末尾の要素の位置を返します。|
|[CObList::InsertAfter](#insertafter)|指定した位置より後に新しい要素を挿入します。|
|[CObList::InsertBefore](#insertbefore)|指定した位置の前に新しい要素を挿入します。|
|[CObList::IsEmpty](#isempty)|空のリストの条件 (要素がない) をテストします。|
|[CObList::RemoveAll](#removeall)|この一覧からすべての要素を削除します。|
|[CObList::RemoveAt](#removeat)|位置によって指定された、このリストから要素を削除します。|
|[CObList::RemoveHead](#removehead)|リストの先頭から要素を削除します。|
|[CObList::RemoveTail](#removetail)|リストの末尾から要素を削除します。|
|[CObList::SetAt](#setat)|指定された位置に要素を設定します。|

## <a name="remarks"></a>Remarks

`CObList` リストは、二重リンク リストのように動作します。

位置の型の変数は、リストのキーです。 一覧を順番に走査する反復子、および位置を保持するブックマークとして位置変数を使用することができます。 位置が、インデックスと同じです。 ただしです。

要素の挿入はリストの先頭、末尾、および既知の位置に非常に高速です。 順次検索は、値またはインデックスで要素を検索する必要があります。 この検索は、リストが長い場合は低速にすることはできます。

`CObList` シリアル化とその要素のダンプをサポートするために IMPLEMENT_SERIAL マクロが組み込まれています。 リストの場合`CObject`アーカイブ、オーバー ロードされた挿入演算子を伴うまたはのいずれかにポインターが格納されている、`Serialize`メンバー関数は、各`CObject`要素が順番にシリアル化します。

個別にダンプする必要がある場合`CObject`リスト内の要素、1 以上に、ダンプ コンテキストの深さを設定する必要があります。

ときに、`CObList`オブジェクトを削除すると、またはときにその要素は削除のみ、`CObject`ポインターを削除すると、参照するオブジェクトではありません。

独自のクラスを派生する`CObList`します。 派生したオブジェクトにポインターを保持するために設計されています。 新しいリスト クラス`CObject`、新しいデータ メンバーおよびメンバーの新しい関数を追加します。 いずれかの挿入できるので、結果のリストは厳密にタイプ セーフでに注意してください`CObject`ポインター。

> [!NOTE]
>  使用する必要があります、 [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)マクロで一覧をシリアル化する場合は、派生クラスの実装。

使用しての詳細については`CObList`、記事をご覧ください[コレクション](../../mfc/collections.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CObList`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxcoll.h

##  <a name="addhead"></a>  CObList::AddHead

このリストの先頭に新しい要素または要素のリストを追加します。

```
POSITION AddHead(CObject* newElement);
void AddHead(CObList* pNewList);
```

### <a name="parameters"></a>パラメーター

*newElement*<br/>
`CObject`このリストに追加するへのポインター。

*pNewList*<br/>
別のポインター`CObList`一覧。 内の要素*pNewList*この一覧に追加されます。

### <a name="return-value"></a>戻り値

最初のバージョンでは、新しく挿入される要素の位置を表す値を返します。

次の表はその他のメンバー関数に似ている`CObList::AddHead`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION AddHead( void** <strong>\*</strong> `newElement` **);**<br /><br /> **void AddHead( CPtrList** <strong>\*</strong> `pNewList` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION AddHead (const CString &** `newElement` **)。**<br /><br /> **POSITION AddHead(LPCTSTR** `newElement` **);**<br /><br /> **void AddHead(CStringList** <strong>\*</strong> `pNewList` **);**|

### <a name="remarks"></a>Remarks

一覧は、操作の前に空にすることができます。

### <a name="example"></a>例

  `CAge`クラスのリストについては、[CObList::CObList](#coblist) を参照してください。

[!code-cpp[NVC_MFCCollections#89](../../mfc/codesnippet/cpp/coblist-class_1.cpp)]

このプログラムからの結果は次のとおりです。

```Output
AddHead example: A CObList with 2 elements
a CAge at $44A8 40
a CAge at $442A 21
```

##  <a name="addtail"></a>  CObList::AddTail

このリストの末尾に新しい要素または要素のリストを追加します。

```
POSITION AddTail(CObject* newElement);
void AddTail(CObList* pNewList);
```

### <a name="parameters"></a>パラメーター

*newElement*<br/>
`CObject`このリストに追加するへのポインター。

*pNewList*<br/>
別のポインター`CObList`一覧。 内の要素*pNewList*この一覧に追加されます。

### <a name="return-value"></a>戻り値

最初のバージョンでは、新しく挿入される要素の位置を表す値を返します。

### <a name="remarks"></a>Remarks

一覧は、操作の前に空にすることができます。

次の表はその他のメンバー関数に似ている`CObList::AddTail`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION AddTail( void** <strong>\*</strong> `newElement` **);**<br /><br /> **void AddTail( CPtrList** <strong>\*</strong> `pNewList` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION AddTail( const CString&** `newElement` **);**<br /><br /> **POSITION AddTail( LPCTSTR** `newElement` **);**<br /><br /> **void AddTail( CStringList** <strong>\*</strong> `pNewList` **);**|

### <a name="example"></a>例

  `CAge`クラスのリストについては、[CObList::CObList](#coblist) を参照してください。

[!code-cpp[NVC_MFCCollections#90](../../mfc/codesnippet/cpp/coblist-class_2.cpp)]

このプログラムからの結果は次のとおりです。

```Output
AddTail example: A CObList with 2 elements
a CAge at $444A 21
a CAge at $4526 40
```

##  <a name="coblist"></a>  CObList::CObList

空の構築`CObject`ポインターのリスト。

```
CObList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>パラメーター

*nBlockSize*<br/>
リストを拡張するためのメモリの割り当て粒度。

### <a name="remarks"></a>Remarks

単位でメモリが割り当てられている、一覧につれ、 *nBlockSize*エントリ。 メモリの割り当てに失敗した場合、`CMemoryException`がスローされます。

次の表はその他のメンバー関数に似ている`CObList::CObList`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**CPtrList( INT_PTR** `nBlockSize` **= 10 );**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CStringList( INT_PTR** `nBlockSize` **= 10 );**|

### <a name="example"></a>例

  一覧を次に示します、 `CObject`-クラスを派生`CAge`コレクションのすべての例で使用します。

[!code-cpp[NVC_MFCCollections#91](../../mfc/codesnippet/cpp/coblist-class_3.h)]

次の例に示します`CObList`コンス トラクターの使用状況。

[!code-cpp[NVC_MFCCollections#92](../../mfc/codesnippet/cpp/coblist-class_4.cpp)]

##  <a name="find"></a>  CObList::Find

最初に検索するには、順番に一覧を検索`CObject`ポインター、指定した照合`CObject`ポインター。

```
POSITION Find(
    CObject* searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>パラメーター

*searchValue*<br/>
この一覧で検索するオブジェクトのポインター。

*startAfter*<br/>
検索の開始位置。

### <a name="return-value"></a>戻り値

イテレーションまたはオブジェクト ポインターの取得に使用できる位置の値オブジェクトが見つからない場合は NULL です。

### <a name="remarks"></a>Remarks

ポインター値を比較することに注意してください、オブジェクトの内容ではありません。

次の表はその他のメンバー関数に似ている`CObList::Find`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION Find (void** <strong>\*</strong> `searchValue` , **POSITION** `startAfter` **= NULL) const**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION Find( LPCTSTR** `searchValue` **, POSITION** `startAfter` **= NULL ) const;**|

### <a name="example"></a>例

`CAge`クラスのリストについては、[CObList::CObList](#coblist) を参照してください。

[!code-cpp[NVC_MFCCollections#93](../../mfc/codesnippet/cpp/coblist-class_5.cpp)]

##  <a name="findindex"></a>  CObList::FindIndex

値を使用して*nIndex*リストのインデックス。

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
検索するリストの要素の 0 から始まるインデックス。

### <a name="return-value"></a>戻り値

イテレーションまたはオブジェクト ポインターの取得に使用できる位置の値場合は NULL *nIndex*が大きすぎます。 (場合に、フレームワークがアサーションを生成*nIndex*が負の値)。

### <a name="remarks"></a>Remarks

上の停止、リストの先頭から順次スキャンを開始、 *n*番目の要素。

次の表はその他のメンバー関数に似ている`CObList::FindIndex`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION FindIndex (INT_PTR** `nIndex` **) const**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION FindIndex (INT_PTR** `nIndex` **) const**|

### <a name="example"></a>例

`CAge`クラスのリストについては、[CObList::CObList](#coblist) を参照してください。

[!code-cpp[NVC_MFCCollections#94](../../mfc/codesnippet/cpp/coblist-class_6.cpp)]

##  <a name="getat"></a>  CObList::GetAt

位置の型の変数は、リストのキーです。

```
CObject*& GetAt(POSITION position);
const CObject*& GetAt(POSITION position) const;
```

### <a name="parameters"></a>パラメーター

*position*<br/>
以前、によって返される位置値`GetHeadPosition`または`Find`メンバー関数の呼び出し。

### <a name="return-value"></a>戻り値

戻り値の説明を参照して[gethead 関数](#gethead)します。

### <a name="remarks"></a>Remarks

、インデックスと同じではありませんし、操作できません。 位置の値を自分でします。 `GetAt` 取得、`CObject`指定した位置に関連付けられたポインター。

位置の値がリスト内の有効な位置を表すことを確認する必要があります。 有効な場合は、Microsoft Foundation Class ライブラリのデバッグ バージョンはアサートします。

次の表はその他のメンバー関数に似ている`CObList::GetAt`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const void\*& GetAt( POSITION** *position* **) const;**<br /><br /> **void\*& GetAt( POSITION** *position* **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString& GetAt( POSITION** *position* **) const;**<br /><br /> **CString& GetAt( POSITION** *position* **);**|

### <a name="example"></a>例

  例をご覧ください[FindIndex](#findindex)します。

##  <a name="getcount"></a>  CObList::GetCount

この一覧には、要素の数を取得します。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>戻り値

要素の数を格納する整数値。

次の表はその他のメンバー関数に似ている`CObList::GetCount`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetCount( ) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetCount( ) const;**|

### <a name="example"></a>例

`CAge`クラスのリストについては、[CObList::CObList](#coblist) を参照してください。

[!code-cpp[NVC_MFCCollections#95](../../mfc/codesnippet/cpp/coblist-class_7.cpp)]

##  <a name="gethead"></a>  CObList::GetHead

取得、`CObject`この一覧の先頭の要素を表すポインターです。

```
CObject*& GetHead();
const CObject*& GetHead() const;
```

### <a name="return-value"></a>戻り値

一覧へのポインターを介してアクセスする場合、 `const CObList`、し`GetHead`を返します、`CObject`ポインター。 これにより、関数は、代入ステートメントの右側にあるでのみ使用し、したがって変更から一覧を保護します。

リストが直接、または、ポインターを介してアクセスされる場合、 `CObList`、し`GetHead`への参照を返します、`CObject`ポインター。 これは、関数は、代入ステートメントの右辺でも左辺でも使用して、できるので、リスト エントリを変更できます。

### <a name="remarks"></a>Remarks

リストが呼び出す前に空でないことを確認する必要があります`GetHead`します。 リストが空の場合、Microsoft Foundation Class ライブラリのデバッグ バージョンはアサートします。 使用[IsEmpty](#isempty)リストに要素が含まれていることを確認します。

次の表はその他のメンバー関数に似ている`CObList::GetHead`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const void\*& GetHead( ) const; void\*& GetHead( );**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString& GetHead( ) const; CString& GetHead( );**|

### <a name="example"></a>例

`CAge`クラスのリストについては、[CObList::CObList](#coblist) を参照してください。

使用例を次に示します`GetHead`代入ステートメントの左側にあります。

[!code-cpp[NVC_MFCCollections#96](../../mfc/codesnippet/cpp/coblist-class_8.cpp)]

##  <a name="getheadposition"></a>  CObList::GetHeadPosition

この一覧の先頭の要素の位置を取得します。

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>戻り値

イテレーションまたはオブジェクト ポインターの取得に使用できる位置の値リストが空の場合は NULL です。

次の表はその他のメンバー関数に似ている`CObList::GetHeadPosition`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION GetHeadPosition( ) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION GetHeadPosition( ) const;**|

### <a name="example"></a>例

`CAge`クラスのリストについては、[CObList::CObList](#coblist) を参照してください。

[!code-cpp[NVC_MFCCollections#97](../../mfc/codesnippet/cpp/coblist-class_9.cpp)]

##  <a name="getnext"></a>  CObList::GetNext

識別される要素を取得*rPosition*を設定し、 *rPosition*を`POSITION`一覧の次のエントリの値。

```
CObject*& GetNext(POSITION& rPosition);
const CObject* GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>パラメーター

*rPosition*<br/>
によって以前返される位置の値への参照を`GetNext`、 `GetHeadPosition`、またはその他のメンバー関数の呼び出し。

### <a name="return-value"></a>戻り値

戻り値の説明を参照して[gethead 関数](#gethead)します。

### <a name="remarks"></a>Remarks

使用することができます`GetNext`への呼び出しを初期位置を確立する場合は、順方向の反復ループで`GetHeadPosition`または`Find`します。

位置の値がリスト内の有効な位置を表すことを確認する必要があります。 有効な場合は、Microsoft Foundation Class ライブラリのデバッグ バージョンはアサートします。

場合は、取得された最後の要素を一覧での新しい値*rPosition* NULL に設定されます。

反復処理中に要素を削除することになります。 例をご覧ください[RemoveAt](#removeat)します。

> [!NOTE]
>  返すこのメソッドの const バージョンが変更された時点で、MFC 8.0`const CObject*`の代わりに`const CObject*&`します。  C++ 標準に準拠コンパイラに変更されました。

次の表はその他のメンバー関数に似ている`CObList::GetNext`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const void* GetNext( POSITION&` `rPosition` `) const;`|
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetNext( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>例

  `CAge`クラスのリストについては、[CObList::CObList](#coblist) を参照してください。

[!code-cpp[NVC_MFCCollections#98](../../mfc/codesnippet/cpp/coblist-class_10.cpp)]

このプログラムからの結果は次のとおりです。

```Output
a CAge at $479C 40
a CAge at $46C0 21
```

##  <a name="getprev"></a>  CObList::GetPrev

識別される要素を取得*rPosition*、設定し、 *rPosition*一覧の前のエントリの位置の値にします。

```
CObject*& GetPrev(POSITION& rPosition);
const CObject* GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>パラメーター

*rPosition*<br/>
によって以前返される位置の値への参照を`GetPrev`またはその他のメンバー関数の呼び出し。

### <a name="return-value"></a>戻り値

戻り値の説明を参照して[gethead 関数](#gethead)します。

### <a name="remarks"></a>Remarks

使用することができます`GetPrev`への呼び出しを初期位置を確立する場合に、逆順イテレーション ループで`GetTailPosition`または`Find`します。

位置の値がリスト内の有効な位置を表すことを確認する必要があります。 有効な場合は、Microsoft Foundation Class ライブラリのデバッグ バージョンはアサートします。

要素を取得した一覧で、最初からの新しい値場合*rPosition* NULL に設定されます。

> [!NOTE]
>  返すこのメソッドの const バージョンが変更された時点で、MFC 8.0`const CObject*`の代わりに`const CObject*&`します。  C++ 標準に準拠コンパイラに変更されました。

次の表はその他のメンバー関数に似ている`CObList::GetPrev`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const void* GetPrev( POSITION&` `rPosition` `) const;`|
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetPrev( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>例

  `CAge`クラスのリストについては、[CObList::CObList](#coblist) を参照してください。

[!code-cpp[NVC_MFCCollections#99](../../mfc/codesnippet/cpp/coblist-class_11.cpp)]

このプログラムからの結果は次のとおりです。

```Output
a CAge at $421C 21
a CAge at $421C 40
```

##  <a name="getsize"></a>  CObList::GetSize

リストの要素の数を返します。

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>戻り値

リストの項目数。

### <a name="remarks"></a>Remarks

リスト内の要素の数を取得するには、このメソッドを呼び出します。

次の表はその他のメンバー関数に似ている`CObList::GetSize`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetSize( ) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetSize( ) const;**|

### <a name="example"></a>例

`CAge`クラスのリストについては、[CObList::CObList](#coblist) を参照してください。

[!code-cpp[NVC_MFCCollections#100](../../mfc/codesnippet/cpp/coblist-class_12.cpp)]

##  <a name="gettail"></a>  CObList::GetTail

取得、`CObject`このリストの末尾の要素を表すポインターです。

```
CObject*& GetTail();
const CObject*& GetTail() const;
```

### <a name="return-value"></a>戻り値

戻り値の説明を参照して[gethead 関数](#gethead)します。

### <a name="remarks"></a>Remarks

リストが呼び出す前に空でないことを確認する必要があります`GetTail`します。 リストが空の場合、Microsoft Foundation Class ライブラリのデバッグ バージョンはアサートします。 使用[IsEmpty](#isempty)リストに要素が含まれていることを確認します。

次の表はその他のメンバー関数に似ている`CObList::GetTail`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const void\*& GetTail( ) const; void\*& GetTail( );**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString& GetTail( ) const; CString& GetTail( );**|

### <a name="example"></a>例

`CAge`クラスのリストについては、[CObList::CObList](#coblist) を参照してください。

[!code-cpp[NVC_MFCCollections#101](../../mfc/codesnippet/cpp/coblist-class_13.cpp)]

##  <a name="gettailposition"></a>  CObList::GetTailPosition

このリストの末尾の要素の位置を取得します。**NULL**リストが空の場合。

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>戻り値

イテレーションまたはオブジェクト ポインターの取得に使用できる位置の値リストが空の場合は NULL です。

次の表はその他のメンバー関数に似ている`CObList::GetTailPosition`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION GetTailPosition( ) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION GetTailPosition( ) const;**|

### <a name="example"></a>例

`CAge`クラスのリストについては、[CObList::CObList](#coblist) を参照してください。

[!code-cpp[NVC_MFCCollections#102](../../mfc/codesnippet/cpp/coblist-class_14.cpp)]

##  <a name="insertafter"></a>  CObList::InsertAfter

指定した位置にある要素の後にこのリストに要素を追加します。

```
POSITION InsertAfter(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>パラメーター

*position*<br/>
以前、によって返される位置値`GetNext`、 `GetPrev`、または`Find`メンバー関数の呼び出し。

*newElement*<br/>
この一覧に追加するオブジェクトのポインター。

次の表はその他のメンバー関数に似ている`CObList::InsertAfter`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION InsertAfter( POSITION** *position* **, void** <strong>\*</strong> `newElement` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION InsertAfter (POSITION** *position* **, const CString&** `newElement` **);**<br /><br /> **POSITION InsertAfter( POSITION** *position* **, LPCTSTR** `newElement` **);**|

### <a name="return-value"></a>戻り値

これは、*position* パラメーターと同じ POSITION 値です。

### <a name="example"></a>例

  `CAge`クラスのリストについては、[CObList::CObList](#coblist) を参照してください。

[!code-cpp[NVC_MFCCollections#103](../../mfc/codesnippet/cpp/coblist-class_15.cpp)]

このプログラムからの結果は次のとおりです。

```Output
InsertAfter example: A CObList with 3 elements
a CAge at $4A44 40
a CAge at $4A64 65
a CAge at $4968 21
```

##  <a name="insertbefore"></a>  CObList::InsertBefore

一覧の指定した位置にある要素の前に要素を追加します。

```
POSITION InsertBefore(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>パラメーター

*position*<br/>
以前、によって返される位置値`GetNext`、 `GetPrev`、または`Find`メンバー関数の呼び出し。

*newElement*<br/>
この一覧に追加するオブジェクトのポインター。

### <a name="return-value"></a>戻り値

イテレーションまたはオブジェクト ポインターの取得に使用できる位置の値リストが空の場合は NULL です。

次の表はその他のメンバー関数に似ている`CObList::InsertBefore`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION InsertBefore( POSITION** *position* **, void** <strong>\*</strong> `newElement` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION InsertBefore (POSITION** *POSITION* **, const CString&** `newElement` **);**<br /><br /> **POSITION InsertBefore( POSITION** *position* **, LPCTSTR** `newElement` **);**|

### <a name="example"></a>例

  `CAge`クラスのリストについては、[CObList::CObList](#coblist) を参照してください。

[!code-cpp[NVC_MFCCollections#104](../../mfc/codesnippet/cpp/coblist-class_16.cpp)]

このプログラムからの結果は次のとおりです。

```Output
InsertBefore example: A CObList with 3 elements
a CAge at $4AE2 40
a CAge at $4B02 65
a CAge at $49E6 21
```

##  <a name="isempty"></a>  CObList::IsEmpty

このリストに要素が含まれないかどうかを示します。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>戻り値

この場合は 0 以外のリストは空です。それ以外の場合 0 を返します。

次の表はその他のメンバー関数に似ている`CObList::IsEmpty`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Const; BOOL IsEmpty)**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Const; BOOL IsEmpty)**|

### <a name="example"></a>例

  例をご覧ください[RemoveAll](#removeall)します。

##  <a name="removeall"></a>  CObList::RemoveAll

この一覧からすべての要素を削除し、関連付けられている解放`CObList`メモリ。

```
void RemoveAll();
```

### <a name="remarks"></a>Remarks

リストが空で既に場合、エラーは発生しません。

要素を削除するときに、 `CObList`、一覧からオブジェクトのポインターを削除します。 オブジェクト自体を削除するユーザーの責任になります。

次の表はその他のメンバー関数に似ている`CObList::RemoveAll`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void RemoveAll( );**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void RemoveAll( );**|

### <a name="example"></a>例

`CAge`クラスのリストについては、[CObList::CObList](#coblist) を参照してください。

[!code-cpp[NVC_MFCCollections#105](../../mfc/codesnippet/cpp/coblist-class_17.cpp)]

##  <a name="removeat"></a>  CObList::RemoveAt

この一覧から、指定した要素を削除します。

```
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>パラメーター

*position*<br/>
一覧から削除する要素の位置。

### <a name="remarks"></a>Remarks

要素を削除するときに、 `CObList`、一覧からオブジェクトへのポインターを削除します。 オブジェクト自体を削除するユーザーの責任になります。

位置の値がリスト内の有効な位置を表すことを確認する必要があります。 有効な場合は、Microsoft Foundation Class ライブラリのデバッグ バージョンはアサートします。

次の表はその他のメンバー関数に似ている`CObList::RemoveAt`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void RemoveAt( POSITION** *position* **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void RemoveAt( POSITION** *position* **);**|

### <a name="example"></a>例

  リストの反復処理中に要素を削除するときは注意してください。 次の例は、[GetNext](#getnext) の有効な **POSITION** 値を保証する削除手法です。

`CAge`クラスのリストについては、[CObList::CObList](#coblist) を参照してください。

[!code-cpp[NVC_MFCCollections#106](../../mfc/codesnippet/cpp/coblist-class_18.cpp)]

このプログラムからの結果は次のとおりです。

`RemoveAt example: A CObList with 2 elements`

`a CAge at $4C1E 65`

`a CAge at $4B22 21`

##  <a name="removehead"></a>  CObList::RemoveHead

リストの先頭から要素を削除し、ポインターを返します。

```
CObject* RemoveHead();
```

### <a name="return-value"></a>戻り値

`CObject`リストの先頭の前のポインター。

### <a name="remarks"></a>Remarks

リストが呼び出す前に空でないことを確認する必要があります`RemoveHead`します。 リストが空の場合、Microsoft Foundation Class ライブラリのデバッグ バージョンはアサートします。 使用[IsEmpty](#isempty)リストに要素が含まれていることを確認します。

次の表はその他のメンバー関数に似ている`CObList::RemoveHead`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* RemoveHead( );**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CString RemoveHead( );**|

### <a name="example"></a>例

`CAge`クラスのリストについては、[CObList::CObList](#coblist) を参照してください。

[!code-cpp[NVC_MFCCollections#107](../../mfc/codesnippet/cpp/coblist-class_19.cpp)]

##  <a name="removetail"></a>  CObList::RemoveTail

リストの末尾から要素を削除し、ポインターを返します。

```
CObject* RemoveTail();
```

### <a name="return-value"></a>戻り値

リストの末尾にあったオブジェクトへのポインター。

### <a name="remarks"></a>Remarks

リストが呼び出す前に空でないことを確認する必要があります`RemoveTail`します。 リストが空の場合、Microsoft Foundation Class ライブラリのデバッグ バージョンはアサートします。 使用[IsEmpty](#isempty)リストに要素が含まれていることを確認します。

次の表はその他のメンバー関数に似ている`CObList::RemoveTail`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* RemoveTail( );**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CString RemoveTail( );**|

### <a name="example"></a>例

`CAge`クラスのリストについては、[CObList::CObList](#coblist) を参照してください。

[!code-cpp[NVC_MFCCollections#108](../../mfc/codesnippet/cpp/coblist-class_20.cpp)]

##  <a name="setat"></a>  CObList::SetAt

指定された位置に要素を設定します。

```
void SetAt(
    POSITION pos,
    CObject* newElement);
```

### <a name="parameters"></a>パラメーター

*pos*<br/>
設定する要素の位置。

*newElement*<br/>
`CObject`一覧に書き込むへのポインター。

### <a name="remarks"></a>Remarks

位置の型の変数は、リストのキーです。 、インデックスと同じではありませんし、操作できません。 位置の値を自分でします。 `SetAt` 書き込み、`CObject`リスト内の指定位置へのポインター。

位置の値がリスト内の有効な位置を表すことを確認する必要があります。 有効な場合は、Microsoft Foundation Class ライブラリのデバッグ バージョンはアサートします。

次の表はその他のメンバー関数に似ている`CObList::SetAt`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void SetAt( POSITION** `pos` **, const CString&** `newElement` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void SetAt( POSITION** `pos` **, LPCTSTR** `newElement` **);**|

### <a name="example"></a>例

  `CAge`クラスのリストについては、[CObList::CObList](#coblist) を参照してください。

[!code-cpp[NVC_MFCCollections#109](../../mfc/codesnippet/cpp/coblist-class_21.cpp)]

このプログラムからの結果は次のとおりです。

```Output
SetAt example: A CObList with 2 elements
a CAge at $4D98 40
a CAge at $4DB8 65
```

## <a name="see-also"></a>関連項目

[CObject クラス](../../mfc/reference/cobject-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CStringList クラス](../../mfc/reference/cstringlist-class.md)<br/>
[CPtrList クラス](../../mfc/reference/cptrlist-class.md)
