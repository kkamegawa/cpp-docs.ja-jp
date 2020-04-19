---
title: __ud2
ms.date: 09/02/2019
f1_keywords:
- __ud2
helpviewer_keywords:
- UD2 instruction
- __ud2 intrinsic
ms.assetid: 0831cd5a-8b65-402e-bb57-11e1d5d7ffd2
ms.openlocfilehash: b5aa20804099af4d75dcc62a5e62ccc0d4a09566
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219762"
---
# <a name="__ud2"></a>__ud2

**Microsoft 固有の仕様**

未定義の命令を生成します。

## <a name="syntax"></a>構文

```C
void __ud2();
```

## <a name="remarks"></a>Remarks

定義されていない命令を実行すると、プロセッサは無効なオペコード例外を発生させます。

関数は`UD2`コンピューター命令と同じであり、カーネルモードでのみ使用できます。 `__ud2` 詳細については、「Intel Architecture Software Developer's Manual, Volume 2:命令セットリファレンス、「 [」を参照してください](https://software.intel.com/articles/intel-sdm)。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__ud2`|x86、x64|

**ヘッダーファイル**\<>

**Microsoft 固有の仕様はここまで**

## <a name="example"></a>例

次の例では、未定義の命令を実行して、例外を発生させます。 次に、例外ハンドラーは、リターンコードを0から1に変更します。

```cpp
// __ud2_intrinsic.cpp
#include <stdio.h>
#include <intrin.h>
#include <excpt.h>
// compile with /EHa

int main() {

// Initialize the return code to 0.
int ret = 0;

// Attempt to execute an undefined instruction.
  printf("Before __ud2(). Return code = %d.\n", ret);
  __try {
  __ud2();
  }

// Catch any exceptions and set the return code to 1.
  __except(EXCEPTION_EXECUTE_HANDLER){
  printf("  In the exception handler.\n");
  ret = 1;
  }

// Report the value of the return code.
  printf("After __ud2().  Return code = %d.\n", ret);
  return ret;
}
```

```Output
Before __ud2(). Return code = 0.
  In the exception handler.
After __ud2().  Return code = 1.
```

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
