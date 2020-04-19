---
title: CComUnkArray クラス
ms.date: 11/04/2016
f1_keywords:
- CComUnkArray
- ATLCOM/ATL::CComUnkArray
- ATLCOM/ATL::CComUnkArray::CComUnkArray
- ATLCOM/ATL::CComUnkArray::Add
- ATLCOM/ATL::CComUnkArray::begin
- ATLCOM/ATL::CComUnkArray::end
- ATLCOM/ATL::CComUnkArray::GetCookie
- ATLCOM/ATL::CComUnkArray::GetUnknown
- ATLCOM/ATL::CComUnkArray::Remove
helpviewer_keywords:
- connection points [C++], managing
- CComUnkArray class
ms.assetid: 5fd4b378-a7b5-4cc1-8866-8ab72a73639e
ms.openlocfilehash: 7a73158e407279b529f76484e4c32f0a8a7a63c2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62259457"
---
# <a name="ccomunkarray-class"></a>CComUnkArray クラス

このクラスは格納`IUnknown`ポインターへのパラメーターとして使用するものでは、 [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)テンプレート クラス。

## <a name="syntax"></a>構文

```
template<unsigned int nMaxSize>
class CComUnkArray
```

#### <a name="parameters"></a>パラメーター

*nMaxSize*<br/>
最大数`IUnknown`静的配列に格納できるポインター。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CComUnkArray::CComUnkArray](#ccomunkarray)|コンストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CComUnkArray::Add](#add)|追加するには、このメソッドを呼び出す、`IUnknown`配列へのポインター。|
|[CComUnkArray::begin](#begin)|最初のポインターを返します`IUnknown`コレクション内のポインター。|
|[CComUnkArray::end](#end)|最後にポインターを返します`IUnknown`コレクション内のポインター。|
|[CComUnkArray::GetCookie](#getcookie)|関連付けられているクッキーを取得するには、このメソッドを呼び出して、指定された`IUnknown`ポインター。|
|[CComUnkArray::GetUnknown](#getunknown)|取得するには、このメソッドを呼び出す、`IUnknown`ポインターに関連付けられたクッキーを指定します。|
|[CComUnkArray::Remove](#remove)|削除するには、このメソッドを呼び出す、`IUnknown`配列からポインター。|

## <a name="remarks"></a>Remarks

`CComUnkArray` 固定数を保持`IUnknown`ポインター、接続のインターフェイスの各ポイントします。 `CComUnkArray` パラメーターとして使用できる、 [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)テンプレート クラス。 `CComUnkArray<1>` テンプレート特殊化した`CComUnkArray`が 1 つのコネクション ポイントの最適化です。

`CComUnkArray`メソッド[開始](#begin)と[エンド](#end)(たとえば、イベントが発生したときに) すべてのコネクション ポイントをループするために使用できます。

参照してください[オブジェクトへの接続ポイントの追加](../../atl/adding-connection-points-to-an-object.md)詳細については接続の作成を自動化することでプロキシをポイントします。

> [!NOTE]
> **注**クラス[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)によって使用されます、**クラスの追加**接続ポイントを持つコントロールを作成するときにウィザード。 接続ポイントの数を手動で指定する場合は、変更からの参照を`CComDynamicUnkArray`に`CComUnkArray<` *n* `>`ここで、 *n*コネクション ポイントの数です必須。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom.h

##  <a name="add"></a>  CComUnkArray::Add

追加するには、このメソッドを呼び出す、`IUnknown`配列へのポインター。

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>パラメーター

*pUnk*<br/>
追加するには、このメソッドを呼び出す、`IUnknown`配列へのポインター。

### <a name="return-value"></a>戻り値

配列は、新しいポインターを格納するのに十分な大きさがない場合は、新しく追加されたポインター、または 0 に関連付けられているクッキーを返します。

##  <a name="begin"></a>  CComUnkArray::begin

コレクションの先頭にポインターを返します`IUnknown`インターフェイス ポインター。

```
IUnknown**
    begin();
```

### <a name="return-value"></a>戻り値

ポインター、`IUnknown`インターフェイス ポインター。

### <a name="remarks"></a>Remarks

コレクションにはとしてローカルに格納されているインターフェイスへのポインターが含まれています`IUnknown`します。 それぞれをキャストする`IUnknown`インターフェイスを実際のインターフェイス型としています。 まず、インターフェイスに対してクエリを実行する必要はありません。

使用する前に、`IUnknown`インターフェイス、NULL がないこと確認する必要があります。

##  <a name="ccomunkarray"></a>  CComUnkArray::CComUnkArray

コンストラクターです。

```
CComUnkArray();
```

### <a name="remarks"></a>Remarks

設定を保持するコレクション`nMaxSize``IUnknown`ポインター、および NULL へのポインターを初期化します。

##  <a name="end"></a>  CComUnkArray::end

最後にポインターを返します`IUnknown`コレクション内のポインター。

```
IUnknown**
    end();
```

### <a name="return-value"></a>戻り値

ポインター、`IUnknown`インターフェイス ポインター。

### <a name="remarks"></a>Remarks

`CComUnkArray`メソッド`begin`と`end`イベントが発生したときに、すべての接続ポイントは、たとえば、ループ処理に使用できます。

[!code-cpp[NVC_ATL_COM#44](../../atl/codesnippet/cpp/ccomunkarray-class_1.cpp)]

##  <a name="getcookie"></a>  CComUnkArray::GetCookie

関連付けられているクッキーを取得するには、このメソッドを呼び出して、指定された`IUnknown`ポインター。

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>パラメーター

*ppFind*<br/>
`IUnknown`ポインターに関連付けられている cookie が必要です。

### <a name="return-value"></a>戻り値

関連付けられているクッキーを返します、`IUnknown`ポインター、または一致する場合は 0`IUnknown`ポインターが見つかりました。

### <a name="remarks"></a>Remarks

同じ 1 つ以上のインスタンスがある場合`IUnknown`ポインター、この関数は、1 つ目の cookie を返します。

##  <a name="getunknown"></a>  CComUnkArray::GetUnknown

取得するには、このメソッドを呼び出す、`IUnknown`ポインターに関連付けられたクッキーを指定します。

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>パラメーター

*dwCookie*<br/>
Cookie を関連付けられている`IUnknown`ポインターが必要です。

### <a name="return-value"></a>戻り値

返します、`IUnknown`ポインター、または一致する cookie が検出されない場合は NULL です。

##  <a name="remove"></a>  CComUnkArray::Remove

削除するには、このメソッドを呼び出す、`IUnknown`配列からポインター。

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>パラメーター

*dwCookie*<br/>
Cookie を参照すること、`IUnknown`ポインター、配列から削除します。

### <a name="return-value"></a>戻り値

かどうか、ポインターが削除された、それ以外の場合は TRUE を返します。

## <a name="see-also"></a>関連項目

[CComDynamicUnkArray クラス](../../atl/reference/ccomdynamicunkarray-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
