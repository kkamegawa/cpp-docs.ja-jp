---
title: リンカー入力としての .res ファイル
ms.date: 11/04/2016
helpviewer_keywords:
- RES files as linker input
- .res files as linker input
- linking [C++], resource files
- resource files, linking
ms.assetid: 9c37ab00-97df-4d9a-91cd-6bf132970683
ms.openlocfilehash: 68bb9da55faa7e41d743e1f3a45ca4b79f7f2242
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293148"
---
# <a name="res-files-as-linker-input"></a>リンカー入力としての .res ファイル

プログラムをリンクするときに、.res ファイルを指定できます。 リソース コンパイラ (RC) では、.res ファイルが作成されます。 リンクは、COFF に .res ファイルを自動的に変換します。 CVTRES.exe ツールは、LINK.exe と同じディレクトリ内、または、PATH 環境変数で指定したディレクトリである必要があります。

## <a name="see-also"></a>関連項目

[LINK の入力ファイル](link-input-files.md)<br/>
[MSVC リンカー オプション](linker-options.md)
