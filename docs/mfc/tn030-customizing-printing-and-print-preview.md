---
title: TN030:印刷と印刷プレビューのカスタマイズ
ms.date: 06/28/2018
f1_keywords:
- vc.print
helpviewer_keywords:
- TN030
- customizing printing and print preview
- printing [MFC], views
- printing views [MFC]
- print preview [MFC], customizing
ms.assetid: 32744697-c91c-41b6-9a12-b8ec01e0d438
ms.openlocfilehash: 09938c5cec2812998d5e76e15154754ad3ac3e0b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62305685"
---
# <a name="tn030-customizing-printing-and-print-preview"></a>TN030:印刷と印刷プレビューのカスタマイズ

> [!NOTE]
> 次のテクニカル ノートは、最初にオンライン ドキュメントの一部とされてから更新されていません。 結果として、一部のプロシージャおよびトピックが最新でないか、不正になります。 最新の情報について、オンライン ドキュメントのキーワードで関係のあるトピックを検索することをお勧めします。

この注は、印刷と印刷プレビューのカスタマイズのプロセスについて説明しで使用されるコールバック ルーチンの目的について説明します`CView`のメンバー関数とコールバック ルーチン`CPreviewView`します。

## <a name="the-problem"></a>問題を

MFC では、ほとんどの印刷用の完全なソリューションが用意されていて、印刷プレビューの必要があります。 ほとんどの場合、わずかな追加コードは、印刷プレビューを表示する必要があります。 ただし、印刷を最適化するために、開発者は、かなりの労力を必要とする方法は、一部のアプリケーションは、印刷プレビュー モードに特定のユーザー インターフェイス要素を追加する必要があります。

## <a name="efficient-printing"></a>効率的な印刷

MFC アプリケーションが標準的なメソッドを使用してを印刷する場合、Windows は、メモリ内のメタファイルにすべてのグラフィック デバイス インターフェイス (GDI) の出力呼び出しを指示します。 ときに`EndPage`が呼び出されると、Windows で 1 つのページを印刷するプリンターを必要とする各物理バンドに対して 1 回メタファイルを再生します。 このレンダリング中に GDI は、その継続する必要がありますを決定する、中止の手順を頻繁にクエリします。 通常、中止の手順では、印刷ダイアログを使用して印刷ジョブを中止する可能性があるため、処理するメッセージが可能です。

残念ながら、印刷処理速度の遅いこのことができます。 場合は、印刷、アプリケーションでは、標準的な技法を使用して実現できるよりも高速である必要があります、手動の縞模様を実装する必要があります。

## <a name="print-banding"></a>縞模様を印刷します。

手作業でバンド、再実装する必要あります印刷ループように`OnPrint`(バンド) 1 ページあたり複数回と呼びます。 印刷ループの実装で、 `OnFilePrint` viewprnt.cpp 内の関数。 `CView`-派生クラスで、print コマンドを処理するためのメッセージ マップ エントリが印刷関数を呼び出すように、この関数がオーバー ロードします。 コピー、`OnFilePrint`ルーチンと変更、印刷ループの縞模様を実装します。 おそらくは、バンド四角形を関数に渡す、印刷、印刷されるページのセクションに基づく描画を最適化するようにもします。

次に、頻繁に呼び出す必要があります`QueryAbort`バンドの描画中にします。 それ以外の場合、中止プロシージャが呼び出されないと、ユーザーが印刷ジョブを取り消すことができません。

## <a name="print-preview-electronic-paper-with-user-interface"></a>Print Preview:電子ペーパーでは、ユーザー インターフェイス

印刷プレビューでは、基本的に、しようとプリンターのエミュレーションを表示します。 既定では、メイン ウィンドウのクライアント領域はウィンドウ内に完全に 1 つまたは 2 つのページを表示するために使用します。 ユーザーはより詳細に表示するページの領域にズーム インできます。 追加のサポートとユーザーをプレビュー モードでドキュメントを編集する許可も可能性があります。

## <a name="customizing-print-preview"></a>印刷プレビューのカスタマイズ

印刷プレビューの変更の 1 つの側面にのみ説明します。プレビュー モードにする UI を追加します。 その他の変更が可能であればには、このような変更がこの説明のスコープ外に出るは。

## <a name="to-add-ui-to-the-preview-mode"></a>プレビュー モードに UI を追加するには

1. ビューからクラスを派生`CPreviewView`します。

2. 必要なユーザー インターフェイスに対するコマンド ハンドラーを追加します。

3. 表示する視覚的な側面を追加する場合は、オーバーライド`OnDraw`呼び出した後、描画を実行して`CPreviewView::OnDraw`します。

## <a name="onfileprintpreview"></a>OnFilePrintPreview

これは、印刷プレビューのコマンド ハンドラーです。 既定の実装を示します。

