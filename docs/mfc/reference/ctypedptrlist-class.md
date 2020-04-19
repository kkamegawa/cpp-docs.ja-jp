---
title: CTypedPtrList クラス
ms.date: 11/04/2016
f1_keywords:
- CTypedPtrList
- AFXTEMPL/CTypedPtrList
- AFXTEMPL/CTypedPtrList::AddHead
- AFXTEMPL/CTypedPtrList::AddTail
- AFXTEMPL/CTypedPtrList::GetAt
- AFXTEMPL/CTypedPtrList::GetHead
- AFXTEMPL/CTypedPtrList::GetNext
- AFXTEMPL/CTypedPtrList::GetPrev
- AFXTEMPL/CTypedPtrList::GetTail
- AFXTEMPL/CTypedPtrList::RemoveHead
- AFXTEMPL/CTypedPtrList::RemoveTail
- AFXTEMPL/CTypedPtrList::SetAt
helpviewer_keywords:
- CTypedPtrList [MFC], AddHead
- CTypedPtrList [MFC], AddTail
- CTypedPtrList [MFC], GetAt
- CTypedPtrList [MFC], GetHead
- CTypedPtrList [MFC], GetNext
- CTypedPtrList [MFC], GetPrev
- CTypedPtrList [MFC], GetTail
- CTypedPtrList [MFC], RemoveHead
- CTypedPtrList [MFC], RemoveTail
- CTypedPtrList [MFC], SetAt
ms.assetid: c273096e-1756-4340-864b-4a08b674a65e
ms.openlocfilehash: 9233e83a08fde87c15be5cc1c42a2f1dd3b56511
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324507"
---
# <a name="ctypedptrlist-class"></a>CTypedPtrList クラス

`CPtrList`クラスのオブジェクトに対してタイプ セーフな "ラップ" が用意されています。

## <a name="syntax"></a>構文

```
template<class BASE_CLASS, class TYPE>
class CTypedPtrList : public BASE_CLASS
```

#### <a name="parameters"></a>パラメーター

*BASE_CLASS*<br/>
型付きポインター リスト クラスの基本クラスポインター リスト クラスでなければなりません (`CObList`または`CPtrList`)。

