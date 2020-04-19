---
title: CAtlAutoThreadModule クラス
ms.date: 11/04/2016
f1_keywords:
- CAtlAutoThreadModule
- atlbase/ATL::CAtlAutoThreadModule
helpviewer_keywords:
- CAtlAutoThreadModule class
ms.assetid: 3be834aa-55ef-403e-94ae-41979691b15f
ms.openlocfilehash: 1ec66bf77d8dd705cb2e1e93f70a885ab96420a6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62247298"
---
# <a name="catlautothreadmodule-class"></a>CAtlAutoThreadModule クラス

このクラスは、スレッド プール、アパートメント モデルの COM サーバーを実装します。

> [!IMPORTANT]
> このクラスとそのメンバーは、Windows ランタイムで実行するアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
class CAtlAutoThreadModule : public CAtlAutoThreadModuleT<CAtlAutoThreadModule>
```

## <a name="remarks"></a>Remarks

`CAtlAutoThreadModule` 派生した[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)し、スレッド プール、アパートメント モデルの COM サーバーを実装します。 `CAtlAutoThreadModule` 使用して[CComApartment](../../atl/reference/ccomapartment-class.md)モジュール内の各スレッド アパートメントを管理します。

使用する必要があります、 [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread)を指定するオブジェクトのクラス定義でマクロ[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)クラス ファクトリとして。 派生したクラスの 1 つのインスタンスを追加する必要がありますし、`CAtlAutoThreadModuleT`など`CAtlAutoThreadModule`します。 例:

`CAtlAutoThreadModule _AtlAutoModule; // name is immaterial.`

> [!NOTE]
> このクラスは廃止された置換[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)クラス。

## <a name="inheritance-hierarchy"></a>継承階層

`IAtlAutoThreadModule`

[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)

`CAtlAutoThreadModule`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase.h

## <a name="see-also"></a>関連項目

[CAtlAutoThreadModuleT クラス](../../atl/reference/catlautothreadmodulet-class.md)<br/>
[IAtlAutoThreadModule クラス](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)<br/>
[モジュール クラス](../../atl/atl-module-classes.md)
