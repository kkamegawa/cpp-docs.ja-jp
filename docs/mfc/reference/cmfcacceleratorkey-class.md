---
title: CMFCAcceleratorKey クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::Format
- AFXACCELERATORKEY/CMFCAcceleratorKey::SetAccelerator
helpviewer_keywords:
- CMFCAcceleratorKey [MFC], CMFCAcceleratorKey
- CMFCAcceleratorKey [MFC], Format
- CMFCAcceleratorKey [MFC], SetAccelerator
ms.assetid: d140fbf7-23db-45ea-a63e-414a5ec7b3d5
ms.openlocfilehash: 6a99ad00a43ac7912320ee469d542b6bf9cca3de
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403959"
---
# <a name="cmfcacceleratorkey-class"></a>CMFCAcceleratorKey クラス

仮想キーのマッピングおよび書式設定を実装するヘルパー クラス。

## <a name="syntax"></a>構文

```
class CMFCAcceleratorKey : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCAcceleratorKey::CMFCAcceleratorKey](#cmfcacceleratorkey)|`CMFCAcceleratorKey` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCAcceleratorKey::Format](#format)|ACCEL 構造体のビジュアル表現を変換します。|
|[CMFCAcceleratorKey::SetAccelerator](#setaccelerator)|ショートカット キーの設定、`CMFCAcceleratorKey`オブジェクト。|

## <a name="remarks"></a>Remarks

アクセラレータ キーは、ショートカット キーとも呼ばれます。 ユーザーが入力するキーボード ショートカットを表示する場合、 [CMFCAcceleratorKeyAssignCtrl クラス](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)マップのショートカット キー、Alt + Shift + S など"Alt + Shift + S"などのカスタム テキスト形式にします。 各`CMFCAcceleratorKey`オブジェクトがテキスト形式を単一のショートカット キーをマップします。

ショートカット キーとアクセラレータ テーブルを使用する方法の詳細については、次を参照してください。 [CKeyboardManager クラス](../../mfc/reference/ckeyboardmanager-class.md)します。

## <a name="example"></a>例

次の例は、構築する方法を示します、`CMFCAcceleratorKey`オブジェクトと、使用する方法、`Format`メソッド。

[!code-cpp[NVC_MFC_RibbonApp#30](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkey-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CMFCAcceleratorKey`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxacceleratorkey.h

##  <a name="cmfcacceleratorkey"></a>  CMFCAcceleratorKey::CMFCAcceleratorKey

構築、 [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md)オブジェクト。

```
CMFCAcceleratorKey();
CMFCAcceleratorKey(LPACCEL lpAccel);
```

### <a name="parameters"></a>パラメーター

*lpAccel*<br/>
[in]ショートカット キーへのポインター。

### <a name="remarks"></a>Remarks

作成するときに、ショートカット キーを指定しないかどうか、`CMFCAccleratorKey`を使用して、 [CMFCAcceleratorKey::SetAccelerator](#setaccelerator)のショートカット キーを関連付ける方法、`CMFCAcceleratorKey`オブジェクト。

##  <a name="format"></a>  CMFCAcceleratorKey::Format

ACCEL 構造体を関連付けられている文字列値を変換します。

```
void Format(CString& str) const;
```

### <a name="parameters"></a>パラメーター

*str*<br/>
[out]参照を`CString`メソッドが変換されたショートカット キーを書き込むオブジェクト。

### <a name="remarks"></a>Remarks

このメソッドは、関連付けられているショートカット キーの文字列形式を取得します。 文字列形式を設定することができます、 [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md)オブジェクト コンス トラクターまたはメソッドのいずれかを使用して[CMFCAcceleratorKey::SetAccelerator](#setaccelerator)します。

##  <a name="setaccelerator"></a>  CMFCAcceleratorKey::SetAccelerator

ショートカット キーの設定、 [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md)オブジェクト。

```
void SetAccelerator(LPACCEL lpAccel);
```

### <a name="parameters"></a>パラメーター

*lpAccel*<br/>
[in]ショートカット キーへのポインター。

### <a name="remarks"></a>Remarks

このメソッドのショートカット キーの設定を使用して、`CMFCAcceleratorKey`の作成時に、ショートカット キーを指定しなかったかどうか、`CMFCAcceleratorKey`します。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CKeyboardManager クラス](../../mfc/reference/ckeyboardmanager-class.md)
