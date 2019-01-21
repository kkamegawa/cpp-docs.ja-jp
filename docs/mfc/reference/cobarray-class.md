---
title: CObArray クラス
ms.date: 11/04/2016
f1_keywords:
- CObArray
- AFXCOLL/CObArray
- AFXCOLL/CObArray::CObArray
- AFXCOLL/CObArray::Add
- AFXCOLL/CObArray::Append
- AFXCOLL/CObArray::Copy
- AFXCOLL/CObArray::ElementAt
- AFXCOLL/CObArray::FreeExtra
- AFXCOLL/CObArray::GetAt
- AFXCOLL/CObArray::GetCount
- AFXCOLL/CObArray::GetData
- AFXCOLL/CObArray::GetSize
- AFXCOLL/CObArray::GetUpperBound
- AFXCOLL/CObArray::InsertAt
- AFXCOLL/CObArray::IsEmpty
- AFXCOLL/CObArray::RemoveAll
- AFXCOLL/CObArray::RemoveAt
- AFXCOLL/CObArray::SetAt
- AFXCOLL/CObArray::SetAtGrow
- AFXCOLL/CObArray::SetSize
helpviewer_keywords:
- CObArray [MFC], CObArray
- CObArray [MFC], Add
- CObArray [MFC], Append
- CObArray [MFC], Copy
- CObArray [MFC], ElementAt
- CObArray [MFC], FreeExtra
- CObArray [MFC], GetAt
- CObArray [MFC], GetCount
- CObArray [MFC], GetData
- CObArray [MFC], GetSize
- CObArray [MFC], GetUpperBound
- CObArray [MFC], InsertAt
- CObArray [MFC], IsEmpty
- CObArray [MFC], RemoveAll
- CObArray [MFC], RemoveAt
- CObArray [MFC], SetAt
- CObArray [MFC], SetAtGrow
- CObArray [MFC], SetSize
ms.assetid: 27894efd-2370-4776-9ed9-24a98492af17
ms.openlocfilehash: 031f163a5a4b5663b296dc6615712fe7dd5dbc56
ms.sourcegitcommit: 53f75afaf3c0b3ed481c5503357ed2b7b87aac6d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53657605"
---
# <a name="cobarray-class"></a>CObArray クラス

`CObject` ポインターの配列をサポートします。

## <a name="syntax"></a>構文

