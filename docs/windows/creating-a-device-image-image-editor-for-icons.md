---
title: デバイス イメージの作成 (アイコン用イメージ エディター)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.icon
- vc.editors.newimagetype
- vc.editors.customimage
- vc.editors.opendeviceimage
helpviewer_keywords:
- cursors [C++], creating
- icons [C++], creating
- display devices [C++], creating image
- images [C++], creating for display devices
- icons [C++], inserting
- New <Device> Image Type dialog box [C++]
- Custom Image dialog box [C++]
- Open <Device> Image dialog box [C++]
ms.assetid: 5a536928-32df-4ace-beb1-1521ce3b871f
ms.openlocfilehash: ce1069f6f410d7a60d631461086ca8870ef679c0
ms.sourcegitcommit: efcc8c97570ddf7631570226c700e8f6ebb6c7be
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2019
ms.locfileid: "55560297"
---
# <a name="creating-a-device-image-image-editor-for-icons"></a>デバイス イメージの作成 (アイコン用イメージ エディター)

新しいアイコンやカーソルのリソースを作成するときに、**イメージ**エディターが特定のスタイル (32 × 32 の 16 色のアイコンと 32 × 32、カーソルのモノクロ) で最初にイメージを作成します。 初期のアイコンやカーソルをさまざまなサイズとスタイルのイメージを追加し、必要に応じて、別のディスプレイ デバイスの各追加のイメージを編集できます。 既存のイメージの種類やグラフィックス プログラムで作成したビットマップからカット アンド ペースト操作を使用してイメージを編集することもできます。

アイコンまたはカーソルのリソースを開くと、[イメージ エディター](../windows/image-editor-for-icons.md)、密接に現在のディスプレイ デバイスを照合ほとんどが既定で表示するイメージ。

マネージ プロジェクトにリソースを追加する方法については、次を参照してください。 [Resources in Desktop Apps](/dotnet/framework/resources/index)で、 *.NET Framework 開発者ガイド*します。 マネージ プロジェクトにリソース ファイルを手動で追加、リソースへのアクセス、静的リソースの表示方法、およびリソース文字列のプロパティを割り当てる方法については、次を参照してください。[デスクトップ アプリのリソース ファイルの作成](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)です。 管理対象アプリ内のリソースのグローバリゼーションとローカリゼーションについては、次を参照してください。 [Globalizing and Localizing .NET Framework Applications](/dotnet/standard/globalization-localization/index)します。

## <a name="new-ltdevicegt-image-type-dialog-box"></a>新しい&lt;デバイス&gt;イメージの種類 ダイアログ ボックス

**新規&lt;デバイス&gt;イメージの種類** ダイアログ ボックスでは、指定した型の新しいデバイス イメージを作成することができます。 開くには、**新規\<デバイス > イメージ**ダイアログ ボックスで、**イメージ タイプの新規**上、**イメージ**メニュー。 次のプロパティが含まれている**ターゲット イメージ タイプ**と**カスタム**します。

### <a name="target-image-type"></a>ターゲット イメージ タイプ

使用可能なイメージの種類を一覧表示します。 開きたい画像の種類を選択します。

||||
|-|-|-|
|の 16 x 16 16 色|-48 48 x 16 色|-96 x 96 16 色|
|-16 x 16、256 色|-48 x 48 256 色|-96 x 96 256 色|
|-16 x 16、モノクロ|-48、モノクロ x 48|-96、モノクロ x 96|
|-32 x 32 の 16 色|x64 では、64 16 色||
|-32 x 32、256 色|x64 では、64 256 色||
|-32 x 32、モノクロ|x 64、モノクロ 64||

> [!NOTE]
> 既存のイメージは、この一覧に表示されません。

### <a name="custom"></a>カスタム

開く、**カスタム イメージ**ダイアログ ボックスでカスタムのサイズと色の数を新しいイメージを作成できます。

**カスタム イメージ** ダイアログ ボックスでは、カスタムのサイズと色の数で新しいイメージを作成することができます。 次のプロパティは次のとおりです。

|プロパティ|説明|
|---|---|
|**Width**|カスタム イメージの幅をピクセル (1 ~ 512 の制限を 2048) で入力する場所を提供します。|
|**Height**|ピクセル (1 ~ 512 の制限を 2048) でカスタム イメージの高さを入力する場所を提供します。|
|**色**|カスタム イメージの色の数を選択する場所を提供します。2、16、または 256 です。|

## <a name="open-ltdevicegt-image-dialog-box"></a>開いている&lt;デバイス&gt;イメージ ダイアログ ボックス

使用して、**開く&lt;デバイス&gt;イメージ**を C++ プロジェクトでデバイスのイメージを開く ダイアログ ボックス。 現在のリソース (現在のリソースの一部であるイメージ) の既存のデバイスのイメージが一覧表示します。 次のプロパティは次のとおりです。

|プロパティ|説明|
|---|---|
|**現在のイメージ**|リソースに含まれるイメージを一覧表示します。 開きたい画像の種類を選択します。|

## <a name="to-create-a-new-icon-or-cursor"></a>新しいアイコンやカーソルを作成するには

1. [リソース ビュー](../windows/resource-view-window.md)、.rc ファイルを右クリックし**リソースの挿入**ショートカット メニューからです。 (を右クリックしてなど、カーソル、.rc ファイルに既存のイメージ リソースが既にある場合、**カーソル**フォルダーと選択**挿入カーソル**ショートカット メニューから)。

   > [!NOTE]
   > プロジェクトに .rc ファイルがまだ含まれていない場合は、「 [リソース スクリプト ファイルの新規作成](../windows/how-to-create-a-resource-script-file.md)」を参照してください。

1. [リソースの挿入 ダイアログ ボックス](../windows/add-resource-dialog-box.md)を選択します**アイコン**または**カーソル**選択**新規**します。 アイコンには、この操作は、32 × 32、16 色のアイコンのアイコン リソースを作成します。 カーソルの場合は 32 × 32、モノクロの (2 色) イメージが作成されます。

   プラス記号の場合 (**+**) でイメージ リソースの種類の横に表示、**リソースの挿入**ダイアログ ボックスで、ツールバーのテンプレートがあることを意味します。 テンプレートの一覧を展開し、テンプレートを選択して、選択、プラス記号を選択します。**新規**します。

## <a name="requirements"></a>必要条件

なし

## <a name="see-also"></a>関連項目

[アイコンとカーソル:ディスプレイ デバイスのイメージ リソース](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)<br/>
[アクセラレータ キー](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[アイコンとカーソル:ディスプレイ デバイスのイメージ リソース](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)<br/>
[[イメージ] メニュー](../windows/image-menu-image-editor-for-icons.md)<br/>
[アイコン用イメージ エディター](../windows/image-editor-for-icons.md)<br/>
