---
title: 外観、ATL コントロール ウィザード
ms.date: 08/31/2018
f1_keywords:
- vc.codewiz.class.atl.control.misc
helpviewer_keywords:
- ATL Control Wizard, appearance
ms.assetid: cc16d7ff-74d7-4c15-9ebd-4b19201ff457
ms.openlocfilehash: e07dc017241848f1a670c17b12c2254de6d1b8e1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492184"
---
# <a name="appearance-atl-control-wizard"></a>外観、ATL コントロール ウィザード

ウィザードのこのページを使用して、コントロールの追加のユーザー要素オプションを識別します。 このページとして識別されるコントロールの使用可能な**標準コントロール** **コントロール型** 上、[オプション、ATL コントロール ウィザード](../../atl/reference/options-atl-control-wizard.md)ページ。

## <a name="uielement-list"></a>UIElement の一覧

- **状態の表示**

   コンテナー内のコントロールの外観を設定します。

   - 非**透過**:[Viewstatus](/windows/win32/api/ocidl/ne-ocidl-viewstatus)列挙体の VIEWSTATUS_OPAQUE ビットを設定し、 [CComControlBase:: OnDraw](../../atl/reference/ccomcontrolbase-class.md#ondraw)メソッドに渡されるコントロールの四角形全体を描画します。 コントロールは完全に不透明で表示され、コンテナーは制御境界の背後に表示されません。

      この設定により、コンテナーはコントロールをよりすばやく描画できます。 このオプションが選択されていない場合、コントロールに透明部分を含めることができます。

      不透明なコントロールのみが、背景を塗りつぶすことができます。

   - **単色の背景**:VIEWSTATUS 列挙体の VIEWSTATUS_SOLIDBKGND ビットを設定します。 コントロールの背景は、パターンのない純色として表示されます。

      このオプションは、 **[不透明]** オプションも選択されている場合にのみ使用できます。

- **に基づいたコントロールの追加**

   コントロールを実装するクラスに[CContainedWindow](ccontainedwindowt-class.md)データメンバーを追加することによって、コントロールを Windows コントロール型に基づいて設定します。 また、メッセージマップとメッセージハンドラー関数を追加して、コントロールの Windows メッセージを処理します。 作成する Windows コントロールの種類を一覧から選択します (存在する場合)。

   - **Button**

   - **ListBox**

   - **SysAnimate32**

   - **SysListView32**

   - **ComboBox**

   - **RichEdit**

   - **SysDateTimePick32**

   - **SysMonthCal32**

   - **ComboBoxEx32**

   - **ScrollBar**

   - **SysHeader32**

   - **SysTabControl32**

   - **編集**

   - **Static**

   - **SysIPAddress32**

   - **SysTreeView32**

- **その他の状態**

   コントロールの外観と動作に関する追加のオプションを設定します。

   - **実行時に非**表示:実行時に非表示になるようにコントロールを設定します。 非表示のコントロールを使用して、一定の間隔でイベントを発生させるなど、バックグラウンドで操作を実行できます。

   - 次の**ように動作**します。[OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc)列挙体の OLEMISC_ACTSLIKEBUTTON ビットを設定して、コントロールがボタンのように動作できるようにします。 コンテナーがコントロールのクライアントサイトを既定のボタンとしてマークしている場合、このオプションをオンにすると、ボタンコントロールは、周囲のフレームで描画することによって、ボタンコントロール自体を既定のボタンとして表示できます。 詳細については、「 [CComControlBase:: GetAmbientDisplayAsDefault](../../atl/reference/ccomcontrolbase-class.md#getambientdisplayasdefault) 」を参照してください。

   - **ラベルのように機能**します。OLEMISC 列挙体の OLEMISC_ACTSLIKELABEL ビットを設定して、コントロールがコンテナーのネイティブラベルを置き換えることができるようにします。 コンテナーは、このフラグを使用して何を行うかを決定します (存在する場合)。

- **その他**

   コントロールの追加の動作オプションを設定します。

   - **正規化**された DC:コントロールが、それ自体を描画するために呼び出されたときに、正規化されたデバイスコンテキストを作成するように設定します。 この操作により、コントロールの外観は標準化されますが、描画効率が低下します。

   - **ウィンドウのみ**:コントロールをウィンドウなしにすることを指定します。 このオプションを選択しない場合、コントロールはウィンドウなしのオブジェクトをサポートするコンテナーで自動的にウィンドウウィンドウに表示され、ウィンドウなしのオブジェクトをサポートしていないコンテナーで自動的にウィンドウに表示されます。 このオプションを選択すると、ウィンドウなしのオブジェクトをサポートするコンテナーであっても、コントロールは強制的にウィンドウに配置されます。

   - **挿入**可能:このオプションを選択すると、Word や Excel などのアプリケーションの **[オブジェクトの挿入]** ダイアログボックスにコントロールが表示されます。 このダイアログボックスを使用して、埋め込みオブジェクトをサポートする任意のアプリケーションでコントロールを挿入できます。

## <a name="see-also"></a>関連項目

[ATL コントロール ウィザード](../../atl/reference/atl-control-wizard.md)<br/>
[SUBEDIT サンプル:標準の Windows コントロールをスーパークラスにする](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit)
