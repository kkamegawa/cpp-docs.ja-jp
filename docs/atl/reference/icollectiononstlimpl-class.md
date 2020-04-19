---
title: ICollectionOnSTLImpl クラス
ms.date: 11/04/2016
f1_keywords:
- ICollectionOnSTLImpl
- ATLCOM/ATL::ICollectionOnSTLImpl
- ATLCOM/ATL::ICollectionOnSTLImpl::get__NewEnum
- ATLCOM/ATL::ICollectionOnSTLImpl::getcount
- ATLCOM/ATL::ICollectionOnSTLImpl::get_Item
- ATLCOM/ATL::ICollectionOnSTLImpl::m_coll
helpviewer_keywords:
- ICollectionOnSTLImpl class
ms.assetid: 683c88b0-0d97-4779-a762-e493334ba7f9
ms.openlocfilehash: 6842f1c75ebbc9c3dfdd93f30d52fd2cb2936c03
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62275788"
---
# <a name="icollectiononstlimpl-class"></a>ICollectionOnSTLImpl クラス

このクラスは、コレクション クラスで使用されるメソッドを提供します。

## <a name="syntax"></a>構文

```
template <class T, class CollType, class ItemType, class CopyItem, class EnumType>
class ICollectionOnSTLImpl : public T
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
COM コレクションのインターフェイス。

*CollType*<br/>
C++ 標準ライブラリ コンテナー クラス。

*ItemType*<br/>
コンテナー インターフェイスによって公開される項目の種類。

*CopyItem*<br/>
A[コピー ポリシー クラス](../../atl/atl-copy-policy-classes.md)します。

*EnumType*<br/>
A [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)-互換性のある列挙子クラス。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[ICollectionOnSTLImpl::get__NewEnum](#newenum)|コレクションの列挙子オブジェクトを返します。|
|[ICollectionOnSTLImpl::getcount](#get_count)|コレクション内の要素の数を返します。|
|[ICollectionOnSTLImpl::get_Item](#get_item)|要求された項目をコレクションから返します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[ICollectionOnSTLImpl::m_coll](#m_coll)|コレクション。|

## <a name="remarks"></a>Remarks

このクラスは、3 つの方法、コレクション インターフェイスの実装を提供します。 [getcount](#get_count)、 [get_Item](#get_item)、および[get__NewEnum](#newenum)します。

このクラスを使用します。

- 実装するコレクション インターフェイスを定義 (または借用)。

- 特殊化クラスを派生`ICollectionOnSTLImpl`このコレクションのインターフェイスに基づいています。

- 派生クラスを使用してによって処理されないコレクション インターフェイスからすべてのメソッドを実装する`ICollectionOnSTLImpl`します。

> [!NOTE]
>  コレクション インターフェイスがデュアル インターフェイスの場合は、派生クラスから[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)を渡して、`ICollectionOnSTLImpl`特殊化の実装を提供する場合は、最初のテンプレート パラメーターとして、 `IDispatch`メソッド。

- 項目の追加、 [m_coll](#m_coll)コレクションを設定するメンバー。

詳細と例については、次を参照してください。 [ATL のコレクションと列挙子](../../atl/atl-collections-and-enumerators.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

`T`

`ICollectionOnSTLImpl`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom.h

##  <a name="get_count"></a>  ICollectionOnSTLImpl::getcount

このメソッドは、コレクション内の項目の数を返します。

```
STDMETHOD(getcount)(long* pcount);
```

### <a name="parameters"></a>パラメーター

*pcount*<br/>
[out]コレクション内の要素の数。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

##  <a name="get_item"></a>  ICollectionOnSTLImpl::get_Item

このメソッドは、指定した項目をコレクションから返します。

```
STDMETHOD(get_Item)(long Index, ItemType* pvar);
```

### <a name="parameters"></a>パラメーター

*Index*<br/>
[in]コレクション内の項目の 1 から始まるインデックス。

*pvar*<br/>
[out]対応する項目*インデックス*します。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

指定した位置にあるデータをコピーすることによって、アイテムの取得は[m_coll](#m_coll)の copy メソッドを使用して、[コピー ポリシー クラス](../../atl/atl-copy-policy-classes.md)のテンプレート引数として渡される、`ICollectionOnSTLImpl`特殊化します。

##  <a name="newenum"></a>  ICollectionOnSTLImpl::get__NewEnum

コレクションの列挙子オブジェクトを返します。

```
STDMETHOD(get__NewEnum)(IUnknown** ppUnk);
```

### <a name="parameters"></a>パラメーター

*ppUnk*<br/>
[out]**IUnknown**新しく作成された列挙子オブジェクトのポインター。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

新しく作成された列挙子が元のコレクションの反復子を保持`m_coll`(コピーは作成されません) ため、未処理の列挙子があるときに、コレクションが存続することを確認するコレクション オブジェクトの COM の参照を保持しています。

##  <a name="m_coll"></a>  ICollectionOnSTLImpl::m_coll

このメンバーは、コレクションによって表される項目を保持します。

```
CollType m_coll;
```

## <a name="see-also"></a>関連項目

[ATLCollections サンプル](../../overview/visual-cpp-samples.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
