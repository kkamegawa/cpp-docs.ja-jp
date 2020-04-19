---
title: /IMPORTS (DUMPBIN)
ms.date: 11/04/2016
f1_keywords:
- /imports
helpviewer_keywords:
- IMPORTS dumpbin option
- /IMPORTS dumpbin option
- -IMPORTS dumpbin option
ms.assetid: 6a296216-2b1b-40f8-8736-cd4553a22456
ms.openlocfilehash: c8b0f88b38eb657fe4d3916ef0df13972e985cbe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291841"
---
# <a name="imports-dumpbin"></a>/IMPORTS (DUMPBIN)

```
/IMPORTS[:file]
```

このオプションは、Dll の一覧を表示します (どちらも静的にリンクされていると[遅延読み込み](linker-support-for-delay-loaded-dlls.md)) からこれらの各 Dll を実行可能ファイルまたは DLL を個別にインポートされるすべてインポートします。

省略可能な`file`仕様では、のみ、その DLL のインポートが表示されることを指定できます。 例:

```
dumpbin /IMPORTS:msvcrt.dll
```

## <a name="remarks"></a>Remarks

このオプションによって表示される出力は、 [/exports](dash-exports.md)出力します。

のみ、 [/HEADERS](headers.md) DUMPBIN オプションがで生成されたファイルで使用できる、 [/GL](gl-whole-program-optimization.md)コンパイラ オプション。

## <a name="see-also"></a>関連項目

[DUMPBIN オプション](dumpbin-options.md)
