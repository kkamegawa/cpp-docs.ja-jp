---
title: TN041:Mfc/ole1 から MFC/OLE 2 へ
ms.date: 10/18/2018
helpviewer_keywords:
- OLE1 [MFC]
- migrating OLE1 to OLE2
- migration [MFC], OLE1 to OLE2
- OLE2 [MFC]
- porting OLE1 to OLE2
- converting OLE1 to OLE2
- upgrading Visual C++ applications [MFC], OLE1 to OLE2
- TN041
ms.assetid: 67f55552-4b04-4ddf-af0b-4d9eaf5da957
ms.openlocfilehash: 78ffefb198b92acbac5c3c18acd9496835845e6f
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65610999"
---
# <a name="tn041-mfcole1-migration-to-mfcole-2"></a>TN041:Mfc/ole1 から MFC/OLE 2 へ

> [!NOTE]
> 次のテクニカル ノートは、最初にオンライン ドキュメントの一部とされてから更新されていません。 結果として、一部のプロシージャおよびトピックが最新でないか、不正になります。 最新の情報について、オンライン ドキュメントのキーワードで関係のあるトピックを検索することをお勧めします。

## <a name="general-issues-relating-to-migration"></a>移行に関連する一般的な問題

MFC 2.0 では OLE 1.0 のサポートのために、同じアーキテクチャの多くを維持 (以降) MFC 2.5 では、OLE 2 クラスの設計目標の 1 つでした。 このバージョンの MFC にまだ存在多く MFC 2.0 では、同じ OLE クラスの結果として、(`COleDocument`、 `COleServerDoc`、 `COleClientItem`、 `COleServerItem`)。 さらに、これらのクラスで Api の多くはまったく同じです。 ただし、OLE 2 は、その詳細の一部が変更されたことを想定して OLE 1.0 を大幅に異なります。 MFC 2.0 の OLE1 サポートについてご存知の場合は、自宅で MFC の 2.0 のサポートと感じられます。

既存の MFC OLE1/アプリケーションを実行しを OLE 2 の機能を追加している場合は、この注をまずお読みください。 この注 MFC/OLE 2 へ、OLE1 の機能を移植するときに発生し、MFC 2.0 に含まれる 2 つのアプリケーションを移植するときに検出された問題を説明しますいくつかの一般的な問題の説明: MFC OLE サンプル[OCLIENT](../overview/visual-cpp-samples.md)と。[HIERSVR](../overview/visual-cpp-samples.md)します。

## <a name="mfc-documentview-architecture-is-important"></a>MFC ドキュメント/ビュー アーキテクチャが重要です。

アプリケーションが MFC のドキュメント/ビュー アーキテクチャを使用せず、OLE 2 のサポートをアプリケーションに追加する場合は、ここで、ドキュメント/ビューに移動する時間です。 MFC の OLE 2 クラスの利点の多くは、アプリケーションが組み込みのアーキテクチャと MFC のコンポーネントを使用するとにのみ実現されます。

MFC アーキテクチャを使用せず、サーバーまたはコンテナーを実装が可能であれば、推奨されません。

## <a name="use-mfc-implementation-instead-of-your-own"></a>MFC 実装を使用して、独自の代わりに

などのクラスの実装を MFC「固定」 `CToolBar`、 `CStatusBar`、および`CScrollView`OLE 2 のサポートの組み込みの特殊なケース コードがあります。 そのため場合、これらのクラスを使用するには、アプリケーションで役に立つ、それらになるように努力して OLE に注意してください。 このため、クラスの"ロール your own"ここで行うことが、お勧めできません。 同様の機能を実装する必要がある場合、(特に、インプレース アクティブ化に関しては) 場合、MFC のソース コードでは OLE の細かい点の一部に対処するための優れた参考文献が使用します。

## <a name="examine-the-mfc-sample-code"></a>MFC のサンプル コードを調べる

OLE の機能を含む MFC のサンプルを数多くあります。 これらの各アプリケーションには、さまざまな角度から OLE が実装されています。

- [HIERSVR](../overview/visual-cpp-samples.md)通常サーバー アプリケーションとして使用するために利用します。 MFC/OLE1 アプリケーションとしての MFC 2.0 に含まれていたとがされて MFC/OLE 2 へ移植し、OLE 2 で使用できる多数の OLE 機能を実装できるように、拡張します。

- [OCLIENT](../overview/visual-cpp-samples.md)スタンドアロンのコンテナー アプリケーションをコンテナーの観点から OLE の機能の多くをデモンストレーションするためのものになります。 MFC 2.0 から移植された OLE の高度な機能で、カスタムのクリップボードの形式と埋め込みアイテムへのリンクなどの多くをサポートするように拡張しと。

- [DRAWCLI](../overview/visual-cpp-samples.md)このアプリケーションを実装する OLE コンテナーのサポートより OCLIENT と同様、する点を除いて、これは既存のオブジェクト指向の描画プログラムのフレームワーク内で。 OLE コンテナーのサポートを実装し、既存のアプリケーションに統合する方法を示します。

- [SUPERPAD](../overview/visual-cpp-samples.md)このアプリケーションと問題のスタンドアロン アプリケーション、OLE サーバー。 サーバーのサポートの実装では、限です。 特に興味深いは、データをクリップボードにコピーする OLE クリップボード サービスの使用方法しますが、貼り付けのクリップボード機能を実装するために、Windows の「編集」コントロールに組み込まれた機能を使用します。 これには、従来の Windows API の使用方法と新しい OLE Api との統合の興味深いを混在させるが表示されます。

サンプル アプリケーションの詳細については、「MFC サンプル ヘルプ」を参照してください。

## <a name="case-study-oclient-from-mfc-20"></a>ケース スタディ: MFC 2.0 から OCLIENT

