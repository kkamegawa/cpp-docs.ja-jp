---
title: CComDynamicUnkArray クラス
ms.date: 11/04/2016
f1_keywords:
- CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray::CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray::Add
- ATLCOM/ATL::CComDynamicUnkArray::begin
- ATLCOM/ATL::CComDynamicUnkArray::clear
- ATLCOM/ATL::CComDynamicUnkArray::end
- ATLCOM/ATL::CComDynamicUnkArray::GetAt
- ATLCOM/ATL::CComDynamicUnkArray::GetCookie
- ATLCOM/ATL::CComDynamicUnkArray::GetSize
- ATLCOM/ATL::CComDynamicUnkArray::GetUnknown
- ATLCOM/ATL::CComDynamicUnkArray::Remove
helpviewer_keywords:
- connection points [C++], managing
- CComDynamicUnkArray class
ms.assetid: 202470d7-9a1b-498f-b96d-659d681acd65
ms.openlocfilehash: d55a6d6bfbcc6921fa0633753365f5799388dc27
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497249"
---
# <a name="ccomdynamicunkarray-class"></a>CComDynamicUnkArray クラス

このクラスは、ポインターの`IUnknown`配列を格納します。

## <a name="syntax"></a>構文

```
class CComDynamicUnkArray
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CComDynamicUnkArray::CComDynamicUnkArray](#ccomdynamicunkarray)|コンストラクターです。 コレクションの値を NULL に、コレクションのサイズを0に初期化します。|
|[CComDynamicUnkArray:: ~ CComDynamicUnkArray](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CComDynamicUnkArray::Add](#add)|配列への`IUnknown`ポインターを追加するには、このメソッドを呼び出します。|
|[CComDynamicUnkArray:: begin](#begin)|コレクション内の最初`IUnknown`のポインターへのポインターを返します。|
|[CComDynamicUnkArray::clear](#clear)|配列を空にします。|
|[CComDynamicUnkArray:: end](#end)|コレクション内の最後`IUnknown`のポインターの1つ後ろへのポインターを返します。|
|[CComDynamicUnkArray::GetAt](#getat)|指定したインデックス位置にある要素を取得します。|
|[CComDynamicUnkArray::GetCookie](#getcookie)|指定`IUnknown`したポインターに関連付けられているクッキーを取得するには、このメソッドを呼び出します。|
|[CComDynamicUnkArray::GetSize](#getsize)|配列の長さを返します。|
|[CComDynamicUnkArray:: GetUnknown](#getunknown)|特定のクッキーに関連付け`IUnknown`られているポインターを取得するには、このメソッドを呼び出します。|
|[CComDynamicUnkArray::Remove](#remove)|配列から`IUnknown`ポインターを削除するには、このメソッドを呼び出します。|

## <a name="remarks"></a>Remarks

`CComDynamicUnkArray`接続ポイントのインターフェイスを動的`IUnknown`に割り当てられたポインターの配列を保持します。 `CComDynamicUnkArray`は、 [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)テンプレートクラスのパラメーターとして使用できます。

[begin](#begin) および [end](#end) メソッドを使用して、すべてのコネクションポイントをループ処理できます (たとえば、イベントが発生したとき)。 `CComDynamicUnkArray`

接続ポイントプロキシの作成を自動化する方法の詳細については[、「オブジェクトへの接続ポイントの追加](../../atl/adding-connection-points-to-an-object.md)」を参照してください。

> [!NOTE]
> **メモ**クラス`CComDynamicUnkArray`は、接続ポイントを持つコントロールを作成するときに、**クラスの追加**ウィザードによって使用されます。 接続ポイントの数を手動で指定する場合は、参照`CComDynamicUnkArray`をから*n* `>`に`CComUnkArray<`変更します。ここで、 *n*は必要な接続ポイントの数です。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom. h

##  <a name="add"></a>  CComDynamicUnkArray::Add

配列への`IUnknown`ポインターを追加するには、このメソッドを呼び出します。

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>パラメーター

*pUnk*<br/>
配列に追加するポインター。`IUnknown`

### <a name="return-value"></a>戻り値

新しく追加されたポインターに関連付けられているクッキーを返します。

##  <a name="begin"></a>CComDynamicUnkArray:: begin

インターフェイスポインターの`IUnknown`コレクションの先頭へのポインターを返します。

```
IUnknown**
    begin();
