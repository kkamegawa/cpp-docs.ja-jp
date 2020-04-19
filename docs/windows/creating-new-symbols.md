---
title: '方法: シンボル (C++) の作成します。'
ms.date: 02/14/2019
f1_keywords:
- vc.editors.symbol.creating
- vc.editors.symbol.managing
- vc.editors.resourcesymbols
- vc.editors.symbol.resource
helpviewer_keywords:
- New Symbol dialog box [C++]
- symbols [C++], creating
- resources [C++], viewing
- resource symbols
- symbols [C++], viewing
- New Symbol dialog box [C++]
- Resource Symbols dialog box [C++]
- Change Symbol dialog box [C++]
- resource symbols
- View Use button
- resource editors [C++], resource symbols
ms.assetid: 35168d31-3af6-4ecd-9362-3707d47b53f3
ms.openlocfilehash: d03246d2c701961c824b55fb0cbb781ee3f65028
ms.sourcegitcommit: 6cf0c67acce633b07ff31b56cebd5de3218fd733
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/24/2019
ms.locfileid: "67344200"
---
# <a name="how-to-create-symbols-c"></a>方法: シンボル (C++) の作成します。

新しいプロジェクトを開始しているときに割り当てられるが、リソースの作成する前に必要なシンボル名をマップする便利なことがあります。

> [!NOTE]
> 場合は、プロジェクトに .rc ファイル含まれていないを参照してください。[方法。リソースを作成する](../windows/how-to-create-a-resource-script-file.md)します。

**リソース シンボル** ダイアログ ボックスでは、新しいリソース シンボルの追加、シンボルが表示されます、またはシンボルが使用中は、ソース コード内の場所へのスキップを変更することができます。

ダイアログ ボックスには、次のプロパティが含まれています。

|プロパティ|説明|
|--------------------------|------------------------------------------|
|**Name**|シンボルの名前を表示します。<br/><br/>詳細については、次を参照してください。[シンボル名の制限](../windows/symbol-name-restrictions.md)します。|
|**[値]**|シンボルの数値を表示します。<br/><br/>詳細については、次を参照してください。[シンボル値の制限](../windows/symbol-value-restrictions.md)します。|
|**使用中**|シンボルが 1 つ以上のリソースで使用されることを指定する場合にオンにします。<br/><br/>リソースまたはリソースに表示されます、**で使用される**ボックス。|
|**読み取り専用のシンボルを表示します。**|読み取り専用のリソースを表示する場合にオンにします。<br/><br/>既定で、**リソース シンボル** ダイアログ ボックスにリソース スクリプト ファイルで変更可能なリソースのみが表示されますが、このオプションを選択すると、変更可能なリソースは太字で表示されます。 および読み取り専用のリソースはプレーン テキストで表示されます。|
|**使用されます。**|シンボル一覧で選択したシンボルを使用するリソースが表示されます。<br/><br/>特定のリソース エディターに移動するでリソースを選択します。、**で使用される**ボックス**ビュー使用**。|
|**新規**|開く、**新しいシンボル** ダイアログ ボックス名を定義することができ、必要に応じて、新しいシンボル リソース識別子の値。|
|**変更**|開く、**シンボルの変更**名前またはシンボルの値を変更することができます ダイアログ ボックス。<br/><br/>使用中のコントロールまたはリソースのシンボルを変更するには、対応するリソース エディターを使用する必要があります。 詳細については、次を参照してください。[管理シンボル](../windows/changing-unassigned-symbols.md)します。|
|**ビューの使用**|対応するリソース エディターで、シンボルが含まれたリソースを開きます。|

## <a name="create-symbols"></a>シンボルを作成します。

### <a name="to-create-a-new-symbol"></a>新しいシンボルを作成するには

1. **リソース シンボル** ダイアログ ボックスで、選択**新規**します。

1. **名前**ボックスに、シンボル名を入力します。

1. 割り当てられたシンボル値を受け入れるか、新しい値を入力、**値**ボックス。

1. 選択**OK**新しいシンボルをシンボルの一覧に追加します。

> [!NOTE]
> 既に存在するシンボルの名前を入力すると、その名前のシンボルが既に定義されていることを示すメッセージ ボックスが表示されます。 同じ名前の 2 つ以上のシンボルを定義することはできませんが、同じ数値を持つ異なるシンボルを定義することができます。

## <a name="to-view-resource-symbols"></a>リソース シンボルを表示するには

[リソース ビュー](how-to-create-a-resource-script-file.md#create-resources)を右クリックし、 *.rc*ファイルおよび選択**リソース シンボル**リソース シンボル テーブルを表示する、**リソース シンボル** ダイアログ ボックス。

> [!NOTE]
> 定義済みのシンボルを表示するには、確認、**読み取り専用のシンボルを表示**チェック ボックスをオンします。

### <a name="to-open-the-resource-editor-for-a-given-symbol"></a>特定のシンボルに対するリソース エディターを開く

シンボルを参照しているときに、**リソース シンボル**、特定のシンボルの使用方法の詳細についてをする可能性があります。 **ビュー使用**ボタンはこの情報を取得する簡単な方法を提供します。

1. **リソース シンボル** ダイアログ ボックスで、**名前**ボックスで、シンボルを選択します。

1. **使用者**ボックスで、興味のあるリソースの種類を選択します。

1. 選択、**ビュー使用**ボタンをクリックします。

   リソースが適切なエディターに表示されます。

## <a name="requirements"></a>必要条件

Win32

## <a name="see-also"></a>関連項目

[リソース識別子 (シンボル)](../windows/symbols-resource-identifiers.md)<br/>
[方法: シンボルの管理](../windows/changing-a-symbol-or-symbol-name-id.md)<br/>
[定義済みシンボル ID](../windows/predefined-symbol-ids.md)<br/>