前述したように、 [OCLIENT](../overview/visual-cpp-samples.md) MFC 2.0 に含まれていたし、MFC/OLE1 を使用して OLE を実装します。 使用されるこのアプリケーションが最初に MFC/OLE 2 クラスを使用する変換の手順を以下に示します。 しかし、MFC/OLE クラスをよく示すために、初期の移植が完了した後、さまざまな機能が追加されました。 これらの機能はここでは説明されません。これらの高度な機能の詳細については、サンプル アプリケーションを参照してください。

> [!NOTE]
> コンパイラ エラーおよびステップ バイ ステップのプロセスは、Visual C 2.0 で作成されました。 特定のエラー メッセージと場所は、Visual C 4.0 に変更可能性がありますが、概念的な情報は有効です。

## <a name="getting-it-up-and-running"></a>起動と実行

MFC/OLE に oclient を移植する方法は、ビルドし、原因となる明らかなコンパイラ エラーを修正して始めることです。 MFC 2.0 から oclient し、MFC のこのバージョンでコンパイルし、解決するのには多くのエラーがないことがわかります。 発生した順序でエラーを以下に示します。

## <a name="compile-and-fix-errors"></a>コンパイルとエラーの修正

```Output
\oclient\mainview.cpp(104) : error C2660: 'Draw' : function does not take 4 parameters
```

最初のエラーの懸念事項`COleClientItem::Draw`します。 MFC/OLE1 MFC/OLE バージョンは、多くのパラメーターをかかりました。 パラメーターを追加でした。 多くの場合、必要であり (この例では) のように、通常は NULL。 このバージョンの MFC は、CDC に描画されているが、メタファイル DC、lpWBounds の値を自動的に判断できます。 さらに、フレームワークでは、"DC"の属性に渡される pDC から 1 つはビルドから pFormatDC パラメーターは必要ありません。 2 つの削除だけこの問題を解決するように余分な描画呼び出しのパラメーターは NULL です。

```Output
\oclient\mainview.cpp(273) : error C2065: 'OLE_MAXNAMESIZE' : undeclared identifier
\oclient\mainview.cpp(273) : error C2057: expected constant expression
\oclient\mainview.cpp(280) : error C2664: 'CreateLinkFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
\oclient\mainview.cpp(286) : error C2664: 'CreateFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
\oclient\mainview.cpp(288) : error C2664: 'CreateStaticFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
```

結果という事実を上記のエラーをすべての`COleClientItem::CreateXXXX`MFC/OLE1 内の関数の項目を表す一意の名前が渡されることが必要です。 これは、基になる OLE API の要件です。 これは不要な MFC/OLE 2 OLE 2 では、DDE (名前は、DDE メッセージ交換で使用された) 基になる通信メカニズムとして使用しないためです。 この問題を解決するには削除、`CreateNewName`への参照がすべて、関数。 各 MFC/OLE 関数で想定される内容では、このバージョンの呼び出しにカーソルを置き、F1 キーを押すだけですぐに確認できます。

大きく異なる別の領域は、OLE 2 のクリップボード処理です。 OLE1、クリップボードを使用した Windows クリップボード Api の操作を使用します。 OLE 2 これは、別のメカニズムで行われます。 MFC/OLE1 Api では、コピーする前に、クリップボードが開いていると見なされます、`COleClientItem`クリップボード オブジェクト。 これが不要と MFC/OLE のすべてのクリップボード操作が失敗すると。 依存関係を削除するコードを編集するときに`CreateNewName`、Windows クリップボードを開いたり閉じたりするコードを削除することも必要があります。

```Output
\oclient\mainview.cpp(332) : error C2065: 'AfxOleInsertDialog' : undeclared identifier
\oclient\mainview.cpp(332) : error C2064: term does not evaluate to a function
\oclient\mainview.cpp(344) : error C2057: expected constant expression
\oclient\mainview.cpp(347) : error C2039: 'CreateNewObject' : is not a member of 'CRectItem'
```

これらのエラーがの結果として、`CMainView::OnInsertObject`ハンドラー。 「オブジェクトの挿入」コマンドの処理は、点が大幅に変更されました、もう 1 つの領域です。 ここでは、単に新しい OLE コンテナー アプリケーションの AppWizard によって提供される元の実装をマージする最も簡単なは。 実際には、これは、他のアプリケーションを移植するときに適用できる手法です。 呼び出して"オブジェクトの挿入 ダイアログの表示で MFC/OLE1`AfxOleInsertDialog`関数。 このバージョンで構築、`COleInsertObject`ダイアログ オブジェクトと呼び出し`DoModal`します。 新しい OLE 項目を作成するさらに、 **CLSID** classname 文字列の代わりにします。 最終的な結果は次のようになります

```cpp
COleInsertDialog dlg;
if (dlg.DoModal() != IDOK)
    return;

BeginWaitCursor();

CRectItem* pItem = NULL;
TRY
{
    // First create the C++ object
    pItem = GetDocument()->CreateItem();
    ASSERT_VALID(pItem);

    // Initialize the item from the dialog data.
    if (!dlg.CreateItem(pItem))
        AfxThrowMemoryException();
            // any exception will do
    ASSERT_VALID(pItem);

    // run the object if appropriate
    if (dlg.GetSelectionType() == COleInsertDialog::createNewItem)
        pItem->DoVerb(OLEIVERB_SHOW, this);

    // update right away
    pItem->UpdateLink();
    pItem->UpdateItemRectFromServer();

    // set selection to newly inserted item
    SetSelection(pItem);
    pItem->Invalidate();
}
CATCH (CException, e)
{
    // clean up item
    if (pItem != NULL)
        GetDocument()->DeleteItem(pItem);

    AfxMessageBox(IDP_FAILED_TO_CREATE);
}
END_CATCH

EndWaitCursor();
```

