---
title: ダイアログ ボックス クラス
ms.date: 11/04/2016
f1_keywords:
- vc.classes.dialog
helpviewer_keywords:
- property sheet classes
- dialog box classes
- OLE common dialog classes
- common dialog classes [MFC]
- tab dialog boxes
ms.assetid: db75da23-4eff-4c6c-beae-79cf046fbce9
ms.openlocfilehash: 5747e4450816b803f97ad5ff6338b9e01ad41bca
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394612"
---
# <a name="dialog-box-classes"></a>ダイアログ ボックス クラス

クラス`CDialog`とその派生クラスがダイアログ ボックスの機能をカプセル化します。 ダイアログ ボックスはウィンドウの特殊なので`CDialog`から派生`CWnd`します。 ダイアログ クラスを派生`CDialog`またはいずれかを使用開始や印刷、フォントや色を選択すると、ファイルの保存などの標準のダイアログ ボックスのコモン ダイアログ クラスの検索と置換操作を開始するか、実行するさまざまな OLE 関連操作です。

[CDialog](../mfc/reference/cdialog-class.md)<br/>
すべてのダイアログ ボックス、モーダルとモードレスの両方の基本クラス。

[CDataExchange](../mfc/reference/cdataexchange-class.md)<br/>
ダイアログ ボックスのデータの交換と検証情報を提供します。

## <a name="common-dialogs"></a>コモン ダイアログ

これらのダイアログ ボックス クラスは、Windows のコモン ダイアログ ボックスをカプセル化します。 複雑なダイアログ ボックスの使いやすい実装を提供します。

[CCommonDialog](../mfc/reference/ccommondialog-class.md)<br/>
すべての一般的なダイアログ ボックスの基本クラス。

[CFileDialog](../mfc/reference/cfiledialog-class.md)<br/>
開くか、ファイルを保存するのには、標準のダイアログ ボックスを提供します。

[CColorDialog](../mfc/reference/ccolordialog-class.md)<br/>
色を選択するためには、標準のダイアログ ボックスを提供します。

[CFontDialog](../mfc/reference/cfontdialog-class.md)<br/>
フォントを選択するためには、標準のダイアログ ボックスを提供します。

[CFindReplaceDialog](../mfc/reference/cfindreplacedialog-class.md)<br/>
検索と置換操作を標準のダイアログ ボックスを提供します。

[CPrintDialog](../mfc/reference/cprintdialog-class.md)<br/>
ファイルの印刷には、標準のダイアログ ボックスを提供します。

[CPrintDialogEx](../mfc/reference/cprintdialogex-class.md)<br/>
Windows 印刷のプロパティ シートを提供します。

[CPageSetupDialog](../mfc/reference/cpagesetupdialog-class.md)<br/>
追加サポートと共に設定および印刷の余白を変更するための Windows コモン ページ設定ダイアログ ボックスが提供するサービスをカプセル化します。

## <a name="ole-common-dialogs"></a>OLE コモン ダイアログ

OLE では、Windows にいくつかのコモン ダイアログ ボックスを追加します。 これらのクラスは、OLE コモン ダイアログ ボックスをカプセル化します。

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
サーバーがビジー状態とサーバーが応答していないダイアログ ボックスを使用中のアプリケーションへの呼び出しを処理するための標準のユーザー インターフェイスを表示します。 通常、によって自動的に表示されます、 [COleMessageFilter](../mfc/reference/colemessagefilter-class.md)実装します。

## <a name="property-sheet-classes"></a>プロパティ シート クラス

プロパティ シートのクラスには、アプリケーションで、プロパティ シートとも呼ばれるタブ付きダイアログ ボックスを使用するができます。 プロパティ シートは、1 つのダイアログ ボックスのコントロールの数が多いを整理する効率的な方法です。

[CPropertyPage](../mfc/reference/cpropertypage-class.md)<br/>
プロパティ シート内の各ページを提供します。 クラスを派生`CPropertyPage`プロパティ シートに追加するには、各ページ。

[CPropertySheet](../mfc/reference/cpropertysheet-class.md)<br/>
複数のプロパティ ページのフレームを提供します。 プロパティ シートのクラスを派生`CPropertySheet`のプロパティ シートを迅速に実装します。

[COlePropertyPage](../mfc/reference/colepropertypage-class.md)<br/>
ダイアログ ボックスのようなグラフィカル インターフェイスで制御する OLE のプロパティを表示します。

## <a name="html-based-dialog-classes"></a>HTML ベースのダイアログ クラス

[CDHtmlDialog](../mfc/reference/cdhtmldialog-class.md)<br/>
ダイアログではなく、HTML リソースによるユーザー インターフェイスを実装するダイアログ ボックスを作成するために使用します。

[CMultiPageDHtmlDialog](../mfc/reference/cmultipagedhtmldialog-class.md)<br/>
複数の HTML ページを順番に表示し、各ページのイベントを処理します。

## <a name="related-classes"></a>関連するクラス

これらのクラスは本質的にダイアログ ボックスされてされませんが、ダイアログ ボックスのテンプレートを使用して、また、ダイアログ ボックスの動作の多くがあります。

[CDialogBar](../mfc/reference/cdialogbar-class.md)<br/>
ダイアログ ボックスのテンプレートに基づくコントロール バーです。

[CFormView](../mfc/reference/cformview-class.md)<br/>
レイアウトを持つが、ダイアログ ボックスのテンプレートで定義されているスクロール可能なビュー。 クラスを派生`CFormView` ダイアログ ボックスのテンプレートに基づくユーザー インターフェイスを実装します。

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
フォーム ビューのデータ アクセス オブジェクト (DAO) のレコード セット オブジェクトに直接接続します。 などのすべてのフォーム ビュー、 `CDaoRecordView`  ダイアログ ボックスのテンプレートに基づきます。

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
フォーム ビューの Open Database Connectivity (ODBC) レコード セット オブジェクトに直接接続されています。 などのすべてのフォーム ビュー、 `CRecordView`  ダイアログ ボックスのテンプレートに基づきます。

[CPrintInfo](../mfc/reference/cprintinfo-structure.md)<br/>
印刷または印刷プレビュー ジョブに関する情報を含む構造体。 印刷アーキテクチャで使用される[CView](../mfc/reference/cview-class.md)します。

## <a name="see-also"></a>関連項目

[クラスの概要](../mfc/class-library-overview.md)
