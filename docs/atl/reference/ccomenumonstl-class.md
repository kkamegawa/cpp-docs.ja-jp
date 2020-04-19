---
title: CComEnumOnSTL クラス
ms.date: 11/04/2016
f1_keywords:
- CComEnumOnSTL
- atlcom/ATL::CComEnumOnSTL
helpviewer_keywords:
- CComEnumOnSTL class
ms.assetid: befe1a44-7a00-4f28-9a2e-cc0fa526643c
ms.openlocfilehash: ab11ea5e5347c9c8684e8710e9742fdbcad8a46b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497161"
---
# <a name="ccomenumonstl-class"></a>CComEnumOnSTL クラス

このクラスは、 C++標準ライブラリコレクションに基づいて COM 列挙子オブジェクトを定義します。

## <a name="syntax"></a>構文

```
template <class Base,
    const IID* piid, class T, class Copy, class CollType, class ThreadModel = CComObjectThreadModel>
class ATL_NO_VTABLE CComEnumOnSTL : public IEnumOnSTLImpl<Base, piid,
T,
    Copy,
CollType>,
    public CComObjectRootEx<ThreadModel>
```

#### <a name="parameters"></a>パラメーター

*常用*<br/>
COM 列挙子。 例については、「 [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) 」を参照してください。

*piid*<br/>
列挙子インターフェイスのインターフェイス ID へのポインター。

*T*<br/>
列挙子インターフェイスによって公開される項目の型。

*コピー*<br/>
[コピーポリシー](../../atl/atl-copy-policy-classes.md)クラス。

*文字の種類*<br/>
C++標準ライブラリコンテナークラス。

## <a name="remarks"></a>Remarks

`CComEnumOnSTL`C++標準ライブラリコレクションに基づいて COM 列挙子オブジェクトを定義します。 このクラスは、独自のまたは[ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)と組み合わせて使用できます。 このクラスを使用するための一般的な手順を次に示します。 詳細については、「 [ATL コレクションと列挙子](../../atl/atl-collections-and-enumerators.md)」を参照してください。

## <a name="to-use-this-class-with-icollectiononstlimpl"></a>ICollectionOnSTLImpl でこのクラスを使用するには、次のようにします。

- このクラスの特殊化を**typedef**します。

- の`ICollectionOnSTLImpl`特殊化では、最終的なテンプレート引数として**typedef**を使用します。

例については、「 [ATL のコレクションと列挙子](../../atl/atl-collections-and-enumerators.md)」を参照してください。

## <a name="to-use-this-class-independently-of-icollectiononstlimpl"></a>このクラスを ICollectionOnSTLImpl とは無関係に使用するには、次のようにします。

- このクラスの特殊化を**typedef**します。

- の`CComObject`特殊化では、テンプレート引数として**typedef**を使用します。

- `CComObject`特殊化のインスタンスを作成します。

- [IEnumOnSTLImpl:: Init](../../atl/reference/ienumonstlimpl-class.md#init)を呼び出して、列挙子オブジェクトを初期化します。

- クライアントに列挙子インターフェイスを返します。

## <a name="inheritance-hierarchy"></a>継承階層

`CComObjectRootBase`

`Base`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)

`CComEnumOnSTL`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom. h

## <a name="example"></a>例

次に示すコードは、列挙子オブジェクトの作成と初期化を処理する汎用関数を提供します。

[!code-cpp[NVC_ATL_COM#34](../../atl/codesnippet/cpp/ccomenumonstl-class_1.h)]

このテンプレート関数を使用すると、次`_NewEnum`に示すように、コレクションインターフェイスのプロパティを実装できます。

[!code-cpp[NVC_ATL_COM#35](../../atl/codesnippet/cpp/ccomenumonstl-class_2.h)]

このコードは、 `CComEnumOnSTL` `CComVariant`インターフェイスを使用してのベクターを公開するのtypedefを作成し`IEnumVariant`ます。 クラス`CVariantCollection`は、この`CreateSTLEnumerator`型の列挙子オブジェクトを操作することを単に専門としています。

## <a name="see-also"></a>関連項目

[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)<br/>
[ATLCollections のサンプル:ICollectionOnSTLImpl、CComEnumOnSTL、およびカスタムコピーポリシークラスの例を示します。](../../overview/visual-cpp-samples.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)<br/>
[CComObjectRootEx クラス](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)<br/>
[IEnumOnSTLImpl クラス](../../atl/reference/ienumonstlimpl-class.md)
