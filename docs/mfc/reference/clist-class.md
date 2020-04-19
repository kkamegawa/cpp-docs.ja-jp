---
title: CList クラス
ms.date: 11/04/2016
f1_keywords:
- CList
- AFXTEMPL/CList
- AFXTEMPL/CList::CList
- AFXTEMPL/CList::AddHead
- AFXTEMPL/CList::AddTail
- AFXTEMPL/CList::Find
- AFXTEMPL/CList::FindIndex
- AFXTEMPL/CList::GetAt
- AFXTEMPL/CList::GetCount
- AFXTEMPL/CList::GetHead
- AFXTEMPL/CList::GetHeadPosition
- AFXTEMPL/CList::GetNext
- AFXTEMPL/CList::GetPrev
- AFXTEMPL/CList::GetSize
- AFXTEMPL/CList::GetTail
- AFXTEMPL/CList::GetTailPosition
- AFXTEMPL/CList::InsertAfter
- AFXTEMPL/CList::InsertBefore
- AFXTEMPL/CList::IsEmpty
- AFXTEMPL/CList::RemoveAll
- AFXTEMPL/CList::RemoveAt
- AFXTEMPL/CList::RemoveHead
- AFXTEMPL/CList::RemoveTail
- AFXTEMPL/CList::SetAt
helpviewer_keywords:
- CList [MFC], CList
- CList [MFC], AddHead
- CList [MFC], AddTail
- CList [MFC], Find
- CList [MFC], FindIndex
- CList [MFC], GetAt
- CList [MFC], GetCount
- CList [MFC], GetHead
- CList [MFC], GetHeadPosition
- CList [MFC], GetNext
- CList [MFC], GetPrev
- CList [MFC], GetSize
- CList [MFC], GetTail
- CList [MFC], GetTailPosition
- CList [MFC], InsertAfter
- CList [MFC], InsertBefore
- CList [MFC], IsEmpty
- CList [MFC], RemoveAll
- CList [MFC], RemoveAt
- CList [MFC], RemoveHead
- CList [MFC], RemoveTail
- CList [MFC], SetAt
ms.assetid: 6f6273c3-c8f6-47f5-ac2a-0a950379ae5d
ms.openlocfilehash: 383222e4892bccc653f010ce4939bca23f2adc93
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62225296"
---
# <a name="clist-class"></a>CList クラス

オブジェクト (重複あり) を順に並べたリストをサポートします。このリストには、シーケンシャル アクセスまたは値指定によるアクセスを行うことができます。

## <a name="syntax"></a>構文

```
template<class TYPE, class ARG_TYPE = const TYPE&>
class CList : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CList::CList](#clist)|空の順序付きリストを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CList::AddHead](#addhead)|(新しい head は、) リストの先頭に要素 (または別のリストのすべての要素) を追加します。|
|[CList::AddTail](#addtail)|(新しい末尾になります)、リストの末尾に要素 (または別のリストのすべての要素) を追加します。|
|[CList::Find](#find)|ポインター値で指定された要素の位置を取得します。|
|[CList::FindIndex](#findindex)|0 から始まるインデックスで指定した要素の位置を取得します。|
|[CList::GetAt](#getat)|指定された位置に要素を取得します。|
|[CList::GetCount](#getcount)|この一覧には、要素の数を返します。|
|[CList::GetHead](#gethead)|(空にすることはできません) の一覧の先頭の要素を返します。|
|[CList::GetHeadPosition](#getheadposition)|リストの先頭の要素の位置を返します。|
|[CList::GetNext](#getnext)|反復処理するためには、次の要素を取得します。|
|[CList::GetPrev](#getprev)|反復処理するためには、直前の要素を取得します。|
|[CList::GetSize](#getsize)|この一覧には、要素の数を返します。|
|[CList::GetTail](#gettail)|(空にすることはできません)、リストの末尾の要素を返します。|
|[CList::GetTailPosition](#gettailposition)|リストの末尾の要素の位置を返します。|
|[CList::InsertAfter](#insertafter)|指定した位置より後に新しい要素を挿入します。|
|[CList::InsertBefore](#insertbefore)|指定した位置の前に新しい要素を挿入します。|
|[CList::IsEmpty](#isempty)|空のリストの条件 (要素がない) をテストします。|
|[CList::RemoveAll](#removeall)|この一覧からすべての要素を削除します。|
|[CList::RemoveAt](#removeat)|位置によって指定された、このリストから要素を削除します。|
|[CList::RemoveHead](#removehead)|リストの先頭から要素を削除します。|
|[CList::RemoveTail](#removetail)|リストの末尾から要素を削除します。|
|[CList::SetAt](#setat)|指定された位置に要素を設定します。|

#### <a name="parameters"></a>パラメーター

*TYPE*<br/>
リストに格納されているオブジェクトの型。

*ARG_TYPE*<br/>
型リストに格納されているオブジェクトを参照するために使用します。 参照であることができます。

## <a name="remarks"></a>Remarks

`CList` リストは、二重リンク リストのように動作します。

位置の型の変数は、リストのキーです。 POSITION 変数は、位置を保持するのにブックマークとして、順番にリストを走査するのに反復子として使用できます。 位置が、インデックスと同じです。 ただしです。

要素の挿入はリストの先頭、末尾、および既知の位置に非常に高速です。 順次検索は、値またはインデックスで要素を検索する必要があります。 この検索は、リストが長い場合は低速にすることはできます。

リスト内の個々 の要素のダンプが必要な場合は、1 以上にダンプ コンテキストの深さを設定する必要があります。

ほとんどの用途のグローバルなヘルパー関数をこのクラスの呼び出しの一部のメンバー関数をカスタマイズする必要があります、`CList`クラス。 参照してください[コレクション クラスのヘルパー](../../mfc/reference/collection-class-helpers.md) 「マクロとグローバル変数」セクションでします。

使用しての詳細については`CList`、記事をご覧ください[コレクション](../../mfc/collections.md)します。

## <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#35](../../mfc/codesnippet/cpp/clist-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CList`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxtempl.h

