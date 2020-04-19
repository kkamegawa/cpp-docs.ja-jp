---
title: クリップボード:コピーと貼り付けデータ
ms.date: 11/04/2016
helpviewer_keywords:
- Clipboard, copying data to
- Clipboard, pasting
ms.assetid: 580e10be-241f-4f9f-94cf-8302edc5beef
ms.openlocfilehash: cff9094315dc97e2040eb4dbad25d044c7c51a81
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62327146"
---
# <a name="clipboard-copying-and-pasting-data"></a>クリップボード:コピーと貼り付けデータ

このトピックにコピーし、OLE アプリケーションでクリップボードから貼り付けを実装するために必要な最低限の作業について説明します。 確認することをお勧め、[データ オブジェクトとデータ ソース (OLE)](../mfc/data-objects-and-data-sources-ole.md)トピックを続行する前にします。

コピーまたは貼り付けを実装することができます、前に、[編集] メニュー、コピー、切り取り、および貼り付けのオプションを処理する関数を指定してください。

##  <a name="_core_copying_or_cutting_data"></a> コピーまたは切り取りデータ

#### <a name="to-copy-data-to-the-clipboard"></a>データをクリップボードにコピーするには

1. データをコピーする、ネイティブ データまたは埋め込みまたはリンクされた項目かどうかを決定します。

   - データが埋め込まれたかリンクされている場合へのポインターを取得、`COleClientItem`が選択されているオブジェクト。

   - 作成から派生した新しいオブジェクトの場合は、データがネイティブ アプリケーションが、サーバー、`COleServerItem`選択したデータを格納しています。 それ以外の場合、作成、`COleDataSource`データ オブジェクト。

1. 選択した項目を呼び出す`CopyToClipboard`メンバー関数。

1. 場合は、ユーザーがコピー操作ではなく切り取り操作を選択してアプリケーションから、選択したデータを削除します。

このシーケンスの例を参照してください、`OnEditCut`と`OnEditCopy`関数で、MFC OLE サンプル プログラム[OCLIENT](../overview/visual-cpp-samples.md)と[HIERSVR](../overview/visual-cpp-samples.md)します。 手順 1 は既に完了しているために、これらのサンプルが、現在選択されているデータへのポインターを保持することに注意してください。

##  <a name="_core_pasting_data"></a> データの貼り付け

データの貼り付けは、アプリケーションに、データの貼り付けで使用する形式を選択する必要があるため、コピーするより複雑です。

#### <a name="to-paste-data-from-the-clipboard"></a>クリップボードからデータを貼り付ける

1. ビュー クラスで実装`OnEditPaste`の編集 メニューから、貼り付け オプションを選択するユーザーを処理します。

1. `OnEditPaste`関数を作成、`COleDataObject`オブジェクトと呼び出しの`AttachClipboard`クリップボードのデータにこのオブジェクトをリンクするメンバー関数。

1. 呼び出す`COleDataObject::IsDataAvailable`を特定の形式が使用できるかどうかを確認します。

   また、使用することができます`COleDataObject::BeginEnumFormats`アプリケーションに最適なものが見つかるまでその他の形式を検索します。

1. 形式の貼り付けを実行します。

この動作の例では、実装を参照してください、 `OnEditPaste` MFC OLE サンプル プログラムで定義されているビュー クラスのメンバー関数[OCLIENT](../overview/visual-cpp-samples.md)と[HIERSVR](../overview/visual-cpp-samples.md)します。

> [!TIP]
>  貼り付け操作を独自の関数を分離することの主な利点は、ドラッグ アンド ドロップ操作中に、アプリケーションでデータが削除されるときに、同じコードで貼り付けを使用できることです。 OCLIENT および HIERSVR のように、`OnDrop`関数を呼び出すことも`DoPasteItem`、貼り付けの操作を実装するために記述されたコードを再利用します。

[編集] メニューの貼り付け コマンドを処理するには、トピックを参照してください。 [OLE のダイアログ ボックス](../mfc/dialog-boxes-in-ole.md)です。

### <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [その他のデータ形式の追加](../mfc/clipboard-adding-other-formats.md)

- [OLE データ オブジェクトとデータ ソースと統一されたデータの転送します。](../mfc/data-objects-and-data-sources-ole.md)

- [OLE ドラッグ アンド ドロップ](../mfc/drag-and-drop-ole.md)

- [OLE](../mfc/ole-background.md)

## <a name="see-also"></a>関連項目

[クリップボード: OLE クリップボード機構の使用方法](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)
