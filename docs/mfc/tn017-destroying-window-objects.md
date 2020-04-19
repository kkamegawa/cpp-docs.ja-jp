---
title: TN017:ウィンドウ オブジェクトの破棄
ms.date: 11/04/2016
f1_keywords:
- vc.objects
helpviewer_keywords:
- destroying windows
- TN017
- PostNcDestroy method [MFC]
ms.assetid: 5bf208a5-5683-439b-92a1-547c5ded26cd
ms.openlocfilehash: 9e52112bed0f583a3f5652f9213bd5049d543a80
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306156"
---
# <a name="tn017-destroying-window-objects"></a>TN017:ウィンドウ オブジェクトの破棄

この注の説明の使用、 [:postncdestroy](../mfc/reference/cwnd-class.md#postncdestroy)メソッド。 カスタマイズされた割り当てを実行する場合は、このメソッドを使用して`CWnd`の派生オブジェクト。 このメモを使用する理由についても説明[に](../mfc/reference/cwnd-class.md#destroywindow)の代わりに、C++ Windows オブジェクトを破棄する、**削除**演算子。

このトピックのガイドラインに従う場合は、いくつかのクリーンアップに関する問題があります。 削除/のようなシステム リソースを解放し忘れる C++ のメモリを解放し忘れたなどの問題、これらの問題が生じる`HWND`、またはオブジェクトを何回も解放します。

## <a name="the-problem"></a>問題を

Windows の各オブジェクト (クラスのオブジェクトから派生した`CWnd`) C++ オブジェクトを表す、 `HWND`。 C++ のオブジェクトがアプリケーションのヒープで割り当てられると`HWND`ウィンドウ マネージャーによってシステム リソースに s が割り当てられています。 システムを回避するルールのセットを提供する必要がありますウィンドウ オブジェクトを破棄するいくつかの方法があるため、リソースまたはメモリ リークが発生します。 オブジェクトと Windows のハンドルが複数回破棄されるおそれもあります。

## <a name="destroying-windows"></a>Windows の破棄

以下は、Windows オブジェクトを破棄する許可されている 2 つの方法です。

- 呼び出す`CWnd::DestroyWindow`Windows API または`DestroyWindow`します。

- 明示的に削除する、**削除**演算子。

最初のケースが最も一般的です。 コードを呼び出さない場合でも、このケースが適用されます`DestroyWindow`直接します。 ユーザーが直接フレーム ウィンドウを閉じるし、この操作は、WM_CLOSE メッセージを生成、このメッセージに既定の応答を呼び出すことです`DestroyWindow.`親ウィンドウが破棄されると、Windows を呼び出す`DestroyWindow`すべての子。

2 番目のケースでの使用、**削除**演算子を Windows のオブジェクトには、まれでする必要があります。 以下のものを使用している場合も**削除**は適切な選択肢です。

## <a name="auto-cleanup-with-cwndpostncdestroy"></a>:Postncdestroy を使用して自動クリーンアップ

システムでは、Windows のウィンドウを破棄、ウィンドウに送信された最後の Windows メッセージはへが。 既定の`CWnd`そのメッセージのハンドラーは、 [cwnd::onncdestroy](../mfc/reference/cwnd-class.md#onncdestroy)します。 `OnNcDestroy` デタッチは、 `HWND` C++ からオブジェクトし、仮想関数を呼び出す`PostNcDestroy`します。 いくつかのクラスは、C++ オブジェクトを削除するには、この関数をオーバーライドします。

既定の実装`CWnd::PostNcDestroy`ウィンドウ オブジェクトのスタック フレームに割り当てられた、またはその他のオブジェクトに埋め込まれたに適切なは、何もしません。 これは、他のオブジェクトのヒープに割り当てられるように設計されたウィンドウのオブジェクトを適していません。 つまり、他の C++ オブジェクトに埋め込まれていないウィンドウのオブジェクトの適切ながありません。

単独でヒープに割り当てられるように設計されたこれらのクラスでオーバーライド、`PostNcDestroy`を実行するメソッド、**削除**します。 このステートメントは、C++ オブジェクトに関連付けられているメモリを解放します。 場合でも、既定`CWnd`デストラクター呼び出し`DestroyWindow`場合*m_hWnd*が NULL 以外の場合、これが発生しても無限再帰のハンドルがクリーンアップ フェーズ中に分離され、NULL であるがためです。

> [!NOTE]
>  通常、システムを呼び出します`CWnd::PostNcDestroy`Windows へのメッセージを処理した後、`HWND`とC++ウィンドウ オブジェクトが接続されていません。 システムは呼び出すことも`CWnd::PostNcDestroy`ほとんどの実装で[cwnd::create](../mfc/reference/cwnd-class.md#create)障害が発生した場合に呼び出します。 自動クリーンアップの規則は、このトピックの後半で説明します。

## <a name="auto-cleanup-classes"></a>自動クリーンアップ クラス

自動クリーンアップは、次のクラスは設計されていません。 値型は、通常他の C++ オブジェクトまたはスタックに埋め込まれます。

- すべての標準の Windows コントロール (`CStatic`、 `CEdit`、`CListBox`など)。

- すべての子ウィンドウから直接派生した`CWnd`(たとえば、カスタム コントロール)。

- 分割ウィンドウ (`CSplitterWnd`)。

- 既定のコントロール バー (クラスから派生した`CControlBar`を参照してください[テクニカル ノート 31](../mfc/tn031-control-bars.md)コントロール バー オブジェクト用の自動削除を有効にするため)。

- ダイアログ ボックス (`CDialog`) スタック フレームのモーダル ダイアログ ボックス用に設計されています。

- 除くすべての標準のダイアログ`CFindReplaceDialog`します。

- ClassWizard によって作成された既定のダイアログ ボックス。

自動クリーンアップは、次のクラスは設計されています。 単独でヒープに通常割り当てられます。

- メイン フレーム ウィンドウ (から直接または間接的に派生した`CFrameWnd`)。

- Windows の表示 (から直接または間接的に派生した`CView`)。

これらの規則に違反する場合は、オーバーライド、`PostNcDestroy`派生クラスのメソッド。 自動クリーンアップをクラスに追加するには基本クラスを呼び出すし、操作を行います、**削除**します。 クラスから自動クリーンアップを削除するには、呼び出す`CWnd::PostNcDestroy`はなく直接、`PostNcDestroy`直接基底クラスのメソッド。

自動クリーンアップの動作を変更する最も一般的な用途では、ヒープに割り当て可能なモードレスのダイアログを作成します。

## <a name="when-to-call-delete"></a>呼び出しを削除するタイミング

呼び出すことをお勧めします。 `DestroyWindow` 、C++ メソッドまたはグローバルのいずれかで、Windows オブジェクトを破棄する`DestroyWindow`API。

グローバル呼び出さない`DestroyWindow`MDI 子ウィンドウを破棄する API。 仮想メソッドを使用する必要があります`CWnd::DestroyWindow`代わりにします。

C++ ウィンドウ オブジェクトの自動クリーンアップを行わない場合、使用して、**削除**演算子を呼び出すしようとするとメモリ リークが発生できる`DestroyWindow`で、`CWnd::~CWnd`デストラクターの場合は、VTBL が正しく派生クラスを指していません。 これは、システムは、適切な破棄を呼び出すメソッドを検出できないため、発生します。 使用して`DestroyWindow`の代わりに**削除**これらの問題を回避できます。 これは微妙なエラーなので、デバッグ モードでコンパイルすると、危険性が場合に、次の警告が生成されます。

```
Warning: calling DestroyWindow in CWnd::~CWnd
    OnDestroy or PostNcDestroy in derived class will not be called
```

場合は、自動クリーンアップが実行されている C++ Windows オブジェクトを呼び出す必要があります`DestroyWindow`します。 使用する場合、**削除**演算子を直接、MFC の診断メモリ アロケーターいたします 2 倍、メモリが解放されます。 2 つのインスタンスは、最初の明示的な呼び出しおよび間接呼び出し**削除**の自動クリーンアップの実装で`PostNcDestroy`します。

呼び出した後`DestroyWindow`、非自動クリーンアップ オブジェクトで、C++オブジェクトがまだ存在しますが、 *m_hWnd*は NULL になります。 呼び出した後`DestroyWindow`自動クリーンアップ オブジェクトでは、C++ のオブジェクトが失われますの自動クリーンアップの実装で C++ delete 演算子によって解放`PostNcDestroy`します。

## <a name="see-also"></a>関連項目

[番号順テクニカル ノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカル ノート](../mfc/technical-notes-by-category.md)
