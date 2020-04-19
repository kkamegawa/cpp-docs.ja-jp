---
title: CMFCDisableMenuAnimation クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation::Restore
helpviewer_keywords:
- CMFCDisableMenuAnimation [MFC], Restore
ms.assetid: c6eb07da-c382-43d6-8028-007f2320e50e
ms.openlocfilehash: bf8c598e9e105569e0a5676267e205b3d3939712
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62345605"
---
# <a name="cmfcdisablemenuanimation-class"></a>CMFCDisableMenuAnimation クラス

ポップアップ メニューのアニメーションを無効にします。

## <a name="syntax"></a>構文

```
class CMFCDisableMenuAnimation
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|||
|-|-|
|名前|説明|
|`CMFCDisableMenuAnimation::CMFCDisableMenuAnimation`|`CMFCDisableMenuAnimation` オブジェクトを構築します。|
|`CMFCDisableMenuAnimation::~CMFCDisableMenuAnimation`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|||
|-|-|
|名前|説明|
|[CMFCDisableMenuAnimation::Restore](#restore)|ポップアップ メニューを表示するために使用、framework の前のアニメーションを復元します。|

### <a name="data-members"></a>データ メンバー

|||
|-|-|
|名前|説明|
|`CMFCDisableMenuAnimation::m_animType`|前のポップアップ メニューのアニメーションの種類を格納します。|

### <a name="remarks"></a>Remarks

このヘルパー クラスを使用すると、(たとえば、マウスやキーボード コマンドを処理するときに) ポップアップ メニューのアニメーションを一時的に無効にします。

A`CMFCDisableMenuAnimation`オブジェクトは、その有効期間中にポップアップ メニューのアニメーションを無効にします。 コンス トラクターでは、現在のポップアップ メニュー アニメーション型を格納する、`m_animType`フィールドと現在のアニメーションの種類をセット`CMFCPopupMenu::NO_ANIMATION`します。 デストラクターは、前のアニメーションの種類を復元します。

作成することができます、`CMFCDisableMenuAnimation`を 1 つの関数全体でのポップアップ メニューのアニメーションを無効にするスタック上のオブジェクト。 関数の間でのポップアップ メニューのアニメーションを無効にする場合は、作成、`CMFCDisableMenuAnimation`ヒープ上のオブジェクトし、ポップアップ メニューのアニメーションを復元するときに削除します。

## <a name="example"></a>例

次の例では、スタックを使用して、メニューのアニメーションを一時的に無効にする方法を示します。

[!code-cpp[NVC_MFC_Misc#1](../../mfc/reference/codesnippet/cpp/cmfcdisablemenuanimation-class_1.h)]

## <a name="inheritance-hierarchy"></a>継承階層

[CMFCDisableMenuAnimation](../../mfc/reference/cmfcdisablemenuanimation-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxpopupmenu.h

##  <a name="restore"></a>  CMFCDisableMenuAnimation::Restore

ポップアップ メニューを表示するために使用、framework の前のアニメーションを復元します。

```
void Restore ();
```

### <a name="remarks"></a>Remarks

このメソッドを呼び出して、`CMFCDisableMenuAnimation`フレームワーク ポップアップ メニューを表示するために使用する前のアニメーションを復元するデストラクター。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPopupMenu クラス](../../mfc/reference/cmfcpopupmenu-class.md)