```
class CObArray : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CObArray::CObArray](#cobarray)|空の配列を構築`CObject`ポインター。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CObArray::Add](#add)|配列の末尾に要素を追加します。必要に応じて、配列を大きくします。|
|[CObArray::Append](#append)|配列に別の配列を追加します。必要に応じて、配列を大きくします。|
|[CObArray::Copy](#copy)|配列に別の配列をコピーします。必要に応じて、配列を大きくします。|
|[CObArray::ElementAt](#elementat)|配列内の要素ポインターへの一時的な参照を返します。|
|[CObArray::FreeExtra](#freeextra)|現在の上限を超えている未使用のメモリをすべて解放します。|
|[CObArray::GetAt](#getat)|指定されたインデックス位置にある値を返します。|
|[CObArray::GetCount](#getcount)|この配列内の要素の数を取得します。|
|[CObArray::GetData](#getdata)|配列内の要素へのアクセスを許可します。 NULL にすることができます。|
|[CObArray::GetSize](#getsize)|この配列内の要素の数を取得します。|
|[CObArray::GetUpperBound](#getupperbound)|有効な最大のインデックスを返します。|
|[CObArray::InsertAt](#insertat)|指定されたインデックス位置に要素 (または別の配列内のすべての要素) を挿入します。|
|[CObArray::IsEmpty](#isempty)|配列が空かどうかを判別します。|
|[CObArray::RemoveAll](#removeall)|この配列からすべての要素を削除します。|
|[CObArray::RemoveAt](#removeat)|特定のインデックス位置にある要素を削除します。|
|[CObArray::SetAt](#setat)|指定されたインデックスの値を設定します。配列は大きくできません。|
|[CObArray::SetAtGrow](#setatgrow)|指定されたインデックスの値を設定します。必要に応じて、配列を大きくします。|
|[CObArray::SetSize](#setsize)|この配列に含まれる要素の数を設定します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CObArray::operator \[ \]](#operator_at)|指定されたインデックス位置にある要素を設定または取得します。|

## <a name="remarks"></a>Remarks

これらのオブジェクトの配列は c 言語の配列に似ていますが、動的に縮小し、必要に応じて大きくなります。

配列のインデックスは、常に、位置 0 から開始します。 上限の境界を修正するか、過去の現在のバインド要素を追加するときに展開先の配列を許可するかどうかを決定できます。 メモリでは、いくつかの要素が null の場合でも、上限が連続的に割り当てられます。

Win32 でのサイズ、`CObArray`オブジェクトが使用可能なメモリのみに制限されています。

C 言語の配列では、アクセスする時間と同様、`CObArray`が定数であり、配列のサイズに依存しないインデックス付けされた要素。

`CObArray` シリアル化とその要素のダンプをサポートするために IMPLEMENT_SERIAL マクロが組み込まれています。 配列の場合`CObject`ポインターがオーバー ロードされた挿入演算子を使用するかでアーカイブに格納されている、`Serialize`メンバー関数は、各`CObject`要素は、その配列のインデックスと共に、シリアル化します。

個別にダンプする必要がある場合`CObject`配列内の要素の深さを設定する必要があります、`CDumpContext`を 1 以上のオブジェクト。

ときに、`CObArray`オブジェクトを削除すると、またはときにその要素は削除のみ、`CObject`ポインターを削除すると、参照するオブジェクトではありません。

> [!NOTE]
>  配列を使用する前に、`SetSize` を使用してそのサイズを設定し、メモリを割り当てます。 `SetSize` を使用しない場合、配列に要素を追加すると、配列の再割り当てとコピーが頻繁に発生します。 頻繁な再割り当てとコピーは非効率であり、メモリが断片化される可能性があります。

配列クラスの派生は、リストの派生に似ています。 詳細については、特殊なリスト クラスの派生は、記事を参照してください。[コレクション](../../mfc/collections.md)します。

> [!NOTE]
>  配列をシリアル化する場合は、派生クラスの実装で IMPLEMENT_SERIAL マクロを使用する必要があります。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CObArray`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxcoll.h

##  <a name="add"></a>  CObArray::Add

配列を 1 つの拡張、配列の末尾に新しい要素を追加します。

```
INT_PTR Add(CObject* newElement);
```

### <a name="parameters"></a>パラメーター

*newElement*<br/>
`CObject`この配列に追加するポインター。

### <a name="return-value"></a>戻り値

追加された要素のインデックス。

### <a name="remarks"></a>Remarks

