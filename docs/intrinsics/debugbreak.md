---
title: __debugbreak
ms.date: 09/02/2019
f1_keywords:
- __debugbreak_cpp
- __debugbreak
helpviewer_keywords:
- breakpoints, __debugbreak intrinsic
- __debugbreak intrinsic
ms.assetid: 1d1e1c0c-891a-4613-ae4b-d790094ba830
ms.openlocfilehash: e4cf2c85818a878417c560ddb5a80f8690e60a93
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217927"
---
# <a name="__debugbreak"></a>__debugbreak

**Microsoft 固有の仕様**

コードのブレークポイントを発生させます。ここで、デバッガーを実行するように求めるメッセージがユーザーに表示されます。

## <a name="syntax"></a>構文

```C
void __debugbreak();
```

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|Header|
|---------------|------------------|------------|
|`__debugbreak`|x86、x64、ARM、ARM64|\<intrin.h>|

## <a name="remarks"></a>Remarks

[DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) `__debugbreak`のようなコンパイラ組み込みは、移植可能な Win32 によってブレークポイントを発生させます。

> [!NOTE]
> **/Clr**を指定してコンパイルすると`__debugbreak` 、を含む関数が MSIL にコンパイルされます。 `asm int 3` により、関数がネイティブにコンパイルされます。 詳細については、「 [__asm](../assembler/inline/asm.md)」を参照してください。

例えば:

```C
main() {
   __debugbreak();
}
```

上記のコードは、以下と似ています。

```C
main() {
   __asm {
      int 3
   }
}
```

このコードは x86 コンピューターにあります。

ARM64 `__debugbreak`では、組み込みは命令`brk #0xF000`にコンパイルされます。

このルーチンは、組み込みとしてのみ使用できます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)\
[キーワード](../cpp/keywords-cpp.md)
