---
title: 必要な値の計算
ms.date: 11/04/2016
helpviewer_keywords:
- helper functions, calculating necessary values
ms.assetid: 4f037d0f-881a-4a48-a9d2-9f8872dfccb7
ms.openlocfilehash: 75952bbcdf823aa675b35702841c81e511105ca8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272651"
---
# <a name="calculating-necessary-values"></a>必要な値の計算

2 つの重要な情報は、遅延読み込みヘルパー ルーチンによって計算する必要があります。 そのために、2 つのインライン関数にはこの情報を計算するための delayhlp.cpp です。

- 1 つ目は、(インポート アドレス テーブル (IAT)、バインドされたインポート アドレス テーブル (BIAT)、およびバインドされていないインポート アドレス テーブル (UIAT))、3 つの異なるテーブルにインポートする現在のインデックスを計算します。

- 2 つ目は、有効な IAT のインポートの数をカウントします。

```cpp
// utility function for calculating the index of the current import
// for all the tables (INT, BIAT, UIAT, and IAT).
__inline unsigned
IndexFromPImgThunkData(PCImgThunkData pitdCur, PCImgThunkData pitdBase) {
    return pitdCur - pitdBase;
    }

// utility function for calculating the count of imports given the base
// of the IAT. NB: this only works on a valid IAT!
__inline unsigned
CountOfImports(PCImgThunkData pitdBase) {
    unsigned        cRet = 0;
    PCImgThunkData  pitd = pitdBase;
    while (pitd->u1.Function) {
        pitd++;
        cRet++;
        }
    return cRet;
    }
```

## <a name="see-also"></a>関連項目

[ヘルパー関数について](understanding-the-helper-function.md)
