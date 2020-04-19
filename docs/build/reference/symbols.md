---
title: /SYMBOLS
ms.date: 09/05/2018
f1_keywords:
- /symbols
helpviewer_keywords:
- symbols, dumping
- public symbols
- symbols, displaying COFF symbol table
- symbol tables
- SYMBOLS dumpbin option
- /SYMBOLS dumpbin option
- -SYMBOLS dumpbin option
ms.assetid: 34bcae90-4561-4c77-a80c-065508dec39a
ms.openlocfilehash: a47b7da9f0b01353ef15e8b5c070c19e7c521c37
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317706"
---
# <a name="symbols"></a>/SYMBOLS

```
/SYMBOLS
```

このオプションは、COFF シンボル テーブルを表示します。 シンボル テーブルは、すべてのオブジェクト ファイルに存在します。 COFF シンボル テーブルは、/DEBUG にリンクされている場合にのみ、イメージ ファイルに表示されます。

/SYMBOLS の出力の説明を次に示します。 /SYMBOLS 出力の意味については、winnt.h (IMAGE_SYMBOL および IMAGE_AUX_SYMBOL) または COFF ドキュメントではあります。

次のサンプルのダンプを指定します。

```
Dump of file main.obj
File Type: COFF OBJECT

COFF SYMBOL TABLE
000 00000000 DEBUG    notype       Filename     | .file
    main.cpp
002 000B1FDB ABS      notype       Static       | @comp.id
003 00000000 SECT1    notype       Static       | .drectve
    Section length     26, #relocs    0, #linenums    0, checksum 722C964F
005 00000000 SECT2    notype       Static       | .text
    Section length     23, #relocs    1, #linenums    0, checksum 459FF65F, selection    1 (pick no duplicates)
007 00000000 SECT2    notype ()    External     | _main
008 00000000 UNDEF    notype ()    External     | ?MyDump@@YAXXZ (void __cdecl MyDump(void))

String Table Size = 0x10 bytes

  Summary

         26 .drectve
         23 .text
```

## <a name="remarks"></a>Remarks

シンボルの番号で始まる行を次の説明では、ユーザーに関連する情報を含む列について説明します。

- 最初の 3 桁の数字は、シンボルのインデックス/数です。

- 3 番目の列には、セクターが含まれている場合*x*シンボルがオブジェクト ファイルのセクションで定義されています。 そのオブジェクトで定義されていないと、別の場所を解決する必要があります UNDEF が表示された場合。

- (静的、外部) の 5 番目の列は、シンボルが、そのオブジェクト内でのみ表示されるかどうかがパブリックかどうかを示します (表示されている外部)。 _Sym とのスタティック シンボルは、パブリック シンボル _sym; にリンクはありません。_sym という名前の関数の 2 つの異なるインスタンスになります。

番号付きの行の最後の列は、シンボル名は、装飾形式し非装飾します。

のみ、 [/HEADERS](headers.md) DUMPBIN オプションがで生成されたファイルで使用できる、 [/GL](gl-whole-program-optimization.md)コンパイラ オプション。

## <a name="see-also"></a>関連項目

[DUMPBIN オプション](dumpbin-options.md)
