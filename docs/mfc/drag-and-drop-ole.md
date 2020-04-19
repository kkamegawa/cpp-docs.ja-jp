---
title: OLE のドラッグ アンド ドロップ
description: Microsoft Foundation Classes の概要 (MFC) OLE ドラッグアンドドロップ、ドロップソースの実装方法、ドロップ先、およびドラッグアンドドロップをカスタマイズする方法について説明します。
ms.date: 02/09/2020
helpviewer_keywords:
- OLE server applications [MFC], drag and drop
- drag and drop [MFC]
- OLE applications [MFC], drag and drop
- File Manager drag and drop support [MFC]
- drag and drop [MFC], about OLE drag and drop
- OLE drag and drop [MFC]
ms.assetid: a4595350-ca06-4400-88a1-f0175c76b77b
ms.openlocfilehash: c601e8f0324510346513dc8da48dd1a83c95bceb
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127869"
---
# <a name="ole-drag-and-drop"></a>OLE のドラッグ アンド ドロップ

OLE のドラッグアンドドロップ機能は、主にデータのコピーと貼り付けを行うためのショートカットです。 クリップボードを使用してデータをコピーまたは貼り付ける場合は、いくつかの手順を実行する必要があります。 データを選択し、 **[編集]** メニューの **[切り取り]** または **[コピー]** をクリックします。 次に、目的のアプリまたはウィンドウに移動し、ターゲットの場所にカーソルを置きます。 最後に、メニューから [**編集** > **貼り付け**] を選択します。

OLE ドラッグアンドドロップ機能は、ファイルマネージャーのドラッグアンドドロップメカニズムとは異なります。 ファイルマネージャーは、ファイル名のみを処理でき、ファイル名をアプリケーションに渡すために特に設計されています。 OLE でのドラッグアンドドロップは、より一般的な操作です。 これにより、クリップボードに配置できる任意のデータをドラッグアンドドロップすることができます。

OLE ドラッグアンドドロップを使用する場合は、プロセスから2つのステップを削除します。 ソースウィンドウ ("ドロップソース") からデータを選択し、それを目的の場所 ("ドロップターゲット") にドラッグします。 マウスボタンを放してドロップします。 操作を行うと、メニューが不要になり、コピー/貼り付けの順序よりも速くなります。 要件は1つだけです。ドロップソースとドロップ先の両方が開いている必要があり、少なくとも画面に部分的に表示されている必要があります。

OLE ドラッグアンドドロップを使用すると、データを1つの場所から別の場所に簡単に転送できます。ドキュメント内、異なるドキュメント間、またはアプリケーション間でデータを転送できます。 コンテナーまたはサーバーアプリケーションで実装される場合があります。 すべてのアプリケーションには、ドロップソース、ドロップ先、またはその両方を指定できます。 アプリケーションがドロップソースとドロップ先の両方のサポートを実装している場合は、子ウィンドウ間でドラッグアンドドロップを行うことも、1つのウィンドウ内でドラッグアンドドロップすることもできます。 この機能により、アプリケーションの使用が非常に簡単になります。

[データオブジェクトとデータソース (OLE)](../mfc/data-objects-and-data-sources-ole.md)の記事では、アプリケーションにデータ転送を実装する方法について説明します。 また、MFC OLE サンプル[OCLIENT](../overview/visual-cpp-samples.md)および[HIERSVR](../overview/visual-cpp-samples.md)を調べると便利です。

## <a name="implement-a-drop-source"></a>ドロップソースの実装

アプリケーションでドラッグアンドドロップ操作にデータを提供するには、ドロップソースを実装します。 ドロップソースの基本的な実装は比較的単純です。 最初の手順は、ドラッグ操作を開始するイベントを特定することです。 推奨されるユーザーインターフェイスガイドラインでは、選択したデータ内のあるポイントで**WM_LBUTTONDOWN**イベントが発生したときのドラッグ操作の開始を定義します。 MFC OLE サンプル[OCLIENT](../overview/visual-cpp-samples.md)および[HIERSVR](../overview/visual-cpp-samples.md)は、次のガイドラインに従います。

