---
title: ウィンドウ ペイン (アイコン用イメージ エディター)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
helpviewer_keywords:
- graphics editor [C++]
- Image editor [C++], panes
- Image editor [C++], magnification
- grids, pixel
- pixel grid, Image editor
- Image editor [C++], pixel grid
- Image editor [C++], grid settings
- grid settings, Image editor
ms.assetid: d66ea5b3-e2e2-4fc4-aa99-f50022cc690e
ms.openlocfilehash: 72b7cf056147cdbd216d861f0e710da423951c5a
ms.sourcegitcommit: efcc8c97570ddf7631570226c700e8f6ebb6c7be
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2019
ms.locfileid: "55560310"
---
# <a name="window-panes-image-editor-for-icons"></a>ウィンドウ ペイン (アイコン用イメージ エディター)

**イメージ エディター**ウィンドウは通常の分割バーで区切られた 2 つのペインでイメージを表示します。 1 つのビューは、実際のサイズと、他方は拡大 (既定の倍率は 6)。 これら 2 つのペインでビューが自動的に更新されます。 1 つのペインで行った変更は、他のすぐに表示します。 2 つのペインを簡単に、イメージを個々 のピクセルの区別を、同時に確認できます、作業のイメージの実際のサイズのビューへの影響の拡大表示で作業します。

左側のウィンドウの使用が必要な限り多くの領域 (の半分、**イメージ**ウィンドウ)、イメージの 1:1 のビュー (既定値) を表示します。 右側のウィンドウには、拡大した画像 (既定では 6:1 拡大率) が表示されます。 使用して各ペインの表示倍率を変更することができます、**拡大**ツールを[イメージ エディターのツールバー](../windows/toolbar-image-editor-for-icons.md)またはアクセラレータ キーを使用します。

小さいウィンドウを大きくことができます、**イメージ エディター**ウィンドウと、2 つのペインを使用して、大きなイメージのさまざまなリージョンを表示します。 を選択して、ウィンドウ内で選択します。

分割バーにポインターを合わせて、分割バーを右または左に移動して、ペインの相対的なサイズを変更できます。 分割バーは、1 つのペインで作業する場合、いずれかの側に移動できます。

場合、**イメージ エディター**ウィンドウが 4 の倍数で拡大した以上、イメージ内の個々 のピクセルを区切るピクセル グリッドを表示することができます。

マネージ プロジェクトにリソースを追加する方法については、次を参照してください。 [Resources in Desktop Apps](/dotnet/framework/resources/index)で、 *.NET Framework 開発者ガイド*します。 マネージ プロジェクトにリソース ファイルを手動で追加、リソースへのアクセス、静的リソースの表示方法、およびリソース文字列のプロパティを割り当てる方法については、次を参照してください。[デスクトップ アプリのリソース ファイルの作成](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)です。 管理対象アプリ内のリソースのグローバリゼーションとローカリゼーションについては、次を参照してください。 [Globalizing and Localizing .NET Framework Applications](/dotnet/standard/globalization-localization/index)します。

## <a name="to-change-the-magnification-factor"></a>ズームの倍率を変更するには

既定で、**イメージ**エディターでは、実際のサイズでは、左側のウィンドウで、ビューが表示されますおよび 6 では、右側のウィンドウで、ビューが実際のサイズ。 拡大率 (ワークスペースの下部にあるステータス バーに表示) は、イメージの実際のサイズと表示されているサイズの比率です。 既定の係数が 6 と範囲が 1 から 10 には。

1. 選択、**イメージ エディター**ウィンドウ拡大率を変更します。

1. [イメージ エディターのツールバー](../windows/toolbar-image-editor-for-icons.md)の右側にある矢印を選択、 [[拡大] ツール](../windows/toolbar-image-editor-for-icons.md)サブメニューから拡大率を選択します。**1 X**、 **2 X**、 **6 X**、または**8 X**します。

   > [!NOTE]
   > 記載されている以外の拡大率を選択する、**拡大**ツールで、アクセラレータ キーを使用します。

## <a name="to-display-or-hide-the-pixel-grid"></a>ピクセル グリッドの表示と非表示

すべての**イメージ エディター** 4 以上の拡大率と共にウィンドウ、イメージ内の個々 のピクセルを区切るグリッドを表示することができます。

1. **イメージ**メニューの **グリッド設定**します。

1. 選択、**ピクセル グリッド**グリッドを表示またはグリッドを非表示にするボックスをオフにする チェック ボックス。

> [!TIP]
> ツール バー ボタンの上にカーソルを置くとツール ヒントが表示されます。 これらのヒントは、各ボタンの機能を識別するのに役立ちます。

## <a name="requirements"></a>必要条件

なし

## <a name="see-also"></a>関連項目

[アクセラレータ キー](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[アイコン用イメージ エディター](../windows/image-editor-for-icons.md)