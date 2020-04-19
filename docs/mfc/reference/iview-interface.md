---
title: IView インターフェイス
ms.date: 11/04/2016
f1_keywords:
- IView
- AFXWINFORMS/IView
- AFXWINFORMS/IView::OnActivateView
- AFXWINFORMS/IView::OnInitialUpdate
- AFXWINFORMS/IView::OnUpdate
helpviewer_keywords:
- views [MFC]
- IView class [MFC]
- views [MFC], classes
ms.assetid: 9321f299-486e-4551-bee9-d2c4a7b91548
ms.openlocfilehash: 22e08a70ff4cc742406a1489899c0ba1df7eb664
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321950"
---
# <a name="iview-interface"></a>IView インターフェイス

いくつかのメソッドを実装する[CWinFormsView](../../mfc/reference/cwinformsview-class.md)を使用してマネージ コントロールを表示通知を送信します。

## <a name="syntax"></a>構文

```
interface class IView
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[IView::OnActivateView](#onactivateview)|ビューがアクティブ化または非アクティブ化されたときに、MFC によって呼び出されます。|
|[IView::OnInitialUpdate](#oninitialupdate)|ビューが最初に、ドキュメントに接続されているが、ビューが最初に表示される前に、フレームワークによって呼び出されます。|
|[IView::OnUpdate](#onupdate)|ビューのドキュメントが変更された後に、MFC によって呼び出されますこの関数は、ビューの変更を反映するように表示を更新できます。|

## <a name="remarks"></a>Remarks

`IView` いくつかのメソッドを実装する`CWinFormsView`を使用してホストされているマネージ コントロールを一般的な通知の表示を転送します。 これらは[OnInitialUpdate](#oninitialupdate)、 [OnUpdate](#onupdate)と[OnActivateView](#onactivateview)します。

`IView` ような[CView](../../mfc/reference/cview-class.md)が管理されたビューとコントロールでのみ使用されます。

Windows フォームの使用に関する詳細については、次を参照してください。 [MFC における Windows フォーム ユーザー コントロールを使用して](../../dotnet/using-a-windows-form-user-control-in-mfc.md)します。

## <a name="requirements"></a>必要条件

ヘッダー: afxwinforms.h が (アセンブリ atlmfc\lib\mfcmifc80.dll で定義)

## <a name="onactivateview"></a> IView::OnActivateView

ビューがアクティブ化または非アクティブ化されたときに、MFC によって呼び出されます。
```
void OnActivateView(bool activate);
```

## <a name="parameters"></a>パラメーター

*activate*<br/>
表示されているかどうかを示しますがアクティブまたは非アクティブ化します。

## <a name="oninitialupdate"></a> IView::OnInitialUpdate

ビューが最初に、ドキュメントに接続されているが、ビューが最初に表示される前に、フレームワークによって呼び出されます。
```
void OnInitialUpdate();
```

## <a name="onupdate"></a> IView::OnUpdate

ビューのドキュメントが変更された後に、MFC によって呼び出されます。
```
void OnUpdate();
```

## <a name="remarks"></a>Remarks

この関数は、ビューの変更を反映するように表示を更新できます。

## <a name="see-also"></a>関連項目

[CWinFormsView クラス](../../mfc/reference/cwinformsview-class.md)<br/>
[CView クラス](../../mfc/reference/cview-class.md)