```

### <a name="return-value"></a>戻り値

`IUnknown`インターフェイスポインターへのポインター。

### <a name="remarks"></a>Remarks

コレクションには、として`IUnknown`ローカルに格納されるインターフェイスへのポインターが含まれています。 各`IUnknown`インターフェイスを実際のインターフェイス型にキャストしてから、を呼び出します。 最初にインターフェイスを照会する必要はありません。

`IUnknown`インターフェイスを使用する前に、それが NULL でないことを確認する必要があります。

##  <a name="clear"></a>CComDynamicUnkArray:: clear

配列を空にします。

```
void clear();
```

##  <a name="ccomdynamicunkarray"></a>CComDynamicUnkArray::CComDynamicUnkArray

コンストラクターです。

```
CComDynamicUnkArray();
```

### <a name="remarks"></a>Remarks

コレクションのサイズをゼロに設定し、値を NULL に初期化します。 必要に応じて、デストラクターによってコレクションが解放されます。

##  <a name="dtor"></a>CComDynamicUnkArray:: ~ CComDynamicUnkArray

デストラクターです。

```
~CComDynamicUnkArray();
```

### <a name="remarks"></a>Remarks

クラスコンストラクターによって割り当てられたリソースを解放します。

##  <a name="end"></a>CComDynamicUnkArray:: end

コレクション内の最後`IUnknown`のポインターの1つ後ろへのポインターを返します。

```
IUnknown**
    end();
```

### <a name="return-value"></a>戻り値

`IUnknown`インターフェイスポインターへのポインター。

##  <a name="getat"></a>CComDynamicUnkArray:: GetAt

指定したインデックス位置にある要素を取得します。

```
IUnknown* GetAt(int nIndex);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
取得する要素のインデックス。

### <a name="return-value"></a>戻り値

[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)インターフェイスへのポインター。

##  <a name="getcookie"></a>  CComDynamicUnkArray::GetCookie

指定`IUnknown`したポインターに関連付けられているクッキーを取得するには、このメソッドを呼び出します。

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>パラメーター

*ppFind*<br/>
関連付けられているクッキーが必要なポインター。`IUnknown`

### <a name="return-value"></a>戻り値

`IUnknown`ポインターに関連付けられているクッキーを返します。 `IUnknown`一致するポインターが見つからない場合は0を返します。

### <a name="remarks"></a>Remarks

同じ`IUnknown`ポインターのインスタンスが複数ある場合、この関数は最初のインスタンスのクッキーを返します。

##  <a name="getsize"></a>CComDynamicUnkArray:: GetSize

配列の長さを返します。

```
int GetSize() const;
```

### <a name="return-value"></a>戻り値

配列の長さ。

##  <a name="getunknown"></a>CComDynamicUnkArray:: GetUnknown

特定のクッキーに関連付け`IUnknown`られているポインターを取得するには、このメソッドを呼び出します。

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>パラメーター

*dwCookie*<br/>
関連付けら`IUnknown`れたポインターが必要なクッキー。

### <a name="return-value"></a>戻り値

`IUnknown`ポインターを返します。一致するクッキーが見つからない場合は NULL を返します。

##  <a name="remove"></a>  CComDynamicUnkArray::Remove

配列から`IUnknown`ポインターを削除するには、このメソッドを呼び出します。

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>パラメーター

*dwCookie*<br/>
配列から削除する`IUnknown`ポインターを参照しているクッキー。

### <a name="return-value"></a>戻り値

ポインターが削除された場合は TRUE を返します。それ以外の場合は FALSE。

## <a name="see-also"></a>関連項目

[CComUnkArray クラス](../../atl/reference/ccomunkarray-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
