---
title: _CRT_DISABLE_PERFCRIT_LOCKS
ms.date: 11/04/2016
f1_keywords:
- _CRT_DISABLE_PERFCRIT_LOCKS
- CRT_DISABLE_PERFCRIT_LOCKS
helpviewer_keywords:
- CRT_DISABLE_PERFCRIT_LOCKS constant
- _CRT_DISABLE_PERFCRIT_LOCKS constant
ms.assetid: 36cc2d86-cdb1-4b2b-a03c-c0d3818e7c6f
ms.openlocfilehash: b6f4d8dee5577e88aa59af9bff017aab0c7eef89
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57740255"
---
# <a name="crtdisableperfcritlocks"></a>_CRT_DISABLE_PERFCRIT_LOCKS

I/O 操作でパフォーマンスが重要なロックを無効にします。

## <a name="syntax"></a>構文

```
#define _CRT_DISABLE_PERFCRIT_LOCKS
```

## <a name="remarks"></a>解説

このシンボルを定義すると、すべての I/O 操作でシングル スレッドの I/O モデルを前提とすることで、シングル スレッドの I/O バウンド プログラムのパフォーマンスを改善できます。 詳細については、「[マルチスレッド ライブラリのパフォーマンス](../c-runtime-library/multithreaded-libraries-performance.md)」をご覧ください。

## <a name="see-also"></a>関連項目

[グローバル定数](../c-runtime-library/global-constants.md)
