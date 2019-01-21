---
title: ヒープ定数
ms.date: 11/04/2016
f1_keywords:
- _HEAPBADPTR
- _HEAPEMPTY
- _HEAPBADBEGIN
- _HEAPOK
- _HEAPBADNODE
- _HEAPEND
helpviewer_keywords:
- _HEAPOK constants
- _HEAPEND constants
- HEAPBADBEGIN constants
- _HEAPBADNODE constants
- HEAPBADNODE constants
- HEAPBADPTR constants
- _HEAPEMPTY constants
- HEAPEND constants
- HEAPOK constants
- HEAPEMPTY constants
- _HEAPBADBEGIN constants
- _HEAPBADPTR constants
- heap constants
ms.assetid: 3f751bb9-2dc4-486f-b5f5-9061c96d3754
ms.openlocfilehash: b8783a5826376a65cb71444e2d64c61b6938eab8
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220219"
---
# <a name="heap-constants"></a>ヒープ定数

## <a name="syntax"></a>構文

```
#include <malloc.h>
```

## <a name="remarks"></a>コメント

これらの定数は、ヒープの状態を示す戻り値を提供します。

|定数|説明|
|--------------|-------------|
|`_HEAPBADBEGIN`|初期ヘッダー情報が見つからないか無効です。|
|`_HEAPBADNODE`|不適切なノードが検出されたか、ヒープが破損しています。|
|`_HEAPBADPTR`|**_HEAPINFO** 構造体の **_pentry** フィールドに、ヒープへの有効なポインターが含まれていません (`_heapwalk` ルーチンのみ)。|
|`_HEAPEMPTY`|ヒープが初期化されていません。|
|`_HEAPEND`|ヒープの末尾に正常に到達しました (`_heapwalk` ルーチンのみ)。|
|`_HEAPOK`|ヒープに一貫性があります (`_heapset` ルーチンと `_heapchk` ルーチンのみ)。 これまでのところエラーはありません。**_HEAPINFO** 構造体に、次のエントリに関する情報が含まれています (`_heapwalk` ルーチンのみ)。|

## <a name="see-also"></a>「

[_heapchk](../c-runtime-library/reference/heapchk.md)<br/>
[_heapset](../c-runtime-library/heapset.md)<br/>
[_heapwalk](../c-runtime-library/reference/heapwalk.md)<br/>
[グローバル定数](../c-runtime-library/global-constants.md)
