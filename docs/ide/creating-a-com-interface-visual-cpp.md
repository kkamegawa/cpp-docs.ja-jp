---
title: COM インターフェイスを作成する
ms.date: 05/14/2019
helpviewer_keywords:
- COM interfaces, creating
- methods [C++], adding to COM interfaces
- COM interfaces, editing
- properties [C++], adding to COM interfaces
ms.assetid: 1be84d3c-6886-4d1e-8493-56c4d38a96d4
ms.openlocfilehash: 09ddc113450fadb208e4f8471bc9aacf596a53f1
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "66182612"
---
# <a name="create-a-com-interface"></a>COM インターフェイスを作成する

Visual Studio には、COM オブジェクトとオートメーション クラスに向けたインターフェイスとディスパッチ インターフェイスを定義する COM を使用するプロジェクトを作成するためのウィザードとテンプレートが用意されています。

これらのウィザードを使用して、次の 3 つの一般的なタスクを実行できます。

- [MFC プロジェクトへの ATL サポートの追加](../mfc/reference/adding-atl-support-to-your-mfc-project.md)

  [MFC アプリケーション ウィザード](../mfc/reference/mfc-application-wizard.md)を使用して MFC プロジェクトを作成し、**MFC に ATL サポートを追加**コード ウィザードを実行した後で、MFC アプリケーションに ATL サポートを追加します。 このサポートは、MFC の実行可能ファイルまたは DLL プロジェクトに追加された単純な COM オブジェクトにのみ適用されます。 このような ATL オブジェクトには複数のインターフェイスが存在することがあります。

- [MFC ActiveX コントロールの作成](../mfc/reference/creating-an-mfc-activex-control.md)

  [MFC ActiveX コントロール ウィザード](../mfc/reference/mfc-activex-control-wizard.md)を開き、それぞれ、.idl ファイルとコントロール クラスで定義されているディスパッチ インターフェイスとイベント マップを含む ActiveX コントロールを作成します。

- [ATL コントロールの追加](../atl/reference/adding-an-atl-control.md)

  [ATL プロジェクト ウィザード](../atl/reference/atl-project-wizard.md)と [ATL コントロール ウィザード](../atl/reference/atl-control-wizard.md)の組み合わせを使用して、ATL ActiveX コントロールを作成します。

  前述のとおり、ATL サポートを追加した MFC プロジェクトに ATL コントロールを追加することもできます。 さらに、 **[クラスの追加]** ダイアログ ボックスで、**ATL コントロール**を選択し、ATL サポートを MFC プロジェクトに追加していない場合、Visual Studio で ATL サポートを MFC プロジェクトに追加することを確認するダイアログ ボックスが表示されます。

  このウィザードは、プロジェクト クラスに IDL ソースと COM マップを生成します。

ATL プロジェクトが開いたら、[[クラスの追加]](../ide/add-class-dialog-box.md) ダイアログ ボックスで、COM インターフェイスをプロジェクトに追加するための追加のウィザードおよびテンプレートを選択できます。 次のウィザードでは、オブジェクトの 1 つまたは複数のインターフェイスを確立できます。

- [ATL COM+ 1.0 コンポーネント ウィザード](../atl/reference/atl-com-plus-1-0-component-wizard.md)
- [ATL シンプル オブジェクト ウィザード](../atl/reference/atl-simple-object-wizard.md)
- [ATL Active Server Page コンポーネント ウィザード](../atl/reference/atl-active-server-page-component-wizard.md)
- [ATL コントロール ウィザード](../atl/reference/atl-control-wizard.md)

また、COM コントロールに新しいインターフェイスを実装することもできます。 クラス ビューでオブジェクトのコントロール クラスを右クリックし、[[インターフェイスの実装]](../ide/implement-interface-wizard.md) を選択します。

> [!NOTE]
> Visual Studio では、インターフェイスをプロジェクトに追加するウィザードは提供されません。 [ATL シンプル オブジェクト ウィザード](../atl/reference/atl-simple-object-wizard.md)を使用してシンプル オブジェクトを追加することで、インターフェイスを ATL プロジェクトに追加するか、[MFC プロジェクトに ATL サポートを追加](../mfc/reference/adding-atl-support-to-your-mfc-project.md)できます。 また、プロジェクトの .idl ファイルを開き、次のように入力してインターフェイスを作成することもできます。

```
interface IMyInterface {
};
```

