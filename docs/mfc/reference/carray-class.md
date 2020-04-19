---
title: CArray クラス
ms.date: 11/04/2016
f1_keywords:
- CArray
- AFXTEMPL/CArray
- AFXTEMPL/CArray::CArray
- AFXTEMPL/CArray::Add
- AFXTEMPL/CArray::Append
- AFXTEMPL/CArray::Copy
- AFXTEMPL/CArray::ElementAt
- AFXTEMPL/CArray::FreeExtra
- AFXTEMPL/CArray::GetAt
- AFXTEMPL/CArray::GetCount
- AFXTEMPL/CArray::GetData
- AFXTEMPL/CArray::GetSize
- AFXTEMPL/CArray::GetUpperBound
- AFXTEMPL/CArray::InsertAt
- AFXTEMPL/CArray::IsEmpty
- AFXTEMPL/CArray::RemoveAll
- AFXTEMPL/CArray::RemoveAt
- AFXTEMPL/CArray::SetAt
- AFXTEMPL/CArray::SetAtGrow
- AFXTEMPL/CArray::SetSize
helpviewer_keywords:
- CArray [MFC], CArray
- CArray [MFC], Add
- CArray [MFC], Append
- CArray [MFC], Copy
- CArray [MFC], ElementAt
- CArray [MFC], FreeExtra
- CArray [MFC], GetAt
- CArray [MFC], GetCount
- CArray [MFC], GetData
- CArray [MFC], GetSize
- CArray [MFC], GetUpperBound
- CArray [MFC], InsertAt
- CArray [MFC], IsEmpty
- CArray [MFC], RemoveAll
- CArray [MFC], RemoveAt
- CArray [MFC], SetAt
- CArray [MFC], SetAtGrow
- CArray [MFC], SetSize
ms.assetid: fead8b00-4cfd-4625-ad0e-251df62ba92f
ms.openlocfilehash: f82dbf7dce2e14bf760bb76d23d23f667797ee0f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "78874512"
---
# <a name="carray-class"></a>CArray クラス

は C 配列に似た配列をサポートしますが、必要に応じて動的に縮小および拡張できます。

## <a name="syntax"></a>構文

```
template <class TYPE, class ARG_TYPE = const TYPE&>
class CArray : public CObject
```

#### <a name="parameters"></a>パラメーター

*TYPE*<br/>
配列に格納されているオブジェクトの型を指定するテンプレートパラメーター。 *型*は `CArray`によって返されるパラメーターです。

