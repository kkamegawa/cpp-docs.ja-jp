---
title: IEnumOnSTLImpl クラス
ms.date: 11/04/2016
f1_keywords:
- IEnumOnSTLImpl
- ATLCOM/ATL::IEnumOnSTLImpl
- ATLCOM/ATL::IEnumOnSTLImpl::Clone
- ATLCOM/ATL::IEnumOnSTLImpl::Init
- ATLCOM/ATL::IEnumOnSTLImpl::Next
- ATLCOM/ATL::IEnumOnSTLImpl::Reset
- ATLCOM/ATL::IEnumOnSTLImpl::Skip
- ATLCOM/ATL::IEnumOnSTLImpl::m_iter
- ATLCOM/ATL::IEnumOnSTLImpl::m_pcollection
- ATLCOM/ATL::IEnumOnSTLImpl::m_spUnk
helpviewer_keywords:
- IEnumOnSTLImpl class
ms.assetid: 1789e77b-88b8-447d-a490-806b918912ce
ms.openlocfilehash: 7cf777f3ff0d298f224157735a06bf57a2c10cf5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495858"
---
# <a name="ienumonstlimpl-class"></a>IEnumOnSTLImpl クラス

このクラスは、 C++標準ライブラリコレクションに基づいて列挙子インターフェイスを定義します。

## <a name="syntax"></a>構文

```
template <class Base,
    const IID* piid, class T, class Copy, class CollType>
class ATL_NO_VTABLE IEnumOnSTLImpl : public Base
```

#### <a name="parameters"></a>パラメーター

*常用*<br/>
COM 列挙子。 例については、「 [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) 」を参照してください。

*piid*<br/>
列挙子インターフェイスのインターフェイス ID へのポインター。

*T*<br/>
列挙子インターフェイスによって公開される項目の型。

*コピー*<br/>
[コピーポリシークラス](../../atl/atl-copy-policy-classes.md)。

*文字の種類*<br/>
C++標準ライブラリコンテナークラス。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[IEnumOnSTLImpl:: Clone](#clone)|**複製**の実装。|
|[IEnumOnSTLImpl::Init](#init)|列挙子を初期化します。|
|[IEnumOnSTLImpl:: 次へ](#next)|**Next**の実装。|
|[IEnumOnSTLImpl::Reset](#reset)|**Reset**の実装。|
|[IEnumOnSTLImpl:: Skip](#skip)|**Skip**の実装。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[IEnumOnSTLImpl::m_iter](#m_iter)|コレクション内の列挙子の現在位置を表す反復子。|
|[IEnumOnSTLImpl::m_pcollection](#m_pcollection)|列挙される項目C++を保持する標準ライブラリコンテナーへのポインター。|
|[IEnumOnSTLImpl::m_spUnk](#m_spunk)|コレクションを提供するオブジェクトのポインター。`IUnknown`|

## <a name="remarks"></a>Remarks

`IEnumOnSTLImpl`列挙される項目がC++標準ライブラリと互換性のあるコンテナーに格納される、COM 列挙子インターフェイスの実装を提供します。 このクラスは、配列に基づく列挙子インターフェイスの実装を提供する[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)クラスに似ています。

> [!NOTE]
>  `CComEnumImpl`との違いの詳細については、 `IEnumOnSTLImpl`「 [CComEnumImpl:: Init](../../atl/reference/ccomenumimpl-class.md#init) 」を参照してください。

通常、このインターフェイスの実装から派生することで、独自の列挙子クラスを作成する必要はあり*ません*。 C++標準ライブラリコンテナーに基づいて ATL で提供される列挙子を使用する場合は、 [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)のインスタンスを作成するか、[ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md) から派生することによって列挙子を返すコレクションクラスを作成するのが一般的です。

ただし、カスタム列挙子を提供する必要がある場合 (列挙子インターフェイスに加えてインターフェイスを公開するものなど)、このクラスから派生させることができます。 このような状況では、独自の実装を提供するために[Clone](#clone)メソッドをオーバーライドする必要があります。

## <a name="inheritance-hierarchy"></a>継承階層

`Base`

`IEnumOnSTLImpl`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom. h

##  <a name="init"></a>IEnumOnSTLImpl:: Init

列挙子を初期化します。

```
HRESULT Init(
    IUnknown* pUnkForRelease,
    CollType& collection);
```

### <a name="parameters"></a>パラメーター

*pUnkForRelease*<br/>
から列挙子の有効期間中に保持する必要があるオブジェクトのポインター。`IUnknown` そのようなオブジェクトが存在しない場合は、NULL を渡します。

*collection*<br/>
列挙される項目C++を保持する標準ライブラリコンテナーへの参照。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

別のオブジェクト`Init`に保持されているコレクションへの参照を渡す場合は、 *pUnkForRelease*パラメーターを使用して、列挙子が必要とする限り、オブジェクトとそのオブジェクトが保持しているコレクションを確実に使用できます。

列挙子インターフェイスへのポインターを任意のクライアントに渡す前に、このメソッドを呼び出す必要があります。

##  <a name="clone"></a>IEnumOnSTLImpl:: Clone

このメソッドは、型`CComEnumOnSTL`のオブジェクトを作成し、現在のオブジェクトによって使用される同じコレクションと反復子を使用して初期化し、新しく作成されたオブジェクトのインターフェイスを返すことによって、 **Clone**メソッドの実装を提供します。

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>パラメーター

*ppEnum*<br/>
入出力現在の列挙子から複製された、新しく作成されたオブジェクトの列挙子インターフェイス。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

##  <a name="m_spunk"></a>IEnumOnSTLImpl::m_spUnk

コレクションを提供するオブジェクトのポインター。`IUnknown`

```
CComPtr<IUnknown> m_spUnk;
```

### <a name="remarks"></a>Remarks

このスマートポインターは、 [IEnumOnSTLImpl:: Init](#init)に渡されたオブジェクトへの参照を保持し、列挙子の有効期間中もそのままの状態を維持します。

##  <a name="m_pcollection"></a>IEnumOnSTLImpl::m_pcollection

このメンバーは、列挙子インターフェイスの実装を推進するデータを提供するコレクションを指します。

```
CollType* m_pcollection;
```

### <a name="remarks"></a>Remarks

このメンバーは、 [IEnumOnSTLImpl:: Init](#init)への呼び出しによって初期化されます。

##  <a name="m_iter"></a>IEnumOnSTLImpl::m_iter

このメンバーは、コレクション内の現在位置をマークし、後続の要素に移動するために使用される反復子を保持します。

```
CollType::iterator m_iter;
```

##  <a name="next"></a>IEnumOnSTLImpl:: 次へ

このメソッドは、**次**のメソッドの実装を提供します。

```
STDMETHOD(Next)(
    ULONG celt,
    T* rgelt,
    ULONG* pceltFetched);
```

### <a name="parameters"></a>パラメーター

*中*<br/>
から要求された要素の数。

*rgelt*<br/>
入出力要素を格納する配列。

*フェッチされる pcelt*<br/>
入出力*Rgelt*で実際に返される要素の数。 リストに保持されて*いる要素数が2未満*の場合は、この値を*2 未満に*することができます。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

##  <a name="reset"></a>  IEnumOnSTLImpl::Reset

このメソッドは、 **Reset**メソッドの実装を提供します。

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

##  <a name="skip"></a>IEnumOnSTLImpl:: Skip

このメソッドは、 **Skip**メソッドの実装を提供します。

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>パラメーター

*中*<br/>
からスキップする要素の数。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
