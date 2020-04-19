---
title: 共有モード定数
ms.date: 11/04/2016
f1_keywords:
- _SH_DENYNO
- _SH_DENYRD
- _SH_DENYRW
- _SH_DENYWR
- _SH_COMPAT
helpviewer_keywords:
- _SH_DENYRW constant
- SH_DENYRD constant
- _SH_COMPAT constant
- _SH_DENYRD constant
- SH_DENYRW constant
- sharing constants
- SH_DENYNO constant
- _SH_DENYWR constant
- SH_DENYWR constant
- _SH_DENYNO constant
- SH_COMPAT constant
ms.assetid: 95fadc3a-55dc-473d-98b5-e8211900465d
ms.openlocfilehash: dc27b3af0d430aedb8159b4591004f46d197ccd5
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57751545"
---
# <a name="sharing-constants"></a>共有モード定数

ファイル共有モードの定数。

## <a name="syntax"></a>構文

```
#include <share.h>
```

## <a name="remarks"></a>解説

*shflag* 引数で、1 つまたは複数のマニフェスト定数で構成される共有モードを決定します。 これらは、*oflag* 引数と組み合わせて使用できます (「[ファイル定数](../c-runtime-library/file-constants.md)」をご覧ください)。

次の表に、定数とそれぞれの意味を示します。

|定数|説明|
|--------------|-------------|
|`_SH_DENYRW`|ファイルへの読み取りおよび書き込みアクセスを拒否|
|`_SH_DENYWR`|ファイルへの書き込みアクセスを拒否|
|`_SH_DENYRD`|ファイルへの読み取りアクセスを拒否|
|`_SH_DENYNO`|読み取りおよび書き込みアクセスを許可|
|`_SH_SECURE`|セキュリティで保護されたモードを設定 (共有読み取り、排他的な書き込みアクセス)。|

## <a name="see-also"></a>関連項目

[_sopen、_wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[_fsopen、_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)<br/>
[グローバル定数](../c-runtime-library/global-constants.md)
