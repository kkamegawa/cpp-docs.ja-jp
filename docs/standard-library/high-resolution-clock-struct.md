---
title: high_resolution_clock 構造体 |Microsoft Docs
ms.custom: ''
ms.date: 05/22/2018
ms.technology: cpp-standard-libraries
ms.topic: reference
f1_keywords:
- chrono/std::chrono::high_resolution_clock
dev_langs:
- C++
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0b00b20e7cea4fa24b37ad33d5536eb9844e6953
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269124"
---
# <a name="steady_clock-struct"></a>steady_clock 構造体

表す、 *high_resolution*クロック。

## <a name="syntax"></a>構文

```cpp
class high_resolution_clock
```

## <a name="members"></a>メンバー

### <a name="typedefs"></a>Typedef

|名前|説明|
|----------|-----------------|
|`duration`|シノニム`nanoseconds`で定義された\<chrono >。|
|`period`|シノニム`nano`で定義された\<ratio >。|
|`rep`|シノニム**long** **long**に含まれているインスタンス化のクロック ティック数を表すために使用される型`duration`します。|
|`time_point`|`chrono::time_point<high_resolution_clock>` と同義。|

## <a name="functions"></a>関数

|||
|-|-|
|`now`|として現在の時刻を返します、`time_point`値。|

## <a name="constants"></a>定数

|名前|説明|
|----------|-----------------|
|`is_steady`|保持している**true**します。 `high_resolution_clock` は*安定*しています。|
