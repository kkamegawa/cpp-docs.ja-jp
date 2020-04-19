---
title: コレクション クラスのヘルパー
ms.date: 11/04/2016
helpviewer_keywords:
- DestructElements function
- ConstructElements function
- SerializeElements function
- collection classes [MFC], helper functions
- helper functions collection class [MFC]
ms.assetid: bc3a2368-9edd-4748-9e6a-13cba79517ca
ms.openlocfilehash: 6839427d916068deaf2041dd21a282e0b470f404
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65612261"
---
# <a name="collection-class-helpers"></a>コレクション クラスのヘルパー

コレクション クラス`CMap`、 `CList`、および`CArray`を比較する、コピー、および要素をシリアル化するためにグローバル テンプレートのヘルパー関数を使用します。 基づくクラスの実装の一部として`CMap`、 `CList`、および`CArray`、必要に応じて、これらの関数は、マップ、リスト、または配列に格納されたデータの種類に合うようにオーバーライドする必要があります。 などのヘルパー関数を上書きする方法について`SerializeElements`、記事をご覧ください[コレクション。タイプ セーフなコレクションを作成する方法](../../mfc/how-to-make-a-type-safe-collection.md)します。 なお`ConstructElements`と`DestructElements`非推奨とされました。

Microsoft Foundation Class ライブラリは、コレクション クラスをカスタマイズするために afxtempl.h で次のグローバル関数を提供します。

### <a name="collection-class-helpers"></a>コレクション クラスのヘルパー

