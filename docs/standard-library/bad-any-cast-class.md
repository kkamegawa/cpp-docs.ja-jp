---
title: bad_any_cast クラス
ms.date: 04/04/2019
f1_keywords:
- any/std::bad_any_cast
- any/std::bad_any_cast::what
helpviewer_keywords:
- any/std::bad_any_cast
- any/std::bad_any_cast::what
ms.openlocfilehash: 5172281d1918a8b4ac33bcf412bf4be82b04ef56
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268684"
---
# <a name="badanycast-class"></a>bad_any_cast クラス

オブジェクトが、失敗したによってスローされた`any_cast`します。

## <a name="syntax"></a>構文

```cpp
class bad_any_cast
```

### <a name="member-functions"></a>メンバー関数

|||
|-|-|
|[どのような](#what)|型を返します。|

## <a name="what"></a> どのような

型を返します。

```cpp
const char* what() const noexcept override;
```
