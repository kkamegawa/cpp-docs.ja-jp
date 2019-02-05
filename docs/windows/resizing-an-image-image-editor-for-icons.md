---
title: イメージのサイズ変更 (アイコン用イメージ エディター)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.image.editing
helpviewer_keywords:
- Image editor [C++], resizing images
- graphics [C++], resizing
- images [C++], resizing
- resizing images
- size [C++], images
- images [C++], cropping
- images [C++], extending
- Image editor [C++], cropping or extending images
- Image editor [C++], shrinking and stretching images
- images [C++], stretching
- images [C++], shrinking
- bitmaps [C++], shrinking
- bitmaps [C++], stretching
ms.assetid: d83a02c4-4dfe-4586-a0df-51a50c2ba71d
ms.openlocfilehash: d88a4cccff5b9b7b6303329782b7367cb953b13d
ms.sourcegitcommit: 5270117dbecc4c49bca0cf10b927bae3c9930038
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484969"
---
# <a name="resizing-an-image-image-editor-for-icons"></a>イメージのサイズ変更 (アイコン用イメージ エディター)

動作、**イメージ**イメージのサイズ変更中にエディターがしたかどうかに依存[選択](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)イメージ全体または一部だけです。

選択範囲には、イメージの一部のみが含まれている場合、**イメージ**エディターが現在の背景色で領域をピクセル単位の行または列を削除して選択範囲を縮小します。 ピクセルの行または列を複製することにより、選択範囲に拡大または縮小できますも。

選択範囲には、全体のイメージが含まれている場合、**イメージ**エディターか、圧縮、イメージを拡大またはトリミングおよび拡張されています。

イメージのサイズ変更の 2 つのメカニズムがある: サイズ変更ハンドルと[プロパティ ウィンドウ](/visualstudio/ide/reference/properties-window)します。 イメージの一部またはすべてのサイズを変更するサイズ変更ハンドルをドラッグするとします。 サイズ変更ハンドルをドラッグすることは、solid です。 白抜きのハンドルをドラッグすることはできません。 使用して、**プロパティ**全体のサイズを変更するにはウィンドウのイメージのみ、選択したパーツではありません。

![サイズ変更ハンドルをビットマップに](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")<br/>
サイズ変更ハンドル

> [!NOTE]
> ある場合、**タイル グリッド**で選択したオプション、[グリッドの設定 ダイアログ ボックス](../windows/grid-settings-dialog-box-image-editor-for-icons.md)、[次へ] のタイル グリッド線にスナップのサイズを変更します。 だけの場合、**ピクセル グリッド**オプションは、(既定の設定) を選択するには、次のピクセルにスナップのサイズを変更します。

マネージ プロジェクトにリソースを追加する方法については、次を参照してください。 [Resources in Desktop Apps](/dotnet/framework/resources/index)で、 *.NET Framework 開発者ガイド*します。 マネージ プロジェクトにリソース ファイルを手動で追加、リソースへのアクセス、静的リソースの表示方法、およびリソース文字列のプロパティを割り当てる方法については、次を参照してください。[デスクトップ アプリのリソース ファイルの作成](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)です。 管理対象アプリ内のリソースのグローバリゼーションとローカリゼーションについては、次を参照してください。 [Globalizing and Localizing .NET Framework Applications](/dotnet/standard/globalization-localization/index)します。

## <a name="to-resize-an-entire-image-using-the-properties-window"></a>[プロパティ] ウィンドウを使用してイメージ全体のサイズを変更するには

1. イメージを変更するプロパティを開きます。

1. **幅**と**高さ**ボックス、[プロパティ ウィンドウ](/visualstudio/ide/reference/properties-window)、目的のサイズを入力します。

   イメージのサイズを増加している場合、**イメージ**エディターは、イメージ、下、右またはその両方を拡張し、新しいリージョンを現在の背景色で塗りつぶします。 イメージが伸縮されていません。

   イメージのサイズを短縮する場合、**イメージ**エディター右端または下端またはその両方でイメージをトリミングします。

   > [!NOTE]
   > 使用することができます、**幅**と**高さ**部分的な選択範囲のサイズを変更しないように、のみ全体イメージのサイズを変更するプロパティ。

## <a name="to-crop-or-extend-an-entire-image"></a>トリミングまたはイメージ全体の拡張

1. イメージ全体を選択します。

   イメージの一部が現在選択されているイメージ全体を選択する場合は、任意の場所、現在の選択範囲の境界線の外側にあるイメージを選択します。

1. イメージが適切なサイズまでは、サイズ変更ハンドルをドラッグします。

通常、**イメージ**トリミングまたはサイズ変更ハンドルを移動してサイズを変更するときに、イメージを拡張します。 押しながら場合、 **Shift**キーのサイズ変更ハンドルを移動すると、**イメージ**エディターの縮小または拡大イメージ。

## <a name="to-shrink-or-stretch-an-entire-image"></a>イメージ全体を拡大または縮小するには

1. イメージ全体を選択します。

   イメージの一部が現在選択されているイメージ全体を選択する場合は、任意の場所、現在の選択範囲の境界線の外側にあるイメージを選択します。

1. 押しながら、 **Shift**キーし、イメージが適切なサイズになるまで、サイズ変更ハンドルをドラッグします。

## <a name="to-shrink-or-stretch-part-of-an-image"></a>イメージの一部を拡大または縮小するには

1. サイズを変更するイメージの一部を選択します。 詳細については、次を参照してください。[領域のイメージの選択](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)します。

1. 選択範囲が適切なサイズになるまでは、サイズ変更ハンドルのいずれかをドラッグします。

## <a name="requirements"></a>必要条件

なし

## <a name="see-also"></a>関連項目

[アクセラレータ キー](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[グラフィカル リソースの編集](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[アイコン用イメージ エディター](../windows/image-editor-for-icons.md)