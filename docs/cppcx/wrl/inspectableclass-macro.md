---
title: InspectableClass マクロ
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
ms.openlocfilehash: ee2a76edb967923a03ce6720b4163baf1cc48c32
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500477"
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
[TrustLevel](/windows/win32/api/inspectable/ne-inspectable-trustlevel)列挙値のいずれか。

## <a name="remarks"></a>Remarks

**InspectableClass**マクロは Windows ランタイム型でのみ使用できます。

## <a name="requirements"></a>必要条件

**Header:** を実装します。

**名前空間:** Microsoft:: WRL

## <a name="see-also"></a>関連項目

[RuntimeClass クラス](runtimeclass-class.md)