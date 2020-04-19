---
title: エクスプローラー形式の MFC アプリケーションの作成
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfcexplorer.project
helpviewer_keywords:
- browsers [MFC], Explorer-style applications
- MFC applications [MFC], Windows Explorer-style
- Explorer-style applications [MFC], creating
ms.assetid: f843ab5d-2d5d-41ca-88a4-badc0d2f8052
ms.openlocfilehash: 16969b7ef9c0447dfce971af8d329c5b93367041
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372245"
---
# <a name="creating-a-file-explorer-style-mfc-application"></a>エクスプローラー形式の MFC アプリケーションの作成

多くの Windows システムのアプリケーションでは、ファイル エクスプ ローラーのユーザー インターフェイス (UI) を使用します。 ファイル エクスプ ローラーを起動するとなどが表示をクライアント領域を分割バーの垂直方向の分割を使用したアプリケーション。 クライアント領域の左側にあるナビゲーションと参照の機能を提供し、左側のウィンドウでクライアント領域の右側にあるが選択範囲に関連にある詳細を示します。 ユーザーは、左側のウィンドウ内の項目をクリックすると、アプリケーションには、右側のウィンドウが再作成されます。 MDI アプリケーションでのコマンドを使用することができます、**ビュー**  メニューの右側のウィンドウで表示する詳細の量を変更します。 (SDI またはマルチ トップレベル ドキュメント アプリケーションでは、ツールバーのボタンのみを使用して、詳細を変更できます)。

ペインの内容は、アプリケーションに依存します。 ファイル システム ブラウザーでは、左側のウィンドウは、右側のウィンドウは、フォルダー、個々 のファイルまたはマシン、およびそれらの詳細が表示されます。 ディレクトリ、コンピューター、またはコンピューターのグループの階層ビューを示します。 内容をファイル必要はありません。 電子メール メッセージ、エラー レポート、またはデータベースの他のアイテムがある可能性があります。

ウィザードでは、次のクラスを作成します。

- `CLeftView`クラスは、クライアント領域の左側のウィンドウを定義します。 常に由来[CTreeView](../../mfc/reference/ctreeview-class.md)します。

- C*ProjName*ビュー クラスがクライアント領域の右側のウィンドウを定義します。 派生される、既定で[CListView](../../mfc/reference/clistview-class.md)から指定したクラスによってビューの別の型を指定できますが、**基本クラス**の一覧で、[生成されたクラス](../../mfc/reference/generated-classes-mfc-application-wizard.md)のページ、ウィザード。

生成されたアプリケーションには、シングル ドキュメント インターフェイス (SDI)、マルチ ドキュメント インターフェイス (MDI)、または複数のドキュメントの最上位アーキテクチャを持つことができます。 使用して各フレーム ウィンドウが、アプリケーションの作成が垂直方向に分割[CSplitterWnd](../../mfc/reference/csplitterwnd-class.md)します。 このアプリケーションの種類をコーディングすることは、スプリッターを使用する通常の MFC アプリケーションをコーディングする点を除いて、この種類のアプリケーションがある各分割ペイン内の個別のコントロール ビューに似ています。

右側のウィンドウで、既定のリスト ビューを使用する場合、ウィザードは、大きいアイコン、小さいアイコン、リスト、および詳細モードの間で、ビューのスタイルを切り替えるには、(MDI アプリケーションの場合のみ) で追加のメニューの選択肢とツール バー ボタンを作成します。

### <a name="to-begin-creating-a-file-explorer-style-mfc-executable"></a>ファイル エクスプ ローラー スタイルの MFC の実行可能ファイルの作成を開始するには

1. 指示に従って[MFC アプリケーションを作成する](../../mfc/reference/creating-an-mfc-application.md)します。

1. MFC アプリケーション ウィザードで[アプリケーションの種類](../../mfc/reference/application-type-mfc-application-wizard.md)] ページで、[、**ファイル エクスプ ローラー**プロジェクトのスタイル。

1. ウィザードの他のページで、必要に応じてその他のオプションを設定します。

1. クリックして**完了**スケルトン アプリケーションを生成します。

詳細については次を参照してください:

- [複数のドキュメント タイプ、ビュー、フレーム ウィンドウ](../../mfc/multiple-document-types-views-and-frame-windows.md)

- [派生ビュー クラス](../../mfc/derived-view-classes-available-in-mfc.md)

- [アプリケーションのデザイン上の検討事項](../../mfc/application-design-choices.md)

## <a name="see-also"></a>関連項目

[MFC アプリケーション ウィザード](../../mfc/reference/mfc-application-wizard.md)<br/>
[Web ブラウザー形式の MFC アプリケーションの作成](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)<br/>
[フォーム ベースの MFC アプリケーションの作成](../../mfc/reference/creating-a-forms-based-mfc-application.md)