|||
|-|-|
|[CompareElements](#compareelements)|要素が同じであるかどうかを示します。|
|[CopyElements](#copyelements)|別の 1 つの配列から要素をコピーします。|
|[DumpElements](#dumpelements)|ストリーム指向の診断出力を提供します。|
|[HashKey](#hashkey)|ハッシュ キーを計算します。|
|[SerializeElements](#serializeelements)|保存またはアーカイブからの要素を取得します。|

##  <a name="compareelements"></a>  CompareElements

によって直接呼び出されます。 [CList::Find] (clist class.md #not_found.md #clist__find と間接的に[cmap__lookup](cmap-class.md#lookup)と[cmap__operator &#91; &#93;](cmap-class.md#operator_at)します。

```
template<class TYPE, class ARG_TYPE>
BOOL AFXAPI
CompareElements(
    const TYPE* pElement1,
    const ARG_TYPE* pElement2);
```

### <a name="parameters"></a>パラメーター

*TYPE*<br/>
比較する最初の要素の型。

*pElement1*<br/>
比較する最初の要素へのポインター。

*ARG_TYPE*<br/>
比較する 2 番目の要素の型。

*pElement2*<br/>
比較する 2 番目の要素へのポインター。

### <a name="return-value"></a>戻り値

によって、オブジェクトを指している場合、0 以外の場合*pElement1*が指すオブジェクトと等しい*pElement2*。 それ以外の場合に 0 です。

### <a name="remarks"></a>Remarks

`CMap`使用を呼び出し、`CMap`テンプレート パラメーター*キー*と*ARG_KEY*します。

既定の実装の比較の結果を返します *\*pElement1*と *\*pElement2*します。 アプリケーションの適切な方法で要素を比較できるように、この関数をオーバーライドします。

C++ 言語では、比較演算子を定義します ( `==`) の単純型 (**char**、 **int**、 **float**など) の比較演算子を定義しません。クラスと構造体。 使用する場合`CompareElements`、それを使用するコレクション クラスのいずれかをインスタンス化する比較演算子を定義するか、オーバー ロードまたは`CompareElements`したバージョンに適切な値を返します。

### <a name="requirements"></a>必要条件

   **ヘッダー:** afxtempl.h

##  <a name="copyelements"></a>  CopyElements

この関数はによって直接呼び出さ[CArray::Append](carray-class.md#append)と[CArray::Copy](carray-class.md#copy)します。

```
template<class TYPE>
void AFXAPI CopyElements(
    TYPE* pDest,
    const TYPE* pSrc,
    INT_PTR nCount);
```

### <a name="parameters"></a>パラメーター

*TYPE*<br/>
コピーされる要素の型を指定するテンプレート パラメーター。

*pDest*<br/>
要素のコピー先へのポインター。

*pSrc*<br/>
コピーする要素のソースへのポインター。

*nCount*<br/>
コピーする要素の数。

### <a name="remarks"></a>Remarks

既定の実装は、単純な代入演算子を使用して ( **=** ) コピー操作を実行します。 コピーされた型が、オーバー ロードされた演算子を持たない場合 =、既定の実装は、ビットごとのコピーを実行します。

これと他のヘルパー関数を実装する方法の詳細については、この記事を参照してください。[コレクション。タイプ セーフなコレクションを作成する方法](../how-to-make-a-type-safe-collection.md)します。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxtempl.h

##  <a name="dumpelements"></a>  DumpElements

オーバーライドされた場合、コレクションの要素のテキスト形式でのストリーム指向の診断出力を提供します。

```
template<class TYPE>
void  AFXAPI DumpElements(
    CDumpContext& dc,
    const TYPE* pElements,
    INT_PTR nCount);
```

### <a name="parameters"></a>パラメーター

*dc*<br/>
要素をダンプするためのコンテキストをダンプします。

*TYPE*<br/>
要素の型を指定するテンプレート パラメーター。

*pElements*<br/>
ダンプする要素を指すポインター。

*nCount*<br/>
ダンプする要素の数。

### <a name="remarks"></a>Remarks

`CArray::Dump`、 `CList::Dump`、および`CMap::Dump`ダンプの深さが 0 より大きい場合は、この関数呼び出し。

既定の実装では、何も行われません。 場合は、コレクションの要素から派生`CObject`、オーバーライドは通常、反復、コレクションの要素を呼び出す`Dump`の各要素に有効にします。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxtempl.h

##  <a name="hashkey"></a>  HashKey

指定されたキーのハッシュ値を計算します。

```
template<class ARG_KEY>
AFX_INLINE UINT AFXAPI HashKey(ARG_KEY  key);
```

### <a name="parameters"></a>パラメーター

*ARG_KEY*<br/>
マップ キーにアクセスするために使用するデータ型を指定するテンプレート パラメーター。

*key*<br/>
ハッシュ値が計算されるキー。

### <a name="return-value"></a>戻り値

キーのハッシュ値。

### <a name="remarks"></a>Remarks

この関数はによって直接呼び出さ[CMap::RemoveKey](cmap-class.md#removekey)と間接的に[CMap::Lookup](cmap-class.md#lookup)と[CMap::Operator &#91; &#93;](cmap-class.md#operator_at)します。

既定の実装は、移行することによってハッシュ値を作成します*キー* 4 つの位置を右。 アプリケーションに適切なハッシュ値を返すように、この関数をオーバーライドします。

### <a name="example"></a>例

```cpp
template <> UINT AFXAPI HashKey(unsigned __int64 key)
{
   // Generate the hash value by XORing the lower 32 bits of the number
   // with the upper 32 bits
   return(UINT(key) ^ UINT(key >> 32));
}
```

### <a name="requirements"></a>必要条件

  **ヘッダー** afxtempl.h

##  <a name="serializeelements"></a>  SerializeElements

[CArray](carray-class.md)、 [CList](clist-class.md)、および[CMap](cmap-class.md)要素をシリアル化するには、この関数を呼び出します。

```
template<class TYPE>
void AFXAPI SerializeElements(CArchive& ar, TYPE* pElements, INT_PTR nCount);
```

### <a name="parameters"></a>パラメーター

*TYPE*<br/>
要素の型を指定するテンプレート パラメーター。

*ar*<br/>
またはからにアーカイブするアーカイブ オブジェクト。

*pElements*<br/>
アーカイブされている要素へのポインター。

*nCount*<br/>
アーカイブされている要素の数

### <a name="remarks"></a>Remarks

既定の実装は、ビットごとの読み取りまたは書き込み。

これと他のヘルパー関数を実装する方法の詳細については、この記事を参照してください。[コレクション。タイプ セーフなコレクションを作成する方法](../how-to-make-a-type-safe-collection.md)します。

### <a name="example"></a>例

記事の例を参照してください。[コレクション。タイプ セーフなコレクションを作成する方法](../how-to-make-a-type-safe-collection.md)します。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxtempl.h

## <a name="see-also"></a>関連項目

[マクロとグローバル](mfc-macros-and-globals.md)<br/>
[CMap クラス](cmap-class.md)<br/>
[CList クラス](clist-class.md)<br/>
[CArray クラス](carray-class.md)