アプリケーションがコンテナーであり、選択したデータが `COleClientItem`型のリンクされたオブジェクトまたは埋め込みオブジェクトの場合は、その `DoDragDrop` メンバー関数を呼び出します。 それ以外の場合は、`COleDataSource` オブジェクトを構築し、選択範囲で初期化して、データソースオブジェクトの `DoDragDrop` メンバー関数を呼び出します。 アプリケーションがサーバーの場合は、`COleServerItem::DoDragDrop`を使用します。 標準のドラッグアンドドロップ動作のカスタマイズの詳細については、「[ドラッグアンドドロップのカスタマイズ](#customize-drag-and-drop)」セクションを参照してください。

`DoDragDrop` が**DROPEFFECT_MOVE**を返した場合は、ソースドキュメントからすぐにソースデータを削除します。 `DoDragDrop` からのその他の戻り値には、ドロップソースに対する影響はありません。

詳細については、「 [ole データオブジェクトとデータソース: 作成と破棄](../mfc/data-objects-and-data-sources-creation-and-destruction.md)」および「 [ole データオブジェクトとデータソース: 操作](../mfc/data-objects-and-data-sources-manipulation.md)\.」を参照してください。

## <a name="implement-a-drop-target"></a>ドロップ先の実装

ドロップソースよりもドロップターゲットを実装するには若干の作業が必要ですが、比較的単純です。

### <a name="to-implement-an-ole-drop-target"></a>OLE ドロップターゲットを実装するには

1. まだ存在していない場合は、アプリケーションの `InitInstance` メンバー関数に `AfxOleInit` の呼び出しを追加します。 この呼び出しは、OLE ライブラリを初期化するために必要です。

1. ドロップ先にするアプリケーションの各ビューにメンバー変数を追加します。 このメンバー変数は `COleDropTarget` 型であるか、またはそれから派生したクラスである必要があります。

1. **WM_CREATE**メッセージ (通常 `OnCreate`) を処理するビュークラスの関数から、新しいメンバー変数の `Register` メンバー関数を呼び出します。 ビューが破棄されると、`Revoke` が自動的に呼び出されます。

1. 次の関数をオーバーライドします。 アプリケーション全体で同じ動作が必要な場合は、これらの関数をビュークラスでオーバーライドします。 分離されたケースで動作を変更する場合、または非`CView` ウィンドウでの削除を有効にする場合は、`COleDropTarget`派生クラスでこれらの関数をオーバーライドします。

   | オーバーライド | 許可する方法 |
   | -------- | -------- |
   | `OnDragEnter` | ウィンドウで削除操作を実行します。 カーソルがウィンドウに最初に入ったときに呼び出されます。 |
   | `OnDragLeave` | ドラッグ操作によって指定されたウィンドウが離れたときの特殊な動作。 |
   | `OnDragOver` | ウィンドウで削除操作を実行します。 カーソルがウィンドウ間をドラッグしているときに呼び出されます。 |
   | `OnDrop` | 指定されたウィンドウにドロップされるデータの処理。 |
   | `OnScrollBy` | ターゲットウィンドウでのスクロールが必要な場合の特殊な動作。 |

MAINVIEW を参照してください。これらの関数を連携させる方法の例については、MFC OLE サンプル[OCLIENT](../overview/visual-cpp-samples.md)の一部である CPP ファイルをご利用ください。

詳細については、「 [ole データオブジェクトとデータソース: 作成と破棄](../mfc/data-objects-and-data-sources-creation-and-destruction.md)」および「 [ole データオブジェクトとデータソース: 操作](../mfc/data-objects-and-data-sources-manipulation.md)\.」を参照してください。

## <a name="customize-drag-and-drop"></a>ドラッグアンドドロップのカスタマイズ

ほとんどのアプリケーションでは、ドラッグアンドドロップ機能の既定の実装で十分です。 ただし、アプリケーションによっては、この標準動作の変更が必要になる場合があります。 ここでは、これらの既定値を変更するために必要な手順について説明します。 この手法を使用すると、複合ドキュメントをサポートしていないアプリケーションをドロップソースにすることができます。

標準の OLE ドラッグアンドドロップ動作をカスタマイズしている場合、または OLE 以外のアプリケーションがある場合は、データを格納する `COleDataSource` オブジェクトを作成する必要があります。 ユーザーがドラッグアンドドロップ操作を開始すると、コードでは、ドラッグアンドドロップ操作をサポートする他のクラスからではなく、このオブジェクトから `DoDragDrop` 関数を呼び出す必要があります。

必要に応じて、`COleDropSource` オブジェクトを作成して、変更する動作の種類に応じて、削除を制御し、その機能の一部をオーバーライドすることもできます。 このドロップソースオブジェクトを `COleDataSource::DoDragDrop` に渡して、これらの関数の既定の動作を変更します。 これらの異なるオプションを使用すると、アプリケーションでドラッグアンドドロップ操作をサポートする方法に大きな柔軟性がもたらされます。 データソースの詳細については、「[データオブジェクトとデータソース (OLE)](../mfc/data-objects-and-data-sources-ole.md)」を参照してください。

ドラッグアンドドロップ操作をカスタマイズするには、次の関数をオーバーライドします。

| オーバーライド | カスタマイズするには |
| -------- | ------------ |
| `OnBeginDrag` | `DoDragDrop`を呼び出した後に、ドラッグ操作を開始する方法。 |
| `GiveFeedback` | さまざまなドロップ結果の視覚的なフィードバック (カーソルの外観など)。 |
| `QueryContinueDrag` | ドラッグアンドドロップ操作の終了。 この関数を使用すると、ドラッグ操作中に修飾子キーの状態を確認できます。 |

## <a name="see-also"></a>参照

[OLE](../mfc/ole-in-mfc.md)\
[OLE データオブジェクトとデータソース](../mfc/data-objects-and-data-sources-ole.md)\
[OLE データオブジェクトとデータソース:\ の作成と破棄](../mfc/data-objects-and-data-sources-creation-and-destruction.md)
[OLE データオブジェクトとデータソース: 操作](../mfc/data-objects-and-data-sources-manipulation.md)\
[COleClientItem::D odragdrop](../mfc/reference/coleclientitem-class.md#dodragdrop)\
[COleDataSource クラス](../mfc/reference/coledatasource-class.md)\
[COleDataSource::D odragdrop](../mfc/reference/coledatasource-class.md#dodragdrop)\
[COleDropSource クラス](../mfc/reference/coledropsource-class.md)\
[COleDropTarget クラス](../mfc/reference/coledroptarget-class.md)\
[CView:: OnDragLeave](../mfc/reference/cview-class.md#ondragleave)
