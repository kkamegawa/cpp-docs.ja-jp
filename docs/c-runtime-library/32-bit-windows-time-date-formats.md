---
title: 32 ビット Windows の時刻と日付の形式
ms.date: 11/04/2016
f1_keywords:
- vc.time
helpviewer_keywords:
- 32-bit Windows
ms.assetid: ef1589db-84d7-4b24-8799-7c7a22cfe2bf
ms.openlocfilehash: 4827f82df08273dfa369d6242b9fe2be84875128
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57746358"
---
# <a name="32-bit-windows-timedate-formats"></a>32 ビット Windows の時刻と日付の形式

ファイルの時刻と日付は、ビット フィールドに符号なし整数を利用し、個別に保存されます。 ファイルの時刻と日付は次のようにパックされます。

### <a name="time"></a>時刻

|ビット位置:|0   1   2   3   4|5   6   7   8   9   A|B   C   D   E   F|
|-------------------|-----------------------|---------------------------|-----------------------|
|長さ:|5|6|5|
|コンテンツ:|時間|分|2 秒増加|
|値範囲:|0-23|0-59|2 秒間隔 (0-29)|

### <a name="date"></a>日付

|ビット位置:|0   1   2   3   4   5   6|7   8   9   A|B   C   D   E   F|
|-------------------|-------------------------------|-------------------|-----------------------|
|長さ:|7|4|5|
|コンテンツ:|年|月|日|
|値範囲:|0-119|1-12|1-31|
||(1980 に対して)|||

## <a name="see-also"></a>関連項目

[グローバル定数](../c-runtime-library/global-constants.md)
