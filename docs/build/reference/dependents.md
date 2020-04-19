---
title: /DEPENDENTS
ms.date: 07/15/2019
f1_keywords:
- /dependents
helpviewer_keywords:
- -DEPENDENTS dumpbin option
- /DEPENDENTS dumpbin option
- DEPENDENTS dumpbin option
ms.assetid: 9b31da2a-75ac-4bbf-a3f1-adf8b0ecbbb4
ms.openlocfilehash: 88f0062a6bbca3f9199a12f739c2ade5f9d912cd
ms.sourcegitcommit: 7f5b29e24e1be9b5985044a030977485fea0b50c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2019
ms.locfileid: "68299739"
---
# <a name="dependents"></a>/DEPENDENTS

イメージが関数をインポートするときに使用する Dll の名前をダンプします。 一覧を使用して、アプリと共に再配布する Dll を指定したり、不足している依存関係の名前を検索したりすることができます。

## <a name="syntax"></a>構文

> **/DEPENDENTS**

このオプションは、コマンドラインで指定したすべての実行可能ファイルに適用されます。 引数を受け取ることはありません。

## <a name="remarks"></a>Remarks

**/依存**関係オプションは、イメージが関数を出力にインポートするときに使用する dll の名前を追加します。 このオプションでは、インポートされた関数の名前はダンプされません。 インポートされた関数の名前を表示するには、 [/IMPORTS](imports-dumpbin.md)オプションを使用します。

[/GL](gl-whole-program-optimization.md) コンパイラ オプションで生成したファイルで使用できるのは、[/HEADERS](headers.md) DUMPBIN オプションだけです。

## <a name="example"></a>例

この例では、チュートリアルで[ビルドされたクライアント実行可能ファイルの **/依存**オプションの DUMPBIN 出力を示します。独自のダイナミックリンクライブラリ](../walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)を作成して使用します。

```cmd
C:\Users\username\Source\Repos\MathClient\Debug>dumpbin /DEPENDENTS MathClient.exe
Microsoft (R) COFF/PE Dumper Version 14.16.27032.1
Copyright (C) Microsoft Corporation.  All rights reserved.


Dump of file MathClient1322.exe

File Type: EXECUTABLE IMAGE

  Image has the following dependencies:

    MathLibrary.dll
    MSVCP140D.dll
    VCRUNTIME140D.dll
    ucrtbased.dll
    KERNEL32.dll

  Summary

        1000 .00cfg
        1000 .data
        2000 .idata
        1000 .msvcjmc
        3000 .rdata
        1000 .reloc
        1000 .rsrc
        8000 .text
       10000 .textbss
```

## <a name="see-also"></a>関連項目

[DUMPBIN オプション](dumpbin-options.md)