*TYPE*<br/>
基底クラス リストに格納されている要素の型。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CTypedPtrList::AddHead](#addhead)|(新しい head は、) リストの先頭に要素 (または別のリストのすべての要素) を追加します。|
|[CTypedPtrList::AddTail](#addtail)|(新しい末尾になります)、リストの末尾に要素 (または別のリストのすべての要素) を追加します。|
|[CTypedPtrList::GetAt](#getat)|指定された位置に要素を取得します。|
|[CTypedPtrList::GetHead](#gethead)|(空にすることはできません) の一覧の先頭の要素を返します。|
|[CTypedPtrList::GetNext](#getnext)|反復処理するためには、次の要素を取得します。|
|[CTypedPtrList::GetPrev](#getprev)|反復処理するためには、直前の要素を取得します。|
|[CTypedPtrList::GetTail](#gettail)|(空にすることはできません)、リストの末尾の要素を返します。|
|[CTypedPtrList::RemoveHead](#removehead)|リストの先頭から要素を削除します。|
|[CTypedPtrList::RemoveTail](#removetail)|リストの末尾から要素を削除します。|
|[CTypedPtrList::SetAt](#setat)|指定された位置に要素を設定します。|

## <a name="remarks"></a>Remarks

使用すると`CTypedPtrList`なく`CObList`または`CPtrList`C++ の型チェック機能は、一致しないポインター型で発生したエラーを解消します。

さらに、`CTypedPtrList`を使用した場合に必要になるキャストの多くを実行するラッパー`CObList`または`CPtrList`します。

すべて`CTypedPtrList`関数はインラインで、このテンプレートの使用が大幅には影響しません、コードの速度またはサイズ。

派生したリスト`CObList`ができるはから派生したものですが、シリアル化できる`CPtrList`ことはできません。

`CTypedPtrList` オブジェクトが削除されたとき、またはその要素が削除されたときは、ポインターだけが削除されます。ポインターが参照するエンティティは削除されません。

使用しての詳細については`CTypedPtrList`、記事を参照して[コレクション](../../mfc/collections.md)と[クラスのテンプレートに基づく](../../mfc/template-based-classes.md)します。

## <a name="example"></a>例

この例のインスタンスを作成する`CTypedPtrList`、1 つのオブジェクトを追加、リストをディスクにシリアル化およびからオブジェクトを削除します。

[!code-cpp[NVC_MFCCollections#110](../../mfc/codesnippet/cpp/ctypedptrlist-class_1.cpp)]

[!code-cpp[NVC_MFCCollections#111](../../mfc/codesnippet/cpp/ctypedptrlist-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

`BASE_CLASS`

`_CTypedPtrList`

`CTypedPtrList`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxtempl.h

##  <a name="addhead"></a>  CTypedPtrList::AddHead

このメンバー関数を呼び出す`BASE_CLASS` **:: AddHead**します。

```
POSITION AddHead(TYPE newElement);
void AddHead(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```

### <a name="parameters"></a>パラメーター

*TYPE*<br/>
基底クラス リストに格納されている要素の型。

*newElement*<br/>
この一覧に追加するオブジェクトのポインター。 NULL 値が許可されているとします。

*BASE_CLASS*<br/>
型付きポインター リスト クラスの基本クラスポインター リスト クラスでなければなりません ( [CObList](../../mfc/reference/coblist-class.md)または[CPtrList](../../mfc/reference/cptrlist-class.md))。

*pNewList*<br/>
別のポインター [CTypedPtrList](../../mfc/reference/ctypedptrlist-class.md)オブジェクト。 内の要素*pNewList*この一覧に追加されます。

### <a name="return-value"></a>戻り値

最初のバージョンでは、新しく挿入される要素の位置を表す値を返します。

### <a name="remarks"></a>Remarks

最初のバージョンでは、リストの先頭の前に新しい要素を追加します。 2 番目のバージョンでは、別のリストの先頭の前に要素を追加します。

##  <a name="addtail"></a>  CTypedPtrList::AddTail

このメンバー関数を呼び出す`BASE_CLASS` **:: AddTail**します。

```
POSITION AddTail(TYPE newElement);
void AddTail(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```

### <a name="parameters"></a>パラメーター

*TYPE*<br/>
基底クラス リストに格納されている要素の型。

*newElement*<br/>
この一覧に追加するオブジェクトのポインター。 NULL 値が許可されているとします。

*BASE_CLASS*<br/>
型付きポインター リスト クラスの基本クラスポインター リスト クラスでなければなりません ( [CObList](../../mfc/reference/coblist-class.md)または[CPtrList](../../mfc/reference/cptrlist-class.md))。

*pNewList*<br/>
別のポインター [CTypedPtrList](../../mfc/reference/ctypedptrlist-class.md)オブジェクト。 内の要素*pNewList*この一覧に追加されます。

### <a name="return-value"></a>戻り値

最初のバージョンでは、新しく挿入される要素の位置を表す値を返します。

### <a name="remarks"></a>Remarks

最初のバージョンでは、リストの末尾の後に新しい要素を追加します。 2 番目のバージョンでは、リストの末尾の後に別の要素のリストを追加します。

##  <a name="getat"></a>  CTypedPtrList::GetAt

位置の型の変数は、リストのキーです。

```
TYPE& GetAt(POSITION position);
TYPE GetAt(POSITION position) const;
```

### <a name="parameters"></a>パラメーター

*TYPE*<br/>
リストに格納されている要素の種類を指定するテンプレート パラメーター。

*position*<br/>
以前、によって返される位置値`GetHeadPosition`または`Find`メンバー関数の呼び出し。

### <a name="return-value"></a>戻り値

一覧へのポインターを介してアクセスする場合、 `const CTypedPtrList`、し`GetAt`テンプレート パラメーターで指定された型のポインターを返します*型*します。 これにより、関数は、代入ステートメントの右側にあるでのみ使用し、したがって変更から一覧を保護します。

リストが直接、または、ポインターを介してアクセスされる場合、 `CTypedPtrList`、し`GetAt`テンプレート パラメーターで指定された型のポインターへの参照を返します*型*します。 これは、関数は、代入ステートメントの右辺でも左辺でも使用して、できるので、リスト エントリを変更できます。

### <a name="remarks"></a>Remarks

、インデックスと同じではありませんし、操作できません。 位置の値を自分でします。 `GetAt` 取得、`CObject`指定した位置に関連付けられたポインター。

位置の値がリスト内の有効な位置を表すことを確認する必要があります。 有効な場合は、Microsoft Foundation Class ライブラリのデバッグ バージョンはアサートします。

このインライン関数`BASE_CLASS` **:: GetAt**します。

##  <a name="gethead"></a>  CTypedPtrList::GetHead

この一覧の先頭の要素を表すポインターを取得します。

```
TYPE& GetHead();
TYPE GetHead() const;
```

### <a name="parameters"></a>パラメーター

*TYPE*<br/>
リストに格納されている要素の種類を指定するテンプレート パラメーター。

### <a name="return-value"></a>戻り値

一覧へのポインターを介してアクセスする場合、 `const CTypedPtrList`、し`GetHead`テンプレート パラメーターで指定された型のポインターを返します*型*します。 これにより、関数は、代入ステートメントの右側にあるでのみ使用し、したがって変更から一覧を保護します。

リストが直接、または、ポインターを介してアクセスされる場合、 `CTypedPtrList`、し`GetHead`テンプレート パラメーターで指定された型のポインターへの参照を返します*型*します。 これは、関数は、代入ステートメントの右辺でも左辺でも使用して、できるので、リスト エントリを変更できます。

### <a name="remarks"></a>Remarks

リストが呼び出す前に空でないことを確認する必要があります`GetHead`します。 リストが空の場合、Microsoft Foundation Class ライブラリのデバッグ バージョンはアサートします。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)リストに要素が含まれていることを確認します。

##  <a name="getnext"></a>  CTypedPtrList::GetNext

識別される要素を取得*rPosition*、設定し、 *rPosition*一覧の次のエントリの位置の値にします。

```
TYPE& GetNext(POSITION& rPosition);
TYPE GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>パラメーター

*TYPE*<br/>
この一覧に含まれる要素の型を指定するテンプレート パラメーター。

*rPosition*<br/>
によって以前返される位置の値への参照を`GetNext`、 `GetHeadPosition`、またはその他のメンバー関数の呼び出し。

### <a name="return-value"></a>戻り値

一覧へのポインターを介してアクセスする場合、 `const CTypedPtrList`、し`GetNext`テンプレート パラメーターで指定された型のポインターを返します*型*します。 これにより、関数は、代入ステートメントの右側にあるでのみ使用し、したがって変更から一覧を保護します。

リストが直接、または、ポインターを介してアクセスされる場合、 `CTypedPtrList`、し`GetNext`テンプレート パラメーターで指定された型のポインターへの参照を返します*型*します。 これは、関数は、代入ステートメントの右辺でも左辺でも使用して、できるので、リスト エントリを変更できます。

### <a name="remarks"></a>Remarks

使用することができます`GetNext`への呼び出しを初期位置を確立する場合は、順方向の反復ループで`GetHeadPosition`または[CPtrList::Find](../../mfc/reference/coblist-class.md#find)します。

位置の値がリスト内の有効な位置を表すことを確認する必要があります。 有効な場合は、Microsoft Foundation Class ライブラリのデバッグ バージョンはアサートします。

場合は、取得された最後の要素を一覧での新しい値*rPosition* NULL に設定されます。

反復処理中に要素を削除することになります。 例をご覧ください[CObList::RemoveAt](../../mfc/reference/coblist-class.md#removeat)します。

##  <a name="getprev"></a>  CTypedPtrList::GetPrev

識別される要素を取得*rPosition*、設定し、 *rPosition*一覧の前のエントリの位置の値にします。

```
TYPE& GetPrev(POSITION& rPosition);
TYPE GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>パラメーター

*TYPE*<br/>
この一覧に含まれる要素の型を指定するテンプレート パラメーター。

*rPosition*<br/>
によって以前返される位置の値への参照を`GetPrev`またはその他のメンバー関数の呼び出し。

### <a name="return-value"></a>戻り値

一覧へのポインターを介してアクセスする場合、 `const CTypedPtrList`、し`GetPrev`テンプレート パラメーターで指定された型のポインターを返します*型*します。 これにより、関数は、代入ステートメントの右側にあるでのみ使用し、したがって変更から一覧を保護します。

リストが直接、または、ポインターを介してアクセスされる場合、 `CTypedPtrList`、し`GetPrev`テンプレート パラメーターで指定された型のポインターへの参照を返します*型*します。 これは、関数は、代入ステートメントの右辺でも左辺でも使用して、できるので、リスト エントリを変更できます。

### <a name="remarks"></a>Remarks

使用することができます`GetPrev`への呼び出しを初期位置を確立する場合に、逆順イテレーション ループで`GetTailPosition`または`Find`します。

位置の値がリスト内の有効な位置を表すことを確認する必要があります。 有効な場合は、Microsoft Foundation Class ライブラリのデバッグ バージョンはアサートします。

要素を取得した一覧で、最初からの新しい値場合*rPosition* NULL に設定されます。

##  <a name="gettail"></a>  CTypedPtrList::GetTail

この一覧の先頭の要素を表すポインターを取得します。

```
TYPE& GetTail();
TYPE GetTail() const;
```

### <a name="parameters"></a>パラメーター

*TYPE*<br/>
リストに格納されている要素の種類を指定するテンプレート パラメーター。

### <a name="return-value"></a>戻り値

一覧へのポインターを介してアクセスする場合、 `const CTypedPtrList`、し`GetTail`テンプレート パラメーターで指定された型のポインターを返します*型*します。 これにより、関数は、代入ステートメントの右側にあるでのみ使用し、したがって変更から一覧を保護します。

リストが直接、または、ポインターを介してアクセスされる場合、 `CTypedPtrList`、し`GetTail`テンプレート パラメーターで指定された型のポインターへの参照を返します*型*します。 これは、関数は、代入ステートメントの右辺でも左辺でも使用して、できるので、リスト エントリを変更できます。

### <a name="remarks"></a>Remarks

リストが呼び出す前に空でないことを確認する必要があります`GetTail`します。 リストが空の場合、Microsoft Foundation Class ライブラリのデバッグ バージョンはアサートします。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)リストに要素が含まれていることを確認します。

##  <a name="removehead"></a>  CTypedPtrList::RemoveHead

リストの先頭から要素を削除し、それを返します。

```
TYPE RemoveHead();
```

### <a name="parameters"></a>パラメーター

*TYPE*<br/>
リストに格納されている要素の種類を指定するテンプレート パラメーター。

### <a name="return-value"></a>戻り値

一覧の先頭の前のポインター。 このポインターは、テンプレート パラメーターで指定された型*型*します。

### <a name="remarks"></a>Remarks

リストが呼び出す前に空でないことを確認する必要があります`RemoveHead`します。 リストが空の場合、Microsoft Foundation Class ライブラリのデバッグ バージョンはアサートします。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)リストに要素が含まれていることを確認します。

##  <a name="removetail"></a>  CTypedPtrList::RemoveTail

リストの末尾から要素を削除し、それを返します。

```
TYPE RemoveTail();
```

### <a name="parameters"></a>パラメーター

*TYPE*<br/>
リストに格納されている要素の種類を指定するテンプレート パラメーター。

### <a name="return-value"></a>戻り値

リストの末尾に以前のポインター。 このポインターは、テンプレート パラメーターで指定された型*型*します。

### <a name="remarks"></a>Remarks

リストが呼び出す前に空でないことを確認する必要があります`RemoveTail`します。 リストが空の場合、Microsoft Foundation Class ライブラリのデバッグ バージョンはアサートします。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)リストに要素が含まれていることを確認します。

##  <a name="setat"></a>  CTypedPtrList::SetAt

このメンバー関数を呼び出す`BASE_CLASS` **:: SetAt**します。

```
void SetAt(POSITION pos, TYPE newElement);
```

### <a name="parameters"></a>パラメーター

*pos*<br/>
設定する要素の位置。

*TYPE*<br/>
基底クラス リストに格納されている要素の型。

*newElement*<br/>
一覧に書き込まれるオブジェクトのポインター。

### <a name="remarks"></a>Remarks

位置の型の変数は、リストのキーです。 、インデックスと同じではありませんし、操作できません。 位置の値を自分でします。 `SetAt` オブジェクトへのポインターをリスト内の指定した位置に書き込みます。

位置の値がリスト内の有効な位置を表すことを確認する必要があります。 有効な場合は、Microsoft Foundation Class ライブラリのデバッグ バージョンはアサートします。

詳細についてを参照してください。 [CObList::SetAt](../../mfc/reference/coblist-class.md#setat)します。

## <a name="see-also"></a>関連項目

[MFC サンプルの収集](../../overview/visual-cpp-samples.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CPtrList クラス](../../mfc/reference/cptrlist-class.md)<br/>
[CObList クラス](../../mfc/reference/coblist-class.md)
