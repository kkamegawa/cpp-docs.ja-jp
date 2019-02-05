---
title: さまざまなカラー パレットの保存と読み込み (アイコン用イメージ エディター)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.image.color
- vc.editors.loadcolorpalette
helpviewer_keywords:
- color palettes [C++]
- palettes
- palettes, Image editor
- colors [C++], Image editor
- Image editor [C++], palettes
- color palettes
- Load Palette Colors dialog box [C++]
ms.assetid: 694b6346-e606-4f19-aa01-9b4ceb47f423
ms.openlocfilehash: fd2664407d33d8e3ed594921501b7f80e6c8850b
ms.sourcegitcommit: efcc8c97570ddf7631570226c700e8f6ebb6c7be
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2019
ms.locfileid: "55560271"
---
# <a name="saving-and-loading-different-color-palettes-image-editor-for-icons"></a>さまざまなカラー パレットの保存と読み込み (アイコン用イメージ エディター)

保存して読み込む、**色**が含まれるパレット[色をカスタマイズ](../windows/customizing-or-changing-colors-image-editor-for-icons.md)します。 (既定で、**色**Visual Studio を起動すると、最も最近使用したパレットが自動的に読み込まれます)。

> [!TIP]
> 以降、**イメージ**エディターは既定値を復元する手段を持たない**色**パレットで、既定値を保存する必要があります**色**パレットなどの名前で *"standard.pal"* または *"default.pal"* 既定の設定を簡単に復元できるようにします。

使用して、**読み込むパレットの色**C++ プロジェクトで使用する特殊なカラー パレットの読み込み ダイアログ ボックス。 次のプロパティは次のとおりです。

|プロパティ|説明|
|---|---|
|**ファイルの場所します。**|ファイルまたはフォルダーを検索する場所を指定します。 別の場所を選択するには、矢印を選択するか、レベルに移動 ツールバーでフォルダー アイコンを選択します。|
|**ファイル名**|開くファイルの名前を入力する場所を提供します。 以前開いたファイルをすばやく検索するには、使用可能な場合に、ボックスの一覧でファイル名を選択します。<br/><br/>ファイルを検索する場合は、ワイルドカードとしてアスタリスク (*) を使用できます。 たとえば、「 \*。\*すべてファイル一覧を表示します。 ファイル、たとえば、C:\My Documents\MyColorPalette.pal の完全なパスを入力することもできます。 または\\\NetworkServer\MyFolder\MyColorPalette.pal します。|
|**ファイルの種類**|表示するファイルの種類を示します。 パレット (* *.pal) のカラー パレットの既定のファイルの種類します。|

## <a name="to-save-a-custom-colors-palette"></a>カスタム カラー パレットを保存するには

1. **イメージ**] メニューの [選択**パレットの保存**します。

1. パレットを保存するディレクトリに移動し、パレット名を入力します。

1. **[保存]** を選択します。

## <a name="to-load-a-custom-colors-palette"></a>カスタム カラー パレットを読み込むには

1. **イメージ**] メニューの [選択**パレットの読み込み**します。

1. **カラー パレットの読み込み** ダイアログ ボックス、適切なディレクトリに移動し、読み込むパレットを選択します。 **色**パレットは、拡張子 .pal と共に保存されます。

## <a name="requirements"></a>必要条件

なし

## <a name="see-also"></a>関連項目

[アクセラレータ キー](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[カラーを使用します。](../windows/working-with-color-image-editor-for-icons.md)<br/>
[アイコン用イメージ エディター](../windows/image-editor-for-icons.md)