```cpp
void CView::OnFilePrintPreview()
{
    // In derived classes, implement special window handling here
    // Be sure to Unhook Frame Window close if hooked.

    // must not create this on the frame. Must outlive this function
    CPrintPreviewState* pState = new CPrintPreviewState;

    if (!DoPrintPreview(AFX_IDD_PREVIEW_TOOLBAR, this,
        RUNTIME_CLASS(CPreviewView), pState))
    {
        // In derived classes, reverse special window handling
        // here for Preview failure case

        TRACE0("Error: DoPrintPreview failed");
        AfxMessageBox(AFX_IDP_COMMAND_FAILURE);
        delete pState;  // preview failed to initialize, delete State now
    }
}
```

`DoPrintPreview` アプリケーションのメイン ウィンドウを非表示になります。 コントロール バー、ステータス バーなどを保持できる、pState でそれらを指定]-> [*dwStates* (これは、ビット マスクとビット個々 のコントロール バーが AFX_CONTROLBAR_MASK (AFX_IDW_MYBAR) で定義されている) メンバー。 ウィンドウ pState]-> [*nIDMainPane*は自動的に非表示し、reshown はウィンドウです。 `DoPrintPreview` 標準のプレビュー UI のボタン バーが作成されます。 ウィンドウの特別な処理が必要な場合は、前に行う必要がある他のウィンドウを表示または非表示など`DoPrintPreview`が呼び出されます。

既定で、印刷プレビューを終了すると、コントロール バーを返しますに元の状態と、メイン ウィンドウに表示されます。 特別な処理が必要な場合は、オーバーライドで行う必要があります`EndPrintPreview`します。 場合`DoPrintPreview`失敗した場合も特別な処理を提供します。

呼び出すと呼びます。

- プレビュー ツールバーのダイアログ テンプレートのリソース ID。

- 印刷プレビュー、印刷を実行するビューへのポインター。

- [プレビュー] ビュー クラスのランタイム クラスです。 呼び出すで動的に作成します。

- CPrintPreviewState のポインター。 CPrintPreviewState 構造体 (またはより多くの状態が保持されますが、アプリケーションに必要がある場合は、派生構造) する必要が*いない*フレーム上に作成します。 呼び出すはモードレスあり、そのときが呼び出されるまで、この構造体は存続する必要があります。

  > [!NOTE]
  > 個別のビューまたはビューのクラスは、印刷のサポートの必要がある場合は、2 番目のパラメーターとしてそのオブジェクトへのポインターを渡す必要があります。

## <a name="endprintpreview"></a>そのとき

これは、印刷プレビュー モードを終了すると呼ばれます。 印刷プレビューで最後に表示されたドキュメントのページに移動することが望ましいです。 `EndPrintPreview` そのためには、アプリケーションのチャンスです。 PInfo]-> [*m_nCurPage*メンバーが (最も左にある 2 つのページが表示されていた場合)、表示された最後のページで、ポインターがページの場所に、ユーザーが関心がについてのヒント。 アプリケーションのビューの構造がフレームワークに既知でないために、選択したポイントに移動するコードを提供する必要があります。

呼び出しの前に、ほとんどのアクションを実行する必要があります`CView::EndPrintPreview`します。 この呼び出しの効果を反転させます`DoPrintPreview`pView や pDC への pInfo を削除します。

```cpp
// Any further cleanup should be done here.
CView::EndPrintPreview(pDC, pInfo, point, pView);
```

## <a name="cwinapponfileprintsetup"></a>CWinApp::OnFilePrintSetup

これは、印刷のセットアップ メニュー項目にマップする必要があります。 ほとんどの場合は、実装をオーバーライドする必要はありません。

## <a name="page-nomenclature"></a>ページの命名規則

別の問題では、ページの番号と注文です。 簡単なワード プロセッサの種類のアプリケーションでは、これは、簡単な問題です。 ほとんどの印刷プレビューのシステムでは、各印刷ページがドキュメント内の 1 つのページに対応するいると仮定します。

汎用化されたソリューションを提供しようとするは、次の点を検討してください。 CAD システムを想像してください。 ユーザーは、いくつかの E サイズの用紙をカバーする描画を持ちます。 E サイズで (またはより小さいスケール) プロッター、ページ番号場合の簡単なようになります。 用紙 1 枚あたり 16 A サイズのページの印刷、レーザー プリンターは印刷プレビュー検討事項「ページ」が、

導入の段落が示すよう、プリンターのように印刷プレビューが機能しています。 そのため、ユーザーが選択されている特定のプリンターからなるものが表示されます。 各ページに印刷するイメージを決定するビューの責任です。

ページの説明文字列、`CPrintInfo`構造体には、1 ページあたり 1 つの数値として表現できる場合に、ユーザーにページ番号を表示する手段を提供します (「ページ 1」のようにまたは"ページ 1-2")。 この文字列の既定の実装で使用されます`CPreviewView::OnDisplayPageNumber`します。 別のディスプレイが必要な場合は、たとえば、"シート 1 のセクションでは A、B"を提供する仮想関数をオーバーライドいずれかの可能性があります。

## <a name="see-also"></a>関連項目

[番号順テクニカル ノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカル ノート](../mfc/technical-notes-by-category.md)
