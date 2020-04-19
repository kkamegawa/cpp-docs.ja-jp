---
title: optimize プラグマ
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.optimize
- optimize_CPP
helpviewer_keywords:
- pragmas, optimize
- optimize pragma
ms.assetid: cb13c1cc-186a-45bc-bee7-95a8de7381cc
ms.openlocfilehash: 6d7b99b7a72c133d56a209cf42fa9ef670a4a7f9
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220518"
---
# <a name="optimize-pragma"></a>optimize プラグマ

関数ごとの最適化を指定します。

## <a name="syntax"></a>構文

> **最適化 #pragma ("** [*最適化-リスト*] **"、** { **on** | **off** } **)**

## <a name="remarks"></a>Remarks

**Optimize**プラグマは関数の外に置く必要があります。 このメソッドは、プラグマが検出された後に定義された最初の関数で有効になります。 **On**引数と**off**引数は、*最適化リスト*に指定されているオプションを有効または無効にします。

*最適化リスト*には、次の表に示すパラメーターの0個以上を指定できます。

### <a name="parameters-of-the-optimize-pragma"></a>optimize プラグマのパラメーター

| パラメーター | 最適化の種類 |
|--------------------|--------------------------|
| **g** | グローバル最適化を有効にします。 |
| **s**または**t** | マシン語コードの省略シーケンスまたは高速シーケンスを指定します。 |
| **y** | プログラム スタックにフレーム ポインターを生成します。 |

これらのパラメーターは、 [/o](../build/reference/o-options-optimize-code.md)コンパイラオプションで使用される文字と同じです。 たとえば、次のプラグマは `/Os` コンパイラ オプションと等価です。

```cpp
#pragma optimize( "s", on )
```

**Optimize**プラグマを空の文字列 ( **""** ) と共に使用することは、ディレクティブの特殊な形式です。

**Off**パラメーターを使用すると、すべての最適化、 **g**、 **s**、 **t**、および**y**がオフになります。

**On**パラメーターを使用すると、 [/o](../build/reference/o-options-optimize-code.md)コンパイラオプションを使用して指定した最適化がリセットされます。

```cpp
#pragma optimize( "", off )
/* unoptimized code section */
#pragma optimize( "", on )
```

## <a name="see-also"></a>関連項目

[プラグマディレクティブと __ プラグマキーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
