---
title: 'コンテナー : コンテナーの実装'
ms.date: 11/04/2016
helpviewer_keywords:
- applications [OLE], OLE container
- OLE containers [MFC], implementing
ms.assetid: af1e2079-619a-4eac-9327-985ad875823a
ms.openlocfilehash: ed95324b8df978a6ab2f7582c0ddf626a45e7fe1
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127921"
---
# <a name="containers-implementing-a-container"></a>コンテナー : コンテナーの実装

この記事では、コンテナーを実装する手順の概要を説明し、コンテナーの実装に関する詳細な説明が記載されている他の記事を紹介します。 また、実装するオプションの OLE 機能と、これらの機能について説明している記事も示しています。

#### <a name="to-prepare-your-cwinapp-derived-class"></a>CWinApp 派生クラスを準備するには

1. `InitInstance` メンバー関数で `AfxOleInit` を呼び出して、OLE ライブラリを初期化します。

1. `InitInstance` で `CDocTemplate::SetContainerInfo` を呼び出して、埋め込み項目がインプレースでアクティブになったときに使用されるメニューおよびアクセラレータリソースを割り当てます。 このトピックの詳細については、「 [Activation](../mfc/activation-cpp.md)」を参照してください。

これらの機能は、MFC アプリケーションウィザードを使用してコンテナーアプリケーションを作成するときに、自動的に提供されます。 「 [MFC EXE プログラムの作成」を](../mfc/reference/mfc-application-wizard.md)参照してください。

#### <a name="to-prepare-your-view-class"></a>ビュークラスを準備するには

1. 選択された項目を、ポインター、または複数選択をサポートしている場合はポインターのリストを保持して、選択した項目を追跡します。 `OnDraw` 関数は、すべての OLE 項目を描画する必要があります。

1. `IsSelected` をオーバーライドして、渡された項目が現在選択されているかどうかを確認します。

1. **[オブジェクトの挿入]** ダイアログボックスを表示するための `OnInsertObject` メッセージハンドラーを実装します。

1. `OnSetFocus` メッセージハンドラーを実装して、ビューからインプレースアクティブ OLE 埋め込みアイテムにフォーカスを転送します。

1. 四角形を変更する必要があることを OLE 埋め込み項目に通知する `OnSize` メッセージハンドラーを実装します。これにより、含まれるビューのサイズの変更が反映されます。

これらの機能の実装はアプリケーションによって大きく異なるため、アプリケーションウィザードには基本的な実装のみが用意されています。 アプリケーションを正しく機能させるには、これらの関数をカスタマイズする必要があります。 この例については、[コンテナー](../overview/visual-cpp-samples.md)のサンプルを参照してください。

#### <a name="to-handle-embedded-and-linked-items"></a>埋め込み項目とリンクされた項目を処理するには

1. [COleClientItem](../mfc/reference/coleclientitem-class.md)からクラスを派生させます。 このクラスのオブジェクトは、OLE ドキュメントに埋め込まれている、またはリンクされている項目を表します。

1. `OnChange`、`OnChangeItemPosition`、および `OnGetItemPosition`をオーバーライドします。 これらの関数は、埋め込みおよびリンクされた項目のサイズ変更、配置、および変更を処理します。

クラスはアプリケーションウィザードによって派生されますが、前述の手順 2. で一覧表示された `OnChange` とその他の関数をオーバーライドする必要が生じる可能性があります。 スケルトン実装は、アプリケーションごとに異なる方法で実装されるため、ほとんどのアプリケーションに合わせてカスタマイズする必要があります。 この例については、MFC のサンプル[DRAWCLI](../overview/visual-cpp-samples.md)と[コンテナー](../overview/visual-cpp-samples.md)を参照してください。

OLE をサポートするには、コンテナーアプリケーションのメニュー構造に複数の項目を追加する必要があります。 これらの詳細については、「[メニューとリソース: コンテナーの追加](../mfc/menus-and-resources-container-additions.md)」を参照してください。

コンテナーアプリケーションで、次の機能の一部をサポートすることもできます。

- 埋め込み項目を編集するときのインプレースアクティブ化。

   詳細については、「 [Activation](../mfc/activation-cpp.md)」を参照してください。

- サーバーアプリケーションから選択項目をドラッグアンドドロップして、OLE 項目を作成します。

   詳細については、「 [OLE ドラッグアンドドロップ](../mfc/drag-and-drop-ole.md)」を参照してください。

- 埋め込みオブジェクトまたは組み合わせたコンテナー/サーバーアプリケーションへのリンク。

   詳細については、「[コンテナー: 高度な機能](../mfc/containers-advanced-features.md)」を参照してください。

## <a name="see-also"></a>参照

[Containers](../mfc/containers.md)<br/>
[コンテナー: クライアント アイテム](../mfc/containers-client-items.md)
