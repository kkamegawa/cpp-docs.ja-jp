---
title: FactoryCacheFlags 列挙型
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::FactoryCacheFlags
ms.assetid: 6f54258f-0144-4264-9608-414e5905f6fb
ms.openlocfilehash: 6fecacd6038d1c41e57515307c1b810d0623d16f
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336794"
---
# <a name="factorycacheflags-enumeration"></a>FactoryCacheFlags 列挙型

ファクトリ オブジェクトをキャッシュするかどうかを判断します。

## <a name="syntax"></a>構文

```cpp
enum FactoryCacheFlags;
```

## <a name="remarks"></a>Remarks

既定では、出荷時のキャッシュ ポリシーとして指定、 [ModuleType](moduletype-enumeration.md)テンプレート パラメーターを作成するとき、[モジュール](module-class.md)オブジェクト。 このポリシーを上書きするには、指定、 **FactoryCacheFlags**ファクトリ オブジェクトを作成するときの値します。

|||
|-|-|
|`FactoryCacheDefault`|キャッシュ ポリシー、`Module`オブジェクトを使用します。|
|`FactoryCacheEnabled`|により、ファクトリをキャッシュに関係なく、`ModuleType`を作成するために使用するテンプレート パラメーターを`Module`オブジェクト。|
|`FactoryCacheDisabled`|ファクトリをキャッシュに関係なく無効になります、`ModuleType`を作成するために使用するテンプレート パラメーターを`Module`オブジェクト。|

## <a name="requirements"></a>必要条件

**ヘッダー:** implements.h

**名前空間:** Microsoft::wrl

## <a name="see-also"></a>関連項目

[Microsoft::WRL 名前空間](microsoft-wrl-namespace.md)