> [!NOTE]
> 新しいオブジェクトの挿入があります、アプリケーションによって異なる)。

含める必要も\<afxodlgs.h > の宣言を含む、`COleInsertObject`ダイアログ クラスと MFC によって提供されるその他の標準のダイアログ。

```Output
\oclient\mainview.cpp(367) : error C2065: 'OLEVERB_PRIMARY' : undeclared identifier
\oclient\mainview.cpp(367) : error C2660: 'DoVerb' : function does not take 1 parameters
```

これらのエラーは、同じ概念があるにもかかわらずに OLE 2 でいくつかの OLE1 定数が変更されているという事実が原因です。 ここで`OLEVERB_PRIMARY` に変わって`OLEIVERB_PRIMARY`します。 OLE1 と OLE 2 の両方では、ユーザーが項目をダブルクリックすると主動詞をコンテナーで実行されます通常。

さらに、`DoVerb`追加パラメーターを受け取るようになりました: ビューへのポインター (`CView`*)。 このパラメーターは、「ビジュアル編集」(またはインプレース アクティブ化) を実装するためにのみ使用されます。 ここでそのパラメーターに設定する null の場合、この時点でこの機能を実装していないためです。

オーバーライドする必要があります、framework ことはありません、インプレースしようとしてアクティブにするようにするには、`COleClientItem::CanActivate`次のようにします。

```cpp
BOOL CRectItem::CanActivate()
{
    return FALSE;
}
```

```Output
\oclient\rectitem.cpp(53) : error C2065: 'GetBounds' : undeclared identifier
\oclient\rectitem.cpp(53) : error C2064: term does not evaluate to a function
\oclient\rectitem.cpp(84) : error C2065: 'SetBounds' : undeclared identifier
\oclient\rectitem.cpp(84) : error C2064: term does not evaluate to a function
```

MFC/OLE1 で`COleClientItem::GetBounds`と`SetBounds`クエリを実行し、項目の範囲を操作するために使用された (、`left`と`top`メンバーが 0 では常に)。 MFC/OLE 2 でより直接的でサポートされる`COleClientItem::GetExtent`と`SetExtent`、対処する、**サイズ**または`CSize`代わりにします。

コードを新しい SetItemRectToServer では、次のように UpdateItemRectFromServer 呼び出しと。

```cpp
BOOL CRectItem::UpdateItemRectFromServer()
{
    ASSERT(m_bTrackServerSize);
    CSize size;
    if (!GetExtent(&size))
        return FALSE;    // blank

    // map from HIMETRIC to screen coordinates
    {
        CClientDC screenDC(NULL);
        screenDC.SetMapMode(MM_HIMETRIC);
        screenDC.LPtoDP(&size);
    }
    // just set the item size
    if (m_rect.Size() != size)
    {
        // invalidate the old size/position
        Invalidate();
        m_rect.right = m_rect.left + size.cx;
        m_rect.bottom = m_rect.top + size.cy;
        // as well as the new size/position
        Invalidate();
    }
    return TRUE;
}

BOOL CRectItem::SetItemRectToServer()
{
    // set the official bounds for the embedded item
    CSize size = m_rect.Size();
    {
        CClientDC screenDC(NULL);
        screenDC.SetMapMode(MM_HIMETRIC);
        screenDC.DPtoLP(&size);
    }
    TRY
    {
        SetExtent(size);    // may do a wait
    }
    CATCH(CException, e)
    {
        return FALSE;  // links will not allow SetBounds
    }
    END_CATCH
    return TRUE;
}
```

```Output
\oclient\frame.cpp(50) : error C2039: 'InWaitForRelease' : is not a member of 'COleClientItem'
\oclient\frame.cpp(50) : error C2065: 'InWaitForRelease' : undeclared identifier
\oclient\frame.cpp(50) : error C2064: term does not evaluate to a function
```

MFC/OLE1 同期 API でコンテナーからサーバーへの呼び出しはいました*シミュレートされた*OLE1 が多くの場合は本質的に非同期であるため、します。 ユーザーからのコマンドを処理する前に、進行中の非同期呼び出しを確認する必要がありました。 指定された MFC/OLE1、`COleClientItem::InWaitForRelease`これを行うための関数。 MFC/OLE 2 で必要ない、すべてをまとめて CMainFrame で OnCommand のオーバーライドを削除することができます。

この時点で OCLIENT のコンパイルし、リンクします。

## <a name="other-necessary-changes"></a>その他の必要な変更

いくつかの点が行われていませんが、保持する OCLIENT の実行、ただしがあります。 以降ではなく今すぐこれらの問題を修正することをお勧めします。

最初に、OLE ライブラリを初期化するために必要です。 これは、呼び出すことで`AfxOleInit`から`InitInstance`:

```cpp
if (!AfxOleInit())
{
    AfxMessageBox("Failed to initialize OLE libraries");
    return FALSE;
}
```

仮想関数のパラメーター リストの変更を確認することをお勧めします。 このような機能の 1 つ`COleClientItem::OnChange`、MFC/OLE コンテナーのすべてのアプリケーションでオーバーライドします。 オンライン ヘルプを調べることで、余分な 'DWORD について' が追加されたことが表示されます。 新しい CRectItem::OnChange は次のようになります。

```cpp
void
CRectItem::OnChange(OLE_NOTIFICATION wNotification, DWORD dwParam)
{
    if (m_bTrackServerSize && !UpdateItemRectFromServer())
    {
        // Blank object
        if (wNotification == OLE_CLOSED)
        {
            // no data received for the object - destroy it
            ASSERT(!IsVisible());
            GetDocument()->DeleteItem(this);
            return; // no update (item is gone now)
        }
    }
    if (wNotification != OLE_CLOSED)
        Dirty();
    Invalidate();
    // any change will cause a redraw
}
```