場合[SetSize](#setsize)で使用されている、 *nGrowBy* 1、余分なメモリより大きい値を割り当てることができます。 ただし、上限は、1 つだけ高くなります。

次の表はその他のメンバー関数に似ている`CObArray::Add`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR の追加 (バイト** `newElement` **)。**<br /><br /> **スロー (CMemoryException\* )。**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR の追加 (DWORD** `newElement` **)。**<br /><br /> **スロー (CMemoryException\* )。**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR の追加 (void** <strong>\*</strong> `newElement` **)。**<br /><br /> **スロー (CMemoryException\* )。**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR の追加 (LPCTSTR** `newElement` **); スロー (CMemoryException\* )。**<br /><br /> **INT_PTR Add(const CString&** `newElement` **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR の追加 (UINT** `newElement` **)。**<br /><br /> **スロー (CMemoryException\* )。**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR の追加 (WORD** `newElement` **)。**<br /><br /> **スロー (CMemoryException\* )。**|

### <a name="example"></a>例

  参照してください[使われて](../../mfc/reference/coblist-class.md#coblist)の一覧については、`CAge`コレクションのすべての例で使用されるクラス。

[!code-cpp[NVC_MFCCollections#75](../../mfc/codesnippet/cpp/cobarray-class_1.cpp)]

このプログラムからの結果は次のとおりです。

```Output
Add example: A CObArray with 2 elements
[0] = a CAge at $442A 21
[1] = a CAge at $4468 40
```

##  <a name="append"></a>  CObArray::Append

指定された配列の末尾に別の配列の内容を追加するには、このメンバー関数を呼び出します。

```
INT_PTR Append(const CObArray& src);
```

### <a name="parameters"></a>パラメーター

*src*<br/>
配列に追加する要素のソースです。

### <a name="return-value"></a>戻り値

追加された最初の要素のインデックス。

### <a name="remarks"></a>Remarks

配列は同じ型でなければなりません。

必要に応じて、`Append`配列に追加された要素に対応するために余分なメモリを割り当てることができます。

次の表はその他のメンバー関数に似ている`CObArray::Append`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR の追加 (const CByteArray &** *src* **)。**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR の追加 (const CDWordArray &** *src* **)。**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR の追加 (const CPtrArray &** *src* **)。**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR の追加 (const CStringArray &** *src* **)。**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR の追加 (const CUIntArray &** *src* **)。**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR の追加 (const CWordArray &** *src* **)。**|

### <a name="example"></a>例

参照してください[使われて](../../mfc/reference/coblist-class.md#coblist)の一覧については、`CAge`コレクションのすべての例で使用されるクラス。

[!code-cpp[NVC_MFCCollections#76](../../mfc/codesnippet/cpp/cobarray-class_2.cpp)]

##  <a name="copy"></a>  CObArray::Copy

同じ型の別の配列の要素で指定された配列の要素を上書きするには、このメンバー関数を呼び出します。

```
void Copy(const CObArray& src);
```

### <a name="parameters"></a>パラメーター

*src*<br/>
配列にコピーする要素のソースです。

### <a name="remarks"></a>Remarks

`Copy` メモリを解放しませんただし、必要に応じて`Copy`配列にコピーされた要素に対応するために余分なメモリを割り当てることができます。

次の表はその他のメンバー関数に似ている`CObArray::Copy`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**コピーを無効にする (const CByteArray &** *src* **)。**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**コピーを無効にする (const CDWordArray &** *src* **)。**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**コピーを無効にする (const CPtrArray &** *src* **)。**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**コピーを無効にする (const CStringArray &** *src* **)。**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**コピーを無効にする (const CUIntArray &** *src* **)。**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**コピーを無効にする (const CWordArray &** *src* **)。**|

### <a name="example"></a>例

参照してください[使われて](../../mfc/reference/coblist-class.md#coblist)の一覧については、`CAge`コレクションのすべての例で使用されるクラス。

[!code-cpp[NVC_MFCCollections#77](../../mfc/codesnippet/cpp/cobarray-class_3.cpp)]

##  <a name="cobarray"></a>  CObArray::CObArray

空の構築`CObject`ポインターの配列。

```
CObArray();
```

### <a name="remarks"></a>Remarks

配列は、一度に 1 つの要素を拡張します。

次の表に、他のコンス トラクターに似ている`CObArray::CObArray`します。

|クラス|コンストラクター|
|-----------|-----------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**CByteArray ();**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**CDWordArray ();**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**CPtrArray ();**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CStringArray ();**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**CUIntArray ();**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**CWordArray ();**|

### <a name="example"></a>例

[!code-cpp[NVC_MFCCollections#78](../../mfc/codesnippet/cpp/cobarray-class_4.cpp)]

##  <a name="elementat"></a>  CObArray::ElementAt

配列内の要素ポインターへの一時的な参照を返します。

```
CObject*& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
0 以上である整数インデックスによって返される値以下`GetUpperBound`します。

### <a name="return-value"></a>戻り値

参照を`CObject`ポインター。

### <a name="remarks"></a>Remarks

配列の左側の代入演算子を実装するために使用されます。 これは、特殊な配列の演算子を実装するためだけに使用する必要があります高度な関数であることに注意してください。

次の表はその他のメンバー関数に似ている`CObArray::ElementAt`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**バイト & ElementAt (INT_PTR** `nIndex` **)。**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD & ElementAt (INT_PTR** `nIndex` **)。**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void\*& ElementAt (INT_PTR** `nIndex` **)。**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString & ElementAt (INT_PTR** `nIndex` **)。**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT & ElementAt (INT_PTR** `nIndex` **)。**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD & ElementAt (INT_PTR** `nIndex` **)。**|

### <a name="example"></a>例

  例をご覧ください[CObArray::GetSize](#getsize)します。

##  <a name="freeextra"></a>  CObArray::FreeExtra

配列が拡張されたときに割り当てられたすべての余分なメモリを解放します。

```
void FreeExtra();
```

### <a name="remarks"></a>Remarks

この関数は、サイズまたは配列の上限に影響を与えません。

次の表はその他のメンバー関数に似ている`CObArray::FreeExtra`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void FreeExtra ();**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void FreeExtra ();**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void FreeExtra ();**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void FreeExtra ();**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void FreeExtra ();**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void FreeExtra ();**|

### <a name="example"></a>例

  例をご覧ください[CObArray::GetData](#getdata)します。

##  <a name="getat"></a>  CObArray::GetAt

指定したインデックス位置にある配列要素を返します。

```
CObject* GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
0 以上である整数インデックスによって返される値以下`GetUpperBound`します。

### <a name="return-value"></a>戻り値

`CObject`ポインターの要素を指定したインデックス位置。

### <a name="remarks"></a>Remarks

> [!NOTE]
>  によって返される値より大きい負の値または値を渡す`GetUpperBound`アサーションは失敗になります。

次の表はその他のメンバー関数に似ている`CObArray::GetAt`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**バイト GetAt (INT_PTR** `nIndex` **) const です。**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD GetAt (INT_PTR** `nIndex` **) const です。**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void\* GetAt (INT_PTR** `nIndex` **) const です。**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString GetAt (INT_PTR** `nIndex` **) const です。**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT GetAt (INT_PTR** `nIndex` **) const です。**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD GetAt (INT_PTR** `nIndex` **) const です。**|

### <a name="example"></a>例

参照してください[使われて](../../mfc/reference/coblist-class.md#coblist)の一覧については、`CAge`コレクションのすべての例で使用されるクラス。

[!code-cpp[NVC_MFCCollections#79](../../mfc/codesnippet/cpp/cobarray-class_5.cpp)]

##  <a name="getcount"></a>  CObArray::GetCount

配列要素の数を返します。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>戻り値

配列内の項目の数。

### <a name="remarks"></a>Remarks

配列内の要素の数を取得するには、このメソッドを呼び出します。 インデックスが 0 から始まるので、サイズは、インデックスの最大値より大きい 1 になります。

次の表はその他のメンバー関数に似ている`CObArray::GetCount`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**Const; INT_PTR GetCount)**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**Const; INT_PTR GetCount)**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**Const; INT_PTR GetCount)**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Const; INT_PTR GetCount)**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**Const; INT_PTR GetCount)**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**Const; INT_PTR GetCount)**|

### <a name="example"></a>例

参照してください[使われて](../../mfc/reference/coblist-class.md#coblist)の一覧については、`CAge`コレクションのすべての例で使用されるクラス。

[!code-cpp[NVC_MFCCollections#80](../../mfc/codesnippet/cpp/cobarray-class_6.cpp)]

##  <a name="getdata"></a>  CObArray::GetData

配列内の要素に直接アクセスするのにには、このメンバー関数を使用します。

```
const CObject** GetData() const;

CObject** GetData();
```

### <a name="return-value"></a>戻り値

配列へのポインター`CObject`ポインター。

### <a name="remarks"></a>Remarks

要素がない場合、 `GetData` null 値を返します。

呼び出すときに注意を使用して、配列の要素への直接アクセスより早く作業する際に役立つ、 `GetData`; 直接行ったすべてのエラーが、配列の要素に影響します。

次の表はその他のメンバー関数に似ている`CObArray::GetData`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**const バイト\*const; GetData)バイト\*GetData ();**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**const DWORD\* GetData const (); DWORD\* GetData ();**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**const void\* \* GetData () const; void\* \* GetData ();**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**const CString\* const; GetData)CString\* GetData ();**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**const UINT\* const; GetData)UINT\* GetData ();**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**const WORD\* const; GetData)WORD\* GetData ();**|

### <a name="example"></a>例

参照してください[使われて](../../mfc/reference/coblist-class.md#coblist)の一覧については、`CAge`コレクションのすべての例で使用されるクラス。

[!code-cpp[NVC_MFCCollections#81](../../mfc/codesnippet/cpp/cobarray-class_7.cpp)]

##  <a name="getsize"></a>  CObArray::GetSize

配列のサイズを返します。

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>Remarks

インデックスが 0 から始まるために、サイズは、インデックスの最大値より大きい 1 になります。

次の表はその他のメンバー関数に似ている`CObArray::GetSize`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**Const; INT_PTR GetSize)**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**Const; INT_PTR GetSize)**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**Const; INT_PTR GetSize)**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Const; INT_PTR GetSize)**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**Const; INT_PTR GetSize)**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**Const; INT_PTR GetSize)**|

### <a name="example"></a>例

参照してください[使われて](../../mfc/reference/coblist-class.md#coblist)の一覧については、`CAge`コレクションのすべての例で使用されるクラス。

[!code-cpp[NVC_MFCCollections#82](../../mfc/codesnippet/cpp/cobarray-class_8.cpp)]

##  <a name="getupperbound"></a>  CObArray::GetUpperBound

この配列の現在の上限を返します。

```
INT_PTR GetUpperBound() const;
```

### <a name="return-value"></a>戻り値

上限 (0 から始まる) インデックス。

### <a name="remarks"></a>Remarks

配列のインデックスが 0 から始まるので、この関数は値 1 を返しますより小さい`GetSize`します。

条件`GetUpperBound( )`=-1 は、配列に要素が含まれていないことを示します。

次の表はその他のメンバー関数に似ている`CObArray::GetUpperBound`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**Const; INT_PTR です)**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**Const; INT_PTR です)**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**Const; INT_PTR です)**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Const; INT_PTR です)**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**Const; INT_PTR です)**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**Const; INT_PTR です)**|

### <a name="example"></a>例

参照してください[使われて](../../mfc/reference/coblist-class.md#coblist)の一覧については、`CAge`コレクションのすべての例で使用されるクラス。

[!code-cpp[NVC_MFCCollections#83](../../mfc/codesnippet/cpp/cobarray-class_9.cpp)]

##  <a name="insertat"></a>  CObArray::InsertAt

指定されたインデックス位置に要素 (または別の配列内のすべての要素) を挿入します。

```
void InsertAt(
    INT_PTR nIndex,
    CObject* newElement,
    INT_PTR nCount = 1);

void InsertAt(
    INT_PTR nStartIndex,
    CObArray* pNewArray);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
によって返される値よりも大きい可能性がある整数インデックス`GetUpperBound`します。

*newElement*<br/>
`CObject`この配列に配置するへのポインター。 A *newElement*値の NULL は許可されます。

*nCount*<br/>
(既定値は 1) を挿入する回数がこの要素にする必要があります。

*nStartIndex*<br/>
によって返される値よりも大きい可能性がある整数インデックス`GetUpperBound`します。

*pNewArray*<br/>
この配列に追加する要素を含む別の配列。

### <a name="remarks"></a>Remarks

最初のバージョンの`InsertAt`配列内の指定したインデックス位置にある 1 つの要素 (または要素の複数のコピー) を挿入します。 移動、処理で、上のすべての要素をシフトして、このインデックスにある既存の要素 (増分することで、インデックス)。

2 番目のバージョンから別のすべての要素の挿入`CObArray`開始位置として、コレクション、 *nStartIndex*位置。

`SetAt`関数、これに対し、1 つの指定した配列の要素し、すべての要素を移動しません。

次の表はその他のメンバー関数に似ている`CObArray::InsertAt`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void InsertAt (INT_PTR** `nIndex` **、バイト** `newElement` **、int** `nCount` **= 1)。**<br /><br /> **スロー (CMemoryException\* )。**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **、CByteArray** <strong>\*</strong> `pNewArray` **)。**<br /><br /> **スロー (CMemoryException\* )。**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **、DWORD** `newElement` **、int** `nCount` **= 1)。**<br /><br /> **スロー (CMemoryException\* )。**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **、CDWordArray** <strong>\*</strong> `pNewArray` **)。**<br /><br /> **スロー (CMemoryException\* )。**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, void** <strong>\*</strong> `newElement` **、int** `nCount` **= 1)。**<br /><br /> **スロー (CMemoryException\* )。**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **、CPtrArray** <strong>\*</strong> `pNewArray` **)。**<br /><br /> **スロー (CMemoryException\* )。**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **、LPCTSTR** `newElement` **、int** `nCount` **= 1)。**<br /><br /> **スロー (CMemoryException\* )。**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **、CStringArray** <strong>\*</strong> `pNewArray` **)。**<br /><br /> **スロー (CMemoryException\* )。**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **、UINT** `newElement` **、int** `nCount` **= 1)。**<br /><br /> **スロー (CMemoryException\* )。**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **、CUIntArray** <strong>\*</strong> `pNewArray` **)。**<br /><br /> **スロー (CMemoryException\* )。**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **、WORD** `newElement` **、int** `nCount` **= 1)。**<br /><br /> **スロー (CMemoryException\* )。**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **、CWordArray** <strong>\*</strong> `pNewArray` **)。**<br /><br /> **スロー (CMemoryException\* )。**|

### <a name="example"></a>例

  参照してください[使われて](../../mfc/reference/coblist-class.md#coblist)の一覧については、`CAge`コレクションのすべての例で使用されるクラス。

[!code-cpp[NVC_MFCCollections#84](../../mfc/codesnippet/cpp/cobarray-class_10.cpp)]

このプログラムからの結果は次のとおりです。

```Output
InsertAt example: A CObArray with 3 elements
[0] = a CAge at $45C8 21
[1] = a CAge at $4646 30
[2] = a CAge at $4606 40
```

##  <a name="isempty"></a>  CObArray::IsEmpty

配列が空かどうかを判別します。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>戻り値

配列が空である場合、0 以外の場合それ以外の場合 0 を返します。

##  <a name="operator_at"></a>  CObArray::operator

これらの添字演算子は便利な代替、`SetAt`と`GetAt`関数。

```
CObject*& operator[](int_ptr nindex);
CObject* operator[](int_ptr nindex) const;
```

### <a name="remarks"></a>Remarks

示されていない配列の最初の演算子と呼ばれる**const**右 (右辺値) または代入ステートメントの左側 (左辺値) のいずれかで使用可能性があります。 2 つ目と呼ばれる**const**配列は、右側でのみ使用可能性があります。

ライブラリのデバッグ バージョンはアサート添字 (またはいずれかで、左、代入ステートメントの右側にある) が範囲外です。

次の表に、その他の演算子に類似した`CObArray::operator []`します。

|クラス|演算子|
|-----------|--------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**バイト & 演算子 (int_ptr** `nindex`  **\);**<br /><br /> **Byte[] 演算子 (int_ptr** `nindex`  **\) const です。**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD & 演算子 (int_ptr** `nindex`  **\);**<br /><br /> **DWORD 演算子 (int_ptr** `nindex`  **\) const です。**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void\*& 演算子 (int_ptr** `nindex`  **\);**<br /><br /> **void\*演算子 (int_ptr** `nindex`  **\) const です。**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString & 演算子 (int_ptr** `nindex`  **\);**<br /><br /> **CString 演算子 (int_ptr** `nindex`  **\) const です。**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT & 演算子 (int_ptr** `nindex`  **\);**<br /><br /> **UINT 演算子 (int_ptr** `nindex`  **\) const です。**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD & 演算子 (int_ptr** `nindex`  **\);**<br /><br /> **WORD 演算子 (int_ptr** `nindex`  **\) const です。**|

### <a name="example"></a>例

参照してください[使われて](../../mfc/reference/coblist-class.md#coblist)の一覧については、`CAge`コレクションのすべての例で使用されるクラス。

[!code-cpp[NVC_MFCCollections#88](../../mfc/codesnippet/cpp/cobarray-class_11.cpp)]

##  <a name="removeall"></a>  CObArray::RemoveAll

この配列からすべてのポインターを削除しますが、実際には削除されません、`CObject`オブジェクト。

```
void RemoveAll();
```

### <a name="remarks"></a>Remarks

配列が空で既に場合に、関数が機能します。

`RemoveAll`関数ポインターの記憶域に使用されるすべてのメモリを解放します。

次の表はその他のメンバー関数に似ている`CObArray::RemoveAll`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void RemoveAll( );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void RemoveAll( );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void RemoveAll( );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void RemoveAll( );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void RemoveAll( );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void RemoveAll( );**|

### <a name="example"></a>例

参照してください[使われて](../../mfc/reference/coblist-class.md#coblist)の一覧については、`CAge`コレクションのすべての例で使用されるクラス。

[!code-cpp[NVC_MFCCollections#85](../../mfc/codesnippet/cpp/cobarray-class_12.cpp)]

##  <a name="removeat"></a>  CObArray::RemoveAt

配列内の指定したインデックスから始まる 1 つまたは複数の要素を削除します。

```
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
0 以上である整数インデックスによって返される値以下`GetUpperBound`します。

*nCount*<br/>
削除する要素の数を指定します。

### <a name="remarks"></a>Remarks

プロセスで、削除された要素の上のすべての要素に移動します。 これをデクリメント上にあるが、配列のバインドしますが、メモリを解放しません。

削除のポイントの上、配列内に含まれているより多くの要素を削除しようとすると、ライブラリのデバッグ バージョンがアサートします。

`RemoveAt`関数の削除、`CObject`オブジェクト自体は削除されませんが、配列からポインター。

次の表はその他のメンバー関数に似ている`CObArray::RemoveAt`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **、INT_PTR** `nCount` **= 1)。**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **、INT_PTR** `nCount` **= 1)。**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **、INT_PTR** `nCount` **= 1)。**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **、INT_PTR** `nCount` **= 1)。**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **、INT_PTR** `nCount` **= 1)。**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **、INT_PTR** *nCount* **= 1)。**|

