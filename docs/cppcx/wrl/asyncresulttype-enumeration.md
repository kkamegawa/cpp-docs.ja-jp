---
title: AsyncResultType 列挙型
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncResultType
helpviewer_keywords:
- AsyncResultType enumeration
ms.assetid: 4195d234-3f3f-4363-9118-6ad2a7551cf2
ms.openlocfilehash: d3f99fa85a777ae8361ed6f7cb82fe97ddd8d667
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398798"
---
# <a name="asyncresulttype-enumeration"></a>AsyncResultType 列挙型

によって返される結果の種類を指定します、`GetResults()`メソッド。

## <a name="syntax"></a>構文

```cpp
enum AsyncResultType;
```

## <a name="members"></a>メンバー

### <a name="values"></a>値

|名前|説明|
|----------|-----------------|
|`MultipleResults`|一連の間で段階的に表示されますが、複数の結果`Start`状態とする前に`Close()`が呼び出されます。|
|`SingleResult`|後に示す 1 つの結果、`Complete`イベントが発生します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** async.h

**名前空間:** Microsoft::wrl

## <a name="see-also"></a>関連項目

[Microsoft::WRL 名前空間](microsoft-wrl-namespace.md)