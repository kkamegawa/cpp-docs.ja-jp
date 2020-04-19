---
title: COleControlModule クラス
ms.date: 11/04/2016
f1_keywords:
- OleControlModule
helpviewer_keywords:
- OLE control modules [MFC]
- MFC ActiveX controls [MFC], OLE control modules
- COleControlModule class [MFC]
- control modules [MFC]
ms.assetid: 0721724d-d4af-4eda-ad34-5a2b27810dd4
ms.openlocfilehash: f6d486c7bacb897d70d85414ac3d0bd0d13e447b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62310397"
---
# <a name="colecontrolmodule-class"></a>COleControlModule クラス

OLE コントロール モジュール オブジェクトを派生するための基底クラスです。

## <a name="syntax"></a>構文

```
class COleControlModule : public CWinApp
```

## <a name="remarks"></a>Remarks

このクラスは、コントロール、モジュールを初期化するためのメンバー関数を提供します。 Microsoft Foundation classes を使用する各 OLE コントロール モジュールがから派生した 1 つのオブジェクトを含めることができますのみ`COleControlModule`します。 その他の C++ のグローバル オブジェクトが作成されるときに、このオブジェクトが構築されます。 派生宣言`COleControlModule`グローバル レベルのオブジェクト。

使用しての詳細については、`COleControlModule`クラスを参照してください、 [CWinApp](../../mfc/reference/cwinapp-class.md)クラスと、アーティクル[ActiveX コントロール](../../mfc/mfc-activex-controls.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWinThread](../../mfc/reference/cwinthread-class.md)

[CWinApp](../../mfc/reference/cwinapp-class.md)

`COleControlModule`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxctl.h

## <a name="see-also"></a>関連項目

[MFC サンプル TESTHELP](../../overview/visual-cpp-samples.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)
