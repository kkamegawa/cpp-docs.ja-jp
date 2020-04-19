---
title: __readgsbyte、__readgsdword、__readgsqword、__readgsword
ms.date: 09/02/2019
f1_keywords:
- __readgsbyte
- __readgsdword
- __readgsqword
- __readgsword
helpviewer_keywords:
- __readgsword intrinsic
- __readgsdword intrinsic
- __readgsqword intrinsic
- __readgsbyte intrinsic
ms.assetid: f822632d-854c-4558-a71b-cdfc3eea2236
ms.openlocfilehash: 278f1de33a7e01c5893217ddd8aaa22e68cf0c94
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222356"
---
# <a name="__readgsbyte-__readgsdword-__readgsqword-__readgsword"></a>__readgsbyte、__readgsdword、__readgsqword、__readgsword

**Microsoft 固有の仕様**

GS セグメントの先頭を基準としたオフセットによって指定された場所からメモリを読み取ります。

## <a name="syntax"></a>構文

```C
unsigned char __readgsbyte(
   unsigned long Offset
);
unsigned short __readgsword(
   unsigned long Offset
);
unsigned long __readgsdword(
   unsigned long Offset
);
unsigned __int64 __readgsqword(
   unsigned long Offset
);
```

### <a name="parameters"></a>パラメーター

*影*\
からの`GS`先頭から読み取るオフセット。

## <a name="return-value"></a>戻り値

位置`GS:[Offset]`にある byte、word、double word、または quadword のメモリの内容 (呼び出される関数の名前で示されます)。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__readgsbyte`|x64|
|`__readgsdword`|x64|
|`__readgsqword`|x64|
|`__readgsword`|x64|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

これらのルーチンは、組み込み関数としてのみ使用できます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[__ writ/sbyte、 \_/writ、 \_sqword、/writ/sqword \_](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)\
[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
