---
title: ファイル I/o クラス
ms.date: 11/04/2016
f1_keywords:
- vc.classes.file
helpviewer_keywords:
- disk file classes [MFC]
- stdio classes [MFC]
- OLE streams [MFC]
- I/O [MFC], MFC classes
- translated stream classes [MFC]
- file I/O classes [MFC]
- I/O [MFC], classes
- sockets classes [MFC]
- stream classes [MFC]
- memory file classes [MFC]
ms.assetid: 92821c3f-d9e1-47f6-98c9-3b632d86e811
ms.openlocfilehash: 914325ec56f0cae30c7293305496d65f358f2731
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405808"
---
# <a name="file-io-classes"></a>ファイル I/O クラス

これらのクラスは、従来のディスク ファイル、メモリ内のファイル、Active ストリーム、および Windows ソケットへのインターフェイスを提供します。 すべてのクラスから派生した`CFile`で使用できる、`CArchive`オブジェクトをシリアル化を実行します。

次のクラスを使用して、特に`CArchive`と`CFile`入力/出力の処理を記述する場合は、します。 通常これらのクラスから派生する必要はありません。 アプリケーション フレームワークの既定の実装を使用する場合、**オープン**と**保存**コマンドを**ファイル**メニューは、ファイル I/O を処理する (クラスを使用して`CArchive`)、ドキュメントをオーバーライドする場合に限り、`Serialize`関数を指定するがドキュメントの内容をシリアル化する方法に関する詳細情報します。 ファイルのクラスとシリアル化する方法の詳細については、記事を参照してください。 [MFC のファイル](../mfc/files-in-mfc.md)」および「[シリアル化](../mfc/serialization-in-mfc.md)します。

[CFile](../mfc/reference/cfile-class.md)<br/>
ディスクのバイナリ ファイルにファイルのインターフェイスを提供します。

[CStdioFile](../mfc/reference/cstdiofile-class.md)<br/>
提供、`CFile`テキスト モードでは、通常のバッファー済みストリーム ディスク ファイルへのインターフェイス。

[CMemFile](../mfc/reference/cmemfile-class.md)<br/>
提供、`CFile`メモリ内のファイルへのインターフェイス。

[CSharedFile](../mfc/reference/csharedfile-class.md)<br/>
提供、`CFile`共有メモリ内のファイルへのインターフェイス。

[COleStreamFile](../mfc/reference/colestreamfile-class.md)<br/>
COM を使用して`IStream`インターフェイスを提供する`CFile`複合ファイルにアクセスします。

[CSocketFile](../mfc/reference/csocketfile-class.md)<br/>
提供、 `CFile` Windows ソケット インターフェイス。

## <a name="related-classes"></a>関連するクラス

[CArchive](../mfc/reference/carchive-class.md)<br/>
使用と連携して、`CFile`永続的ストレージにシリアル化を通じてオブジェクトを実装するオブジェクト (を参照してください[cobject::serialize](../mfc/reference/cobject-class.md#serialize))。

[CArchiveException](../mfc/reference/carchiveexception-class.md)<br/>
アーカイブの例外。

[CFileException](../mfc/reference/cfileexception-class.md)<br/>
ファイル指向の例外。

[CFileDialog](../mfc/reference/cfiledialog-class.md)<br/>
開くか、ファイルを保存するのには、標準のダイアログ ボックスを提供します。

[CRecentFileList](../mfc/reference/crecentfilelist-class.md)<br/>
最近使用した (MRU) ファイルの一覧を保持します。

## <a name="see-also"></a>関連項目

[クラスの概要](../mfc/class-library-overview.md)
