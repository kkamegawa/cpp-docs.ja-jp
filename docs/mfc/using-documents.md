---
title: ドキュメントの使い方
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], C++ applications
- data [MFC], reading
- documents [MFC]
- files [MFC], writing to
- data [MFC], documents
- files [MFC]
- views [MFC], C++ applications
- document/view architecture [MFC], documents
- reading data [MFC], documents and views
- printing [MFC], documents
- writing to files [MFC]
ms.assetid: f390d6d8-d0e1-4497-9b6a-435f7ce0776c
ms.openlocfilehash: fb35d1731912b2e322bc61621f7900e0d98e1e72
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411592"
---
# <a name="using-documents"></a>ドキュメントの使い方

ドキュメントとビュー、共に作業。

- 含む、管理、およびアプリケーションに固有の表示[データ](../mfc/managing-data-with-document-data-variables.md)します。

- 構成されるインターフェイスを提供[ドキュメント データ変数](../mfc/managing-data-with-document-data-variables.md)データを操作します。

- 参加[ファイルを読み書き](../mfc/serializing-data-to-and-from-files.md)します。

- 参加[印刷](../mfc/role-of-the-view-in-printing.md)します。

- [処理](../mfc/handling-commands-in-the-document.md)のほとんどのアプリケーションのコマンドおよびメッセージ。

ドキュメントは、データの管理に特に関連します。 通常、ドキュメント クラスのメンバー変数で、データを格納します。 ビューでは、これらの変数を使用して、表示用にデータをアクセスし、更新します。 ドキュメントの既定のシリアル化メカニズムでは、ファイルを送受信するデータの読み書きを管理します。 また、ドキュメントは、コマンド (ただし、WM_COMMAND 以外の Windows メッセージされません) を処理していることもできます。

## <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [CDocument からドキュメント クラスの派生](../mfc/deriving-a-document-class-from-cdocument.md)

- [ドキュメント データ変数を使ったデータの管理](../mfc/managing-data-with-document-data-variables.md)

- [ファイルとデータをシリアル化します。](../mfc/serializing-data-to-and-from-files.md)

- [シリアル化機構のバイパス](../mfc/bypassing-the-serialization-mechanism.md)

- [ドキュメント内のコマンドの処理](../mfc/handling-commands-in-the-document.md)

- [でも実質的メンバー関数は、](../mfc/reference/cdocument-class.md#onnewdocument)

- [DeleteContents メンバー関数は、](../mfc/reference/cdocument-class.md#deletecontents)

## <a name="see-also"></a>関連項目

[ドキュメント/ビュー アーキテクチャ](../mfc/document-view-architecture.md)
