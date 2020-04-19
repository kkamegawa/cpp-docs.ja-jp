---
title: MFC におけるシリアル化
ms.date: 11/04/2016
helpviewer_keywords:
- collection classes [MFC], serialization
- bypassing serialization [MFC]
- MFC, serialization
- serialization [MFC], MFC
- serialization [MFC], bypassing
ms.assetid: fb596a18-4522-47e0-96e0-192732d24c12
ms.openlocfilehash: 5c7dec140635b6d83bdae936d1bb0cef144f825b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308214"
---
# <a name="serialization-in-mfc"></a>MFC におけるシリアル化

この記事では、オブジェクトの間で永続化する許可を Microsoft Foundation Class ライブラリ (MFC) でのシリアル化機構をプログラムの実行について説明します。

シリアル化は、ディスク ファイルなどの永続的なストレージ メディアからの書き込みまたはオブジェクトの読み取りのプロセスです。 シリアル化は、状況が中またはプログラムの実行後に、構造化データ (C++ のクラスまたは構造体) などの状態を維持するために必要な場合に最適です。 MFC によって提供されるシリアル化オブジェクトを使用すると、これには、標準的な一貫した方法で、ファイル操作を手動で実行する必要性からユーザーを軽減できます。

MFC には、クラスでシリアル化のための組み込みサポート`CObject`します。 したがってから派生したすべてのクラス`CObject`活用できる`CObject`のシリアル化プロトコル。

シリアル化の基本的な考え方は、オブジェクトが、通常、永続的ストレージにそのメンバー変数の値によって示される、現在の状態を記述できることです。 後で、読み取り、またはオブジェクトの状態をストレージから逆シリアル化によって、オブジェクトを再作成できます。 シリアル化では、オブジェクト ポインターおよび循環参照オブジェクトをシリアル化するときに使用されるオブジェクトへのすべての詳細を処理します。 重要なポイントは、オブジェクト自体が読み取りと書き込みが自身の状態を担当することです。 したがって、シリアル化できるクラスの基本的なシリアル化操作を実装にする必要があります。 アーティクルのシリアル化のグループに示すようには、簡単にこの機能をクラスに追加できます。

MFC のオブジェクトを使用して、`CArchive`ストレージ メディアとシリアル化するオブジェクトの間の仲介役としてのクラス。 このオブジェクトは常に関連付け、`CFile`からファイル名を含む、シリアル化に必要な情報を取得し、要求された操作が読み取りまたは書き込みがかどうかのオブジェクト。 シリアル化操作を実行するオブジェクトを使用して、`CArchive`ストレージ メディアの種類に関係なくオブジェクト。

A`CArchive`オブジェクトは、オーバー ロードされた挿入を使用して (**<\<**) と抽出 (**>>**) の記述と読み取り操作を実行する演算子。 詳細については、次を参照してください。[の保存とアーカイブを通じた Cobject の読み込み](../mfc/storing-and-loading-cobjects-via-an-archive.md)シリアル化の記事。オブジェクトのシリアル化します。

> [!NOTE]
>  混同しないでください、`CArchive`クラスは、汎用的な iostream クラスは、テキストのみを書式設定します。 `CArchive`クラスは、バイナリ形式でシリアル化されたオブジェクト。

する場合は、永続的なデータ ストレージの独自のメカニズムを作成する MFC のシリアル化をバイパスできます。 ユーザーのコマンドでシリアル化を開始する、クラス メンバー関数をオーバーライドする必要があります。 説明を参照[テクニカル ノート 22:](../mfc/tn022-standard-commands-implementation.md) ID_FILE_OPEN、ID_FILE_SAVE、および ID_FILE_SAVE_AS 標準コマンド。

次の記事では、シリアル化に必要な 2 つの主要なタスクを説明します。

- [シリアル化: シリアル化可能なクラスの作成](../mfc/serialization-making-a-serializable-class.md)

- [シリアル化: オブジェクトのシリアル化](../mfc/serialization-serializing-an-object.md)

この記事[シリアル化します。シリアル化とデータベースの入力/出力](../mfc/serialization-serialization-vs-database-input-output.md)とシリアル化は、データベース アプリケーションでの適切な入力/出力手法について説明します。

## <a name="see-also"></a>関連項目

[概念](../mfc/mfc-concepts.md)<br/>
[MFC の一般的なトピック](../mfc/general-mfc-topics.md)<br/>
[CArchive クラス](../mfc/reference/carchive-class.md)<br/>
[CObject クラス](../mfc/reference/cobject-class.md)<br/>
[CDocument クラス](../mfc/reference/cdocument-class.md)<br/>
[CFile クラス](../mfc/reference/cfile-class.md)
