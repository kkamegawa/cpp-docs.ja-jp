---
title: CMFCMaskedEdit クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCMaskedEdit
- AFXMASKEDEDIT/CMFCMaskedEdit
- AFXMASKEDEDIT/CMFCMaskedEdit::DisableMask
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableGetMaskedCharsOnly
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableMask
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableSelectByGroup
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableSetMaskedCharsOnly
- AFXMASKEDEDIT/CMFCMaskedEdit::GetWindowText
- AFXMASKEDEDIT/CMFCMaskedEdit::SetValidChars
- AFXMASKEDEDIT/CMFCMaskedEdit::SetWindowText
- AFXMASKEDEDIT/CMFCMaskedEdit::IsMaskedChar
helpviewer_keywords:
- CMFCMaskedEdit [MFC], DisableMask
- CMFCMaskedEdit [MFC], EnableGetMaskedCharsOnly
- CMFCMaskedEdit [MFC], EnableMask
- CMFCMaskedEdit [MFC], EnableSelectByGroup
- CMFCMaskedEdit [MFC], EnableSetMaskedCharsOnly
- CMFCMaskedEdit [MFC], GetWindowText
- CMFCMaskedEdit [MFC], SetValidChars
- CMFCMaskedEdit [MFC], SetWindowText
- CMFCMaskedEdit [MFC], IsMaskedChar
ms.assetid: 13b1a645-2d5d-4c37-8599-16d5003f23a5
ms.openlocfilehash: c1dcf89811fa5225283cb5bec120d3bd2fdfb003
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410149"
---
# <a name="cmfcmaskededit-class"></a>CMFCMaskedEdit クラス

`CMFCMaskedEdit`クラスは、ユーザーの入力をマスクを検証し、テンプレートに従って検証結果を表示するマスク エディット コントロールをサポートしています。

## <a name="syntax"></a>構文

