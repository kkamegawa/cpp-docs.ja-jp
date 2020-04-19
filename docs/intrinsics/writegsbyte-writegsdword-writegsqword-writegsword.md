---
title: __writegsbyte、__writegsdword、__writegsqword、__writegsword
ms.date: 09/02/2019
f1_keywords:
- __writegsbyte
- __writegsqword
- __writegsdword
- __writegsword
helpviewer_keywords:
- __writegsqword intrinsic
- __writegsbyte intrinsic
- __writegsword intrinsic
- __writegsdword intrinsic
ms.assetid: 7746cf6d-2259-4139-9aab-c07dd75c8037
ms.openlocfilehash: 7b9e812776e9b2bb0820905d088111669096db64
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221204"
---
# <a name="__writegsbyte-__writegsdword-__writegsqword-__writegsword"></a>__writegsbyte、__writegsdword、__writegsqword、__writegsword

**Microsoft 固有の仕様**

GS セグメントの先頭を基準としたオフセットによって指定された位置にメモリを書き込みます。

## <a name="syntax"></a>構文

```C
void __writegsbyte(
   unsigned long Offset,
   unsigned char Data
);
void __writegsword(
   unsigned long Offset,
   unsigned short Data
);
void __writegsdword(
   unsigned long Offset,
   unsigned long Data
);
void __writegsqword(
   unsigned long Offset,
   unsigned __int64 Data
);
```

### <a name="parameters"></a>パラメーター

*影*\
から書き込み先の GS の先頭からのオフセット。

*データ*\
から書き込む値。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__writegsbyte`|x64|
|`__writegsdword`|x64|
|`__writegsqword`|x64|
|`__writegsword`|x64|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

これらのルーチンは、組み込み関数としてのみ使用できます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[__ readgsbyte、 \_( \_readgsdword)、readgsqword、 \_readgソード](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)\
[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
