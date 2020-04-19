---
title: ファイルの読み書き
ms.date: 11/04/2016
helpviewer_keywords:
- CFile class [MFC], objects
- examples [MFC], reading files
- files [MFC], writing to
- examples [MFC], writing to files
- files [MFC], reading
- MFC, file operations
- CFile class [MFC], reading and writing CFile objects
- reading files
- writing to files [MFC]
ms.assetid: cac0c826-ba56-495f-99b3-ce6336f65763
ms.openlocfilehash: ab1ddc58ec6cc2b67e5843f46afbead3ead54eba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324260"
---
# <a name="reading-and-writing-files"></a>ファイルの読み書き

C ランタイム ライブラリのファイル処理関数を使用した場合は、MFC の読み取りと書き込み操作が使い慣れた表示されます。 この記事では、直接読み取りと書き込みに直接について説明します、`CFile`オブジェクト。 ことができますも行うバッファリングによるファイル I/O、 [CArchive](../mfc/reference/carchive-class.md)クラス。

#### <a name="to-read-from-and-write-to-the-file"></a>ファイルを読み書きする

1. 使用して、`Read`と`Write`ファイルにデータを読み書きするメンバー関数。

     \- または -

1. `Seek`メンバー関数は、ファイル内の特定のオフセットに移動するために使用できることもできます。

`Read` 読み取るバイト数をバッファーへのポインターを受け取るし、実際に読み取られたバイト数を返します。 必要なバイト数読み取れなかったため、ファイルの終わり (EOF) に達すると、実際に読み取られたバイト数が返されます。 読み取りエラーが発生した場合、例外がスローされます。 `Write` ような`Read`が書き込まれたバイト数が返されません。 指定すると、すべてのバイトを書き込んでいませんなど、書き込みエラーが発生した場合、例外がスローされます。 有効ながある場合`CFile`オブジェクトの場合からの読み取りまたは書き込みを次の例に示すようにすることができます。

[!code-cpp[NVC_MFCFiles#2](../atl-mfc-shared/reference/codesnippet/cpp/reading-and-writing-files_1.cpp)]

> [!NOTE]
>  通常、内の入力/出力操作を実行する必要があります、**try**/**catch**例外処理ブロック。 詳細については、次を参照してください。[例外処理 (MFC)](../mfc/exception-handling-in-mfc.md)します。

## <a name="see-also"></a>関連項目

[ファイル](../mfc/files-in-mfc.md)
