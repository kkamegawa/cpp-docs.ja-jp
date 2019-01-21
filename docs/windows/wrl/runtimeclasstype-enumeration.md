---
title: RuntimeClassType 列挙型
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassType
helpviewer_keywords:
- RuntimeClassType enumeration
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
ms.openlocfilehash: 3b869be00cdc405569b82bdf3730f8d4ca4f3aab
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336757"
---
# <a name="runtimeclasstype-enumeration"></a>RuntimeClassType 列挙型

型を指定[RuntimeClass](runtimeclass-class.md)サポートされているインスタンス。

## <a name="syntax"></a>構文

```cpp
enum RuntimeClassType;
```

## <a name="members"></a>メンバー

### <a name="values"></a>値

|名前|説明|
|----------|-----------------|
|`ClassicCom`|クラシック COM ランタイム クラスです。|
|`Delegate`|これは、`ClassicCom` に相当します。|
|`InhibitFtmBase`|無効にします`FtmBase`する際にサポート`__WRL_CONFIGURATION_LEGACY__`が定義されていません。|
|`InhibitWeakReference`|弱い参照のサポートを無効にします。|
|`WinRt`|Windows ランタイム クラスです。|
|`WinRtClassicComMix`|`WinRt` と `ClassicCom` の組み合わせです。|

## <a name="requirements"></a>必要条件

**ヘッダー:** implements.h

**名前空間:** Microsoft::wrl

## <a name="see-also"></a>関連項目

[Microsoft::WRL 名前空間](microsoft-wrl-namespace.md)