*ARG_TYPE*<br/>
配列に格納されているオブジェクトへのアクセスに使用される引数の型を指定するテンプレートパラメーター。 多くの場合、*型*への参照です。 *ARG_TYPE*は `CArray`に渡されるパラメーターです。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|Description|
|----------|-----------------|
|[CArray:: CArray](#carray)|空の配列を生成します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|Description|
|----------|-----------------|
|[CArray:: Add](#add)|配列の末尾に要素を追加します。必要に応じて、配列を大きくします。|
|[CArray:: Append](#append)|配列に別の配列を追加します。必要に応じて配列を拡大します。|
|[CArray:: Copy](#copy)|配列に別の配列をコピーします。必要に応じて、配列を大きくします。|
|[CArray:: ElementAt](#elementat)|配列内の要素ポインターへの一時的な参照を返します。|
|[CArray:: FreeExtra](#freeextra)|現在の上限を超えている未使用のメモリをすべて解放します。|
|[CArray:: GetAt](#getat)|指定されたインデックス位置にある値を返します。|
|[CArray:: GetCount](#getcount)|この配列内の要素の数を取得します。|
|[CArray:: GetData](#getdata)|配列内の要素へのアクセスを許可します。 NULL にすることができます。|
|[CArray:: GetSize](#getsize)|この配列内の要素の数を取得します。|
|[CArray:: System.array.getupperbound](#getupperbound)|有効な最大のインデックスを返します。|
|[CArray:: InsertAt](#insertat)|指定されたインデックス位置に要素 (または別の配列内のすべての要素) を挿入します。|
|[CArray:: IsEmpty](#isempty)|配列が空かどうかを判断します。|
|[CArray:: RemoveAll](#removeall)|この配列からすべての要素を削除します。|
|[CArray:: RemoveAt](#removeat)|特定のインデックス位置にある要素を削除します。|
|[CArray:: SetAt](#setat)|指定されたインデックスの値を設定します。配列は大きくできません。|
|[CArray:: SetAtGrow](#setatgrow)|指定されたインデックスの値を設定します。必要に応じて、配列を大きくします。|
|[CArray:: SetSize](#setsize)|この配列に含まれる要素の数を設定します。|

### <a name="public-operators"></a>パブリック演算子

|Name|Description|
|----------|-----------------|
|[operator&#91;&#93;](#operator_at)|指定されたインデックス位置にある要素を設定または取得します。|

## <a name="remarks"></a>解説

配列インデックスは、常に0の位置から開始します。 現在の境界を越えて要素を追加するときに、上限を修正するか、配列を拡張するかを決定できます。 一部の要素が null であっても、メモリは上限に連続して割り当てられます。

> [!NOTE]
>  `CArray` オブジェクトのサイズを変更したり、要素を追加したりするほとんどのメソッドは、 [memcpy_s](../../c-runtime-library/reference/memcpy-s-wmemcpy-s.md)を使用して要素を移動します。 `memcpy_s` は、コンストラクターを呼び出す必要があるどのオブジェクトとも互換性がないため、この問題が発生します。 `CArray` 内の項目が `memcpy_s`と互換性がない場合は、適切なサイズの新しい `CArray` を作成する必要があります。 [CArray:: Copy](#copy)と[CArray:: SetAt](#setat)を使用して新しい配列にデータを設定する必要があります。これらのメソッドでは `memcpy_s`の代わりに代入演算子が使用されるためです。

C 配列の場合と同様に、`CArray` のインデックス付き要素のアクセス時間は定数であり、配列のサイズとは無関係です。

> [!TIP]
>  配列を使用する前に、 [SetSize](#setsize)を使用してサイズを設定し、メモリを割り当てます。 `SetSize` を使用しない場合、配列に要素を追加すると、配列の再割り当てとコピーが頻繁に発生します。 頻繁な再割り当てとコピーは非効率であり、メモリが断片化される可能性があります。

配列内の個々の要素のダンプが必要な場合は、 [CDumpContext](../../mfc/reference/cdumpcontext-class.md)オブジェクトの深さを1以上に設定する必要があります。

このクラスの特定のメンバー関数は、`CArray` クラスのほとんどの用途に合わせてカスタマイズする必要があるグローバルヘルパー関数を呼び出します。 「MFC マクロとグローバルセクション」の「[コレクションクラスヘルパー](../../mfc/reference/collection-class-helpers.md) 」を参照してください。

配列クラスの派生は、リストの派生に似ています。

`CArray`の使用方法の詳細については、「[コレクション](../../mfc/collections.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CArray`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxtempl.h

##  <a name="add"></a>CArray:: Add

配列の末尾に新しい要素を追加し、配列を1だけ拡大します。

```
INT_PTR Add(ARG_TYPE newElement);
```

### <a name="parameters"></a>パラメーター

*ARG_TYPE*<br/>
この配列内の要素を参照する引数の型を指定するテンプレートパラメーター。

*(Newelement*<br/>
この配列に追加する要素。

### <a name="return-value"></a>戻り値

追加された要素のインデックス。

### <a name="remarks"></a>解説

`nGrowBy` 値が1より大きい場合に[SetSize](#setsize)が使用されていると、余分なメモリが割り当てられる可能性があります。 ただし、上限は1だけ増加します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#22](../../mfc/codesnippet/cpp/carray-class_1.cpp)]

##  <a name="append"></a>CArray:: Append

ある配列の内容を別の配列の末尾に追加するには、このメンバー関数を呼び出します。

```
INT_PTR Append(const CArray& src);
```

### <a name="parameters"></a>パラメーター

*src*<br/>
配列に追加する要素のソース。

### <a name="return-value"></a>戻り値

追加された最初の要素のインデックス。

### <a name="remarks"></a>解説

配列は同じ型である必要があります。

必要に応じて、`Append` は、配列に追加された要素を格納するために追加のメモリを割り当てることができます。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#23](../../mfc/codesnippet/cpp/carray-class_2.cpp)]

##  <a name="carray"></a>CArray:: CArray

空の配列を生成します。

```
CArray();
```

### <a name="remarks"></a>解説

配列は、一度に1つの要素を拡張します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#24](../../mfc/codesnippet/cpp/carray-class_3.cpp)]

##  <a name="copy"></a>CArray:: Copy

1つの配列の要素を別の配列にコピーするには、このメンバー関数を使用します。

```
void Copy(const CArray& src);
```

### <a name="parameters"></a>パラメーター

*src*<br/>
配列にコピーされる要素のソース。

### <a name="remarks"></a>解説

1つの配列の要素を別の配列の要素で上書きするには、このメンバー関数を呼び出します。

`Copy` はメモリを解放しません。ただし、必要に応じて、`Copy` は配列にコピーされた要素を格納するために追加のメモリを割り当てることがあります。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#25](../../mfc/codesnippet/cpp/carray-class_4.cpp)]

##  <a name="elementat"></a>CArray:: ElementAt

配列内の指定された要素への一時的な参照を返します。

```
TYPE& ElementAt(INT_PTR nIndex);
const TYPE& ElementAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
[System.array.getupperbound](#getupperbound)によって返される値以下で、0以上の整数インデックス。この値を超えています。

### <a name="return-value"></a>戻り値

配列要素への参照。

### <a name="remarks"></a>解説

これは、配列の左側の代入演算子を実装するために使用されます。

### <a name="example"></a>例

  [GetSize](#getsize)の例を参照してください。

##  <a name="freeextra"></a>CArray:: FreeExtra

配列が拡張されたときに割り当てられた余分なメモリを解放します。

```
void FreeExtra();
```

### <a name="remarks"></a>解説

この関数は、配列のサイズや上限には影響しません。

### <a name="example"></a>例

  [GetData](#getdata)の例を参照してください。

##  <a name="getat"></a>CArray:: GetAt

指定したインデックス位置にある配列要素を返します。

```
TYPE& GetAt(INT_PTR nIndex);
const TYPE& GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>パラメーター

*TYPE*<br/>
配列要素の型を指定するテンプレートパラメーター。

*nIndex*<br/>
[System.array.getupperbound](#getupperbound)によって返される値以下で、0以上の整数インデックス。この値を超えています。

### <a name="return-value"></a>戻り値

現在このインデックス位置にある配列要素。

### <a name="remarks"></a>解説

`GetUpperBound` によって返された値よりも負の値または値を超える値を渡すと、アサーションは失敗します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#26](../../mfc/codesnippet/cpp/carray-class_5.cpp)]

##  <a name="getcount"></a>CArray:: GetCount

配列要素の数を返します。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>戻り値

配列内の項目の数。

### <a name="remarks"></a>解説

配列内の要素の数を取得するには、このメソッドを呼び出します。 インデックスは0から始まるため、サイズは最大のインデックスよりも1大きい値になります。 このメソッドを呼び出すと、 [CArray:: GetSize](#getsize)メソッドと同じ結果が生成されます。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#27](../../mfc/codesnippet/cpp/carray-class_6.cpp)]

##  <a name="getdata"></a>CArray:: GetData

配列内の要素に直接アクセスするには、このメンバー関数を使用します。

```
const TYPE* GetData() const;
TYPE* GetData();
```

### <a name="parameters"></a>パラメーター

*TYPE*<br/>
配列要素の型を指定するテンプレートパラメーター。

### <a name="return-value"></a>戻り値

配列要素へのポインター。

### <a name="remarks"></a>解説

使用できる要素がない場合、`GetData` は null 値を返します。

配列の要素に直接アクセスして、より迅速に作業を行うことができますが、`GetData`を呼び出すときは注意が必要です。このようなエラーは、配列の要素に直接影響します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#28](../../mfc/codesnippet/cpp/carray-class_7.cpp)]

##  <a name="getsize"></a>CArray:: GetSize

配列のサイズを返します。

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>解説

インデックスは0から始まるため、サイズは最大のインデックスよりも1大きい値になります。 このメソッドを呼び出すと、 [CArray:: GetCount](#getcount)メソッドと同じ結果が生成されます。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#29](../../mfc/codesnippet/cpp/carray-class_8.cpp)]

##  <a name="getupperbound"></a>CArray:: System.array.getupperbound

この配列の現在の上限を返します。

```
INT_PTR GetUpperBound() const;
```

### <a name="remarks"></a>解説

配列インデックスは0から始まるため、この関数は `GetSize`未満の値1を返します。

条件 `GetUpperBound( )` =-1 は、配列に要素が含まれていないことを示します。

### <a name="example"></a>例

  [CArray:: GetAt](#getat)の例を参照してください。

##  <a name="insertat"></a>CArray:: InsertAt

最初のバージョンの `InsertAt` は、配列内の指定したインデックス位置に1つの要素 (または要素の複数のコピー) を挿入します。

```
void InsertAt(
    INT_PTR nIndex,
    ARG_TYPE newElement,
    INT_PTR nCount = 1);

void InsertAt(
    INT_PTR nStartIndex,
    CArray* pNewArray);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
`GetUpperBound`によって返された値よりも大きい可能性のある整数インデックス。

*ARG_TYPE*<br/>
この配列内の要素の型を指定するテンプレートパラメーター。

*(Newelement*<br/>
この配列に配置される要素。

*nCount*<br/>
この要素を挿入する回数 (既定値は 1)。

*nStartIndex*<br/>
[System.array.getupperbound](#getupperbound)によって返される値よりも大きい可能性のある整数インデックス。

*pNewArray*<br/>
この配列に追加する要素を格納している別の配列。

### <a name="remarks"></a>解説

このプロセスでは、このインデックスの既存の要素を (インデックスのインクリメントによって) シフトアップし、その上にあるすべての要素をシフトアップします。

2番目のバージョンでは、 *Nstartindex*位置から開始して、別の `CArray` コレクションのすべての要素を挿入します。

これに対し、`SetAt` 関数は、指定された1つの配列要素を置き換え、要素をシフトしません。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#30](../../mfc/codesnippet/cpp/carray-class_9.cpp)]

##  <a name="isempty"></a>CArray:: IsEmpty

配列が空かどうかを判断します。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>戻り値

配列に要素が含まれていない場合は0以外の。それ以外の場合は0です。

##  <a name="operator_at"></a>CArray:: operator \[\]

これらの添字演算子は、 [SetAt](#setat)関数と[GetAt](#getat)関数に代わる便利な方法です。

```
TYPE& operator[](int_ptr nindex);
const TYPE& operator[](int_ptr nindex) const;
```

### <a name="parameters"></a>パラメーター

*TYPE*<br/>
この配列内の要素の型を指定するテンプレートパラメーター。

*nIndex*<br/>
アクセスされる要素のインデックス。

### <a name="remarks"></a>解説

**Const**でない配列に対して呼び出される最初の演算子は、代入ステートメントの right (右辺値) または left (左辺値) のいずれかで使用できます。 **Const**配列に対して呼び出される2番目のは、右側でのみ使用できます。

ライブラリのデバッグバージョンは、添字 (代入ステートメントの左側または右側) が範囲外である場合にアサートします。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#34](../../mfc/codesnippet/cpp/carray-class_10.cpp)]

##  <a name="relocateelements"></a>CArray:: RelocateElements

配列が拡大または縮小されるときに、新しいバッファーにデータを再配置します。

```
template<class TYPE, class ARG_TYPE>
AFX_INLINE void CArray<TYPE, ARG_TYPE>::RelocateElements(
    TYPE* pNewData,
    const TYPE* pData,
    INT_PTR nCount);
```

### <a name="parameters"></a>パラメーター

*pNewData*<br/>
要素の配列の新しいバッファー。

*pData*<br/>
要素の古い配列。

*nCount*<br/>
古い配列内の要素の数。

### <a name="remarks"></a>解説

*pNewData*は常に、すべての*pData*要素を保持するのに十分な大きさです。

[CArray](../../mfc/reference/carray-class.md)の実装では、このメソッドを使用して、配列が拡大または縮小するときに古いデータを新しいバッファーにコピーします ( [SetSize](#setsize)または[freeextra](#freeextra)が呼び出された場合)。 既定の実装では、データのみがコピーされます。

要素に独自のメンバーの1つへのポインターが含まれているか、または別の構造体に配列要素の1つへのポインターが含まれている配列の場合、ポインターはプレーンコピーで更新されません。 この場合は、関連する型を使用して `RelocateElements` の特殊化を実装することによって、ポインターを修正できます。 また、データのコピーも行います。

##  <a name="removeall"></a>CArray:: RemoveAll

この配列からすべての要素を削除します。

```
void RemoveAll();
```

### <a name="remarks"></a>解説

配列が既に空の場合、関数は引き続き機能します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#31](../../mfc/codesnippet/cpp/carray-class_11.cpp)]

##  <a name="removeat"></a>CArray:: RemoveAt

配列内の指定したインデックスを開始位置として、1つ以上の要素を削除します。

```
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
[System.array.getupperbound](#getupperbound)によって返される値以下で、0以上の整数インデックス。この値を超えています。

*nCount*<br/>
削除する要素の数を指定します。

### <a name="remarks"></a>解説

プロセスでは、削除された要素の上にあるすべての要素を下へ移動します。 配列の上限をデクリメントしますが、メモリは解放されません。

削除ポイントの上の配列に含まれているよりも多くの要素を削除しようとすると、ライブラリのデバッグバージョンがアサートされます。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#32](../../mfc/codesnippet/cpp/carray-class_12.cpp)]

##  <a name="setat"></a>CArray:: SetAt

指定したインデックス位置に配列要素を設定します。

```
void SetAt(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
[System.array.getupperbound](#getupperbound)によって返される値以下で、0以上の整数インデックス。この値を超えています。

*ARG_TYPE*<br/>
配列要素を参照するために使用される引数の型を指定するテンプレートパラメーター。

*(Newelement*<br/>
指定した位置に格納される新しい要素の値。

### <a name="remarks"></a>解説

`SetAt` によって配列が拡張されることはありません。 配列が自動的に拡張されるようにする場合は、 [SetAtGrow](#setatgrow)を使用します。

インデックス値が配列内の有効な位置を表していることを確認する必要があります。 範囲外の場合は、ライブラリのデバッグバージョンがアサートされます。

### <a name="example"></a>例

  [GetAt](#getat)の例を参照してください。

##  <a name="setatgrow"></a>CArray:: SetAtGrow

指定したインデックス位置に配列要素を設定します。

```
void SetAtGrow(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
0以上の整数のインデックスです。

*ARG_TYPE*<br/>
配列内の要素の型を指定するテンプレートパラメーター。

*(Newelement*<br/>
この配列に追加する要素。 NULL 値が許可されます。

### <a name="remarks"></a>解説

必要に応じて配列が自動的に拡張されます (つまり、新しい要素に合わせて上限が調整されます)。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#33](../../mfc/codesnippet/cpp/carray-class_13.cpp)]

##  <a name="setsize"></a>CArray:: SetSize

空または既存の配列のサイズを設定します。必要に応じてメモリを割り当てます。

```
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>パラメーター

*nNewSize*<br/>
新しい配列のサイズ (要素の数)。 0 以上にする必要があります。

*nGrowBy*<br/>
サイズの増加が必要な場合に割り当てる要素スロットの最小数。

### <a name="remarks"></a>解説

新しいサイズが古いサイズより小さい場合は、配列が切り捨てられ、未使用のメモリがすべて解放されます。

配列の使用を開始する前に、この関数を使用して配列のサイズを設定します。 `SetSize` を使用しない場合、配列に要素を追加すると、配列の再割り当てとコピーが頻繁に発生します。 頻繁な再割り当てとコピーは非効率であり、メモリが断片化される可能性があります。

*Ngrowby*パラメーターは、配列が拡大している間の内部メモリの割り当てに影響します。 その使用は、 [GetSize](#getsize)および[system.array.getupperbound](#getupperbound)によって報告された配列のサイズには影響しません。 既定値が使用されている場合は、メモリの断片化を回避し、ほとんどの場合に効率を最適化するために、MFC によって計算された方法でメモリが割り当てられます。

### <a name="example"></a>例

  [GetData](#getdata)の例を参照してください。

## <a name="see-also"></a>参照

[MFC サンプル収集](../../overview/visual-cpp-samples.md)<br/>
[CObject クラス](../../mfc/reference/cobject-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CObArray クラス](../../mfc/reference/cobarray-class.md)<br/>
[コレクション クラスのヘルパー](../../mfc/reference/collection-class-helpers.md)
