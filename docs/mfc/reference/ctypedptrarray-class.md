---
title: CTypedPtrArray クラス
ms.date: 11/04/2016
f1_keywords:
- CTypedPtrArray
- AFXTEMPL/CTypedPtrArray
- AFXTEMPL/CTypedPtrArray::Add
- AFXTEMPL/CTypedPtrArray::Append
- AFXTEMPL/CTypedPtrArray::Copy
- AFXTEMPL/CTypedPtrArray::ElementAt
- AFXTEMPL/CTypedPtrArray::GetAt
- AFXTEMPL/CTypedPtrArray::InsertAt
- AFXTEMPL/CTypedPtrArray::SetAt
- AFXTEMPL/CTypedPtrArray::SetAtGrow
helpviewer_keywords:
- CTypedPtrArray [MFC], Add
- CTypedPtrArray [MFC], Append
- CTypedPtrArray [MFC], Copy
- CTypedPtrArray [MFC], ElementAt
- CTypedPtrArray [MFC], GetAt
- CTypedPtrArray [MFC], InsertAt
- CTypedPtrArray [MFC], SetAt
- CTypedPtrArray [MFC], SetAtGrow
ms.assetid: e3ecdf1a-a889-4156-92dd-ddbd36ccd919
ms.openlocfilehash: 767d4782ec637a0404051e6871d584f73cefdcd2
ms.sourcegitcommit: 53f75afaf3c0b3ed481c5503357ed2b7b87aac6d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53657475"
---
# <a name="ctypedptrarray-class"></a>CTypedPtrArray クラス

`CPtrArray` クラスまたは `CObArray`クラスのオブジェクトに対してタイプセーフな "ラッパー" を提供します。

## <a name="syntax"></a>構文

```
template<class BASE_CLASS, class TYPE>
class CTypedPtrArray : public BASE_CLASS
```

#### <a name="parameters"></a>パラメーター

*BASE_CLASS*<br/>
型指定されたポインター、配列クラスの基本クラス配列クラスである必要があります (`CObArray`または`CPtrArray`)。

