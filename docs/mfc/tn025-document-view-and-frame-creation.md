---
title: TN025:ドキュメント、ビュー、およびフレームの作成
ms.date: 11/04/2016
f1_keywords:
- vc.creation
helpviewer_keywords:
- documents [MFC], view and frame creation
- TN025
ms.assetid: 09254d72-6e1d-43db-80e9-693887dbeda2
ms.openlocfilehash: 4958e7c4ca2c3cf9eed6420d72d0399fa112098d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62305997"
---
# <a name="tn025-document-view-and-frame-creation"></a>TN025:ドキュメント、ビュー、およびフレームの作成

> [!NOTE]
>  次のテクニカル ノートは、最初にオンライン ドキュメントの一部とされてから更新されていません。 結果として、一部のプロシージャおよびトピックが最新でないか、不正になります。 最新の情報について、オンライン ドキュメントのキーワードで関係のあるトピックを検索することをお勧めします。

このノートでは、作成、ウィンドウ、ドキュメント、フレーム、およびビューの作成と所有権の問題について説明します。

## <a name="winapp"></a>WinApp

1 つである`CWinApp`システム内のオブジェクト。

静的に作成され初期化のフレームワークの内部実装によって`WinMain`します。 派生する必要があります`CWinApp`役に立つ何を (例外。MFC 拡張 Dll のない、`CWinApp`インスタンス-で初期化が行われる`DllMain`代わりに)。

1 つ`CWinApp`オブジェクトは、ドキュメント テンプレートの一覧を所有している (、 `CPtrList`)。 アプリケーションごとに 1 つまたは複数のドキュメント テンプレートがあります。 ウィンドウがリソース ファイル (つまり、文字列配列) に、通常は読み込まれて`CWinApp::InitInstance`します。

```
pTemplate = new CDocTemplate(IDR_MYDOCUMENT, ...);

AddDocTemplate(pTemplate);
```

1 つ`CWinApp`オブジェクトには、アプリケーション内のすべてのフレーム ウィンドウが所有しています。 アプリケーションのメイン フレーム ウィンドウに保存する`CWinApp::m_pMainWnd`; 通常設定*m_pMainWnd*で、`InitInstance`実装を AppWizard がある場合。 1 つのシングル ドキュメント インターフェイス (SDI) がこの`CFrameWnd`のみドキュメント フレーム ウィンドウだけでなく、アプリケーションのメイン フレーム ウィンドウとして機能します。 MDI フレームは、マルチ ドキュメント インターフェイス (MDI) (クラス`CMDIFrameWnd`) すべての子を含むアプリケーションのメイン フレーム ウィンドウとして機能する`CFrameWnd`秒。 クラスの各子ウィンドウは、 `CMDIChildWnd` (から派生した`CFrameWnd`) 可能性のある多くのドキュメント フレーム ウィンドウのいずれかとして機能します。

## <a name="doctemplates"></a>ウィンドウ

`CDocTemplate`は作成者およびドキュメントのマネージャー。 作成したドキュメントが所有しています。 派生する必要はありません、アプリケーションでは、以下に示すリソース ベースのアプローチを使用する場合`CDocTemplate`します。

SDI アプリケーションで、クラスの`CSingleDocTemplate`の 1 つ開いているドキュメントを追跡します。 MDI アプリケーションは、クラス`CMultiDocTemplate`リストを保持 (、 `CPtrList`) そのテンプレートから作成されたすべての現在開いているドキュメント。 `CDocTemplate::AddDocument` `CDocTemplate::RemoveDocument`を追加またはテンプレートからドキュメントを削除する仮想メンバー関数を提供します。 `CDocTemplate` フレンド`CDocument`、保護された設定できるように`CDocument::m_pDocTemplate`にドキュメントを作成したドキュメント テンプレートを指すポインターを戻します。

`CWinApp` 既定値の処理`OnFileOpen`実装で、すべてのドキュメント テンプレートはさらにクエリを実行します。 既に開いているドキュメントを検索で新しいドキュメントを開く形式を決定する、実装が含まれます。

`CDocTemplate` ドキュメントおよびフレームの UI のバインドを管理します。

`CDocTemplate` 名前のないドキュメントの数のカウントを保持します。

## <a name="cdocument"></a>CDocument

A`CDocument`が所有、`CDocTemplate`します。

ドキュメントが現在開いているビューの一覧を持つ (から派生した`CView`) のドキュメントを表示する (、 `CPtrList`)。

ドキュメントを作成/破棄しないで、ビューが作成した後に相互接続されました。 ドキュメントを閉じるときに (つまり、を通じてファイル/終了)、接続されているすべてのビューは閉じられます。 (つまり、ウィンドウ/閉じる)、ドキュメントの最後のビューが閉じられたときに、ドキュメントは閉じられます。

`CDocument::AddView`、`RemoveView`インターフェイスは、ビューのリストを維持するために使用されます。 `CDocument` フレンド`CView`セットアップできるように、`CView::m_pDocument`バック ポインター。

## <a name="cframewnd"></a>CFrameWnd

A `CFrameWnd` (フレームとも呼ばれます) が MFC 1.0 では、ように同じロールを果たす、`CFrameWnd`多くの場合に使用する場合、新しいクラスの派生クラスは設計されています。 派生クラス`CMDIFrameWnd`と`CMDIChildWnd`標準コマンドの多くは既に実装されても強化されました。

`CFrameWnd`フレームのクライアント領域内の windows の作成を担当します。 通常は 1 つのメイン ウィンドウ フレームのクライアント領域を埋めます。

MDI フレーム ウィンドウのクライアント領域には、すべての MDI 子フレーム ウィンドウの親である クイック ウォッチ コントロールが格納されます。 SDI フレーム ウィンドウまたは MDI 子フレーム ウィンドウは、クライアント領域は、通常の入力を`CView`-ウィンドウ オブジェクトを派生します。 場合`CSplitterWnd`、ビューのクライアント領域を塗りつぶす、`CSplitterWnd`ウィンドウ オブジェクト、および`CView`-派生ウィンドウ オブジェクト (分割ウィンドウごとに 1 つ) は、ウィンドウの子として作成、`CSplitterWnd`します。

## <a name="see-also"></a>関連項目

[番号順テクニカル ノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカル ノート](../mfc/technical-notes-by-category.md)
