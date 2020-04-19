---
title: CUIntArray クラス
ms.date: 11/04/2016
f1_keywords:
- CUIntArray
- AFXCOLL/CUIntArray
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
ms.assetid: d71f3d8f-ef9f-4e48-9b69-7782c0e2ddf7
ms.openlocfilehash: 39d5fd4707f1c03de78cf9fd078655389c93ba17
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323545"
---
# <a name="cuintarray-class"></a>CUIntArray クラス

符号なし整数の配列をサポートします。

## <a name="syntax"></a>構文

```
class CUIntArray : public CObject
```

## <a name="members"></a>メンバー

メンバー関数は、`CUIntArray`クラスのメンバー関数のような[CObArray](../../mfc/reference/cobarray-class.md)します。 メンバー関数については `CObArray` クラスの説明を参照してください。 任意の場所を確認、`CObject`関数パラメーターまたは戻り値としてのポインターを UINT に置き換えてください。

`CObject* CObArray::GetAt( int <nIndex> ) const;`

たとえば、次のように変換します。

`UINT CUIntArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CObArray::CObArray](../../mfc/reference/cobarray-class.md#cobarray)|空の配列を生成します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CObArray::Add](../../mfc/reference/cobarray-class.md#add)|配列の末尾に要素を追加します。必要に応じて、配列を大きくします。|
|[CObArray::Append](../../mfc/reference/cobarray-class.md#append)|配列に別の配列を追加します。必要に応じて、配列を大きくします。|
|[CObArray::Copy](../../mfc/reference/cobarray-class.md#copy)|配列に別の配列をコピーします。必要に応じて、配列を大きくします。|
|[CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|配列内の要素ポインターへの一時的な参照を返します。|
|[CObArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|現在の上限を超えている未使用のメモリをすべて解放します。|
|[CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|指定されたインデックス位置にある値を返します。|
|[CObArray::GetCount](../../mfc/reference/cobarray-class.md#getcount)|この配列内の要素の数を取得します。|
|[CObArray::GetData](../../mfc/reference/cobarray-class.md#getdata)|配列内の要素へのアクセスを許可します。 NULL にすることができます。|
|[CObArray::GetSize](../../mfc/reference/cobarray-class.md#getsize)|この配列内の要素の数を取得します。|
|[CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|有効な最大のインデックスを返します。|
|[CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|指定されたインデックス位置に要素 (または別の配列内のすべての要素) を挿入します。|
|[CObArray::IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|配列が空かどうかを判別します。|
|[CObArray::RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|この配列からすべての要素を削除します。|
|[CObArray::RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|特定のインデックス位置にある要素を削除します。|
|[CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|指定されたインデックスの値を設定します。配列は大きくできません。|
|[CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|指定されたインデックスの値を設定します。必要に応じて、配列を大きくします。|
|[CObArray::SetSize](../../mfc/reference/cobarray-class.md#setsize)|この配列に含まれる要素の数を設定します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CObArray::operator \[ \]](../../mfc/reference/cobarray-class.md#operator_at)|指定されたインデックス位置にある要素を設定または取得します。|

## <a name="remarks"></a>Remarks

符号なし整数の場合、または UINT、異なりますワード、ダブルワード UINT の物理サイズがターゲットの実行環境に応じて変更できます。 UINT、ダブルワードと同じサイズです。

`CUIntArray` 組み込まれています、 [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)実行時の型へのアクセスとダンプをサポートするためにマクロを[CDumpContext](../../mfc/reference/cdumpcontext-class.md)オブジェクト。 個々 の符号なし整数の要素をダンプする場合は、1 以上、ダンプ コンテキストの深さを設定する必要があります。 符号なし整数の配列をシリアル化することはできません。

> [!NOTE]
>  配列を使用する前に、`SetSize` を使用してそのサイズを設定し、メモリを割り当てます。 `SetSize` を使用しない場合、配列に要素を追加すると、配列の再割り当てとコピーが頻繁に発生します。 頻繁な再割り当てとコピーは非効率であり、メモリが断片化される可能性があります。

使用しての詳細については`CUIntArray`、記事をご覧ください[コレクション](../../mfc/collections.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CUIntArray`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxcoll.h

## <a name="see-also"></a>関連項目

[CObject クラス](../../mfc/reference/cobject-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)
