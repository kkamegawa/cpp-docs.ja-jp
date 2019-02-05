---
title: ダイアログ エディターの状態 (ガイドとグリッド) (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- Dialog Editor [C++], guides and margins
- guides, clearing
- guides
- dialog box controls [C++], placement
- controls [C++], guides and margins
- guides, creating
- guides, moving
- margins, moving
- DLUs (dialog units)
- controls [C++], aligning
- Dialog Editor [C++], snap to guides
- guides, tick mark interval
- dialog box controls [C++], placement
- guides, aligning controls
- dialog units (DLUs)
- snap to guides (Dialog editor)
- controls [C++], sizing
- tick mark interval in Dialog editor
- controls [C++], snap to guides/grid
- guides, disabling snapping
- controls [C++], snap to guides/grid
- controls [C++], layout grid
- snap to layout grid
- grids, turning on or off
- layout grid in Dialog Editor
- grids, changing size
- grid spacing
- guides, settings
- layout grid in Dialog Editor
- controls [C++], snap to guides/grid
- Guide Settings dialog box (Dialog editor)
ms.assetid: dbacf9ef-e8b0-4125-a7ce-84911c482e98
ms.openlocfilehash: 52fc19d8a39680c16692177e2758fba78afc7d3a
ms.sourcegitcommit: 5270117dbecc4c49bca0cf10b927bae3c9930038
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484995"
---
# <a name="dialog-editor-states-guides-and-grids-c"></a>ダイアログ エディターの状態 (ガイドとグリッド) (C++)

ダイアログ ボックスのコントロールを配置することができます、**ダイアログ**エディターで次の 3 つの異なる状態のいずれか。

- ガイドとマージン (既定の設定)

- レイアウト グリッドを使用

- スナップや配置機能なし

[ダイアログ エディター ツールバー](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)状態を制御するボタンが含まれています。 状態を変更するには、適切なアイコンをクリックします。 使用して、状態を変更することも、**番組ガイドの設定**コマンドを**形式**メニュー。

**ガイド設定**ダイアログ ボックスには、次のプロパティ。

|プロパティ|説明|
|---|---|
|**レイアウト ガイド**|レイアウト ガイドの設定を表示します。|
|**None**|レイアウト ツールを非表示にします。|
|**ルーラーとガイド**|有効な場合は、レイアウト ツールにルーラーを追加します。ガイドは、ルーラーに配置することができます。 既定のガイドは、余白は、ドラッグして移動することができます。 ルーラーのガイドを配置を選択します。 ガイドの上または横に、コントロールが移動したときに「スナップ」を制御します。 接続するいると、コントロールは、ガイドにも移動します。 コントロールがそれぞれの側では、ガイドにアタッチされているし、ガイドを移動、コントロールのサイズを変更します。|
|**グリッド**|レイアウト グリッドを作成します。 新しいコントロールがグリッドに自動的に整列します。|
|**グリッドの間隔**|ダイアログ ボックスの単位 (Dlu) では、グリッドの間隔の設定を表示します。|
|**幅：Dlu**|Dlu でレイアウト グリッドの幅を設定します。 水平 DLU は、4、ダイアログ ボックスのフォントの平均幅です。|
|**Height:Dlu**|Dlu でレイアウト グリッドの高さを設定します。 垂直 DLU は 8 で割った値 ダイアログ ボックスのフォントの高さの平均値です。|

マネージ プロジェクトにリソースを追加する方法については、次を参照してください。 [Resources in Desktop Apps](/dotnet/framework/resources/index)で、 *.NET Framework 開発者ガイド*します。 マネージ プロジェクトにリソース ファイルを手動で追加、リソースへのアクセス、静的リソースの表示方法、およびリソース文字列のプロパティを割り当てる方法については、次を参照してください。[デスクトップ アプリのリソース ファイルの作成](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)です。 管理対象アプリ内のリソースのグローバリゼーションとローカリゼーションについては、次を参照してください。 [Globalizing and Localizing .NET Framework Applications](/dotnet/standard/globalization-localization/index)します。

## <a name="create-and-set-guides-and-margins"></a>作成し、ガイドとマージンの設定

コントロールの移動して、コントロールの追加、または現在のレイアウトを並べ替え、ガイドを使用するかどうかは、ダイアログ ボックス内に正確にコントロールを配置します。 ガイドでは、青い点線を表示、エディターの最上部に、左側のルーラーの対応する矢印で表示されるダイアログ ボックスで、**ダイアログ**エディター。

ダイアログ ボックスを作成するときに、次の 4 つの余白が提供されます。 余白は、青い点線として表示される、変更後のガイドです。

### <a name="to-create-a-guide"></a>ガイドを作成するには

ルーラー、ガイドを作成する 1 回クリックします。 (1 回のクリックが新たに作成ガイド; の起動をダブルクリックすると、**番組ガイドの設定** ダイアログ ボックスの番組ガイドの設定を指定することができます)。

### <a name="to-set-a-guide"></a>ガイドを設定するには

ダイアログ ボックスで、ガイドをクリックし、新しい位置にドラッグします。 (できますも矢印をクリックする、ルーラーに関連付けられているガイドをドラッグします。)

ウィンドウの下部にあるステータス バーには、ルーラー、ガイドの座標が表示されます。 ルーラー、ガイドの正確な位置を表示する矢印の上にポインターを移動します。

### <a name="to-delete-a-guide"></a>ガイドを削除するには

ダイアログ ボックスには、番組ガイドをドラッグします。

\- または -

ルーラーから対応する矢印をドラッグします。

### <a name="to-move-margins"></a>余白を移動するには

余白を新しい位置にドラッグします。

マージンを非表示にするには、余白を 0 の位置に移動します。 余白を元に戻します、余白の位置 0 ポインターを置きます、余白を位置に移動します。

## <a name="align-controls-on-a-guide"></a>ガイドのコントロールを配置します。

コントロールのサイズ変更ハンドルは、コントロールの移動、およびガイドに合わせてコントロールがない場合、ガイドがコントロールに合わせるときに、ガイドにスナップされます。 ガイドが移動したときにスナップしたコントロールも移動します。 ガイドでは、いずれかが移動すると、コントロールの 1 つ以上のガイドを基準としてスナップされますがサイズ変更されます。

ガイドとコントロールの間隔を決定する定規の目盛りは、ダイアログ単位 (Dlu) によって定義されます。 DLU は、通常、8 ポイント MS Shell Dlg、ダイアログ ボックス フォントのサイズに基づきます。 水平 DLU は、4、ダイアログ ボックスのフォントの平均幅です。 垂直 DLU は 8 で割った値のフォントの高さの平均値です。

### <a name="to-size-a-group-of-controls-with-guides"></a>ガイドを使用してコントロールのグループのサイズ

1. コントロール (またはコントロール) の一方の側をスナップをガイドします。

1. コントロール (またはコントロール) の反対側のガイドをドラッグします。

   複数のコントロールで必要に応じて、それぞれに 2 番目のガイドへのスナップのサイズします。

1. コントロール (またはコントロール) のサイズのいずれかのガイドに移動します。

### <a name="to-change-the-intervals-of-the-tick-marks"></a>目盛りの間隔を変更するには

1. **形式** メニューの 選択**ガイド設定**です。

1. **ガイド設定** ダイアログ ボックスで、**グリッドの間隔**フィールドに、Dlu の新しい幅と高さを指定します。

## <a name="disable-guides"></a>ガイドを無効にします。

ガイド、スナップに効果を無効にするのに、マウスと組み合わせて特殊なキーを使用できます。 使用して、 **Alt**キーが選択されているガイドのスナップの効果を無効にします。 ガイドを移動、 **Shift**キーは、スナップしたコントロールが、ガイドに移動しないようにします。

### <a name="to-disable-the-snapping-effect-of-the-guides"></a>ガイド、スナップに効果を無効にするには

押しながら、コントロールをドラッグ、 **Alt**キー。

### <a name="to-move-guides-without-moving-the-snapped-controls"></a>スナップしたコントロールを移動せずにガイドを移動するには

押しながら、ガイドをドラッグ、 **Shift**キー。

### <a name="to-turn-off-the-guides"></a>ガイドでは、オフにするには

1. **形式** メニューの 選択**ガイド設定**です。

1. **ガイド設定**ダイアログ ボックスで、**レイアウト ガイド**を選択します**None**します。

   > [!NOTE]
   > アクセスは、ルーラー バーをダブルクリックすることも、**ガイド設定** ダイアログ ボックス。

\- または -

**形式**メニューの **ガイドの切り替え**します。

## <a name="modify-the-layout-grid"></a>レイアウト グリッドを変更します。

配置またはコントロールの配置 ダイアログ ボックスで、する場合より正確な配置レイアウト グリッドを使用できます。 グリッドをオンにするに「スナップ」グリッドの点線帯びたかのようにコントロールが表示されます。 この「グリッドにスナップ」機能を有効または無効にして、レイアウトのグリッド セルのサイズを変更できます。

### <a name="to-turn-the-layout-grid-on-or-off"></a>レイアウト グリッドをオンまたはオフにするには

1. **形式** メニューの 選択**ガイド設定**です。

1. **ガイド設定** ダイアログ ボックスをオンまたはオフ、**グリッド**ボタンをクリックします。

   個々 のグリッドでも制御できます**ダイアログ**エディターのウィンドウを使用して、**グリッドの切り替え**ボタンを[ダイアログ エディター ツールバー](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)します。

### <a name="to-change-the-size-of-the-layout-grid"></a>レイアウト グリッドのサイズを変更するには

1. **形式** メニューの 選択**ガイド設定**です。

1. **ガイド設定** ダイアログ ボックスに、Dlu で、グリッド内のセルの高さと幅を入力します。 最小の高さまたは幅 4 Dlu です。 Dlu の詳細については、次を参照してください。[コントロール ダイアログ ボックスの配置](../windows/arrangement-of-controls-on-dialog-boxes.md)します。

## <a name="requirements"></a>必要条件

Win32

## <a name="see-also"></a>関連項目

[ダイアログ ボックスのコントロール](../windows/controls-in-dialog-boxes.md)<br/>
[コントロール (MFC)](../mfc/controls-mfc.md)<br/>
