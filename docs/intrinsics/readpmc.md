---
title: __readpmc
ms.date: 09/02/2019
f1_keywords:
- __readpmc
helpviewer_keywords:
- Read Performance Monitoring Counters instruction
- __readpmc intrinsic
- rdpmc instruction
ms.assetid: 14ed45a6-28b6-4635-8437-a597c04b43d4
ms.openlocfilehash: af0f1874d991771423ddebfedd4624cd0b71760f
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221033"
---
# <a name="__readpmc"></a>__readpmc

**Microsoft 固有の仕様**

カウンターによって指定されたパフォーマンス監視カウンターを読み取る命令を生成します。`rdpmc`

## <a name="syntax"></a>構文

```C
unsigned __int64 __readpmc(
   unsigned long counter
);
```

### <a name="parameters"></a>パラメーター

*対抗*\
から読み取るパフォーマンスカウンター。

## <a name="return-value"></a>戻り値

指定したパフォーマンスカウンターの値。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__readpmc`|x86、x64|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

組み込みはカーネルモードでのみ使用でき、ルーチンは組み込みとしてのみ使用できます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
