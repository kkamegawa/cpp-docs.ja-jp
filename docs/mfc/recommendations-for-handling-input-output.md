---
title: 入出力処理の推奨事項
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [MFC], about I/O
- file-based I/O options
- I/O [MFC]
- I/O [MFC], options
- I/O [MFC], file-based options
ms.assetid: d664b175-3b4a-40c3-b14b-39de6b12e419
ms.openlocfilehash: 760c213c3af7f9c75374f04e3dfc6b9499eade5c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62218565"
---
# <a name="recommendations-for-handling-inputoutput"></a>入出力処理の推奨事項

ファイル ベースの I/O を使用するかどうかは、次のデシジョン ツリーの質問に応答する方法によって異なります。

**アプリケーションでプライマリ データがディスク ファイル内に存在します。**

- はい、プライマリ データは、ディスク ファイルには。

     **アプリケーションでファイルを開く上のメモリにファイル全体を読み取るし、ファイル全体で書き戻しをディスクにファイルの保存**

   - うん：これは、既定の MFC ドキュメント ケースです。 使用`CDocument`シリアル化します。

   - 違います：これは、通常のファイルの更新トランザクション ベースの場合です。 トランザクションごとのファイルを更新し、不要`CDocument`シリアル化します。

- いいえ、プライマリ データは、ディスク ファイルに存在しません。

     **データは、ODBC データ ソース内で存在します。**

   - はい、ODBC データ ソースのデータが存在します。

         Use MFC's database support. The standard MFC implementation for this case includes a `CDatabase` object, as discussed in the article [MFC: Using Database Classes with Documents and Views](../data/mfc-using-database-classes-with-documents-and-views.md). The application might also read and write an auxiliary file — the purpose of the application wizard "both a database view and file support" option. In this case, you'd use serialization for the auxiliary file.

   - いいえ、ODBC データ ソースのデータが存在しません。

         Examples of this case: the data resides in a non-ODBC DBMS; the data is read via some other mechanism, such as OLE or DDE.

         In such cases, you won't use serialization, and your application won't have Open and Save menu items. You might still want to use a `CDocument` as a home base, just as an MFC ODBC application uses the document to store `CRecordset` objects. But you won't use the framework's default File Open/Save document serialization.

サポートし、オープン、保存、[ファイル] メニューのコマンドを付けて、フレームワークは、ドキュメントのシリアル化を提供します。 シリアル化データ読み取りし、書き込み、クラスから派生したオブジェクトを含む`CObject`に永続的なストレージ、通常のディスク ファイル。 シリアル化は簡単に使用し、ニーズの多くは機能しますが、多くのデータ アクセス アプリケーションで適切でない可能性があります。 データ アクセス アプリケーションは、通常、トランザクション単位でデータを更新します。 トランザクションではなく読み取りと書き込みデータ ファイル全体を一度に影響を受けるレコードだけが更新されます。

シリアル化については、次を参照してください。[シリアル化](../mfc/serialization-in-mfc.md)します。

## <a name="see-also"></a>関連項目

[シリアル化: シリアル化とデータベースの入力/出力](../mfc/serialization-serialization-vs-database-input-output.md)