```
class CMFCMaskedEdit : public CEdit
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|`CMFCMaskedEdit::CMFCMaskedEdit`|既定のコンストラクターです。|
|`CMFCMaskedEdit::~CMFCMaskedEdit`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCMaskedEdit::DisableMask](#disablemask)|ユーザー入力の検証を無効にします。|
|[CMFCMaskedEdit::EnableGetMaskedCharsOnly](#enablegetmaskedcharsonly)|指定するかどうか、`GetWindowText`メソッドは、マスクされた文字のみを取得します。|
|[CMFCMaskedEdit::EnableMask](#enablemask)|編集コントロールのマスクを初期化します。|
|[CMFCMaskedEdit::EnableSelectByGroup](#enableselectbygroup)|マスク エディット コントロールがユーザー入力、またはすべてのユーザー入力の特定のグループを選択するかどうかを指定します。|
|[CMFCMaskedEdit::EnableSetMaskedCharsOnly](#enablesetmaskedcharsonly)|マスク全体またはテキストを検証しているだけで、文字をマスクするかどうかを指定します。|
|`CMFCMaskedEdit::GetThisClass`|ポインターを取得する、framework によって使用される、 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)このクラス型に関連付けられているオブジェクト。|
|[CMFCMaskedEdit::GetWindowText](#getwindowtext)|マスク エディット コントロールからテキストを検証するを取得します。|
|[CMFCMaskedEdit::SetValidChars](#setvalidchars)|ユーザーが入力できる有効な文字の文字列を指定します。|
|[CMFCMaskedEdit::SetWindowText](#setwindowtext)|マスク エディット コントロールで、プロンプトが表示されます。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CMFCMaskedEdit::IsMaskedChar](#ismaskedchar)|対応するマスク文字に対して指定した文字を検証するためにフレームワークによって呼び出されます。|

## <a name="remarks"></a>Remarks

使用する次の手順を実行、`CMFCMaskedEdit`アプリケーションで制御します。

1. 埋め込みを`CMFCMaskedEdit`ウィンドウ クラスのオブジェクト。

2. 呼び出す、 [CMFCMaskedEdit::EnableMask](#enablemask)マスクを指定します。

3. 呼び出す、 [CMFCMaskedEdit::SetValidChars](#setvalidchars)有効な文字の一覧を指定します。

4. 呼び出す、 [CMFCMaskedEdit::SetWindowText](#setwindowtext)マスク エディット コントロールの既定のテキストを指定します。

5. 呼び出す、 [CMFCMaskedEdit::GetWindowText](#getwindowtext)検証済みのテキストを取得します。

マスク、有効な文字、および既定のテキストを初期化するために 1 つまたは複数のメソッドを呼び出すことはありません、標準の編集コントロールの動作と同様に、マスク エディット コントロールが動作します。

## <a name="example"></a>例

次の例では、マスク (電話番号など) を使用して設定する方法、`EnableMask`マスク エディット コントロールのマスクを作成する方法、 `SetValidChars` 、ユーザーが入力できる、有効な文字の文字列を指定する方法`SetWindowText`マスクのプロンプトを表示する方法は、コントロールを編集します。 この例は、[新しいコントロール サンプル](../../overview/visual-cpp-samples.md)します。

[!code-cpp[NVC_MFC_NewControls#11](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#12](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

[CMFCMaskedEdit](../../mfc/reference/cmfcmaskededit-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxmaskededit.h

##  <a name="disablemask"></a>  CMFCMaskedEdit::DisableMask

ユーザー入力の検証を無効にします。

```
void DisableMask();
```

### <a name="remarks"></a>Remarks

ユーザー入力の検証が無効になっている場合、標準的な編集コントロールと同様に、マスク エディット コントロールが動作します。

##  <a name="enablegetmaskedcharsonly"></a>  CMFCMaskedEdit::EnableGetMaskedCharsOnly

指定するかどうか、`GetWindowText`メソッドは、マスクされた文字のみを取得します。

```
void EnableGetMaskedCharsOnly(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>パラメーター

*bEnable*<br/>
[in]指定する場合は TRUE、 [CMFCMaskedEdit::GetWindowText](#getwindowtext)メソッドの取得のみ; 文字をマスクします。メソッドがテキスト全体を取得することを指定する場合は FALSE。 既定値は TRUE です。

### <a name="remarks"></a>Remarks

マスク文字の取得を有効にするのにには、このメソッドを使用します。 (425) 555-0187 など、電話番号に対応するマスク エディット コントロールを作成します。 呼び出す場合、`GetWindowText`メソッドでは、「4255550187」返します。 マスクの文字の取得を無効にした場合、`GetWindowText`メソッド「(425) 555-0187」などのエディット コントロールに表示されるテキストを返します。

##  <a name="enablemask"></a>  CMFCMaskedEdit::EnableMask

編集コントロールのマスクを初期化します。

```
void EnableMask(
    LPCTSTR lpszMask,
    LPCTSTR lpszInputTemplate,
    TCHAR chMaskInputTemplate=_T('_'),
    LPCTSTR lpszValid=NULL);
```

### <a name="parameters"></a>パラメーター

*lpszMask*<br/>
[in]ユーザー入力のそれぞれの位置に表示できる文字の種類を指定するマスク文字列。 長さ、 *lpszInputTemplate*と*lpszMask*パラメーター文字列は同じである必要があります。 マスク文字の詳細については、「解説」を参照してください。

*lpszInputTemplate*<br/>
[in]ユーザー入力の各位置でリテラル文字を指定するマスク テンプレート文字列を表示できます。 文字のプレース ホルダーとしてアンダー スコア文字 ('_') を使用します。 長さ、 *lpszInputTemplate*と*lpszMask*パラメーター文字列は同じである必要があります。

*chMaskInputTemplate*<br/>
[in]既定の文字で、フレームワーク、ユーザーの入力に無効な各文字の代わりに使用します。 このパラメーターの既定値は、アンダー スコア (_) です。

*lpszValid*<br/>
[in]有効な文字のセットを含む文字列。 NULL では、すべての文字が有効であることを示します。 このパラメーターの既定値は、NULL です。

### <a name="remarks"></a>Remarks

マスク エディット コントロールのマスクを作成するのにには、このメソッドを使用します。 派生クラスを`CMFCMaskedEdit`クラスし、オーバーライド、 [CMFCMaskedEdit::IsMaskedChar](#ismaskedchar)カスタム マスク処理に独自のコードを使用する方法。

次の表は、既定のマスク文字を一覧表示します。

|マスク文字|定義|
|--------------------|----------------|
|D|数字です。|
|d|数字またはスペース。|
|+|プラス記号 ('+ ')、マイナス ('-')、または領域です。|
|C|アルファベット文字。|
|c|アルファベット文字またはスペース。|
|A|英数字文字です。|
|a|英数字文字またはスペース。|
|*|印刷可能な文字です。|

##  <a name="enableselectbygroup"></a>  CMFCMaskedEdit::EnableSelectByGroup

マスク エディット コントロールに特定のグループの選択の入力、またはすべての入力をユーザーができるかどうかを指定します。

```
void EnableSelectByGroup(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>パラメーター

*bEnable*<br/>
[in]グループのみを選択する場合は TRUEテキスト全体を選択する場合は FALSE。 既定値は TRUE です。

### <a name="remarks"></a>Remarks

マスク エディット コントロールにユーザー グループまたはテキスト全体を選択できるかどうかを指定するのにには、この関数を使用します。

既定では、グループでの選択が有効にします。 この場合、ユーザーは、有効な文字の連続するグループのみを選択できます。

たとえば、電話番号の検証を次のマスク エディット コントロールを使用する可能性があります。

```cpp
m_wndMaskEdit.EnableMask(
    _T(" ddd  ddd dddd"),  // Mask string
    _T("(___) ___-____"),  // Template string
    _T(' '));              // Default char

m_wndMaskEdit.SetValidChars(NULL); // All characters are valid.

m_wndMaskEdit.SetWindowText(_T("(425) 555-0187")); // Prompt
```

グループでの選択が有効になっている場合、ユーザーはのみ「425」、「555」または「0187」文字列のグループを取得できます。 グループの選択が無効になっている場合、ユーザーが電話番号のテキスト全体を取得できます。"(425) 555-0187"。

##  <a name="enablesetmaskedcharsonly"></a>  CMFCMaskedEdit::EnableSetMaskedCharsOnly

指定しますまたはマスク全体に対してマスク文字だけにテキストを検証するかどうか。

```
void EnableSetMaskedCharsOnly(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>パラメーター

*bEnable*<br/>
[in]ユーザーだけで文字をマスクに対する入力を検証する場合は TRUEマスク全体の検証に使用する場合は FALSE。 既定値は TRUE です。

##  <a name="getwindowtext"></a>  CMFCMaskedEdit::GetWindowText

マスク エディット コントロールからテキストを検証するを取得します。

```
int GetWindowText(
    LPTSTR lpszStringBuf,
    int nMaxCount) const;

void GetWindowText(CString& rstrString) const;
```

### <a name="parameters"></a>パラメーター

*lpszStringBuf*<br/>
[out]エディット コントロールからテキストを受け取るバッファーへのポインター。

*nMaxCount*<br/>
[in]受信する文字の最大数。

*rstrString*<br/>
[out]エディット コントロールからテキストを受け取る文字列オブジェクトへの参照。

### <a name="return-value"></a>戻り値

メソッドのオーバー ロードが先頭にコピーされる文字列のバイト数を返します、 *lpszStringBuf*パラメーター バッファー; マスク エディット コントロールにテキストがあるない場合は 0。

### <a name="remarks"></a>Remarks

このメソッドは、マスク エディット コントロールからテキストをコピー、 *lpszStringBuf*バッファーまたは*rstrString*文字列。

このメソッドを再定義[CWnd::GetWindowText](../../mfc/reference/cwnd-class.md#getwindowtext)します。

##  <a name="ismaskedchar"></a>  CMFCMaskedEdit::IsMaskedChar

対応するマスク文字に対して指定した文字を検証するためにフレームワークによって呼び出されます。

```
virtual BOOL IsMaskedChar(
    TCHAR chChar,
    TCHAR chMaskChar) const;
```

### <a name="parameters"></a>パラメーター

*chChar*<br/>
[in]検証する文字。

*chMaskChar*<br/>
[in]マスク文字列から対応する文字。

### <a name="return-value"></a>戻り値

TRUE の場合、 *chChar*パラメーターで許可されている文字の型が、 *chMaskChar*パラメーター場合は FALSE。

### <a name="remarks"></a>Remarks

ご自身での入力文字を検証するには、このメソッドをオーバーライドします。 マスク文字の詳細については、次を参照してください。、 [CMFCMaskedEdit::EnableMask](#enablemask)メソッド。

##  <a name="setvalidchars"></a>  CMFCMaskedEdit::SetValidChars

ユーザーが入力できる有効な文字の文字列を指定します。

```
void SetValidChars(LPCTSTR lpszValid=NULL);
```

### <a name="parameters"></a>パラメーター

*lpszValid*<br/>
[in]有効な入力文字のセットを含む文字列。 NULL では、すべての文字が有効であることを意味します。 このパラメーターの既定値は、NULL です。

### <a name="remarks"></a>Remarks

このメソッドを使用すると、有効な文字の一覧を定義します。 この一覧に入力文字がない場合マスク エディット コントロールがないにそのまま使用されます。

次のコード例では、16 進数のみを受け入れます。

```cpp
//Mask: 0xFFFF
m_wndMaskEdit.EnableMask(
    _T(" AAAA"),                // The mask string.
    _T("0x____"),               // The literal template string.
    _T('_'));                   // The default character that
                                // replaces the backspace character.
// Valid string characters
m_wndMaskEdit.SetValidChars(_T("1234567890ABCDEFabcdef"));m_wndMaskEdit.SetWindowText(_T("0x01AF"));
```

##  <a name="setwindowtext"></a>  CMFCMaskedEdit::SetWindowText

マスク エディット コントロールで、プロンプトが表示されます。

```
void SetWindowText(LPCTSTR lpszString);
```

### <a name="parameters"></a>パラメーター

*lpszString*<br/>
[in]プロンプトとして使用される null で終わる文字列へのポインター。

### <a name="remarks"></a>Remarks

このメソッドは、コントロールのテキストを設定します。

このメソッドを再定義[とき](../../mfc/reference/cwnd-class.md#setwindowtext)します。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CEdit クラス](../../mfc/reference/cedit-class.md)
