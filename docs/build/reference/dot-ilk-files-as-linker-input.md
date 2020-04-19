---
title: リンカー入力としての .ilk ファイル
ms.date: 11/04/2016
helpviewer_keywords:
- ILK files
- .ilk files
ms.assetid: 7324c104-9e5d-423d-b268-b59f92607bf2
ms.openlocfilehash: 252c1cd6e17346954fce7ebf16134246da76ba57
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293850"
---
# <a name="ilk-files-as-linker-input"></a>リンカー入力としての .ilk ファイル

段階的にリンクする場合、リンクは、最初のインクリメンタル リンク中に作成された .ilk 状態ファイルを更新します。 このファイルが .exe ファイルまたは .dll ファイルとして同じ基本名と拡張子 .ilk が。 以降のインクリメンタル リンク時に、リンクは .ilk ファイルを更新します。 .Ilk ファイルが見つからない場合、リンクがフル リンクを実行し、新しい .ilk ファイルを作成します。 .Ilk ファイルが使用できない場合は、リンクはノンインクリメンタルのリンクを実行します。 詳細については、インクリメンタル リンクは、次を参照してください。、[インクリメンタル リンクを行う (/incremental)](incremental-link-incrementally.md)オプション。

## <a name="see-also"></a>関連項目

[LINK の入力ファイル](link-input-files.md)<br/>
[MSVC リンカー オプション](linker-options.md)
