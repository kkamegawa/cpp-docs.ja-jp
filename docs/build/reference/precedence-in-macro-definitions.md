---
title: マクロ定義の優先順位
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, precedence in macro definitions
- macros, precedence
ms.assetid: 0c13182d-83cb-4cbd-af2d-f4c916b62aeb
ms.openlocfilehash: 38a653a9f460beae81f9f88ea457870d30f25339
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320163"
---
# <a name="precedence-in-macro-definitions"></a>マクロ定義の優先順位

マクロに複数の定義がある場合は、NMAKE が最も高い優先順位の定義を使用します。 次に、高いものから、優先順位の順序を示します。

1. コマンドラインで定義されているマクロ

1. マクロは、メイクファイルで定義されているか、ファイルを含める

1. 継承の環境変数マクロ

1. Tools.ini ファイルで定義されているマクロ

1. 定義済みマクロなど[CC](command-macros-and-options-macros.md)と[AS](command-macros-and-options-macros.md)

/E を使用して、同じ名前のメイクファイルのマクロをオーバーライドする環境変数から継承されたマクロが発生します。 使用 **!UNDEF**コマンドラインを上書きします。

## <a name="see-also"></a>関連項目

[NMAKE マクロの定義](defining-an-nmake-macro.md)
