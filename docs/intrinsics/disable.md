---
title: _disable
ms.date: 09/02/2019
f1_keywords:
- _disable_cpp
- _disable
helpviewer_keywords:
- _disable intrinsic
- rsm instruction
- disable intrinsic
ms.assetid: 52da3df9-815c-4524-9839-6d1742cff5c6
ms.openlocfilehash: 94be850e1d494ff62df84922b46f28481be68314
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216824"
---
# <a name="_disable"></a>_disable

**Microsoft 固有の仕様**

割り込みを無効にします。

## <a name="syntax"></a>構文

```C
void _disable(void);
```

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`_disable`|x86、ARM、x64、ARM64|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

`_disable` は、プロセッサに対して割り込みフラグをクリアするように指示します。 x86 システムでは、この関数は割り込みフラグのクリア (`cli`) 命令を生成します。

この関数はカーネル モードのみで使用できます。 ユーザー モードで使用した場合は、実行時に特権命令例外がスローされます。

ARM および ARM64 プラットフォームでは、このルーチンは組み込みとしてのみ使用できます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
