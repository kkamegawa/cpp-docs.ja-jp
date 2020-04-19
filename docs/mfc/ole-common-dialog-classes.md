---
title: OLE コモン ダイアログ クラス
ms.date: 11/04/2016
f1_keywords:
- vc.classes.ole
helpviewer_keywords:
- ActiveX classes [MFC]
- dialog classes [MFC], OLE
- OLE common dialog classes [MFC]
- common dialog classes [MFC]
ms.assetid: 706526ae-f94f-4909-a0f8-6b5fe954fd97
ms.openlocfilehash: d34c141fc9a2b53eab6a4c0b0ce1799ff5243d84
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62186393"
---
# <a name="ole-common-dialog-classes"></a>OLE コモン ダイアログ クラス

これらのクラスは、さまざまな標準の OLE ダイアログ ボックスを実装して、OLE の一般的なタスクを処理します。 OLE の機能を一貫したユーザー インターフェイスも提供します。

[COleDialog](../mfc/reference/coledialog-class.md)<br/>
すべての OLE ダイアログ ボックスの一般的な実装を格納するフレームワークで使用します。 ユーザー インターフェイス カテゴリ内のすべてのダイアログ ボックス クラスは、この基本クラスから派生します。 `COleDialog` 直接使用することはできません。

[COleInsertDialog](../mfc/reference/coleinsertdialog-class.md)<br/>
リンクまたは埋め込みアイテムの新しい OLE を挿入するは、オブジェクトの挿入 ダイアログ ボックスで、標準のユーザー インターフェイスを表示します。

[COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md)<br/>
貼り付け ダイアログ ボックス、編集貼り付けコマンドを実装するための標準のユーザー インターフェイスを表示します。

[COleLinksDialog](../mfc/reference/colelinksdialog-class.md)<br/>
リンクの編集 ダイアログ ボックスで、リンクされた項目に関する情報を変更するための標準のユーザー インターフェイスを表示します。

[COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md)<br/>
アイコンの変更のダイアログ ボックスで、OLE に関連付けられているアイコンの埋め込みを変更するか、リンクされた項目の標準のユーザー インターフェイスが表示されます。

[COleConvertDialog](../mfc/reference/coleconvertdialog-class.md)<br/>
変換 ダイアログ ボックスで、OLE 項目の 1 つの型を変換するための標準的なユーザー インターフェイスを表示します。

[COlePropertiesDialog](../mfc/reference/colepropertiesdialog-class.md)<br/>
Windows の一般的な OLE プロパティ ダイアログ ボックスをカプセル化します。 共通の OLE プロパティ ダイアログ ボックスを表示し、Windows の標準に準拠した方法での OLE ドキュメント項目のプロパティを変更する簡単な方法を提供します。

[COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md)<br/>
更新プログラム ダイアログ ボックスで、ドキュメント内のすべてのリンクを更新するための標準のユーザー インターフェイスを表示します。 ダイアログ ボックスには、完了するまで、更新手順を閉じる方法を示す進行状況インジケーターが含まれています。

[COleChangeSourceDialog](../mfc/reference/colechangesourcedialog-class.md)<br/>
ソースの変更 ダイアログ ボックスで、宛先またはリンクのソースを変更するための標準のユーザー インターフェイスを表示します。

[COleBusyDialog](../mfc/reference/colebusydialog-class.md)<br/>
サーバーがビジー状態とサーバーが応答していないダイアログ ボックスを使用中のアプリケーションへの呼び出しを処理するための標準のユーザー インターフェイスを表示します。 通常、によって自動的に表示されます、`COleMessageFilter`実装します。

## <a name="see-also"></a>関連項目

[クラスの概要](../mfc/class-library-overview.md)