コンテナー アプリケーションでは、MFC/OLE1 からドキュメント クラスの派生`COleClientDoc`します。 しかし、MFC/OLE 2 でこのクラスが削除されに置き換えられました`COleDocument`(新しい組織をこのやすくコンテナー/サーバー アプリケーションを構築する)。 **#Define**マップされる`COleClientDoc`に`COleDocument`OCLIENT などの MFC/OLE 2/OLE1 MFC アプリケーションの移植を簡略化します。 提供されない機能の 1 つ`COleDocument`によって指定された`COleClientDoc`標準コマンドのメッセージ マップ エントリは、します。 そのためこれは、使用しても、そのサーバー アプリケーション`COleDocument`(間接的に) を搬送しないと、これらのコマンド ハンドラーのオーバーヘッド コンテナー/サーバー アプリケーションがある場合を除いて。 このため CMainDoc メッセージ マップに、次のエントリを追加する必要があります。

```cpp
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE, OnUpdatePasteMenu)
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE_LINK, OnUpdatePasteLinkMenu)
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_LINKS, OnUpdateEditLinksMenu)
ON_COMMAND(ID_OLE_EDIT_LINKS, COleDocument::OnEditLinks)
ON_UPDATE_COMMAND_UI(ID_OLE_VERB_FIRST, OnUpdateObjectVerbMenu)
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_CONVERT, OnUpdateObjectVerbMenu)
ON_COMMAND(ID_OLE_EDIT_CONVERT, OnEditConvert)
```

これらすべてのコマンドの実装は、 `COleDocument`、これは、ドキュメントの基本クラスです。

この時点では、OCLIENT は、機能の OLE コンテナー アプリケーションです。 任意の型 (OLE1 または OLE 2) の項目を挿入することになります。 インプレース アクティブ化を有効にするために必要なコードが実装されていないため項目は OLE1 と同じように、別のウィンドウで編集します。 次のセクションでは、インプレース編集 (「ビジュアル編集」と呼ばれることもあります) を有効にするために必要な変更について説明します。

## <a name="adding-visual-editing"></a>「ビジュアル編集」を追加します。

OLE の最も興味深い機能の 1 つは、インプレース アクティブ化 (または「ビジュアル編集」) です。 この機能は、ユーザーのシームレスな編集インターフェイスを提供するコンテナーのユーザー インターフェイスの一部を引き継ぎ、サーバー アプリケーションを使用できます。 OCLIENT をインプレース アクティブ化を実装するには、いくつかの特殊なリソースといくつか追加のコードを追加する必要があります。 これらのリソースとコードは、通常 AppWizard によって提供される、実際には、「コンテナー」サポートを含む新しい AppWizard アプリケーションから直接借用した次のコードの量。