##  <a name="addhead"></a>  CList::AddHead

このリストの先頭に新しい要素または要素のリストを追加します。

```
POSITION AddHead(ARG_TYPE newElement);
void AddHead(CList* pNewList);
```

### <a name="parameters"></a>パラメーター

*ARG_TYPE*<br/>
一覧の要素の型を指定するテンプレート パラメーター (参照を使用できます)。

*newElement*<br/>
新しい要素。

*pNewList*<br/>
別のポインター`CList`一覧。 内の要素*pNewList*この一覧に追加されます。

### <a name="return-value"></a>戻り値

最初のバージョンでは、新しく挿入される要素の位置を表す値を返します。

### <a name="remarks"></a>Remarks

一覧は、操作の前に空にすることができます。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#36](../../mfc/codesnippet/cpp/clist-class_2.cpp)]

##  <a name="addtail"></a>  CList::AddTail

このリストの末尾に新しい要素または要素のリストを追加します。

```
POSITION AddTail(ARG_TYPE newElement);
void AddTail(CList* pNewList);
```

### <a name="parameters"></a>パラメーター

*ARG_TYPE*<br/>
一覧の要素の型を指定するテンプレート パラメーター (参照を使用できます)。

*newElement*<br/>
この一覧に追加する要素。

*pNewList*<br/>
別のポインター`CList`一覧。 内の要素*pNewList*この一覧に追加されます。

### <a name="return-value"></a>戻り値

最初のバージョンでは、新しく挿入される要素の位置を表す値を返します。

### <a name="remarks"></a>Remarks

一覧は、操作の前に空にすることができます。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#37](../../mfc/codesnippet/cpp/clist-class_3.cpp)]

##  <a name="clist"></a>  CList::CList

空の順序付きリストを構築します。

