---
title: CComPtr クラス
description: Microsoft C++ ACTIVE TEMPLATE LIBRARY (ATL) クラス CComPtr のリファレンスガイドです。
ms.date: 02/07/2020
f1_keywords:
- CComPtr
- ATLBASE/ATL::CComPtr
- ATLBASE/ATL::CComPtr::CComPtr
helpviewer_keywords:
- CComPtr class
ms.assetid: 22d9ea8d-ed66-4c34-940f-141db11e83bd
ms.openlocfilehash: 74a12b460f55a782fa2747b02f7d00287786fae6
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127406"
---
# <a name="ccomptr-class"></a>CComPtr クラス

COM インターフェイスポインターを管理するためのスマートポインタークラス。

## <a name="syntax"></a>構文

```cpp
template<class T>
class CComPtr
```

### <a name="parameters"></a>パラメーター

*T*<br/>
格納するポインターの型を指定する COM インターフェイス。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[CComPtr:: CComPtr](#ccomptr)|コンストラクターです。|

### <a name="public-operators"></a>パブリック演算子

|Name|説明|
|----------|-----------------|
|[CComPtr:: operator =](#operator_eq)|メンバーポインターにポインターを割り当てます。|

## <a name="remarks"></a>コメント

ATL では、`CComPtr` と[CComQIPtr](../../atl/reference/ccomqiptr-class.md)を使用して COM インターフェイスポインターを管理します。 どちらも[CComPtrBase](../../atl/reference/ccomptrbase-class.md)から派生し、両方とも自動参照カウントを行います。

`CComPtr` クラスと[CComQIPtr](../../atl/reference/ccomqiptr-class.md)クラスは、自動参照カウントを実行することで、メモリリークを排除するのに役立ちます。  次の関数は、どちらも同じ論理操作を実行します。 ただし、2番目のバージョンでは `CComPtr` クラスが使用されるため、エラーが発生しにくくなる可能性があります。

[!code-cpp[NVC_ATL_Utilities#130](../../atl/codesnippet/cpp/ccomptr-class_1.cpp)]

[!code-cpp[NVC_ATL_Utilities#131](../../atl/codesnippet/cpp/ccomptr-class_2.cpp)]

デバッグビルドで、コードトレース用に atlsd をリンクします。

## <a name="inheritance-hierarchy"></a>継承階層

[CComPtrBase](../../atl/reference/ccomptrbase-class.md)

`CComPtr`

## <a name="requirements"></a>要件

**ヘッダー:** atlbase. h

## <a name="ccomptr"></a>CComPtr:: CComPtr

コンストラクターです。

```cpp
CComPtr() throw ();
CComPtr(T* lp) throw ();
CComPtr (const CComPtr<T>& lp) throw ();
```

### <a name="parameters"></a>パラメーター

*世代*<br/>
インターフェイスポインターを初期化するために使用されます。

*T*<br/>
COM インターフェイス。

### <a name="remarks"></a>コメント

引数を受け取るコンストラクターは、null ポインターではない場合、 *lp*で `AddRef` 呼び出します。 Null 以外の所有オブジェクトは、CComPtr オブジェクトの破棄時、または新しいオブジェクトが CComPtr オブジェクトに割り当てられている場合に、`Release` の呼び出しを取得します。

## <a name="operator_eq"></a>CComPtr:: operator =

代入演算子。

```cpp
T* operator= (T* lp) throw ();
T* operator= (const CComPtr<T>& lp) throw ();
```

### <a name="return-value"></a>戻り値

更新された `CComPtr` オブジェクトへのポインターを返します。

### <a name="remarks"></a>コメント

この操作では、新しいオブジェクトを追加し、存在する場合は既存のオブジェクトを解放します。

## <a name="see-also"></a>参照

[CComPtr:: CComPtr](#ccomptr)<br/>
[CComQIPtr:: CComQIPtr](../../atl/reference/ccomqiptr-class.md#ccomqiptr)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
