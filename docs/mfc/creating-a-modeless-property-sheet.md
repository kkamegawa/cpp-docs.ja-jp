---
title: モードレス プロパティ シートの作成
ms.date: 11/04/2016
helpviewer_keywords:
- modeless property sheets
- property sheets, modeless
- Create method [MFC], property sheets
ms.assetid: eafd8a92-cc67-4a69-a5fb-742c920d1ae8
ms.openlocfilehash: 90f6dcd5659d308a4b39d6a7d5a42003fc1f2111
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685693"
---
# <a name="creating-a-modeless-property-sheet"></a>モードレス プロパティ シートの作成

通常、作成するプロパティシートはモーダルになります。 モーダルプロパティシートを使用する場合、ユーザーはアプリケーションの他の部分を使用する前に、プロパティシートを閉じる必要があります。 この記事では、アプリケーションの他の部分を使用しているときに、ユーザーがプロパティシートを開いたままにできるようにするモードレスプロパティシートの作成に使用できるメソッドについて説明します。

モーダルダイアログボックスとしてではなく、モードレスダイアログボックスとしてプロパティシートを表示するには、 [DoModal](../mfc/reference/cpropertysheet-class.md#domodal)ではなく[CPropertySheet:: Create](../mfc/reference/cpropertysheet-class.md#create)を呼び出します。 また、モードレスプロパティシートをサポートするために、いくつかの追加タスクを実装する必要があります。

追加のタスクの1つとして、プロパティシートとプロパティシートが開いているときに変更する外部オブジェクトとの間でデータを交換することがあります。 これは、通常、標準のモードレスダイアログボックスの場合と同じタスクです。 このタスクの一部は、モードレスプロパティシートと、プロパティ設定が適用される外部オブジェクトとの間の通信チャネルを実装することです。 モードレスプロパティシートの[CPropertySheet](../mfc/reference/cpropertysheet-class.md)からクラスを派生させると、この実装ははるかに簡単になります。 この記事では、これを行うことを前提としています。

モードレスプロパティシートと外部オブジェクト (ビューで現在選択されている項目など) との間で通信を行う方法の1つは、プロパティシートから外部オブジェクトへのポインターを定義することです。 `CPropertySheet`派生クラスで関数 (`SetMyExternalObject`など) を定義して、ある外部オブジェクトから別の外部オブジェクトにフォーカスが変更されるたびにポインターを変更します。 `SetMyExternalObject` 関数は、新しく選択された外部オブジェクトを反映するように、各プロパティページの設定をリセットする必要があります。 これを実現するには、`SetMyExternalObject` 関数が、`CPropertySheet` クラスに属する[CPropertyPage](../mfc/reference/cpropertypage-class.md)オブジェクトにアクセスできる必要があります。

プロパティシート内のプロパティページへのアクセスを提供する最も便利な方法は、`CPropertySheet`派生オブジェクトに `CPropertyPage` オブジェクトを埋め込むことです。 埋め込み`CPropertyPage`内のオブジェクト、 `CPropertySheet`-派生オブジェクトはモーダル ダイアログ ボックスで、プロパティ シートの所有者を作成する、一般的なデザインとは異なる、`CPropertyPage`オブジェクトを使用して、プロパティ シートに渡す、 [CPropertySheet::AddPage](../mfc/reference/cpropertysheet-class.md#addpage)です。

モードレスプロパティシートの設定を外部オブジェクトに適用するかどうかを判断するための、多くのユーザーインターフェイスの代替手段が用意されています。 別の方法としては、ユーザーが任意の値を変更したときに、現在のプロパティページの設定を適用する方法があります。 別の方法として、[適用] ボタンを用意する方法もあります。このボタンを使用すると、ユーザーはプロパティページに変更を蓄積してから、外部オブジェクトにコミットすることができます。 [適用] ボタンを処理する方法については、記事を参照してください。[適用ボタンの処理](../mfc/handling-the-apply-button.md)です。

## <a name="see-also"></a>参照

[プロパティシート](../mfc/property-sheets-mfc.md)<br/>
[データの交換](../mfc/exchanging-data.md)<br/>
[MFC でのダイアログボックスの操作](../mfc/life-cycle-of-a-dialog-box.md)
