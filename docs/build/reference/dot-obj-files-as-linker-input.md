---
title: リンカー入力としての .obj ファイル
ms.date: 12/29/2017
helpviewer_keywords:
- linker [C++], OBJ files as input
- object files, linker output
- OMF object files
- LINK tool [C++], .obj files
- COFF files
- OBJ files as linker input
- .obj files as linker input
ms.openlocfilehash: 304c9861b85be1925e48d47c6006fcbcdd41dc22
ms.sourcegitcommit: 5f276064779d90a4cfda758f89e0c0f1e4d1a188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2020
ms.locfileid: "75791598"
---
# <a name="obj-files-as-linker-input"></a>リンカー入力としての .obj ファイル

リンカーツール (LINK.EXE) は、COFF (Common Object File Format) 形式の .obj ファイルを受け入れます。

## <a name="remarks"></a>Remarks

Microsoft では、Common Object File Format について完全に説明しています。 詳細については、「 [PE 形式](/windows/win32/Debug/pe-format)」を参照してください。

## <a name="unicode-support"></a>Unicode のサポート

Visual Studio 2005 以降では、Microsoft MSVC compiler は、ISO/IEC C とC++標準で定義されているように、識別子で Unicode 文字をサポートしています。 以前のバージョンのコンパイラでは、識別子で ASCII 文字のみがサポートされていました。 関数、クラス、および静的変数の名前で Unicode をサポートするために、コンパイラとリンカーは、.obj ファイル内の COFF シンボルに Unicode UTF-8 エンコードを使用します。 UTF-8 エンコードは、以前のバージョンの Visual Studio で使用されている ASCII エンコードと upwardly 互換性があります。

コンパイラとリンカーの詳細については、「[コンパイラとリンカーでの Unicode のサポート](unicode-support-in-the-compiler-and-linker.md)」を参照してください。 Unicode 標準の詳細については、「 [unicode](https://home.unicode.org/)組織」を参照してください。

## <a name="see-also"></a>関連項目

[LINK の入力ファイル](link-input-files.md)<br/>
[MSVC リンカー オプション](linker-options.md)<br/>
[Unicode のサポート](../../text/support-for-unicode.md)<br/>
[コンパイラおよびリンカーでの Unicode のサポート](unicode-support-in-the-compiler-and-linker.md)<br/>
[Unicode 標準](https://home.unicode.org/)<br/>
[PE 形式](/windows/win32/Debug/pe-format)