まず、インプレース アクティブである項目がある場合に使用するメニュー リソースを追加する必要があります。 この追加のメニュー リソースを作成するにはビジュアルでC++IDR_OCLITYPE リソースをコピーして除くすべてのファイルとウィンドウのポップアップを削除します、。 2 つの区分線をグループの分離を示すためにファイルとウィンドウのポップアップに挿入されます (ようになります。ファイル&#124;&#124;ウィンドウ)。 これらの区切り記号は何を意味し、サーバーとコンテナーのメニューのマージ方法の詳細については、次を参照してください。[メニューとリソース。メニューのマージ](../mfc/menus-and-resources-menu-merging.md)します。

これらのメニューを作成したら、フレームワークに情報を持っている必要があります。 これは、呼び出すことで`CDocTemplate::SetContainerInfo`に対してドキュメント テンプレートの一覧に追加する前に、ドキュメント テンプレート。 ドキュメント テンプレートを登録する新しいコードのようになります。

```cpp
CDocTemplate* pTemplate = new CMultiDocTemplate(
    IDR_OLECLITYPE,
    RUNTIME_CLASS(CMainDoc),
    RUNTIME_CLASS(CMDIChildWnd), // standard MDI child frame
    RUNTIME_CLASS(CMainView));

pTemplate->SetContainerInfo(IDR_OLECLITYPE_INPLACE);

AddDocTemplate(pTemplate);
```

IDR_OLECLITYPE_INPLACE リソースは、ビジュアルで作成された特別なインプレース リソースC++します。

インプレース アクティブ化を有効にするのには、両方で変更する必要があるもの、`CView`を派生クラスだけでなく`COleClientItem`(行う) クラスを派生します。 AppWizard によって提供されるすべてのこれらのオーバーライドと、ほとんどの実装は、AppWizard の既定のアプリケーションから直接提供されます。

このポートの最初の手順では、インプレース アクティブ化がオーバーライドすることで、完全無効に`COleClientItem::CanActivate`します。 インプレース アクティブ化を許可するには、この上書きを削除してください。 すべての呼び出しに NULL が渡されましたさらに、 `DoVerb` (はそのうち 2 つ)、インプレース アクティブ化に必要なをのみが、ビューを提供するためです。 インプレース アクティブ化を完全に実装するは、正しいビューに渡すために必要な`DoVerb`呼び出します。 これらの呼び出しの 1 つが`CMainView::OnInsertObject`:

```cpp
pItem->DoVerb(OLEIVERB_SHOW, this);
```

もう 1 つは`CMainView::OnLButtonDblClk`:

```cpp
m_pSelection->DoVerb(OLEIVERB_PRIMARY, this);
```

オーバーライドする必要がある`COleClientItem::OnGetItemPosition`します。 これは、サーバーに、項目は、インプレース アクティブ化されるときに、コンテナーのウィンドウを基準とした、ウィンドウを配置する場所を指示します。 OCLIENT の実装は簡単です。

```cpp
void CRectItem::OnGetItemPosition(CRect& rPosition)
{
    rPosition = m_rect;
}
```

ほとんどのサーバーがインプレースで"のサイズを変更します"と呼ばれるものを実装しても これにより、ユーザーがアイテムの編集中の移動とサイズの [サーバー] ウィンドウができます。 コンテナーは、コンテナー ドキュメント自体のサイズと位置を移動または通常は、ウィンドウをサイズ変更に影響するため、この操作に参加する必要があります。 OCLIENT の実装では、なしの新しい位置とサイズでによって管理される四角形の内部を同期します。

```cpp
BOOL CRectItem::OnChangeItemPosition(const CRect& rectPos)
{
    ASSERT_VALID(this);

    if (!COleClientItem::OnChangeItemPosition(rectPos))
        return FALSE;

    Invalidate();
    m_rect = rectPos;
    Invalidate();
    GetDocument()->SetModifiedFlag();

    return TRUE;
}
```

この時点では、インプレース アクティブ化して、アクティブな場合に、項目を移動してサイズ変更を処理するアイテムを許可するための十分なコードがあるが、コードを使用しないユーザーに編集セッションを終了します。 一部のサーバーはこの機能を提供自体は、esc キーを処理することによって、コンテナーは、アイテムを非アクティブ化する 2 つの方法を提供をお勧めします。(1) をおよび (2) を ESC キーを押して、アイテムの外側をクリックします。

ビジュアルでアクセラレータを追加、ESC キーをC++VK_ESCAPE キーをコマンドにマップされる ID_CANCEL_EDIT がリソースに追加します。 このコマンドのハンドラーが次に示します。

```cpp
// The following command handler provides the standard
// keyboard user interface to cancel an in-place
// editing session.void CMainView::OnCancelEdit()
{
    // Close any in-place active item on this view.
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);
    if (pActiveItem != NULL)
        pActiveItem->Close();
    ASSERT(GetDocument()->GetInPlaceActiveItem(this) == NULL);
}
```

ユーザーがアイテムの外側をクリックするケースを処理するための先頭に次のコードを追加する`CMainView::SetSelection`:

```cpp
if (pNewSel != m_pSelection || pNewSel == NULL)
{
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);
    if (pActiveItem != NULL&& pActiveItem != pNewSel)
        pActiveItem->Close();
}
```

アイテムがアクティブのとき、フォーカスが必要です。 これは、ケースかどうかを確認するには、フォーカスは、ビューがフォーカスを受け取ったとき、常にアクティブな項目を転送できるように OnSetFocus を処理します。

```cpp
// Special handling of OnSetFocus and OnSize are required
// when an object is being edited in-place.
void CMainView::OnSetFocus(CWnd* pOldWnd)
{
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);

    if (pActiveItem != NULL &&
        pActiveItem->GetItemState() == COleClientItem::activeUIState)
    {
        // need to set focus to this item if it is same view
        CWnd* pWnd = pActiveItem->GetInPlaceWindow();
        if (pWnd != NULL)
        {
            pWnd->SetFocus();   // don't call the base class
            return;
        }
    }

    CView::OnSetFocus(pOldWnd);
}
```

ビューが変更されたときに、アクティブな項目のクリッピング四角形が変更されたことを通知する必要があります。 ハンドラーを提供してこれを行う`OnSize`:

```cpp
void CMainView::OnSize(UINT nType, int cx, int cy)
{
    CView::OnSize(nType, cx, cy);
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);
    if (pActiveItem != NULL)
        pActiveItem->SetItemRects();
}
```

## <a name="case-study-hiersvr-from-mfc-20"></a>ケース スタディ: MFC 2.0 から HIERSVR

[HIERSVR](../overview/visual-cpp-samples.md) MFC 2.0 にも含まれていたし、MFC/OLE1 を使用して OLE を実装します。 このノートには、使用されるこのアプリケーションが最初に MFC/OLE 2 クラスを使用する変換の手順について簡単にについて説明します。 しかし、MFC/OLE 2 クラスをよく示すために、初期の移植が完了した後、多くの機能が追加されました。 これらの機能はここでは説明されません。これらの高度な機能の詳細については、サンプル アプリケーションを参照してください。

> [!NOTE]
> コンパイラ エラーおよびステップ バイ ステップのプロセスは、Visual C 2.0 で作成されました。 特定のエラー メッセージと場所は、Visual C 4.0 に変更可能性がありますが、概念的な情報は有効です。

## <a name="getting-it-up-and-running"></a>起動と実行

Hiersvr MFC/OLE を移植する方法は、ビルドし、原因となる明らかなコンパイラ エラーを修正して始めることです。 MFC 2.0 から HIERSVR サンプルを実行して、このバージョンの MFC ではコンパイル (ただし、OCLIENT サンプルを使用して複数の) を解決するのには多くのエラーがないことがわかります。 通常、発生した順序でエラーを以下に示します。

## <a name="compile-and-fix-errors"></a>コンパイルとエラーの修正

```Output
\hiersvr\hiersvr.cpp(83) : error C2039: 'RunEmbedded' : is not a member of 'COleTemplateServer'
```

この最初のエラーに大きな問題を示して、`InitInstance`サーバー用の関数。 OLE サーバーに必要な初期化は、おそらく、最も大きな変更を実行するため、MFC/OLE1 アプリケーションする必要がありますのいずれかです。 ベスト プラクティスでは、AppWizard が OLE サーバーの作成を確認し、適切なコードを変更します。 留意するいくつかの点を次に示します。

OLE ライブラリを呼び出すことにより初期化する必要があります。 `AfxOleInit`

サーバーのリソース ハンドルとランタイム クラス情報を設定することはできませんを設定するドキュメント テンプレート オブジェクトの SetServerInfo を呼び出し、`CDocTemplate`コンス トラクター。

コマンドラインで/Embedding がある場合は、アプリケーションのメイン ウィンドウを表示しません。

必要があります、 **GUID**ドキュメント。 これは、ドキュメントの種類 (128 ビット) の一意の識別子です。 AppWizard によってが作成されます: ここで説明されている手法を使用する場合、新しい AppWizard が生成されるサーバー アプリケーションから新しいコードをコピーすることができます単に「スティール」そのアプリケーションからの GUID。 それ以外の場合は、GUIDGEN を使用できます。BIN ディレクトリ内の EXE ユーティリティです。

「接続」する必要があります、`COleTemplateServer`オブジェクトを呼び出すことによって、ドキュメント テンプレート`COleTemplateServer::ConnectTemplate`します。

アプリケーションがスタンドアロンの実行時に、システム レジストリを更新します。 これにより、ユーザーが移動します。アプリケーションの EXE には、新しい場所を指す Windows システムの登録データベースを更新、新しい場所から実行されます。

すべてを作成する AppWizard に基づいてこれらの変更の適用後`InitInstance`、 `InitInstance` (と関連 GUID) HIERSVR を次のように参照する必要があります。

```cpp
// this is the GUID for HIERSVR documents
static const GUID BASED_CODE clsid =
{ 0xA0A16360L, 0xC19B, 0x101A, { 0x8C, 0xE5, 0x00, 0xDD, 0x01, 0x11, 0x3F, 0x12 } };

/////////////////////////////////////////////////////////////////////////////
// COLEServerApp initialization

BOOL COLEServerApp::InitInstance()
{
    // OLE 2 initialization
    if (!AfxOleInit())
    {
        AfxMessageBox("Initialization of the OLE failed!");
        return FALSE;
    }

    // Standard initialization
    LoadStdProfileSettings();   // Load standard INI file options

    // Register document templates
    CDocTemplate* pDocTemplate;
    pDocTemplate = new CMultiDocTemplate(IDR_HIERSVRTYPE,
        RUNTIME_CLASS(CServerDoc),
        RUNTIME_CLASS(CMDIChildWnd),
        RUNTIME_CLASS(CServerView));
    pDocTemplate->SetServerInfo(IDR_HIERSVRTYPE_SRVR_EMB);
    AddDocTemplate(pDocTemplate);

    // create main MDI Frame window
    CMainFrame* pMainFrame = new CMainFrame;
    if (!pMainFrame->LoadFrame(IDR_MAINFRAME))
        return FALSE;
    m_pMainWnd = pMainFrame;

    SetDialogBkColor(); // gray look

    // enable file manager drag/drop and DDE Execute open
    m_pMainWnd->DragAcceptFiles();
    EnableShellOpen();

    m_server.ConnectTemplate(clsid, pDocTemplate, FALSE);
    COleTemplateServer::RegisterAll();

    // try to launch as an OLE server
    if (RunEmbedded())
    {
        // "short-circuit" initialization -- run as server!
        return TRUE;
    }
    m_server.UpdateRegistry();
    RegisterShellFileTypes();

    // not run as OLE server, so show the main window
    if (m_lpCmdLine[0] == '\0')
    {
        // create a new (empty) document
        OnFileNew();
    }
    else
    {
        // open an existing document
        OpenDocumentFile(m_lpCmdLine);
    }

    pMainFrame->ShowWindow(m_nCmdShow);
    pMainFrame->UpdateWindow();

    return TRUE;
}
```

上記のコードが新しいリソース ID、IDR_HIERSVRTYPE_SRVR_EMB を指すことがわかります。 これは、別のコンテナーに埋め込まれているドキュメントを編集する際に使用するメニュー リソースです。 MFC/OLE1 埋め込みアイテムの編集に固有のメニュー項目が、その場で変更されました。 ファイル ベースのドキュメントを編集する代わりに埋め込みアイテムを編集するときに、まったく別のメニュー構造を使用すると、2 つのモードを別のユーザー インターフェイスを提供するはるかに簡単になります。 後で表示されます、よう、埋め込みオブジェクト、一括編集するときに、まったく別のメニュー リソースが使用されます。

このリソースを作成するには、ビジュアルにリソース スクリプトを読み込むC++既存 IDR_HIERSVRTYPE メニュー リソースをコピーします。 (これは、AppWizard では、同じ名前付け規則) IDR_HIERSVRTYPE_SRVR_EMB には、新しいリソースを変更します。 次に「ファイルの更新」;「ファイルの保存」を変更します。コマンド ID ID_FILE_UPDATE を付けます。 "ファイルのコピーを付けて保存する";「ファイルを付けて保存」も変更します。コマンド ID ID_FILE_SAVE_COPY_AS を付けます。 フレームワークは、これらのコマンドの両方の実装を提供します。

```Output
\hiersvr\svritem.h(60) : error C2433: 'OLESTATUS' : 'virtual' not permitted on data declarations
\hiersvr\svritem.h(60) : error C2501: 'OLESTATUS' : missing decl-specifiers
\hiersvr\svritem.h(60) : error C2146: syntax error : missing ';' before identifier 'OnSetData'
\hiersvr\svritem.h(60) : error C2061: syntax error : identifier 'OLECLIPFORMAT'
\hiersvr\svritem.h(60) : error C2501: 'OnSetData' : missing decl-specifiers
```

オーバーライドに起因するエラーのいくつか`OnSetData`を参照しているため、 **OLESTATUS**型。 **OLESTATUS** OLE1 にエラーが返される方法でした。 これは、ように変更が**HRESULT** OLE 2 の MFC は、通常、変換が、 **HRESULT**に、`COleException`エラーを含みます。 この場合は特定のオーバーライド`OnSetData`を行う最も簡単な方法は、それを削除するために必要ではなくなりました。

```Output
\hiersvr\svritem.cpp(30) : error C2660: 'COleServerItem::COleServerItem' : function does not take 1 parameters
```

`COleServerItem`コンス トラクターは、余分な 'BOOL' パラメーターを受け取ります。 上のメモリ管理を行う方法を決定するフラグ、`COleServerItem`オブジェクト。 これらのオブジェクトのメモリ管理を処理しているフレームワークを TRUE に設定すると、— 必要でなくなったときに、それらを削除します。 HIERSVR 使用`CServerItem`(から派生した`COleServerItem`) このフラグを FALSE に設定しますので、ネイティブのデータの一部としてのオブジェクト。 これにより、HIERSVR の各サーバーのアイテムが削除されたときの判断ができます。

```Output
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class
```

これらのエラーが示すようにようにオーバーライドされていない一部の ' 純粋仮想関数があります。 ほとんどの場合は OnDraw のパラメーター リストが変更されたという事実によって発生します。 このエラーを解決するには、次のように変更します。`CServerItem::OnDraw`次のように (およびに宣言)。

```cpp
BOOL CServerItem::OnDraw(CDC* pDC, CSize& rSize)
{
    // request from OLE to draw node
    pDC->SetMapMode(MM_TEXT); // always in pixels
    return DoDraw(pDC, CPoint(0, 0), FALSE);
}
```

新しいパラメーターは、'rSize' です。 これにより、描画領域のサイズを入力できる便利な場合。 このサイズは内で指定する必要があります**HIMETRIC**します。 この場合は、便利ではありません、この値を入力する、フレームワーク`OnGetExtent`エクステントを取得します。 機能するには、実装する必要があります`OnGetExtent`:

```cpp
BOOL CServerItem::OnGetExtent(DVASPECT dwDrawAspect, CSize& rSize)
{
    if (dwDrawAspect != DVASPECT_CONTENT)
        return COleServerItem::OnGetExtent(dwDrawAspect, rSize);

    rSize = CalcNodeSize();
    return TRUE;
}
```

```Output
\hiersvr\svritem.cpp(104) : error C2065: 'm_rectBounds' : undeclared identifier
\hiersvr\svritem.cpp(104) : error C2228: left of '.SetRect' must have class/struct/union type
\hiersvr\svritem.cpp(106) : error C2664: 'void __pascal __far DPtoLP(struct ::tagPOINT __far *,
    int)__far const ' : cannot convert parameter 1 from 'int __far *' to 'struct ::tagPOINT __far *'
```

CServerItem::CalcNodeSize 関数では、アイテムのサイズに変換されます**HIMETRIC**で格納されている*m_rectBounds*します。 記載されていない '*m_rectBounds*' のメンバー`COleServerItem`が存在しない (これは部分的に置き換えられました*です*、OLE 2 でこのメンバーがより使用量が若干異なりますが、*m_rectBounds* OLE1 ででした)。 設定ではなく、 **HIMETRIC**サイズにこのメンバー変数が返すします。 この戻り値がで使用される`OnGetExtent`、以前に実装します。

```cpp
CSize CServerItem::CalcNodeSize()
{
    CClientDC dcScreen(NULL);

    m_sizeNode = dcScreen.GetTextExtent(m_strDescription,
        m_strDescription.GetLength());
    m_sizeNode += CSize(CX_INSET * 2, CY_INSET * 2);

    // set suggested HIMETRIC size
    CSize size(m_sizeNode.cx, m_sizeNode.cy);
    dcScreen.SetMapMode(MM_HIMETRIC);
    dcScreen.DPtoLP(&size);
    return size;
}
```

ようもオーバーライド`COleServerItem::OnGetTextData`します。 この関数は MFC/OLE では古いであり、別のメカニズムが置き換えられます。 MFC 3.0 バージョンの MFC OLE サンプル[HIERSVR](../overview/visual-cpp-samples.md)オーバーライドすることでこの機能を実装して`COleServerItem::OnRenderFileData`します。 OnGetTextData オーバーライドを削除できるように、この機能はこの基本の移植の重要ではありません。

Svritem.cpp で対処していたいない多くの詳細についてエラーがあります。 「本物」のエラーではないが、以前のエラーの原因となったエラーのみです。

```Output
\hiersvr\svrview.cpp(325) : error C2660: 'CopyToClipboard' : function does not take 2 parameters
```

`COleServerItem::CopyToClipboard` サポートしていません、`bIncludeNative`フラグ。 ネイティブのデータ (サーバー項目のシリアル化の関数によって出力されるデータ) は、最初のパラメーターを削除するように常にコピーします。 さらに、 `CopyToClipboard` FALSE を返す代わりにエラーが発生したときに例外をスローします。 次の手順 CServerView::OnEditCopy のコードを変更します。

```cpp
void CServerView::OnEditCopy()
{
    if (m_pSelectedNode == NULL)
        AfxThrowNotSupportedException();

    TRY
    {
        m_pSelectedNode->CopyToClipboard(TRUE);
    }
    CATCH_ALL(e)
    {
        AfxMessageBox("Copy to clipboard failed");
    }
    END_CATCH_ALL
}
```

HIERSVR の MFC 2.0 バージョンのコンパイル結果として OCLIENT の同じバージョンよりも多くのエラーがありましたがあった少ない実際に変更します。

この時点で HIERSVR はコンパイルしリンクし、OLE サーバーが次で実装されている一括編集機能を使用せずに機能します。

## <a name="adding-visual-editing"></a>「ビジュアル編集」を追加します。

このサーバー アプリケーションに「ビジュアル編集」(またはインプレース アクティブ化) を追加するには、いくつかの点の注意する必要がありますのみがあります。

- 項目が、インプレース アクティブなときに使用される特別なメニュー リソースが必要です。

- ツールバー (上記で説明したメニュー リソースに一致)、サーバーからアクセスできるメニュー コマンドに一致するように、標準ツールバーのサブセットのみをする必要がありますので、このアプリケーションは、ツールバーを持ちます。

- 派生した新しいクラスを作成する必要があります`COleIPFrameWnd`で埋め込み先ユーザー インターフェイスを提供する (ようから派生した CMainFrame `CMDIFrameWnd`、MDI ユーザー インターフェイスを提供します)。

- これらの特殊なリソースやクラスをフレームワークに教える必要があります。

メニュー リソースが簡単に作成できます。 実行 Visual C++、IDR_HIERSVRTYPE_SRVR_IP というメニュー リソースに IDR_HIERSVRTYPE メニュー リソースをコピーします。 メニューを変更するは、編集、およびヘルプ] メニューの [ポップアップのままにするようにします。 2 つの区切り記号を編集し、ヘルプ メニュー間にあるメニューに追加 (ようになります。編集&#124;&#124;役立ちます)。 これらの区切り記号は何を意味し、サーバーとコンテナーのメニューのマージする方法の詳細については、次を参照してください。[メニューとリソース。メニューのマージ](../mfc/menus-and-resources-menu-merging.md)します。

サブセットのツールバーのビットマップは、"Server"オプションをオンに新しい AppWizard が生成されたアプリケーションから 1 つをコピーすることで簡単に作成できます。 このビットマップは、Visual C にインポートできます。 ビットマップの ID の IDR_HIERSVRTYPE_SRVR_IP を付与してください。

クラスから派生する`COleIPFrameWnd`サーバーのサポートも AppWizard が生成されたアプリケーションからコピーできます。 IPFRAME、両方のファイルをコピーします。CPP IPFRAME.H し、プロジェクトに追加します。 確認、`LoadBitmap`呼び出しが IDR_HIERSVRTYPE_SRVR_IP、前の手順で作成されたビットマップを参照します。

これですべての新しいリソースやクラスを作成すると、これらについて認識しています (およびこのアプリケーションを今すぐがインプレース編集をサポートしていることを知っている) フレームワークように必要なコードを追加します。 ここにパラメーターを追加では、`SetServerInfo`呼び出し、`InitInstance`関数。

```cpp
pDocTemplate->SetServerInfo(IDR_HIERSVRTYPE_SRVR_EMB,
    IDR_HIERSVRTYPE_SRVR_IP,
    RUNTIME_CLASS(CInPlaceFrame));
```

これで、インプレースを実行する準備が埋めこみ先編集をサポートする任意のコンテナーでします。 ただしは 1 つの小さなバグ、コードでまだ潜んでいます。 HIERSVR は、ユーザーがマウスの右ボタンを押したときに表示される、コンテキスト メニューをサポートします。 このメニューは、HIERSVR は完全に起動していますが、埋め込み先編集時に機能しないときに機能します。 理由は、この 1 行の CServerView::OnRButtonDown でコードをにピン留めできます。

```cpp
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,
    point.x,
    point.y,
    AfxGetApp()->m_pMainWnd);
```

参照に注目してください`AfxGetApp()->m_pMainWnd`します。 インプレース アクティブ化は、メイン ウィンドウと m_pMainWnd を設定するは、通常は表示されません。 さらに、このウィンドウを指す、*メイン*アプリケーションのウィンドウで、サーバーが完全に表示される、MDI フレーム ウィンドウを開く、またはスタンドアロンで実行します。 アクティブなフレーム ウィンドウを参照していません: ときに、インプレース アクティブ化は、フレーム ウィンドウから派生`COleIPFrameWnd`します。 一括編集するには、このバージョンの MFC は、新しい関数を追加するときにも正しいのアクティブなウィンドウを取得する`AfxGetMainWnd`します。 一般に、この関数の代わりを使用する必要があります`AfxGetApp()->m_pMainWnd`します。 このコードは、次のように変更する必要があります。

```cpp
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,
    point.x,
    point.y,
    AfxGetMainWnd());
```

インプレース アクティブ化の機能の有効な最小 OLE サーバーがあるようになりました。 まだ多くの機能/OLE1 MFC で使用できなかった MFC/OLE 2 で使用できます。 機能を実装するのには、他のアイデア HIERSVR サンプルを参照してください。 HIERSVR を実装する機能の一部は、以下に示します。

- ズーム コンテナーに対する真の WYSIWYG 動作として使用します。

- ドラッグ アンド ドロップし、カスタムのクリップボード形式。

- 選択範囲とコンテナーのウィンドウのスクロールが変更されます。

また、MFC 3.0 で HIERSVR サンプルは、サーバー アイテムの若干異なるデザインを使用します。 これにより、メモリを節約できより柔軟なリンクは、します。 HIERSVR の 2.0 バージョンで、ツリー内の各ノード*の*`COleServerItem`します。 `COleServerItem` 実行ごとのこれらのノードでは、必ずしも必要では少し多くのオーバーヘッドが発生が、`COleServerItem`のアクティブなリンクが必要です。 特定の時点が非常にアクティブなリンクがあります、ほとんどの場合。 このバージョンの MFC で HIERSVR をより効率的にするをするには、間のノードから、`COleServerItem`します。 両方の CServerNode と`CServerItem`クラス。 `CServerItem` (から派生した`COleServerItem`) のみが必要に応じて作成します。 コンテナー (またはコンテナー) は、その特定のノードにその特定のリンクを使用して停止とに関連付けられた、CServerNode ようオブジェクトは削除されます。 この設計は、効率と柔軟性を高めるには。 その柔軟性は、複数のリンクを選択範囲を扱う場合にします。 複数の選択をサポート HIERSVR の 2 つのバージョンのどちらを追加する (および、このような選択項目へのリンクをサポートするために) はるかに簡単だ MFC 3.0 バージョン HIERSVR のため、`COleServerItem`はネイティブのデータから分離します。

## <a name="see-also"></a>関連項目

[番号順テクニカル ノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカル ノート](../mfc/technical-notes-by-category.md)
