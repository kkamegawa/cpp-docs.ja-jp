---
title: InspectableClass マクロ
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
ms.openlocfilehash: cedf395ae98a423e0335851327b5fdda1a4bc7d6
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893276"
---
# <a name="inspectableclass-macro"></a>InspectableClass マクロ

ランタイム クラス名と信頼レベルを設定します。

## <a name="syntax"></a>構文

```cpp
InspectableClass(
   runtimeClassName,
   trustLevel)
```

### <a name="parameters"></a>パラメーター

*runtimeClassName*<br/>
ランタイム クラス名のテキスト形式の完全な名前です。

*trustLevel*<br/>
1 つ、 [TrustLevel](/windows/desktop/api/inspectable/ne-inspectable-trustlevel)列挙値。

## <a name="remarks"></a>Remarks

**InspectableClass**マクロは、Windows ランタイム型でのみ使用できます。

## <a name="requirements"></a>必要条件

**ヘッダー:** implements.h

**名前空間:** Microsoft::wrl

## <a name="see-also"></a>関連項目

[RuntimeClass クラス](runtimeclass-class.md)