詳細については、「[インターフェイスの実装](../ide/implementing-an-interface-visual-cpp.md)」および「[ATL プロジェクトへのオブジェクトやコントロールの追加](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)」を参照してください。

Visual C++ では、いくつかの方法を使用して、プロジェクトに対して定義された [COM インターフェイスを表示および編集](#edit-a-com-interface)できます。 [クラス ビュー](/visualstudio/ide/viewing-the-structure-of-code)には、C++ プロジェクトの .idl ファイルで定義されている任意のインターフェイスまたはディスパッチ インターフェイスのアイコンが表示されます。

ATL ベースの COM オブジェクト クラスの場合、クラス ビューは、ATL クラスの COM マップを読み込み、ATL クラスとそれが実装するインターフェイスの間の関係を表示します。

クラス ビューおよびそのショートカット メニューで、インターフェイスを次のように操作できます。

- ATL オブジェクトを MFC ベースのアプリケーションに追加します。
- メソッド、プロパティ、およびイベントを追加します。
- アイテムをダブルクリックして、アイテムのインターフェイス コードに直接ジャンプします。

## <a name="in-this-section"></a>このセクションの内容

- [COM インターフェイスを編集する](#edit-a-com-interface)

## <a name="edit-a-com-interface"></a>COM インターフェイスを編集する

クラス ビューのショートカット メニューからコマンドを使用することで、Visual Studio C++ プロジェクトで COM インターフェイスの新しいメソッドとプロパティを定義できます。 ツールボックスから、ActiveX コントロールのイベントを定義することもできます。

ATL ベースと MFC ベースの COM オブジェクト クラスでは、インターフェイスの編集と同時にクラス実装を編集することができます。

> [!NOTE]
> **[クラスの追加]** ダイアログ ボックス外で定義されたインターフェイスの場合、Visual C++ はメソッドまたはプロパティを .idl ファイルに追加し、メソッドを実装するクラスにスタブを追加します。インターフェイスが手動で追加されている場合でも同様です。

次の 3 つのウィザードは、既存のインターフェイスをカスタマイズするのに役立ちます。 クラス ビューからは以下を利用できます。

|ウィザード|プロジェクトの種類|
|------------|------------------|
|[プロパティ追加ウィザード](../ide/names-add-property-wizard.md)|ATL をサポートする ATL プロジェクトまたは MFC プロジェクト。 プロパティを追加するインターフェイスを右クリックします。<br /><br />Visual C++ ではプロジェクトの種類が検出され、適宜、プロパティ追加ウィザードでオプションが変更されます。<br /><br />- [MFC アプリケーション ウィザード](../mfc/reference/mfc-application-wizard.md)を使用して作成されたプロジェクトのディスパッチ インターフェイスの場合、プロパティ追加ウィザードを起動すると、MFC に固有のオプションが提供されます。<br />- MFC ActiveX コントロール インターフェイスの場合、プロパティ追加ウィザードではストック メソッドとプロパティの一覧が提供されます。これをそのまま使用することも、ご利用のコントロール用にカスタマイズすることもできます。<br />- 他のすべてのインターフェイスの場合、プロパティ追加ウィザードではほとんどの状況で役立つオプションが提供されます。|
|[メソッド追加ウィザード](../ide/add-method-wizard.md)|ATL をサポートする ATL プロジェクトまたは MFC プロジェクト。 メソッドを追加するインターフェイスを右クリックします。<br /><br />Visual C++ ではプロジェクトの種類が検出され、適宜、メソッド追加ウィザードでオプションが変更されます。<br /><br />- [MFC アプリケーション ウィザード](../mfc/reference/mfc-application-wizard.md)を使用して作成されたプロジェクトのディスパッチ インターフェイスの場合、メソッド追加ウィザードを使用すると、MFC に固有のオプションが提供されます。<br />- MFC ActiveX コントロール インターフェイスの場合、メソッド追加ウィザードではストック メソッドとプロパティの一覧が提供されます。これをそのまま使用することも、ご利用のコントロール用にカスタマイズすることもできます。<br />- 他のすべてのインターフェイスの場合、**メソッド追加**ウィザードではほとんどの状況で役立つオプションが提供されます。|

また、COM コントロールに新しいインターフェイスを実装することもできます。 クラス ビューでオブジェクトのコントロール クラスを右クリックし、[[インターフェイスの実装]](../ide/implement-interface-wizard.md) を選択します。
