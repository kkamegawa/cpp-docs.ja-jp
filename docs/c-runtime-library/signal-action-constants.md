---
title: signal のアクション定数
ms.date: 11/04/2016
f1_keywords:
- SIG_IGN
- SIG_DFL
helpviewer_keywords:
- signal action constants
- SIG_IGN constant
- SIG_DFL constant
ms.assetid: c3cb4f15-d39e-4d9d-84f9-0d33e3eb5993
ms.openlocfilehash: 4ff79626d576a05744336d36f99caf95d9b9902d
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743870"
---
# <a name="signal-action-constants"></a>signal のアクション定数

割り込みシグナルを受信したときに実行されるアクションは、`func` の値によって異なります。

## <a name="syntax"></a>構文

```
#include <signal.h>
```

## <a name="remarks"></a>解説

`func` 引数は、関数のアドレス、または SIGNAL.H に定義されている以下のマニフェスト定数のいずれかにする必要があります。

|||
|-|-|
| `SIG_DFL`  | システム既定の応答を使用します。 呼び出し元のプログラムがストリーム I/O を使用している場合、ランタイム ライブラリによって作成されるバッファーはフラッシュされません。  |
| `SIG_IGN`  | 割り込みシグナルを無視します。 プロセスの浮動小数点状態が未定義のままになるため、この値を `SIGFPE` に指定しないでください。  |
| `SIG_SGE`  | シグナルでエラーが発生したことを示します。  |
| `SIG_ACK`  | 受信確認を受け取ったことを示します。  |
| `SIG_ERR`  | エラーが発生したことを示すシグナルからの戻り値の型。  |

## <a name="see-also"></a>関連項目

[signal](../c-runtime-library/reference/signal.md)<br/>
[グローバル定数](../c-runtime-library/global-constants.md)
