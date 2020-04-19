---
title: プリプロセッサへのディレクティブ
ms.date: 11/04/2016
ms.assetid: adc6251e-cf6b-4508-bdbb-55f446c838d3
ms.openlocfilehash: 520d181c3a58ee2c626678a3afd9126f1ef183cc
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149038"
---
# <a name="directives-to-the-preprocessor"></a>プリプロセッサへのディレクティブ

"ディレクティブ" は、コンパイル前にプログラムのテキストに特定の操作を行うように C プリプロセッサに指示します。 [プリプロセッサ ディレクティブ](../preprocessor/preprocessor-directives.md)の詳細については、「*プリプロセッサ リファレンス*」を参照してください。 `#define` プリプロセッサ ディレクティブの使用例を次に示します。

```
#define MAX 100
```

このステートメントは、コンパイル前に `MAX` で `100` を置き換えるようコンパイラに指示します。 C コンパイラのプリプロセッサ ディレクティブは次のとおりです。

|#define|#endif|#ifdef|#line|
|--------------|-------------|-------------|------------|
|`#elif`|`#error`|**#ifndef**|**#pragma**|
|`#else`|`#if`|`#include`|`#undef`|

## <a name="see-also"></a>関連項目

[ソース ファイルとソース プログラム](../c-language/source-files-and-source-programs.md)
