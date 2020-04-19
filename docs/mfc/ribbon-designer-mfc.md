---
title: リボン デザイナー (MFC)
ms.date: 11/19/2018
f1_keywords:
- vc.editors.ribbon.F1
helpviewer_keywords:
- Ribbon Designer (MFC)
- MFC Ribbon Designer
ms.assetid: 0806dfd6-7d11-471a-99e1-4072852231f9
ms.openlocfilehash: a39a3a69b43eb06d67fc806e2d4fa9aec323b650
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2019
ms.locfileid: "70907816"
---
# <a name="ribbon-designer-mfc"></a>リボン デザイナー (MFC)

リボン デザイナーを使用すると、MFC アプリケーションでリボンを作成してカスタマイズできます。 リボンは、複数のコマンドを 1 つの論理グループにまとめたユーザー インターフェイス (UI) 要素です。 これらのグループは、ウィンドウの上部に水平に並んで表示されるタブに別々に表示されます。 リボンは、メニュー バーとツール バーの代わりに表示されます。 リボンは、アプリケーションの使用性を大幅に向上させます。 詳細については、「[リボン](/windows/win32/uxguide/cmd-ribbons)」を参照してください。 リボンを次の図に示します。

![MFC リボンリソースコントロール](../mfc/media/ribbon_no_callouts.png "MFC リボンリソースコントロール")

以前のバージョンの Visual Studio では、 [CMFCRibbonBar クラス](../mfc/reference/cmfcribbonbar-class.md)などの MFC リボンクラスを使用するコードを記述することによって、リボンを作成する必要がありました。 Visual Studio 2010 以降では、リボンデザイナーには、リボンを作成するための別の方法が用意されています。 最初に、リボンをリソースとして作成およびカスタマイズします。 次に、リボン リソースを MFC アプリケーションのコードから読み込みます。 リボン リソースと MFC リボン クラスを同時に使用することもできます。 たとえば、リボンリソースを作成し、コードを使用して、実行時にプログラムによって要素を追加することができます。

## <a name="understanding-the-ribbon-designer"></a>リボン デザイナーについて

リボン デザイナーは、リボンをリソースとして作成および保存します。 リボン リソースを作成すると、リボン デザイナーによって次の 3 つの操作が行われます。

- プロジェクト リソース定義スクリプト (*.rc) にエントリを追加する。 次の例では、IDR_RIBBON は、リボンリソースを識別する一意の名前、RT_RIBBON_XML はリソースの種類、.mfcribbon-ms はリソースファイルの名前です。

```
    IDR_RIBBON RT_RIBBON_XML      "res\\ribbon.mfcribbon-ms"
```

- コマンド ID の定義を resource.h に追加する。

```
#define IDR_RIBBON            307
```

- リボンのボタン、コントロール、および属性を定義する XML コードを含むリボン リソース ファイル (*.mfcribbon-ms) を作成する。 リボン デザイナーで行ったリボンの変更は、リソース ファイルに XML として保存されます。 次のコード例は、.mfcribbon-ms ファイルの\*内容の一部を示しています。

```
<RIBBON_BAR>
<ELEMENT_NAME>RibbonBar</ELEMENT_NAME>
<IMAGE>
<ID>
<NAME>IDB_BUTTONS</NAME>
<VALUE>113</VALUE>
</ID>
```