### <a name="example"></a>例

  参照してください[使われて](../../mfc/reference/coblist-class.md#coblist)の一覧については、`CAge`コレクションのすべての例で使用されるクラス。

[!code-cpp[NVC_MFCCollections#112](../../mfc/codesnippet/cpp/cobarray-class_13.cpp)]

このプログラムからの結果は次のとおりです。

```Output
RemoveAt example: A CObArray with 1 elements
[0] = a CAge at $4606 40
```

##  <a name="setat"></a>  CObArray::SetAt

指定したインデックス位置にある配列要素を設定します。

```
void SetAt(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
0 以上である整数インデックスによって返される値以下`GetUpperBound`します。

*newElement*<br/>
この配列に挿入するオブジェクトのポインター。 NULL 値が許可されているとします。

### <a name="remarks"></a>Remarks

`SetAt` 拡張先の配列は発生しません。 使用`SetAtGrow`する場合は自動的に拡張する配列。

インデックスの値が配列内の有効な位置を表すことを確認する必要があります。 範囲外の場合は、ライブラリのデバッグ バージョンはアサートします。

次の表はその他のメンバー関数に似ている`CObArray::SetAt`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**setat メソッドを void (INT_PTR** `nIndex` **、バイト** `newElement` **)。**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**setat メソッドを void (INT_PTR** `nIndex` **、DWORD** `newElement` **)。**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**setat メソッドを void (INT_PTR** `nIndex` **, void** <strong>\*</strong> `newElement` **)。**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**setat メソッドを void (INT_PTR** `nIndex` **、LPCTSTR** `newElement` **)。**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**setat メソッドを void (INT_PTR** `nIndex` **、UINT** `newElement` **)。**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**setat メソッドを void (INT_PTR** `nIndex` **、WORD** `newElement` **)。**|

### <a name="example"></a>例

  参照してください[使われて](../../mfc/reference/coblist-class.md#coblist)の一覧については、`CAge`コレクションのすべての例で使用されるクラス。

[!code-cpp[NVC_MFCCollections#86](../../mfc/codesnippet/cpp/cobarray-class_14.cpp)]

このプログラムからの結果は次のとおりです。

```Output
SetAt example: A CObArray with 2 elements
[0] = a CAge at $47E0 30
[1] = a CAge at $47A0 40
```

##  <a name="setatgrow"></a>  CObArray::SetAtGrow

指定したインデックス位置にある配列要素を設定します。

```
void SetAtGrow(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
0 以上である整数のインデックス。

*newElement*<br/>
この配列に追加するオブジェクトのポインター。 NULL 値が許可されているとします。

### <a name="remarks"></a>Remarks

必要な場合に、配列が自動的に大きくなる (つまりで上限は、新しい要素を対応するために調整されます)。

次の表はその他のメンバー関数に似ている`CObArray::SetAtGrow`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **、バイト** `newElement` **)。**<br /><br /> **スロー (CMemoryException\* )。**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **、DWORD** `newElement` **)。**<br /><br /> **スロー (CMemoryException\* )。**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **, void** <strong>\*</strong> `newElement` **)。**<br /><br /> **スロー (CMemoryException\* )。**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **、LPCTSTR** `newElement` **)。**<br /><br /> **スロー (CMemoryException\* )。**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **、UINT** `newElement` **)。**<br /><br /> **スロー (CMemoryException\* )。**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **、WORD** `newElement` **)。**<br /><br /> **スロー (CMemoryException\* )。**|

