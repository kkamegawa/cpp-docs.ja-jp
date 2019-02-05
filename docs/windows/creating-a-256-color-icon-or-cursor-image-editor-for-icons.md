---
title: 256 色カラー パレットの使用 (アイコン用イメージ エディター)
ms.date: 11/04/2016
helpviewer_keywords:
- 256-color palette
- cursors [C++], color
- colors [C++], icons
- colors [C++], cursors
- icons, color
- colors [C++], icons and cursors
- color palettes, 256-color
- palettes, 256-color
ms.assetid: 2738089b-4fd3-4c45-96ae-6a15e4c6b780
ms.openlocfilehash: 4e2f2c9ce58799756137bb47db42e52c97a43d39
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702896"
---
# <a name="using-the-256-color-palette-image-editor-for-icons"></a>256 色カラー パレットの使用 (アイコン用イメージ エディター)

使用して、**イメージ**エディター、アイコンとカーソルは、サイズが設定された大きな (64 × 64) 256 色カラー パレットから選択するとします。 リソースを作成すると、デバイスのイメージのスタイルが選択されます。

マネージ プロジェクトにリソースを追加する方法については、次を参照してください。 [Resources in Desktop Apps](/dotnet/framework/resources/index)で、 *.NET Framework 開発者ガイド*します。 マネージ プロジェクトにリソース ファイルを手動で追加、リソースへのアクセス、静的リソースの表示方法、およびリソース文字列のプロパティを割り当てる方法については、次を参照してください。[デスクトップ アプリのリソース ファイルの作成](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)です。 管理対象アプリ内のリソースのグローバリゼーションとローカリゼーションについては、次を参照してください。 [Globalizing and Localizing .NET Framework Applications](/dotnet/standard/globalization-localization/index)します。

## <a name="to-create-a-256-color-icon-or-cursor"></a>256 色のアイコンまたはカーソルを作成するには

1. [リソース ビュー](../windows/resource-view-window.md)、.rc ファイルを右クリックし**リソースの挿入**ショートカット メニューからです。 (を右クリックしてなど、カーソル、.rc ファイルに既存のイメージ リソースが既にある場合、**カーソル**フォルダーと選択**挿入カーソル**ショートカット メニューから)。

   > [!NOTE]
   > プロジェクトに .rc ファイルがまだ含まれていない場合は、「 [リソース スクリプト ファイルの新規作成](../windows/how-to-create-a-resource-script-file.md)」を参照してください。

1. [リソースの挿入 ダイアログ ボックス](../windows/add-resource-dialog-box.md)を選択します**アイコン**または**カーソル**選択**新規**します。

1. **イメージ**メニューの **新しいデバイス イメージ**します。

1. 256 色の画像のスタイルを選択します。

## <a name="to-choose-a-color-from-the-256-color-palette-for-large-icons"></a>大きいアイコンの 256 色カラー パレットから色を選択するには

256 色カラー パレットから選択した場合、描画するから色を選択する必要があります、**色**パレットで、 [[色] ウィンドウ](../windows/colors-window-image-editor-for-icons.md)します。

1. 大きいアイコンまたはカーソルを選択するか、新しいの大きいアイコンまたはカーソルを作成します。

1. 色で表示される 256 色から選択、**色**パレットで、**色**ウィンドウ。

   選択した色に現在の色になります、**色**パレットで、**色**ウィンドウ。

   > [!NOTE]
   > 256 色の画像に使用する初期のパレットがによって返されるパレットと一致する、 `CreateHalftonePalette` Windows API。 Windows シェルは、すべてのアイコンは、パレットの実現化中のちらつきを防ぐためにこのパレットを使用する必要があります。

## <a name="requirements"></a>必要条件

なし

## <a name="see-also"></a>関連項目

[アクセラレータ キー](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[アイコンとカーソル:ディスプレイ デバイスのイメージ リソース](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)
