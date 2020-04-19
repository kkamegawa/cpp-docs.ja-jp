---
title: ダイアログ ボックス
ms.date: 11/04/2016
helpviewer_keywords:
- modeless dialog boxes [MFC], MFC dialog boxes
- MFC, dialog boxes
- modal dialog boxes [MFC], MFC dialog boxes
- CDialog class [MFC], MFC dialog boxes
- MFC dialog boxes
ms.assetid: e4feea1a-8360-4ccb-9b84-507f1ccd9ef3
ms.openlocfilehash: 18b4c4d1386716a0a3282b88d6fdf5a701abce08
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685789"
---
# <a name="dialog-boxes"></a>ダイアログ ボックス

Windows 用アプリケーションは、ダイアログボックスを通じてユーザーと頻繁に通信します。 クラス[CDialog](../mfc/reference/cdialog-class.md)には、ダイアログボックスを管理するためのC++インターフェイスが用意されています。ビジュアルダイアログエディターを使用すると、ダイアログボックスのデザインやダイアログテンプレートリソースの作成が簡単になります。また、コードウィザードを使用すると、ダイアログボックス内のコントロールと、ユーザーが入力した値を収集します。

ダイアログボックスには、次のようなコントロールがあります。

- エディットボックス、プッシュボタン、リストボックス、コンボボックス、ツリーコントロール、リストコントロール、進行状況インジケーターなどの Windows コモンコントロール。

- ActiveX コントロール。

- オーナー描画コントロール: ダイアログボックスでの描画を担当するコントロールです。

ほとんどのダイアログボックスはモーダルであり、プログラムの他の部分を使用する前に、ユーザーがダイアログボックスを閉じる必要があります。 ただし、ダイアログボックスが開いている間にユーザーが他のウィンドウを操作できるように、モードレスのダイアログボックスを作成することもできます。 MFC では、クラス `CDialog` の両方の種類のダイアログボックスがサポートされています。 コントロールは、ダイアログ[エディター](../windows/dialog-editor.md)で作成されたダイアログテンプレートリソースを使用して、配置および管理されます。

タブダイアログボックスとも呼ばれる[プロパティシート](../mfc/property-sheets-mfc.md)は、ダイアログボックスのダイアログボックスコントロールの "ページ" を含むダイアログボックスです。 各ページの上部には、"タブ" というファイルフォルダーがあります。 タブをクリックすると、そのページがダイアログボックスの前に表示されます。

## <a name="what-do-you-want-to-know-more-about"></a>詳細については、次を参照してください。

- [例:メニュー コマンドによるダイアログ ボックスの表示](../mfc/example-displaying-a-dialog-box-via-a-menu-command.md)

- [フレームワークのダイアログボックスコンポーネント](../mfc/dialog-box-components-in-the-framework.md)

- [モーダルおよびモードレスのダイアログボックス](../mfc/modal-and-modeless-dialog-boxes.md)

- ダイアログボックスの[プロパティシートとプロパティページ](../mfc/property-sheets-and-property-pages-mfc.md)

- [ダイアログリソースの作成](../mfc/creating-the-dialog-resource.md)

- [コードウィザードを使用したダイアログクラスの作成](../mfc/creating-a-dialog-class-with-code-wizards.md)

- [MFC でのダイアログボックスの操作](../mfc/life-cycle-of-a-dialog-box.md)

- [ダイアログデータエクスチェンジ (DDX) と検証 (DDV)](../mfc/dialog-data-exchange-and-validation.md)

- [ダイアログボックス内のコントロールへのタイプセーフアクセス](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)

- [Windows メッセージをクラスにマップする](../mfc/mapping-windows-messages-to-your-class.md)

- [通常オーバーライドされるメンバー関数](../mfc/commonly-overridden-member-functions.md)

- [通常追加されるメンバー関数](../mfc/commonly-added-member-functions.md)

- [コモンダイアログクラス](../mfc/common-dialog-classes.md)

- [ダイアログボックス (OLE の)](../mfc/dialog-boxes-in-ole.md)

- ユーザーインターフェイスがダイアログボックスであるアプリケーションを作成する: [CMNCTRL1](../overview/visual-cpp-samples.md)または[CMNCTRL2](../overview/visual-cpp-samples.md)サンプルプログラムを参照してください。 このオプションは、アプリケーションウィザードにも用意されています。

- [サンプル](../mfc/dialog-sample-list.md)

## <a name="see-also"></a>関連項目

[ユーザーインターフェイス要素](../mfc/user-interface-elements-mfc.md)