### <a name="example"></a>例

  参照してください[使われて](../../mfc/reference/coblist-class.md#coblist)の一覧については、`CAge`コレクションのすべての例で使用されるクラス。

[!code-cpp[NVC_MFCCollections#87](../../mfc/codesnippet/cpp/cobarray-class_15.cpp)]

このプログラムからの結果は次のとおりです。

```Output
SetAtGrow example: A CObArray with 4 elements
[0] = a CAge at $47C0 21
[1] = a CAge at $4800 40
[2] = NULL
[3] = a CAge at $4840 65
```

##  <a name="setsize"></a>  CObArray::SetSize

は空または既存の配列のサイズを設定します必要な場合は、メモリを割り当てます。

```
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>パラメーター

*nNewSize*<br/>
新しい配列のサイズ (要素の数)。 0 以上である必要があります。

*nGrowBy*<br/>
サイズの増加が必要な場合に割り当てる要素のスロットの最小数。

### <a name="remarks"></a>Remarks

新しいサイズが元のサイズより小さい場合は、配列が切り捨てられるし、すべての未使用メモリは解放されます。 効率を高めるため、呼び出す`SetSize`を使用する前に、配列のサイズを設定します。 これにより、割り当てし、アイテムが追加されるたびに、配列をコピーする必要があります。

*NGrowBy*パラメーターは、配列が増加しているときに内部メモリの割り当てに影響します。 使用には影響せず、配列のサイズによって報告された`GetSize`と`GetUpperBound`します。

配列のサイズが大きくなった場合、すべての新しく割り当てられた**CObject** <strong>\*</strong>ポインターが NULL に設定されます。

次の表はその他のメンバー関数に似ている`CObArray::SetSize`します。

|クラス|メンバー関数|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**SetSize を無効にする (INT_PTR** `nNewSize` **、int** `nGrowBy` **=-1);**<br /><br /> **スロー (CMemoryException\* )。**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**SetSize を無効にする (INT_PTR** `nNewSize` **、int** `nGrowBy` **=-1);**<br /><br /> **スロー (CMemoryException\* )。**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**SetSize を無効にする (INT_PTR** `nNewSize` **、int** `nGrowBy` **=-1);**<br /><br /> **スロー (CMemoryException\* )。**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**SetSize を無効にする (INT_PTR** `nNewSize` **、int** `nGrowBy` **=-1);**<br /><br /> **スロー (CMemoryException\* )。**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**SetSize を無効にする (INT_PTR** `nNewSize` **、int** `nGrowBy` **=-1);**<br /><br /> **スロー (CMemoryException\* )。**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**SetSize を無効にする (INT_PTR** `nNewSize` **、int** `nGrowBy` **=-1);**<br /><br /> **スロー (CMemoryException\* )。**|

### <a name="example"></a>例

  例をご覧ください[CObArray::GetData](#getdata)します。

## <a name="see-also"></a>関連項目

[CObject クラス](../../mfc/reference/cobject-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CStringArray クラス](../../mfc/reference/cstringarray-class.md)<br/>
[CPtrArray クラス](../../mfc/reference/cptrarray-class.md)<br/>
[CByteArray クラス](../../mfc/reference/cbytearray-class.md)<br/>
[CWordArray クラス](../../mfc/reference/cwordarray-class.md)<br/>
[CDWordArray クラス](../../mfc/reference/cdwordarray-class.md)
