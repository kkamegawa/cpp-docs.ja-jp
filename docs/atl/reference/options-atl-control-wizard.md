---
title: オプション、ATL コントロール ウィザード
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.control.options
helpviewer_keywords:
- ATL Control Wizard, options
ms.assetid: 4607c51a-992d-433e-9281-919c6f519a3d
ms.openlocfilehash: 25db3995687011de5e9cc0a98506cd26f2f1af0b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495452"
---
# <a name="options-atl-control-wizard"></a>オプション、ATL コントロール ウィザード

ウィザードのこのページを使用して、作成するコントロールの種類と、それに含まれるインターフェイスのサポートレベルを定義します。

## <a name="uielement-list"></a>UIElement の一覧

### <a name="control-type"></a>コントロール型

作成するコントロールの種類。

- **標準コントロール**:ActiveX コントロールです。

- **複合コントロール**:(ダイアログボックスと同様に) 他の ActiveX コントロールまたは Windows コントロールを格納できる ActiveX コントロール。 複合コントロールには、次のものが含まれます。

  - 複合コントロールを実装するダイアログボックスのテンプレート。

  - カスタムリソースレジストリ。呼び出されると、複合コントロールが自動的に登録されます。

  - 複合C++コントロールを実装するクラス。

  - 複合コントロールによって公開される COM インターフェイス。

  - 複合コントロールを含む HTML テストページ。

    既定では、このコントロールは[CComControlBase:: m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly)を true に設定して、これがウィンドウコントロールであることを示します。 シンクマップを実装します。 詳細については、「 [DHTML コントロールのサポート](../../atl/atl-support-for-dhtml-controls.md)」を参照してください。

- **DHTML コントロール**:ATL DHTML コントロールは、HTML を使用してユーザーインターフェイスを指定します。 DHTML UI クラスには、COM マップが含まれています。 既定では、このコントロールは[CComControlBase:: m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly)を true に設定して、これがウィンドウコントロールであることを示します。

   詳細については、「 [DHTML コントロールプロジェクトの要素の識別](../../atl/identifying-the-elements-of-the-dhtml-control-project.md)」を参照してください。

### <a name="minimal-control"></a>最小制御

では、ほとんどのコンテナーで絶対に必要なインターフェイスのみがサポートされています。 任意のコントロールの種類に対して**最小限のコントロール**を設定できます。最小限の標準コントロール、最小限の複合コントロール、または最小限の DHTML コントロールを作成できます。

### <a name="aggregation"></a>集約

作成するコントロールの集計サポートを追加します。 詳細については、「[集計](../../atl/aggregation.md)」を参照してください。

- **はい**:集計可能なコントロールを作成します。

- **いいえ**:集計できないコントロールを作成します。

- **のみ**:集計によってのみインスタンス化できるコントロールを作成します。

### <a name="threading-model"></a>スレッド モデル

コントロールによって使用されるスレッドモデルを指定します。

- **単一**:コントロールは、プライマリ COM スレッドでのみ実行されます。

- **アパートメント**:コントロールは、任意の1つのスレッドアパートメントで作成できます。 これが既定値です。

### <a name="interface"></a>Interface

このコントロールがコンテナーに公開するインターフェイスの型。

- **デュアル**:VTBL を通じて`IDispatch` 、または直接、プロパティとメソッドを公開するインターフェイスを作成します。

- **カスタム**: VTBL を通じて直接メソッドを公開するインターフェイスを作成します。

   **[カスタム]** を選択した場合は、コントロールが**オートメーションと互換性**があることを指定できます。 **[オートメーション互換]** を選択すると、ウィザードは[OLEAUTOMATION](../../windows/oleautomation.md)属性を IDL のインターフェイスに追加します。このインターフェイスは、oleaut32.dll の汎用マーシャラーによってマーシャリングできます。 詳細については、Windows SDK の「[マーシャリングの詳細](/windows/win32/com/marshaling-details)」を参照してください。

   また、 **[オートメーション互換]** を選択した場合は、コントロール内のすべてのメソッドのすべてのパラメーターがバリアント互換である必要があります。

### <a name="support"></a>サポート

コントロールの追加のその他のサポートを設定します。

- **接続ポイント**:オブジェクトのクラスを[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)から派生させ、ソースインターフェイスを公開できるようにすることで、オブジェクトの接続ポイントを有効にします。

- **ライセンス**済み:[ライセンス](/windows/win32/com/licensing)のコントロールにサポートを追加します。 ライセンスされたコントロールは、クライアントコンピューターに正しいライセンスがある場合にのみホストできます。

## <a name="see-also"></a>関連項目

[ATL コントロール ウィザード](../../atl/reference/atl-control-wizard.md)
