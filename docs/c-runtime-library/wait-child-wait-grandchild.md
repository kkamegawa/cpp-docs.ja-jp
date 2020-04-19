---
title: _WAIT_CHILD、_WAIT_GRANDCHILD
ms.date: 11/04/2016
f1_keywords:
- _WAIT_GRANDCHILD
- WAIT_CHILD
- WAIT_GRANDCHILD
- _WAIT_CHILD
helpviewer_keywords:
- WAIT_CHILD constant
- WAIT_GRANDCHILD constant
- _WAIT_CHILD constant
- _WAIT_GRANDCHILD constant
ms.assetid: 7acd96fa-d118-4339-bb00-e5afaf286945
ms.openlocfilehash: 98858058add6a0a11d4f9331989c6816e38130aa
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57745051"
---
# <a name="waitchild-waitgrandchild"></a>_WAIT_CHILD、_WAIT_GRANDCHILD

## <a name="syntax"></a>構文

```
#include <process.h>
```

## <a name="remarks"></a>解説

`_cwait` 関数は、あらゆるプロセスで他のすべてのプロセスを待機するために使用できます (プロセス ID がわかっている場合)。 アクションの引数は、次の値のいずれかになります。

|定数|説明|
|--------------|-------------|
|`_WAIT_CHILD`|呼び出しプロセスは、指定した新しいプロセスが終了するまで待機します。|
|`_WAIT_GRANDCHILD`|呼び出しプロセスは、指定した新しいプロセスとその新しいプロセスによって生成されたすべてのプロセスが終了するまで待機します。|

## <a name="see-also"></a>関連項目

[_cwait](../c-runtime-library/reference/cwait.md)<br/>
[グローバル定数](../c-runtime-library/global-constants.md)
