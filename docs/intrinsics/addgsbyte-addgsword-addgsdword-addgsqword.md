---
title: __addgsbyte、__addgsword、__addgsdword、__addgsqword
ms.date: 09/02/2019
f1_keywords:
- __addgsdword
- __addgsqword
- __addgsword_cpp
- __addgsword
- __addgsbyte_cpp
- __addgsqword_cpp
- __addgsbyte
- __addgsdword_cpp
helpviewer_keywords:
- __addgsword intrinsic
- __addgsqword intrinsic
- __addgsdword intrinsic
- __addgsbyte intrinsic
ms.assetid: 4fa03e69-d849-49ed-ba37-1d3aa23c2a21
ms.openlocfilehash: 5dddd8b4a887dc0e01107f8c1036a399b4e52d2e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221079"
---
# <a name="__addgsbyte-__addgsword-__addgsdword-__addgsqword"></a>__addgsbyte、__addgsword、__addgsdword、__addgsqword

**Microsoft 固有の仕様**

`GS`セグメントの先頭を基準としたオフセットによって指定されたメモリ位置に値を追加します。

## <a name="syntax"></a>構文

```C
void __addgsbyte(
   unsigned long Offset,
   unsigned char Data
);
void __addgsword(
   unsigned long Offset,
   unsigned short Data
);
void __addgsdword(
   unsigned long Offset,
   unsigned long Data
);
void __addgsqword(
   unsigned long Offset,
   unsigned __int64 Data
);
```

### <a name="parameters"></a>パラメーター

*影*\
からの`GS`先頭からのオフセット。

*データ*\
からメモリ位置に追加する値。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__addgsbyte`|x64|
|`__addgsword`|x64|
|`__addgsdword`|x64|
|`__addgsqword`|x64|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

これらのルーチンは、組み込み関数としてのみ使用できます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[__ インシデント gsbyte \_、visual ソード、 \_ \_または visual sqword (_t)](../intrinsics/incgsbyte-incgsword-incgsdword-incgsqword.md)\
[__ readgsbyte、 \_( \_readgsdword)、readgsqword、 \_readgソード](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)\
[__ writ/sbyte、 \_/writ、 \_sqword、/writ/sqword \_](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)\
[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