MFC アプリケーションでリボンリソースを使用するには、 [CMFCRibbonBar:: LoadFromResource](../mfc/reference/cmfcribbonbar-class.md#loadfromresource)を呼び出してリソースを読み込みます。

## <a name="creating-a-ribbon-by-using-the-ribbon-designer"></a>リボン デザイナーを使用したリボンの作成

リボン リソースを MFC プロジェクトに追加する方法は 2 つあります。

- MFC アプリケーションを作成し、リボンを作成するように MFC プロジェクト ウィザードを構成する。 詳細については、「[チュートリアル:MFC](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md)を使用してリボンアプリケーションを作成する。

- 既存の MFC プロジェクトにリボン リソースを作成し、それを読み込む。 詳細については、「[チュートリアル:MFC Scribble アプリケーションの更新 (パート 1)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)。

プロジェクトに手動でコード化されたリボンが既に存在する場合でも、MFC には既存のリボンをリボン リソースに変換するために使用できる機能が用意されています。 詳細については、「[方法 :既存の MFC リボンをリボンリソース](../mfc/how-to-convert-an-existing-mfc-ribbon-to-a-ribbon-resource.md)に変換します。

> [!NOTE]
>  リボンはダイアログ ベースのアプリケーションには作成できません。 詳細については、「 [[アプリケーションの種類] (MFC アプリケーションウィザード)](../mfc/reference/application-type-mfc-application-wizard.md)」を参照してください。

## <a name="customizing-ribbons"></a>リボンのカスタマイズ

リボン デザイナーでリボンを開くには、リソース ビューでリボン リソースをダブルクリックします。 デザイナーでは、リボン、アプリケーション ボタン、またはクイック アクセス ツール バーに対する要素の追加、削除、およびカスタマイズを実行できます。 さらに、イベント (ボタン クリック イベントやメニュー イベントなど) をアプリケーション内のメソッドにリンクできます。

リボン デザイナーのさまざまなコンポーネントを次の図に示します。

![MFC リボンデザイナー](../mfc/media/ribbon_designer.png "MFC リボンデザイナー")

- **リソース**デザイナー画面にドラッグできるコントロールを格納します。

- **デザイナー画面:** リボンリソースの視覚的な表現を格納します。

- **[クラスウィザード](reference/mfc-class-wizard.md):** デザイナー画面で選択されている項目の属性を一覧表示します。

- **リソースビューウィンドウ:** プロジェクトのリボンリソースを含むリソースが表示されます。

- **リボンエディターツールバー:** リボンをプレビューし、そのビジュアルテーマを変更するためのコマンドが含まれています。

次のトピックでは、リボン デザイナーの機能の使用方法について説明します。

- [方法: アプリケーション ボタンをカスタマイズする](../mfc/how-to-customize-the-application-button.md)

- [方法: クイック アクセス ツール バーをカスタマイズする](../mfc/how-to-customize-the-quick-access-toolbar.md)

- [方法: リボン コントロールとイベント ハンドラーを追加する](../mfc/how-to-add-ribbon-controls-and-event-handlers.md)

- [方法: MFC アプリケーションからリボン リソースを読み込む](../mfc/how-to-load-a-ribbon-resource-from-an-mfc-application.md)

## <a name="definitions-of-ribbon-elements"></a>リボン要素の定義

![MFC リボン](../mfc/media/ribbon.png "MFC リボン")

- **アプリケーションボタン:** リボンの左上隅に表示されるボタン。 アプリケーション ボタンは [ファイル] メニューの代わりに表示され、リボンが最小化されている場合でも表示されます。 このボタンをクリックすると、コマンド リストを含むメニューが表示されます。

- **クイックアクセスツールバー:** 使用頻度の高いコマンドを表示する、カスタマイズ可能な小さなツールバー。

- **カテゴリ**:リボンタブの内容を表す論理グループ。

- **カテゴリの既定のボタン:** リボンが最小化されたときにリボンに表示されるボタン。 このボタンをクリックすると、カテゴリがメニューとして再表示されます。

- **パネル**関連するコントロールのグループを表示するリボンバーの領域。 すべてのリボン カテゴリには、1 つ以上のリボン パネルが含まれます。

- **リボン要素:** ボタンやコンボボックスなど、パネル内のコントロール。 リボンでホストできるさまざまなコントロールについては、「 [RibbonGadgets Sample:リボンガジェットアプリケーション](../overview/visual-cpp-samples.md)。

## <a name="see-also"></a>関連項目

[ユーザーインターフェイス要素](../mfc/user-interface-elements-mfc.md)<br/>
[リソース ファイルの操作](../windows/working-with-resource-files.md)
