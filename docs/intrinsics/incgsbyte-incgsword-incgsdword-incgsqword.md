---
title: __incgsbyte、__incgsword、__incgsdword、__incgsqword
ms.date: 09/02/2019
f1_keywords:
- __incgsdword
- __incgsqword_cpp
- __incgsword_cpp
- __incgsword
- __incgsbyte
- __incgsbyte_cpp
- __incgsqword
- __incgsdword_cpp
helpviewer_keywords:
- __incgsbyte intrinsic
- __incgsword intrinsic
- __incgsqword intrinsic
- __incgsdword intrinsic
ms.assetid: 06bfdf4f-7643-4fe0-8455-60ce3068073e
ms.openlocfilehash: 8b4e88b4ccd2cf1d2a3130e3a535de1c9a434320
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217797"
---
# <a name="__incgsbyte-__incgsword-__incgsdword-__incgsqword"></a>__incgsbyte、__incgsword、__incgsdword、__incgsqword

**Microsoft 固有の仕様**

`GS`セグメントの先頭を基準としたオフセットによって指定されたメモリ位置の値に1つを追加します。

## <a name="syntax"></a>構文

```C
void __incgsbyte(
   unsigned long Offset
);
void __incgsword(
   unsigned long Offset
);
void __incgsdword(
   unsigned long Offset
);
void __incgsqword(
   unsigned long Offset
);
```

### <a name="parameters"></a>パラメーター

*影*\
からの`GS`先頭からのオフセット。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__incgsbyte`|x64|
|`__incgsword`|x64|
|`__incgsdword`|x64|
|`__incgsqword`|x64|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

これらのルーチンは、組み込み関数としてのみ使用できます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[\_addgsbyte、 \_addgソード、 \_addgsdword、 \_(_s)](../intrinsics/addgsbyte-addgsword-addgsdword-addgsqword.md)\
[\_readgsbyte、 \_ \_readgsdword、readgsqword \_、readgソード](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)\
[\_writ(_s)、writ、sqword、writ/sqword \_、/writ/writ \_ \_](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)\
[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
