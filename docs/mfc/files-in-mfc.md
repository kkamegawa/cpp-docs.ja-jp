---
title: MFC のファイル
ms.date: 11/04/2016
helpviewer_keywords:
- serialization [MFC], MFC files
- I/O [MFC], MFC classes
- files [MFC], MFC
- files [MFC], serialization
- binary access, binary file operations in MFC
- file I/O classes [MFC]
- I/O [MFC]
- persistence [MFC]
- MFC, file operations
- files [MFC], manipulating
- binary access [MFC]
ms.assetid: ae25e2c5-2859-4679-ab97-438824e93ce1
ms.openlocfilehash: cf53c498e61bdf0a233d7638649b30e498e27cc5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392857"
---
# <a name="files-in-mfc"></a>MFC のファイル

Microsoft Foundation Class ライブラリ (MFC) でクラス[CFile](../mfc/reference/cfile-class.md)標準ファイル I/O 操作を処理します。 この一連のトピックでは、開く、ファイルを閉じるだけでなく読み取りし、それらのファイルにデータを書き込む方法について説明します。 ファイルの状態の操作についても説明します。 ファイル内のデータの読み書きの代替方法としての MFC オブジェクト ベースのシリアル化機能を使用する方法については、記事を参照してください。[シリアル化](../mfc/serialization-in-mfc.md)します。

> [!NOTE]
>  MFC を使用すると`CDocument`オブジェクトの場合、フレームワークのシリアル化作業の多くが動作します。 具体的には、フレームワークは作成し、使用、`CFile`オブジェクト。 のみのオーバーライドでコードを記述する必要がある、`Serialize`クラスのメンバー関数`CDocument`します。

`CFile`クラスは、汎用のバイナリ ファイルの操作のインターフェイスを提供します。 `CStdioFile`と`CMemFile`クラスから派生した`CFile`と`CSharedFile`から派生したクラス`CMemFile`より専門的なファイル サービスを提供します。

MFC のファイルの処理に代わる方法の詳細については、次を参照してください。[ファイル処理](../c-runtime-library/file-handling.md)で、*ランタイム ライブラリ リファレンス*します。

については、派生した`CFile`クラスを参照してください、 [MFC 階層グラフ](../mfc/hierarchy-chart.md)します。

## <a name="what-do-you-want-to-do"></a>どうしたいんですか

*CFile を使用します。*

- [CFile でファイルを開く](../mfc/opening-files.md)

- [読み取りし、書き込みファイルの読み書き](../mfc/reading-and-writing-files.md)

- [CFile のファイルを閉じる](../mfc/closing-files.md)

- [アクセスのファイル状態の操作](../mfc/accessing-file-status.md)

*MFC のシリアル化 (オブジェクトの永続性) を使用します。*

- [シリアル化可能なクラスを作成します。](../mfc/serialization-making-a-serializable-class.md)

- [CArchive オブジェクトを使用してオブジェクトをシリアル化します。](../mfc/serialization-serializing-an-object.md)

- [CArchive オブジェクトを作成します。](../mfc/two-ways-to-create-a-carchive-object.md)

- [CArchive を使用して、<\<と >> 演算子](../mfc/using-the-carchive-output-and-input-operators.md)

- [保存し、読み込み Cobject およびアーカイブを通じた CObject から派生したオブジェクト](../mfc/storing-and-loading-cobjects-via-an-archive.md)

## <a name="see-also"></a>関連項目

[概念](../mfc/mfc-concepts.md)<br/>
[MFC の一般的なトピック](../mfc/general-mfc-topics.md)<br/>
[CArchive クラス](../mfc/reference/carchive-class.md)<br/>
[CObject クラス](../mfc/reference/cobject-class.md)
