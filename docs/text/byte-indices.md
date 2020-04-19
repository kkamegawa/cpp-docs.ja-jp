---
title: バイト インデックス
ms.date: 11/04/2016
helpviewer_keywords:
- MBCS [C++], byte indices
- byte indices [C++]
ms.assetid: f6e7774a-86c6-41c2-89e3-74fd46432e47
ms.openlocfilehash: 5305a977c23d7a978a89c84809cc6fab8c5731eb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410723"
---
# <a name="byte-indices"></a>バイト インデックス

次のヒントを使用します。

- バイト単位でインデックスの操作を文字列には、ポインター操作と同様の問題を表示します。 この例では、円記号の文字列をスキャンを検討してください。

    ```cpp
    while ( rgch[ i ] != '\\' )
        i++;
    ```

   末尾バイト、先行バイトではありません、このインデックスの可能性があり、したがってそれを指して可能性がありますいないを`character`します。

- 使用して、 [_mbclen](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)前の問題を解決する関数。

    ```cpp
    while ( rgch[ i ] != '\\' )
        i += _mbclen ( rgch + i );
    ```

   これは、正しくため先行バイトにインデックスを作成する、`character`します。 `_mbclen`関数 (1 つまたは 2 バイト) 文字のサイズを決定します。

## <a name="see-also"></a>関連項目

[MBCS のプログラミングについて](../text/mbcs-programming-tips.md)<br/>
[文字列の最後の文字](../text/last-character-in-a-string.md)
