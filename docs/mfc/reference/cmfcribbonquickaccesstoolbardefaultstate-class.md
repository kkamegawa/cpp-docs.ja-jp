---
title: CMFCRibbonQuickAccessToolBarDefaultState クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::AddCommand
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll
helpviewer_keywords:
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], CMFCRibbonQuickAccessToolBarDefaultState
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], AddCommand
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], CopyFrom
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], RemoveAll
ms.assetid: eca99200-b87b-47ba-b2e8-2f3f2444b176
ms.openlocfilehash: 0ea9ec8de0b657fa4e7c601f9c3e676f550defa9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62380260"
---
# <a name="cmfcribbonquickaccesstoolbardefaultstate-class"></a>CMFCRibbonQuickAccessToolBarDefaultState クラス

リボン バーに配置されるクイック アクセス ツールバーの既定の状態を管理するヘルパー クラス ( [CMFCRibbonBar クラス](../../mfc/reference/cmfcribbonbar-class.md))。

## <a name="syntax"></a>構文

```
class CMFCRibbonQuickAccessToolBarDefaultState
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState](#cmfcribbonquickaccesstoolbardefaultstate)|`CMFCRibbonQuickAccessToolbarDefaultState` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand)|既定の状態にクイック アクセス ツールバーのコマンドを追加します。 これは、操作では、ツールバー自体は変更されません。|
|[CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom](#copyfrom)|別の 1 つのクイック アクセス ツールバーのプロパティをコピーします。|
|[CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll](#removeall)|クイック アクセス ツールバーからすべてのコマンドを削除します。 これは、操作では、ツールバー自体は変更されません。|

## <a name="remarks"></a>Remarks

クイック アクセス ツールバー、アプリケーションを作成した後、呼び出すことによって、既定の状態を設定すること勧め[CMFCRibbonBar::SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate)します。 ユーザーがクリックしたときに、この既定の状態が復元された、**リセット**のボタンでは、**カスタマイズ**、アプリケーションのページ**オプション** ダイアログ ボックス。

## <a name="inheritance-hierarchy"></a>継承階層

[CMFCRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md)

## <a name="example"></a>例

次の例のオブジェクトを構築する方法、`CMFCRibbonQuickAccessToolbarDefaultState`クラスと既定の状態にクイック アクセス ツールバーのコマンドを追加する方法。

[!code-cpp[NVC_MFC_RibbonApp#21](../../mfc/reference/codesnippet/cpp/cmfcribbonquickaccesstoolbardefaultstate-class_1.cpp)]

## <a name="requirements"></a>必要条件

**ヘッダー:** afxribbonquickaccesstoolbar.h

##  <a name="addcommand"></a>  CMFCRibbonQuickAccessToolBarDefaultState::AddCommand

既定の状態にクイック アクセス ツールバーのコマンドを追加します。

```
void AddCommand(
    UINT uiCmd,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>パラメーター

*[in] uiCmd*<br/>
コマンド ID を指定します

*[in] bIsVisible*<br/>
クイック アクセス ツールバーが既定の状態の場合は、コマンドの可視性を設定します。

### <a name="remarks"></a>Remarks

コマンドを CMFCRibbonQuickAccessToolBarDefaultState に追加するには、3 つの結果が実現されます。 最初に、追加した各コマンドは、クイック アクセス ツールバーの右側にあるドロップダウン リストに表示されます。 この方法で、ユーザーが簡単に追加またはクイック アクセス ツールバーからコマンドを削除できます。 表示する記載されているコマンドのみに表示するよう既定の状態で、ユーザーがクリックすると、クイック アクセス ツールバーをリセットする第 2 に、**リセット**ボタン、**カスタマイズ** ダイアログ ボックス。 3 つ目の状態が呼び出さない場合[CMFCRibbonBar::SetQuickAccessCommands](../../mfc/reference/cmfcribbonbar-class.md#setquickaccesscommands)、クイック アクセス ツールバーを使用してこの一覧から表示されるコマンド、既定の表示コマンドとして初めてユーザーがアプリケーションを実行します。 目的のすべてのコマンドを追加した後で呼び出す[CMFCRibbonBar::SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate)そのリボン バーのクイック アクセス ツールバーの既定の状態としてこのインスタンスを設定します。

##  <a name="copyfrom"></a>  CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom

別の 1 つのクイック アクセス ツールバーのプロパティをコピーします。

```
void CopyFrom(const CMFCRibbonQuickAccessToolBarDefaultState& src);
```

### <a name="parameters"></a>パラメーター

*src*<br/>
[in]ソースへの参照を`CMFCRibbonQuickAccessToolBarDefaultState`からコピーするオブジェクト。

### <a name="remarks"></a>Remarks

このメソッドでは、各コマンドをコピー元の`CMFCRibbonQuickAccessToolBarDefaultState`オブジェクトをこのオブジェクトを使用して、 [CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand)メソッド。

##  <a name="cmfcribbonquickaccesstoolbardefaultstate"></a>  CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState

クイック アクセス ツールバーの既定の状態オブジェクトを構築します。

```
CMFCRibbonQuickAccessToolBarDefaultState();
```

### <a name="remarks"></a>Remarks

既定では、一連のコマンドの新しいインスタンス[CMFRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md)が含まれていますが空です。

##  <a name="removeall"></a>  CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll

クイック アクセス ツールバーの既定のコマンドの一覧をクリアします。

```
void RemoveAll();
```

### <a name="remarks"></a>Remarks

この関数がこのインスタンスからすべてのコマンドを削除する前の呼び出し[CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand)を追加します。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBar クラス](../../mfc/reference/cmfcribbonbar-class.md)
