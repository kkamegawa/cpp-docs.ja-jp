---
title: COM インターフェイスのエントリ ポイント
ms.date: 03/27/2019
helpviewer_keywords:
- entry points, COM interfaces
- state management, OLE/COM interfaces
- MFC COM, COM interface entry points
- OLE, interface entry points
- MFC, managing state data
- COM interfaces, entry points
ms.assetid: 9e7421dc-0731-4748-9e1b-90acbaf26d77
ms.openlocfilehash: eb8fc425d6b9849f6367d9b207e5181652386be3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207853"
---
# <a name="com-interface-entry-points"></a>COM インターフェイスのエントリ ポイント

COM インターフェイスのメンバー関数は、使用、`METHOD_PROLOGUE`エクスポートされたインターフェイスのメソッドを呼び出すときに、適切なグローバル状態を維持するためにマクロ。

によって実装されるインターフェイスのメンバー関数の通常、 `CCmdTarget`-の自動初期化を提供する、このマクロを既に使用して派生オブジェクト、`pThis`ポインター。 例:

[!code-cpp[NVC_MFCConnectionPoints#5](../mfc/codesnippet/cpp/com-interface-entry-points_1.cpp)]

詳細については、次を参照してください。[テクニカル ノート 38](../mfc/tn038-mfc-ole-iunknown-implementation.md) MFC/OLE で`IUnknown`実装します。

`METHOD_PROLOGUE`としてマクロが定義されます。

```cpp
#define METHOD_PROLOGUE(theClass, localClass) \
    theClass* pThis = \
    ((theClass*)((BYTE*)this - offsetof(theClass, m_x##localClass))); \
    AFX_MANAGE_STATE(pThis->m_pModuleState) \
```

マクロ、グローバル状態の管理に関連の部分は次のとおりです。

`AFX_MANAGE_STATE( pThis->m_pModuleState )`

この式で*m_pModuleState*親オブジェクトのメンバー変数と見なされます。 によって実装されている、`CCmdTarget`基底クラスとは、適切な値に初期化`COleObjectFactory`オブジェクトがインスタンス化されるときに、します。

## <a name="see-also"></a>関連項目

[MFC モジュールの状態データの管理](../mfc/managing-the-state-data-of-mfc-modules.md)