*TYPE*<br/>
基本クラスの配列に格納されている要素の型。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CTypedPtrArray::Add](#add)|配列の末尾に新しい要素を追加します。 必要に応じて、配列を大きく|
|[CTypedPtrArray::Append](#append)|1 つの配列の内容を別の末尾に追加します。 必要に応じて、配列を大きく|
|[CTypedPtrArray::Copy](#copy)|配列に別の配列をコピーします。必要に応じて、配列を大きくします。|
|[CTypedPtrArray::ElementAt](#elementat)|配列内の要素ポインターへの一時的な参照を返します。|
|[CTypedPtrArray::GetAt](#getat)|指定されたインデックス位置にある値を返します。|
|[CTypedPtrArray::InsertAt](#insertat)|指定されたインデックス位置に要素 (または別の配列内のすべての要素) を挿入します。|
|[CTypedPtrArray::SetAt](#setat)|指定されたインデックスの値を設定します。配列は大きくできません。|
|[CTypedPtrArray::SetAtGrow](#setatgrow)|指定されたインデックスの値を設定します。必要に応じて、配列を大きくします。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CTypedPtrArray::operator \[ \]](#operator_at)|指定されたインデックス位置にある要素を設定または取得します。|

## <a name="remarks"></a>Remarks

使用すると`CTypedPtrArray`なく`CPtrArray`または`CObArray`C++ の型チェック機能は、一致しないポインター型で発生したエラーを解消します。

さらに、`CTypedPtrArray`を使用した場合に必要になるキャストの多くを実行するラッパー`CObArray`または`CPtrArray`します。

すべて`CTypedPtrArray`関数はインラインで、このテンプレートの使用が大幅には影響しません、コードの速度またはサイズ。

使用しての詳細については`CTypedPtrArray`、記事を参照して[コレクション](../../mfc/collections.md)と[クラスのテンプレートに基づく](../../mfc/template-based-classes.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

`BASE_CLASS`

`CTypedPtrArray`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxtempl.h

##  <a name="add"></a>  CTypedPtrArray::Add

このメンバー関数を呼び出す`BASE_CLASS` **:: 追加**します。

```
INT_PTR Add(TYPE newElement);
```

### <a name="parameters"></a>パラメーター

*TYPE*<br/>
配列に追加する要素の型を指定するテンプレート パラメーター。

*newElement*<br/>
この配列に追加する要素。

### <a name="return-value"></a>戻り値

追加された要素のインデックス。

### <a name="remarks"></a>Remarks

詳細についてを参照してください。 [CObArray::Add](../../mfc/reference/cobarray-class.md#add)します。

##  <a name="append"></a>  CTypedPtrArray::Append

このメンバー関数を呼び出す`BASE_CLASS`:: * * 追加します。

```
INT_PTR Append(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>パラメーター

*BASE_CLASS*<br/>
型指定されたポインター、配列クラスの基本クラス配列クラスである必要があります ( [CObArray](../../mfc/reference/cobarray-class.md)または[CPtrArray](../../mfc/reference/cptrarray-class.md))。

*TYPE*<br/>
基本クラスの配列に格納されている要素の型。

*src*<br/>
配列に追加する要素のソースです。

### <a name="return-value"></a>戻り値

追加された最初の要素のインデックス。

### <a name="remarks"></a>Remarks

詳細についてを参照してください。 [CObArray::Append](../../mfc/reference/cobarray-class.md#append)します。

##  <a name="copy"></a>  CTypedPtrArray::Copy

このメンバー関数を呼び出す`BASE_CLASS` **:: コピー**します。

```
void Copy(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>パラメーター

*BASE_CLASS*<br/>
型指定されたポインター、配列クラスの基本クラス配列クラスである必要があります ( [CObArray](../../mfc/reference/cobarray-class.md)または[CPtrArray](../../mfc/reference/cptrarray-class.md))。

*TYPE*<br/>
基本クラスの配列に格納されている要素の型。

*src*<br/>
配列にコピーする要素のソースです。

### <a name="remarks"></a>Remarks

詳細についてを参照してください。 [CObArray::Copy](../../mfc/reference/cobarray-class.md#copy)します。

##  <a name="elementat"></a>  CTypedPtrArray::ElementAt

このインライン関数`BASE_CLASS` **:: ElementAt**します。

```
TYPE& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>パラメーター

*TYPE*<br/>
この配列に格納されている要素の型を指定するテンプレート パラメーター。

*nIndex*<br/>
0 以上である整数インデックスによって返される値以下`BASE_CLASS` **:: です**します。

### <a name="return-value"></a>戻り値

指定された位置にある要素への参照を一時*nIndex*します。 この要素は、テンプレート パラメーターで指定された型*型*します。

### <a name="remarks"></a>Remarks

詳細についてを参照してください。 [CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)します。

##  <a name="getat"></a>  CTypedPtrArray::GetAt

このインライン関数`BASE_CLASS` **:: GetAt**します。

```
TYPE GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>パラメーター

*TYPE*<br/>
配列に格納されている要素の型を指定するテンプレート パラメーター。

*nIndex*<br/>
0 以上である整数インデックスによって返される値以下`BASE_CLASS` **:: です**します。

### <a name="return-value"></a>戻り値

指定された位置にある要素のコピーを*nIndex*します。 この要素は、テンプレート パラメーターで指定された型*型*します。

### <a name="remarks"></a>Remarks

詳細についてを参照してください[CObArray::GetAt。](../../mfc/reference/cobarray-class.md#getat)

##  <a name="insertat"></a>  CTypedPtrArray::InsertAt

このメンバー関数を呼び出す`BASE_CLASS` **:: InsertAt**します。

```
void InsertAt(
    INT_PTR nIndex,
    TYPE newElement,
    INT_PTR nCount = 1);

void InsertAt(
    INT_PTR nStartIndex,
    CTypedPtrArray<BASE_CLASS, TYPE>* pNewArray);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
によって返される値よりも大きい可能性がある整数インデックス[CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)します。

*TYPE*<br/>
基本クラスの配列に格納されている要素の型。

*newElement*<br/>
この配列に格納するオブジェクトのポインター。 A *newElement*値の**NULL**は許可されています。

*nCount*<br/>
(既定値は 1) を挿入する回数がこの要素にする必要があります。

*nStartIndex*<br/>
によって返される値よりも大きい可能性がある整数インデックス`CObArray::GetUpperBound`します。

*BASE_CLASS*<br/>
型指定されたポインター、配列クラスの基本クラス配列クラスである必要があります ( [CObArray](../../mfc/reference/cobarray-class.md)または[CPtrArray](../../mfc/reference/cptrarray-class.md))。

*pNewArray*<br/>
この配列に追加する要素を含む別の配列。

### <a name="remarks"></a>Remarks

詳細についてを参照してください。 [CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)します。

##  <a name="operator_at"></a>  CTypedPtrArray::operator

これらのインライン演算子を呼び出す`BASE_CLASS` **:: 演算子**します。

```
TYPE& operator[ ](int_ptr nindex);
TYPE operator[ ](int_ptr nindex) const;
```

### <a name="parameters"></a>パラメーター

*TYPE*<br/>
配列に格納されている要素の型を指定するテンプレート パラメーター。

*nIndex*<br/>
0 以上である整数インデックスによって返される値以下`BASE_CLASS` **:: です**します。

### <a name="remarks"></a>Remarks

示されていない配列の最初の演算子と呼ばれる**const**右 (右辺値) または代入ステートメントの左側 (左辺値) のいずれかで使用できます。 次が呼び出されます。 **const**配列、は、右側にのみ使用できます。

ライブラリのデバッグ バージョンはアサート添字 (またはいずれかで、左、代入ステートメントの右側にある) が範囲外です。

##  <a name="setat"></a>  CTypedPtrArray::SetAt

このメンバー関数を呼び出す`BASE_CLASS` **:: SetAt**します。

```
void SetAt(
    INT_PTR nIndex,
    TYPE ptr);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
0 以上である整数インデックスによって返される値以下[CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)します。

*TYPE*<br/>
基本クラスの配列に格納されている要素の型。

*ptr*<br/>
位置を nIndex、配列に挿入される要素へのポインター。 NULL 値が許可されているとします。

### <a name="remarks"></a>Remarks

詳細についてを参照してください。 [CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat)します。

##  <a name="setatgrow"></a>  CTypedPtrArray::SetAtGrow

このメンバー関数を呼び出す`BASE_CLASS` **:: SetAtGrow**します。

```
void SetAtGrow(
    INT_PTR nIndex,
    TYPE newElement);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
0 以上である整数のインデックス。

*TYPE*<br/>
基本クラスの配列に格納されている要素の型。

*newElement*<br/>
この配列に追加するオブジェクトのポインター。 A **NULL**値が許可されています。

### <a name="remarks"></a>Remarks

詳細についてを参照してください。 [CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)します。

## <a name="see-also"></a>関連項目

[MFC サンプルの収集](../../visual-cpp-samples.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CPtrArray クラス](../../mfc/reference/cptrarray-class.md)<br/>
[CObArray クラス](../../mfc/reference/cobarray-class.md)