```
CList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>パラメーター

*nBlockSize*<br/>
リストを拡張するためのメモリの割り当て粒度。

### <a name="remarks"></a>Remarks

単位でメモリが割り当てられている、一覧につれ、 *nBlockSize*エントリ。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#38](../../mfc/codesnippet/cpp/clist-class_4.cpp)]

##  <a name="find"></a>  CList::Find

指定された一致する最初の要素を検索するには、順番に一覧を検索*searchValue*します。

```
POSITION Find(
    ARG_TYPE searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>パラメーター

*ARG_TYPE*<br/>
一覧の要素の型を指定するテンプレート パラメーター (参照を使用できます)。

*searchValue*<br/>
一覧で検索する値。

*startAfter*<br/>
検索の開始位置。 値が指定されていない場合は、head 要素で、検索が始まります。

### <a name="return-value"></a>戻り値

イテレーションまたはオブジェクト ポインターの取得に使用できる位置の値オブジェクトが見つからない場合は NULL です。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#39](../../mfc/codesnippet/cpp/clist-class_5.cpp)]

##  <a name="findindex"></a>  CList::FindIndex

値を使用して*nIndex*リストのインデックス。

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
検索するリストの要素の 0 から始まるインデックス。

### <a name="return-value"></a>戻り値

イテレーションまたはオブジェクト ポインターの取得に使用できる位置の値場合は NULL *nIndex*負の値または大きすぎます。

### <a name="remarks"></a>Remarks

上の停止、リストの先頭から順次スキャンを開始、 *n*番目の要素。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#40](../../mfc/codesnippet/cpp/clist-class_6.cpp)]

##  <a name="getat"></a>  CList::GetAt

指定した位置にあるリスト要素を取得します。

```
TYPE& GetAt(POSITION position);
const TYPE& GetAt(POSITION position) const;
```

### <a name="parameters"></a>パラメーター

*TYPE*<br/>
一覧でオブジェクトの種類を指定するテンプレート パラメーター。

*position*<br/>
取得する要素のリスト内の位置。

### <a name="return-value"></a>戻り値

戻り値の説明を参照して`GetHead`します。

### <a name="remarks"></a>Remarks

`GetAt` 指定した位置に関連付けられている要素 (または、要素への参照) を返します。 、インデックスと同じではありませんし、操作できません。 位置の値を自分でします。 位置の型の変数は、リストのキーです。

位置の値がリスト内の有効な位置を表すことを確認する必要があります。 有効な場合は、Microsoft Foundation Class ライブラリのデバッグ バージョンはアサートします。

### <a name="example"></a>例

  例をご覧ください[CList::GetHeadPosition](#getheadposition)します。

##  <a name="getcount"></a>  CList::GetCount

この一覧には、要素の数を取得します。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>戻り値

要素の数を格納する整数値。

### <a name="remarks"></a>Remarks

このメソッドを呼び出すのと同じ結果が生成されます、 [CList::GetSize](#getsize)メソッド。

### <a name="example"></a>例

  例をご覧ください[CList::RemoveHead](#removehead)します。

##  <a name="gethead"></a>  CList::GetHead

この一覧の先頭の要素 (または head 要素への参照) を取得します。

```
const TYPE& GetHead() const;

TYPE& GetHead();
```

### <a name="parameters"></a>パラメーター

*TYPE*<br/>
一覧でオブジェクトの種類を指定するテンプレート パラメーター。

### <a name="return-value"></a>戻り値

リストの場合**const**、`GetHead`リストの先頭にある要素のコピーを返します。 これにより、関数は、代入ステートメントの右側にあるでのみ使用し、変更から一覧を保護します。

リストがない場合**const**、`GetHead`リストの先頭にある要素への参照を返します。 これは、関数は、代入ステートメントの右辺でも左辺でも使用して、できるので、リスト エントリを変更できます。

### <a name="remarks"></a>Remarks

リストが呼び出す前に空でないことを確認する必要があります`GetHead`します。 リストが空の場合、Microsoft Foundation Class ライブラリのデバッグ バージョンはアサートします。 使用[IsEmpty](#isempty)リストに要素が含まれていることを確認します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#41](../../mfc/codesnippet/cpp/clist-class_7.cpp)]

##  <a name="getheadposition"></a>  CList::GetHeadPosition

この一覧の先頭の要素の位置を取得します。

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>戻り値

イテレーションまたはオブジェクト ポインターの取得に使用できる位置の値リストが空の場合は NULL です。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#42](../../mfc/codesnippet/cpp/clist-class_8.cpp)]

##  <a name="getnext"></a>  CList::GetNext

識別される要素を取得*rPosition*、設定し、 *rPosition*一覧の次のエントリの位置の値にします。

```
TYPE& GetNext(POSITION& rPosition);
const TYPE& GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>パラメーター

*TYPE*<br/>
一覧で、要素の型を指定するテンプレート パラメーター。

*rPosition*<br/>
によって以前返される位置の値への参照を`GetNext`、[順](#getheadposition)、またはその他のメンバー関数の呼び出し。

### <a name="return-value"></a>戻り値

リストの場合**const**、`GetNext`リストの要素のコピーを返します。 これにより、関数は、代入ステートメントの右側にあるでのみ使用し、変更から一覧を保護します。

リストがない場合**const**、`GetNext`リストの要素への参照を返します。 これは、関数は、代入ステートメントの右辺でも左辺でも使用して、できるので、リスト エントリを変更できます。

### <a name="remarks"></a>Remarks

使用することができます`GetNext`への呼び出しを初期位置を確立する場合は、順方向の反復ループで`GetHeadPosition`または`Find`します。

位置の値がリスト内の有効な位置を表すことを確認する必要があります。 有効な場合は、Microsoft Foundation Class ライブラリのデバッグ バージョンはアサートします。

場合は、取得された最後の要素を一覧での新しい値`rPosition`NULL に設定されます。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#43](../../mfc/codesnippet/cpp/clist-class_9.cpp)]

##  <a name="getprev"></a>  CList::GetPrev

識別される要素を取得`rPosition`、設定し、`rPosition`一覧の前のエントリの位置の値にします。

```
TYPE& GetPrev(POSITION& rPosition);
const TYPE& GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>パラメーター

*TYPE*<br/>
一覧で、要素の型を指定するテンプレート パラメーター。

*rPosition*<br/>
によって以前返される位置の値への参照を`GetPrev`またはその他のメンバー関数の呼び出し。

### <a name="return-value"></a>戻り値

リストの場合**const**、`GetPrev`リストの先頭にある要素のコピーを返します。 これにより、関数は、代入ステートメントの右側にあるでのみ使用し、変更から一覧を保護します。

リストがない場合**const**、`GetPrev`リストの要素への参照を返します。 これは、関数は、代入ステートメントの右辺でも左辺でも使用して、できるので、リスト エントリを変更できます。

### <a name="remarks"></a>Remarks

使用することができます`GetPrev`への呼び出しを初期位置を確立する場合に、逆順イテレーション ループで`GetTailPosition`または`Find`します。

位置の値がリスト内の有効な位置を表すことを確認する必要があります。 有効な場合は、Microsoft Foundation Class ライブラリのデバッグ バージョンはアサートします。

要素を取得した一覧で、最初からの新しい値場合*rPosition* NULL に設定されます。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#44](../../mfc/codesnippet/cpp/clist-class_10.cpp)]

##  <a name="getsize"></a>  CList::GetSize

リストの要素の数を返します。

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>戻り値

リストの項目数。

### <a name="remarks"></a>Remarks

リスト内の要素の数を取得するには、このメソッドを呼び出します。  このメソッドを呼び出すのと同じ結果が生成されます、[呼び出す](#getcount)メソッド。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#45](../../mfc/codesnippet/cpp/clist-class_11.cpp)]

##  <a name="gettail"></a>  CList::GetTail

取得、`CObject`このリストの末尾の要素を表すポインターです。

```
TYPE& GetTail();
const TYPE& GetTail() const;
```

### <a name="parameters"></a>パラメーター

*TYPE*<br/>
リストの要素の型を指定するテンプレート パラメーター。

### <a name="return-value"></a>戻り値

戻り値の説明を参照して[gethead 関数](../../mfc/reference/coblist-class.md#gethead)します。

### <a name="remarks"></a>Remarks

リストが呼び出す前に空でないことを確認する必要があります`GetTail`します。 リストが空の場合、Microsoft Foundation Class ライブラリのデバッグ バージョンはアサートします。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)リストに要素が含まれていることを確認します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#46](../../mfc/codesnippet/cpp/clist-class_12.cpp)]

##  <a name="gettailposition"></a>  CList::GetTailPosition

このリストの末尾の要素の位置を取得します。リストが空の場合は NULL です。

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>戻り値

イテレーションまたはオブジェクト ポインターの取得に使用できる位置の値リストが空の場合は NULL です。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#47](../../mfc/codesnippet/cpp/clist-class_13.cpp)]

##  <a name="insertafter"></a>  CList::InsertAfter

指定した位置にある要素の後にこのリストに要素を追加します。

```
POSITION InsertAfter(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>パラメーター

*position*<br/>
以前、によって返される位置値`GetNext`、 `GetPrev`、または`Find`メンバー関数の呼び出し。

*ARG_TYPE*<br/>
リストの要素の型を指定するテンプレート パラメーター。

*newElement*<br/>
この一覧に追加する要素。

### <a name="return-value"></a>戻り値

位置の値で、イテレーションまたは一覧の要素の取得に使用できます。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#48](../../mfc/codesnippet/cpp/clist-class_14.cpp)]

##  <a name="insertbefore"></a>  CList::InsertBefore

一覧の指定した位置にある要素の前に要素を追加します。

```
POSITION InsertBefore(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>パラメーター

*position*<br/>
以前、によって返される位置値`GetNext`、 `GetPrev`、または`Find`メンバー関数の呼び出し。

*ARG_TYPE*<br/>
一覧の要素の型を指定するテンプレート パラメーター (参照を使用できます)。

*newElement*<br/>
この一覧に追加する要素。

### <a name="return-value"></a>戻り値

位置の値で、イテレーションまたは一覧の要素の取得に使用できます。

### <a name="remarks"></a>Remarks

場合*位置*が null の場合、一覧の先頭の要素が挿入されます。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#49](../../mfc/codesnippet/cpp/clist-class_15.cpp)]

##  <a name="isempty"></a>  CList::IsEmpty

このリストに要素が含まれないかどうかを示します。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>戻り値

この場合は 0 以外のリストは空です。それ以外の場合 0 を返します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#50](../../mfc/codesnippet/cpp/clist-class_16.cpp)]

##  <a name="removeall"></a>  CList::RemoveAll

この一覧からすべての要素を削除し、関連付けられているメモリを解放します。

```
void RemoveAll();
```

### <a name="remarks"></a>Remarks

リストが空で既に場合、エラーは発生しません。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#51](../../mfc/codesnippet/cpp/clist-class_17.cpp)]

##  <a name="removeat"></a>  CList::RemoveAt

この一覧から、指定した要素を削除します。

```
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>パラメーター

*position*<br/>
一覧から削除する要素の位置。

### <a name="remarks"></a>Remarks

位置の値がリスト内の有効な位置を表すことを確認する必要があります。 有効な場合は、Microsoft Foundation Class ライブラリのデバッグ バージョンはアサートします。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#52](../../mfc/codesnippet/cpp/clist-class_18.cpp)]

##  <a name="removehead"></a>  CList::RemoveHead

リストの先頭から要素を削除し、ポインターを返します。

```
TYPE RemoveHead();
```

### <a name="parameters"></a>パラメーター

*TYPE*<br/>
リストの要素の型を指定するテンプレート パラメーター。

### <a name="return-value"></a>戻り値

以前、リストの先頭にある要素。

### <a name="remarks"></a>Remarks

リストが呼び出す前に空でないことを確認する必要があります`RemoveHead`します。 リストが空の場合、Microsoft Foundation Class ライブラリのデバッグ バージョンはアサートします。 使用[IsEmpty](#isempty)リストに要素が含まれていることを確認します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#53](../../mfc/codesnippet/cpp/clist-class_19.cpp)]

##  <a name="removetail"></a>  CList::RemoveTail

リストの末尾から要素を削除し、ポインターを返します。

```
TYPE RemoveTail();
```

### <a name="parameters"></a>パラメーター

*TYPE*<br/>
リストの要素の型を指定するテンプレート パラメーター。

### <a name="return-value"></a>戻り値

リストの末尾にあった要素。

### <a name="remarks"></a>Remarks

リストが呼び出す前に空でないことを確認する必要があります`RemoveTail`します。 リストが空の場合、Microsoft Foundation Class ライブラリのデバッグ バージョンはアサートします。 使用[IsEmpty](#isempty)リストに要素が含まれていることを確認します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#54](../../mfc/codesnippet/cpp/clist-class_20.cpp)]

##  <a name="setat"></a>  CList::SetAt

位置の型の変数は、リストのキーです。

```
void SetAt(POSITION pos, ARG_TYPE newElement);
```

### <a name="parameters"></a>パラメーター

*pos*<br/>
設定する要素の位置。

*ARG_TYPE*<br/>
一覧の要素の型を指定するテンプレート パラメーター (参照を使用できます)。

*newElement*<br/>
一覧に追加する要素。

### <a name="remarks"></a>Remarks

、インデックスと同じではありませんし、操作できません。 位置の値を自分でします。 `SetAt` リスト内の指定した位置に要素を書き込みます。

位置の値がリスト内の有効な位置を表すことを確認する必要があります。 有効な場合は、Microsoft Foundation Class ライブラリのデバッグ バージョンはアサートします。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#55](../../mfc/codesnippet/cpp/clist-class_21.cpp)]

## <a name="see-also"></a>関連項目

[MFC サンプルの収集](../../overview/visual-cpp-samples.md)<br/>
[CObject クラス](../../mfc/reference/cobject-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CMap クラス](../../mfc/reference/cmap-class.md)<br/>
[CArray クラス](../../mfc/reference/carray-class.md)
