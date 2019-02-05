---
title: コントロールの選択
ms.date: 11/04/2016
helpviewer_keywords:
- Dialog Editor [C++], selecting controls
- dominant controls
- dialog box controls [C++], selecting in editor
- controls [C++], selecting
- size, controls
- controls [C++], dominant
- controls [C++], removing from groups
- Dialog Editor [C++], dominant control
ms.assetid: 27f05450-4550-4229-9f4c-2c9e06365596
ms.author: Michael.Blome
ms.topic: tutorial
ms.service: cpp
author: mikeblome
ms.openlocfilehash: 008c99ae4b2cba5ff8f8b9ab069bb1b8085b7524
ms.sourcegitcommit: b488462a6e035131121e6f32d8f3b108cc798b5e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2019
ms.locfileid: "55293638"
---
# <a name="selecting-controls"></a>コントロールの選択

コントロールのサイズを選択、配置、移動、コピー、または削除したり、およびし操作を完了します。 ほとんどの場合でサイズ変更と配置ツールを使用する 1 つ以上のコントロールを選択する必要があります、[ダイアログ エディター ツールバー](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)します。

コントロールが選択されている、影付きの枠が周囲で実線 (アクティブ) または中空 (非アクティブ) を二乗「サイズ変更ハンドル、」小さいときに選択境界線が表示されます。 複数のコントロールを選択すると主要なコントロールが実線のサイズ変更ハンドルがある白抜きのサイズ変更ハンドルの他のすべての選択したコントロール。

複数のコントロールの配置またはサイズ変更する場合、**ダイアログ**エディターは「主要なコントロール」を使用して、他のコントロールのサイズや配置の方法を決定します。 既定では、主要なコントロールは、選択されている最初のコントロールは。

マネージ プロジェクトにリソースを追加する方法については、次を参照してください。 [Resources in Desktop Apps](/dotnet/framework/resources/index)で、 *.NET Framework 開発者ガイド*します。 マネージ プロジェクトにリソース ファイルを手動で追加、リソースへのアクセス、静的リソースの表示方法、およびリソース文字列のプロパティを割り当てる方法については、次を参照してください。[デスクトップ アプリのリソース ファイルの作成](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)です。 管理対象アプリ内のリソースのグローバリゼーションとローカリゼーションについては、次を参照してください。 [Globalizing and Localizing .NET Framework Applications](/dotnet/standard/globalization-localization/index)します。

## <a name="to-select-multiple-controls"></a>複数のコントロールを選択するには

1. [ツールボックス ウィンドウ](/visualstudio/ide/reference/toolbox)を選択、**ポインター**ツール。

1. 選択ボックスで、ダイアログ ボックスで選択するコントロールの周囲へのポインターをドラッグします。

   マウス ボタンを離すと、すべて内側と、選択ボックスが選択されているを交差を制御します。

   \- または -

   押しながら、 **Shift**キーを選択したいコントロールを選択します。

   \- または -

   押しながら、 **Ctrl**キーを選択したいコントロールを選択します。

## <a name="to-remove-a-control-from-a-group-of-selected-controls-or-to-add-a-control-to-a-group-of-selected-controls"></a>コントロールを選択したコントロールのグループから削除するには、か、コントロールを選択したコントロールのグループに追加するには

1. 押しながら選択コントロールのグループと、 **Shift**キーし、既存の選択範囲を追加または削除するコントロールを選択します。

   > [!NOTE]
   > 押しながら、 **Ctrl**キーと選択範囲内のコントロールを選択するとその選択範囲内の主要なコントロールを制御する、します。

## <a name="to-specify-the-dominant-control"></a>主要なコントロールを指定するには

1. 押しながら、 **Ctrl**キーし、を使用して、サイズやその他のコントロールの場所を制御するコントロールをクリックします。*最初*します。

> [!NOTE]
> 主要なコントロールのサイズ変更ハンドルは下位のコントロールのハンドルは白抜き点灯します。 すべてのさらにサイズ変更や配置は、主要なコントロールに基づいています。

## <a name="to-change-the-dominant-control"></a>主要なコントロールを変更するには

1. 現在選択されているすべてのコントロールの外側をクリックして現在の選択をオフにします。

1. 最初に、別のコントロールを選択すると、前の手順を繰り返します。

## <a name="requirements"></a>必要条件

Win32

## <a name="see-also"></a>関連項目

[ダイアログ ボックスのコントロール](../windows/controls-in-dialog-boxes.md)<br/>
[コントロール](../mfc/controls-mfc.md)