---
title: CComEnum クラス
ms.date: 11/04/2016
f1_keywords:
- CComEnum
- atlcom/ATL::CComEnum
helpviewer_keywords:
- CComEnum class
ms.assetid: bff7dd7b-eb6e-4d6e-96ed-2706e66c8b3b
ms.openlocfilehash: 7252eb2fa5d34618a1c38484a2506bae27a1106a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497221"
---
# <a name="ccomenum-class"></a>CComEnum クラス

このクラスは、配列に基づいて COM 列挙子オブジェクトを定義します。

## <a name="syntax"></a>構文

```
template <class Base,
    const IID* piid, class T, class Copy, class ThreadModel = CcomObjectThreadModel>
class ATL_NO_VTABLE CComEnum : public CComEnumImpl<Base, piid,
T,
    Copy>,
public CComObjectRootEx<ThreadModel>
```

#### <a name="parameters"></a>パラメーター

*常用*<br/>
COM 列挙子インターフェイス。 例については、「 [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) 」を参照してください。

*piid*<br/>
列挙子インターフェイスのインターフェイス ID へのポインター。

*T*<br/>
列挙子インターフェイスによって公開される項目の型。

*コピー*<br/>
同種の[コピーポリシークラス](../../atl/atl-copy-policy-classes.md)。

*ThreadModel*<br/>
クラスのスレッドモデル。 このパラメーターの既定値は、プロジェクトで使用されるグローバルオブジェクトスレッドモデルです。

## <a name="remarks"></a>Remarks

`CComEnum`配列に基づいて COM 列挙子オブジェクトを定義します。 このクラスは、 C++標準ライブラリコンテナーに基づいて列挙子を実装する[CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)に似ています。 このクラスを使用するための一般的な手順を次に示します。 詳細については、「 [ATL コレクションと列挙子](../../atl/atl-collections-and-enumerators.md)」を参照してください。

## <a name="to-use-this-class"></a>このクラスを使用するには:

- このクラスの特殊化を**typedef**します。

- の`CComObject`特殊化では、テンプレート引数として**typedef**を使用します。

- `CComObject`特殊化のインスタンスを作成します。

- [CComEnumImpl:: Init](../../atl/reference/ccomenumimpl-class.md#init)を呼び出して、列挙子オブジェクトを初期化します。

- クライアントに列挙子インターフェイスを返します。

## <a name="inheritance-hierarchy"></a>継承階層

`CComObjectRootBase`

`Base`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)

`CComEnum`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom. h

## <a name="example"></a>例

次に示すコードは、列挙子オブジェクトを作成および初期化するための再利用可能な関数を示しています。

[!code-cpp[NVC_ATL_COM#32](../../atl/codesnippet/cpp/ccomenum-class_1.h)]

このテンプレート関数を使用すると、次`_NewEnum`に示すように、コレクションインターフェイスのプロパティを実装できます。

[!code-cpp[NVC_ATL_COM#33](../../atl/codesnippet/cpp/ccomenum-class_2.h)]

このコードは、 `IEnumVariant`インターフェイスを`CComEnum`使用してバリアントのベクターを公開するの**typedef**を作成します。 クラス`CVariantArrayCollection`は、この`CreateEnumerator`型の列挙子オブジェクトを操作し、必要な引数を渡すことを専門としています。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)<br/>
[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)<br/>
[CComEnumImpl クラス](../../atl/reference/ccomenumimpl-class.md)<br/>
[CComObjectRootEx クラス](../../atl/reference/ccomobjectrootex-class.md)
