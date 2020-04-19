---
title: common_type 構造体
ms.date: 11/04/2016
f1_keywords:
- chrono/std::common_type
ms.assetid: 2b42722c-c3dc-4d62-8613-0271e52b6f00
ms.openlocfilehash: cef9b1fb6bc2723de1202b63ddc711ddd39f0d97
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689803"
---
# <a name="common_type-structure"></a>common_type 構造体

[Duration](../standard-library/duration-class.md)と[time_point](../standard-library/time-point-class.md)のインスタンス化のためのクラステンプレート[common_type](../standard-library/common-type-class.md)の特殊化について説明します。

## <a name="syntax"></a>構文

```cpp
template <class Rep1, class Period1,
    class Rep2, class Period2>
struct common_type
<chrono::duration<Rep1, Period1>,
chrono::duration<Rep2, Period2>>;

template <class Clock,
    class Duration1, class Duration2>
struct common_type
<chrono::time_point<Clock, Duration1>,
chrono::time_point<Clock, Duration2>>;
```

## <a name="requirements"></a>［要件］

**ヘッダー:** \<chrono >

**名前空間:** std

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)
