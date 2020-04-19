---
title: CMFCAcceleratorKeyAssignCtrl クラス
ms.date: 10/18/2018
f1_keywords:
- CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::GetAccel
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::IsFocused
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::IsKeyDefined
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::ResetKey
helpviewer_keywords:
- CMFCAcceleratorKeyAssignCtrl [MFC], CMFCAcceleratorKeyAssignCtrl
- CMFCAcceleratorKeyAssignCtrl [MFC], GetAccel
- CMFCAcceleratorKeyAssignCtrl [MFC], IsFocused
- CMFCAcceleratorKeyAssignCtrl [MFC], IsKeyDefined
- CMFCAcceleratorKeyAssignCtrl [MFC], PreTranslateMessage
- CMFCAcceleratorKeyAssignCtrl [MFC], ResetKey
ms.assetid: 89fb8e62-596e-4e71-8c9a-32740347aaab
ms.openlocfilehash: 5e57bf149fdbc293692c613afcabcf2d11d32221
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505468"
---
# <a name="cmfcacceleratorkeyassignctrl-class"></a>CMFCAcceleratorKeyAssignCtrl クラス

クラス`CMFCAcceleratorKeyAssignCtrl`は、 [CEdit クラス](../../mfc/reference/cedit-class.md)を拡張して、ALT、CONTROL、SHIFT などの追加のシステムボタンをサポートします。

## <a name="syntax"></a>構文

```
class CMFCAcceleratorKeyAssignCtrl : public CEdit
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCAcceleratorKeyAssignCtrl:: CMFCAcceleratorKeyAssignCtrl](#cmfcacceleratorkeyassignctrl)|`CMFCAcceleratorKeyAssignCtrl` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCAcceleratorKeyAssignCtrl::GetAccel](#getaccel)|`CMFCAcceleratorKeyAssignCtrl` オブジェクトで押されるショートカット キーの `ACCEL` 構造体を取得します。|
|[CMFCAcceleratorKeyAssignCtrl:: IsFocused](#isfocused)||
|[CMFCAcceleratorKeyAssignCtrl::IsKeyDefined](#iskeydefined)|ショートカット キーが定義されているかどうかを判断します。|
|[CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage](#pretranslatemessage)|[TranslateMessage](../../mfc/reference/cwinapp-class.md) および [DispatchMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) の各 Windows 関数にディスパッチされる前に、ウィンドウ メッセージを変換するためにクラス [CWinApp](/windows/win32/api/winuser/nf-winuser-dispatchmessage) で使用されます。 ( [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)をオーバーライドします)。|
|[CMFCAcceleratorKeyAssignCtrl::ResetKey](#resetkey)|ショートカット キーをリセットします。|

## <a name="remarks"></a>Remarks

このクラスは、ショートカット キー (アクセラレータ キーとも呼ばれます) をサポートすることで、`CEdit` クラスの機能を拡張します。 クラス`CMFCAcceleratorKeyAssignCtrl`は、 [CEdit クラス](../../mfc/reference/cedit-class.md)として機能し、システムボタンを認識することもできます。

このクラスは、物理的なショートカット キーの組み合わせを文字列値にマップします。 たとえば、キーの組み合わせ Alt + B が文字列 "Alt + B" にマップされている場合、 ユーザーが `CMFCAcceleratorKeyAssignCtrl` オブジェクト内でこのキーの組み合わせを押すと、"Alt + B" が表示されます。 ショートカットキーと文字列形式のマッピングの詳細については、「 [CMFCAcceleratorKey クラス](../../mfc/reference/cmfcacceleratorkey-class.md)」を参照してください。

## <a name="example"></a>例

次の例は、`CMFCAcceleratorKeyAssignCtrl` オブジェクトを構築し、その `ResetKey` メソッドを使用してショートカット キーをリセットする方法について説明しています。

[!code-cpp[NVC_MFC_RibbonApp#31](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkeyassignctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

`CMFCAcceleratorKeyAssignCtrl`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxacceleratorkeyassignctrl

##  <a name="cmfcacceleratorkeyassignctrl"></a>  CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl

[CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)オブジェクトを構築します。

```
CMFCAcceleratorKeyAssignCtrl();
```

##  <a name="getaccel"></a>  CMFCAcceleratorKeyAssignCtrl::GetAccel

[CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) オブジェクトで押されたショートカットキーの構造体を取得し`ACCEL`ます。

```
ACCEL const* GetAccel() const;
```

### <a name="return-value"></a>戻り値

ショートカットキーを記述する構造体。`ACCEL`

### <a name="remarks"></a>Remarks

ユーザーが`CMFCAcceleratorKeyAssignCtrl`オブジェクトに入力し`ACCEL`たショートカットキーの構造体を取得するには、この関数を使用します。

##  <a name="isfocused"></a>  CMFCAcceleratorKeyAssignCtrl::IsFocused

詳細については、Visual Studio のインストール**の\\VC atlmfc\\\\src mfc**フォルダーにあるソースコードを参照してください。

```
BOOL IsFocused() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="iskeydefined"></a>  CMFCAcceleratorKeyAssignCtrl::IsKeyDefined

[CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)オブジェクトでショートカットキーが定義されているかどうかを判断します。

```
BOOL IsKeyDefined() const;
```

### <a name="return-value"></a>戻り値

ショートカットキーを定義するキーの有効な組み合わせをユーザーが既に押している場合は0以外の値。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

ユーザーが`CMFCAcceleratorKeyAssignCtrl`オブジェクトに有効なショートカットキーを入力したかどうかを判断するには、この関数を使用します。 ショートカットキーが存在する場合は、 [CMFCAcceleratorKeyAssignCtrl:: GetAccel](#getaccel)メソッドを使用し`ACCEL`て、このショートカットキーに関連付けられている構造体を取得できます。

##  <a name="pretranslatemessage"></a>  CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage

詳細については、Visual Studio のインストール**の\\VC atlmfc\\\\src mfc**フォルダーにあるソースコードを参照してください。

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>パラメーター

から*pMsg*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="resetkey"></a>  CMFCAcceleratorKeyAssignCtrl::ResetKey

ショートカット キーをリセットします。

```
void ResetKey();
```

### <a name="remarks"></a>Remarks

関数は、エディットコントロールのテキストをクリアします。 これには、ユーザーが押したショートカットキーが含まれます。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCAcceleratorKey クラス](../../mfc/reference/cmfcacceleratorkey-class.md)
