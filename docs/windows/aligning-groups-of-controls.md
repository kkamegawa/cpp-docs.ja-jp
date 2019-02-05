---
title: コントロールを配置します。
ms.date: 11/04/2016
helpviewer_keywords:
- controls [C++], aligning
- controls [C++], positioning
- Space Evenly command
- dialog box controls [C++], placement
- Center in Dialog command
- Arrange Buttons command
- buttons, arranging push buttons in dialog boxes
- push buttons
ms.assetid: a4f49a73-4a17-44b3-8568-aa35f646b5cf
ms.openlocfilehash: abfae0f0146fa736a6427eb1180805717ce8a78e
ms.sourcegitcommit: 5270117dbecc4c49bca0cf10b927bae3c9930038
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484982"
---
# <a name="align-controls"></a>コントロールを配置します。

マネージ プロジェクトにリソースを追加する方法については、次を参照してください。 [Resources in Desktop Apps](/dotnet/framework/resources/index)で、 *.NET Framework 開発者ガイド*します。 マネージ プロジェクトにリソース ファイルを手動で追加、リソースへのアクセス、静的リソースの表示方法、およびリソース文字列のプロパティを割り当てる方法については、次を参照してください。[デスクトップ アプリのリソース ファイルの作成](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)です。 管理対象アプリ内のリソースのグローバリゼーションとローカリゼーションについては、次を参照してください。 [Globalizing and Localizing .NET Framework Applications](/dotnet/standard/globalization-localization/index)します。

次の手順では、コントロールを配置する方法を示します。

## <a name="to-align-groups-of-controls"></a>コントロールのグループを配置するには

1. [コントロールを選択する](../windows/selecting-multiple-controls.md)を配置します。 主要なコントロールを最初にするコントロールを選択することを確認するまたは配置を実行しているか、コマンドのサイズを変更する前に、主要なコントロールに設定します。

   コントロールのグループの最後の位置は、主要なコントロールの位置に依存します。 主要なコントロールを選択する方法の詳細については、次を参照してください。[主要なコントロールを指定する](../windows/specifying-the-dominant-control.md)します。

1. **形式**] メニューの [選択**Align**、以下の配置のいずれかを選択。

   - `Lefts`: 選択したコントロールの左端に揃えて配置します。

   - `Centers`: 選択したコントロールを水平方向の中心点を揃えて配置します。

   - `Rights`: 選択したコントロールの右端に揃えて配置します。

   - `Tops`: 選択したコントロールをそれらの上端に沿って配置します。

   - `Middles`: 選択したコントロールを垂直方向中央の点に配置します。

   - `Bottoms`: 選択したコントロールの下端に揃えて配置します。

## <a name="to-even-the-spacing-between-controls"></a>コントロール間の間隔を均等に

**ダイアログ**等間隔の最も外側のコントロールを選択するエディターを使用します。

1. 配置を変更するコントロールを選択します。

1. **形式**] メニューの [選択**均等スペース**、次の間隔の配置のいずれかを選択します。

   - `Across`: 領域の左端と右端に選択したコントロールの間で均等にコントロール。

   - `Down`: 領域の最上位にある、選択されている最下位のコントロールの間で均等にコントロール。

## <a name="to-center-controls-in-a-dialog-box"></a>ダイアログ ボックスのコントロールの中央に

1. 配置を変更するコントロールを選択します。

1. **形式**] メニューの [選択**ダイアログの中央に**、以下の配置のいずれかを選択します。

   - `Vertical`: ダイアログ ボックスの垂直方向にコントロール センターです。

   - `Horizontal`: ダイアログ ボックスの水平方向にコントロール センターです。

## <a name="to-arrange-push-buttons-along-the-right-or-bottom-of-a-dialog-box"></a>右端またはダイアログ ボックスの下部にあるプッシュ ボタンを配置するには

1. 1 つまたは複数のプッシュ ボタンを選択します。

1. **形式**] メニューの [選択**ボタンの配置**、以下の配置のいずれかを選択します。

   - `Right`: プッシュ ボタン、ダイアログ ボックスの右端に揃えて配置します。

   - `Bottom`: プッシュ ボタン、ダイアログ ボックスの下端に揃えて配置します。

       プッシュ ボタン以外のコントロールを選択した場合の位置に影響を与えません。

## <a name="requirements"></a>必要条件

Win32

## <a name="see-also"></a>関連項目

[ダイアログ ボックスのコントロールの配置](../windows/arrangement-of-controls-on-dialog-boxes.md)<br/>
[ダイアログ ボックスのコントロール](../windows/controls-in-dialog-boxes.md)<br/>
[コントロール](../mfc/controls-mfc.md)