---
title: データのファイルへのシリアル化
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], serialization
- documents [MFC], saving
- saving documents
- deserialization [MFC]
- serialization [MFC], role of document
- serialization [MFC], role of data
- data [MFC]
- data [MFC], serializing
- document data [MFC]
ms.assetid: b42a0c68-4bc4-4012-9938-5433a26d2c24
ms.openlocfilehash: af3cde9445ae4b128e7e54a5f154db01b2eecd3b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308072"
---
# <a name="serializing-data-to-and-from-files"></a>データのファイルへのシリアル化

永続化の基本的な考え方は、オブジェクトが永続的ストレージにそのメンバー変数の値によって示される、現在の状態を記述できることです。 後で、読み取り、または「を逆シリアル化、」永続的なストレージからオブジェクトの状態によって、オブジェクトを再作成できます。 ここで重要な点は、オブジェクト自体が読み取りと書き込みが自身の状態を担当することです。 したがって、永続的にするクラスの基本的なシリアル化操作を実装にする必要があります。

フレームワークは、ドキュメントを保存先への応答ファイルをディスクに保存するための既定の実装を提供し、[ファイル] メニューと開いているコマンドに応答ファイルをディスクからドキュメントの読み込みの名前を付けて保存のコマンド。 ごくわずかな作業は、ファイルとの間のデータを読み書きするドキュメントの機能を実装できます。 行う必要があります、重要なことは、上書き、 [Serialize](../mfc/reference/cobject-class.md#serialize)ドキュメント クラスのメンバー関数。

MFC アプリケーション ウィザードは配置のスケルトンのオーバーライド、`CDocument`メンバー関数は`Serialize`ドキュメント クラスを作成します。 アプリケーションのメンバー変数を実装した後に記入すること、 `Serialize` 「アーカイブ オブジェクト」のファイルに接続されているデータを送信するコードで上書きします。 A [CArchive](../mfc/reference/carchive-class.md)オブジェクトと似ています、 **cin**と**cout** C++ iostream ライブラリからオブジェクトの入力/出力します。 ただし、`CArchive`を書き込み、バイナリ形式でフォーマットされていないテキストを読み取ります。

## <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [シリアル化](../mfc/serialization-in-mfc.md)

- [シリアル化で、ドキュメントの役割](#_core_the_document.92.s_role_in_serialization)

- [シリアル化におけるデータの役割](#_core_the_data.92.s_role_in_serialization)

- [シリアル化機構のバイパス](../mfc/bypassing-the-serialization-mechanism.md)

##  <a name="_core_the_document.92.s_role_in_serialization"></a> シリアル化で、ドキュメントの役割

保存、およびドキュメントを呼び出すことによってコマンドとして保存するファイル メニューのオープン、フレームワークが自動的に応答`Serialize`メンバー関数は実装されている場合。 ID_FILE_OPEN コマンドは、たとえば、アプリケーションのオブジェクト ハンドラー関数を呼び出します。 このプロセス中にユーザーに表示され、ファイルを開く ダイアログ ボックスに応答し、フレームワークが、ユーザーが選択したファイル名を取得します。 フレームワークを作成、`CArchive`オブジェクト用に設定、ドキュメントにデータを読み込むへのアーカイブを渡します`Serialize`します。 フレームワークには、ファイルが既に開かれています。 ドキュメントのコード`Serialize`メンバー関数は、必要に応じて、データ オブジェクトを再構築、アーカイブからのデータを読み取ります。 シリアル化の詳細については、この記事を参照してください。[シリアル化](../mfc/serialization-in-mfc.md)します。

##  <a name="_core_the_data.92.s_role_in_serialization"></a> シリアル化におけるデータの役割

一般に、クラス型のデータは、それ自体をシリアル化できる必要があります。 つまり、アーカイブにオブジェクトを渡すとと、オブジェクトはアーカイブに自体を記述する方法と、アーカイブから自体を読み取る方法を理解する必要があります。 MFC には、この方法でシリアル化可能なクラスを行うためのサポートが用意されています。 データ型を定義するクラスを設計すると、その型のデータをシリアル化する、シリアル化の設計します。

## <a name="see-also"></a>関連項目

[ドキュメントの使い方](../mfc/using-documents.md)
