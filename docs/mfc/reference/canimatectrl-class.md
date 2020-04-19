---
title: CAnimateCtrl クラス
ms.date: 11/04/2016
f1_keywords:
- CAnimateCtrl
- AFXCMN/CAnimateCtrl
- AFXCMN/CAnimateCtrl::CAnimateCtrl
- AFXCMN/CAnimateCtrl::Close
- AFXCMN/CAnimateCtrl::Create
- AFXCMN/CAnimateCtrl::CreateEx
- AFXCMN/CAnimateCtrl::IsPlaying
- AFXCMN/CAnimateCtrl::Open
- AFXCMN/CAnimateCtrl::Play
- AFXCMN/CAnimateCtrl::Seek
- AFXCMN/CAnimateCtrl::Stop
helpviewer_keywords:
- CAnimateCtrl [MFC], CAnimateCtrl
- CAnimateCtrl [MFC], Close
- CAnimateCtrl [MFC], Create
- CAnimateCtrl [MFC], CreateEx
- CAnimateCtrl [MFC], IsPlaying
- CAnimateCtrl [MFC], Open
- CAnimateCtrl [MFC], Play
- CAnimateCtrl [MFC], Seek
- CAnimateCtrl [MFC], Stop
ms.assetid: 5e8eb1bd-96b7-47b8-8de2-6bcbb3cc299b
ms.openlocfilehash: 18adead999f26768ae669d3a829b557bf9632a29
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177446"
---
# <a name="canimatectrl-class"></a>CAnimateCtrl クラス

Windows コモン アニメーション コントロールの機能が用意されています。

## <a name="syntax"></a>構文

```
class CAnimateCtrl : public CWnd
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CAnimateCtrl:: CAnimateCtrl](#canimatectrl)|`CAnimateCtrl` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAnimateCtrl:: Close](#close)|AVI クリップを閉じます。|
|[CAnimateCtrl::Create](#create)|アニメーションコントロールを作成し、 `CAnimateCtrl`オブジェクトにアタッチします。|
|[CAnimateCtrl::CreateEx](#createex)|指定した Windows 拡張スタイルを使用してアニメーションコントロールを作成し`CAnimateCtrl` 、それをオブジェクトにアタッチします。|
|[CAnimateCtrl:: IsPlaying](#isplaying)|オーディオビデオインターリーブ (AVI) クリップが再生中かどうかを示します。|
|[CAnimateCtrl::Open](#open)|ファイルまたはリソースから AVI クリップを開き、最初のフレームを表示します。|
|[CAnimateCtrl::P のレイアウト](#play)|サウンドを使用せずに AVI クリップを再生します。|
|[CAnimateCtrl:: Seek](#seek)|AVI クリップの選択された1フレームを表示します。|
|[CAnimateCtrl:: Stop](#stop)|AVI クリップの再生を停止します。|

## <a name="remarks"></a>Remarks

このコントロール (および`CAnimateCtrl`クラス) は、windows 95、windows 98、および windows NT バージョン3.51 以降で実行されているプログラムに対してのみ使用できます。

アニメーションコントロールとは、AVI (Audio Video Interleaved) 形式 (標準の Windows ビデオ/オーディオ形式) でクリップを表示する四角形のウィンドウです。 AVI クリップは、ムービーのような一連のビットマップフレームです。

アニメーションコントロールは、単純な AVI クリップだけを再生できます。 具体的には、アニメーションコントロールによって再生されるクリップは、次の要件を満たしている必要があります。

- 1つのビデオストリームだけが必要であり、少なくとも1つのフレームが必要です。

- ファイルには最大で2つのストリームが存在する場合があります (通常、他のストリームはオーディオストリームですが、アニメーションコントロールはオーディオ情報を無視します)。

- クリップは、圧縮されていないか、RLE8 圧縮を使用して圧縮されている必要があります。

- ビデオストリームでは、パレットの変更は許可されていません。

Avi のクリップは、avi リソースとしてアプリケーションに追加することも、アプリケーションに別の AVI ファイルとして添付することもできます。

AVI クリップが表示されている間、スレッドは実行を続けているため、アニメーションコントロールの一般的な用途の1つは、時間のかかる操作中にシステムの動作を示すことです。 たとえば、ファイルエクスプローラーの [検索] ダイアログボックスには、システムがファイルを検索するときに、移動中の虫眼鏡が表示されます。

ダイアログボックス内で`CAnimateCtrl` 、またはダイアログエディターを使用してダイアログリソースからオブジェクトを作成した場合、ユーザーがダイアログボックスを閉じたときに自動的に破棄されます。

ウィンドウ内に`CAnimateCtrl`オブジェクトを作成する場合は、そのオブジェクトを破棄する必要がある場合があります。 スタックに`CAnimateCtrl`オブジェクトを作成すると、そのオブジェクトは自動的に破棄されます。 新しい関数を使用`CAnimateCtrl`してヒープにオブジェクトを作成する場合は、オブジェクトに対して**delete**を呼び出して破棄する必要があります。 から`CAnimateCtrl`新しいクラスを派生させ、そのクラスにメモリを割り当てる場合は、 `CAnimateCtrl`デストラクターをオーバーライドして割り当てを破棄します。

の使用方法`CAnimateCtrl`の詳細については、「 [Controls](../../mfc/controls-mfc.md) and [using CAnimateCtrl](../../mfc/using-canimatectrl.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CAnimateCtrl`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxcmn.h

##  <a name="canimatectrl"></a>CAnimateCtrl:: CAnimateCtrl

`CAnimateCtrl` オブジェクトを構築します。

```
CAnimateCtrl();
```

### <a name="remarks"></a>Remarks

作成したオブジェクトに対して他の操作を実行する前に、 [create](#create) member 関数を呼び出す必要があります。

### <a name="example"></a>例

[!code-cpp[NVC_MFCControlLadenDialog#56](../../mfc/codesnippet/cpp/canimatectrl-class_1.cpp)]

##  <a name="close"></a>CAnimateCtrl:: Close

アニメーションコントロールで以前に開いていた AVI クリップ (存在する場合) を閉じ、メモリから削除します。

```
BOOL Close();
```

### <a name="return-value"></a>戻り値

成功した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="example"></a>例

  [CAnimateCtrl:: CAnimateCtrl](#canimatectrl)の例を参照してください。

##  <a name="create"></a>  CAnimateCtrl::Create

アニメーションコントロールを作成し、 `CAnimateCtrl`オブジェクトにアタッチします。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>パラメーター

*dwStyle*<br/>
アニメーションコントロールのスタイルを指定します。 後述の「解説」で説明されている windows スタイルと、Windows SDK の「[アニメーションコントロールスタイル](/windows/win32/Controls/animation-control-styles)」で説明されているアニメーションコントロールスタイルの任意の組み合わせを適用します。

*rect*<br/>
アニメーションコントロールの位置とサイズを指定します。 これは、 [CRect](../../atl-mfc-shared/reference/crect-class.md)オブジェクトまたは[RECT](/windows/win32/api/windef/ns-windef-rect)構造体のいずれかになります。

*pParentWnd*<br/>
アニメーションコントロールの親ウィンドウ (通常は`CDialog`) を指定します。 NULL にすることはできません。

*nID*<br/>
アニメーションコントロールの ID を指定します。

### <a name="return-value"></a>戻り値

成功した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

を作成する`CAnimateCtrl`には、2つの手順を実行します。 まず、コンストラクターを呼び出し、次にを`Create`呼び出します。これにより、アニメーションコントロールが作成`CAnimateCtrl`され、オブジェクトにアタッチされます。

次の[ウィンドウスタイル](../../mfc/reference/styles-used-by-mfc.md#window-styles)をアニメーションコントロールに適用します。

- 常に WS_CHILD

- WS_VISIBLE 通常

- WS_DISABLED はまれ

アニメーションコントロールで拡張 windows スタイルを使用する場合は、ではなく`Create` [CreateEx](#createex) を呼び出します。

上に示したウィンドウスタイルに加えて、1つまたは複数のアニメーションコントロールスタイルをアニメーションコントロールに適用することもできます。 [アニメーションコントロールスタイル](/windows/win32/Controls/animation-control-styles)の詳細については、Windows SDK を参照してください。

### <a name="example"></a>例

  [CAnimateCtrl:: CAnimateCtrl](#canimatectrl)の例を参照してください。

##  <a name="createex"></a>CAnimateCtrl:: CreateEx

コントロール (子ウィンドウ) を作成し、 `CAnimateCtrl`オブジェクトに関連付けます。

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>パラメーター

*dwExStyle*<br/>
作成するコントロールの拡張スタイルを指定します。 拡張 Windows スタイルの一覧については、Windows SDK の[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)の*dwexstyle*パラメーターを参照してください。

*dwStyle*<br/>
アニメーションコントロールのスタイルを指定します。 Windows SDK の「[アニメーションコントロールのスタイル](/windows/win32/Controls/animation-control-styles)」で説明されている、ウィンドウとアニメーションのコントロールスタイルを任意に組み合わせて適用します。

*rect*<br/>
*PParentWnd*のクライアント座標で、作成されるウィンドウのサイズと位置を記述する[RECT](/previous-versions/dd162897\(v=vs.85\))構造体への参照。

*pParentWnd*<br/>
コントロールの親であるウィンドウへのポインター。

*nID*<br/>
コントロールの子ウィンドウ ID。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

Windows `CreateEx`拡張スタイルの先頭**WS_EX_** によって指定された拡張 windows スタイルを適用するには、[[作成](#create)] ではなくを使用します。

##  <a name="isplaying"></a>  CAnimateCtrl::IsPlaying

オーディオビデオインターリーブ (AVI) クリップが再生中かどうかを示します。

```
BOOL IsPlaying() const;
```

### <a name="return-value"></a>戻り値

AVI クリップが再生中の場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[ACM_ISPLAYING](/windows/win32/Controls/acm-isplaying)メッセージを送信します。

##  <a name="open"></a>  CAnimateCtrl::Open

AVI クリップを開き、その最初のフレームを表示するには、この関数を呼び出します。

```
BOOL Open(LPCTSTR lpszFileName);
BOOL Open(UINT nID);
```

### <a name="parameters"></a>パラメーター

*lpszFileName*<br/>
Avi ファイルの名前または avi リソースの名前のいずれかを含む、null で終わる文字列へのオブジェクトまたはポインター。`CString` このパラメーターが NULL の場合、アニメーションコントロール (存在する場合) に対して以前に開かれていた AVI クリップがシステムによって閉じられます。

*nID*<br/>
AVI リソース識別子。 このパラメーターが NULL の場合、アニメーションコントロール (存在する場合) に対して以前に開かれていた AVI クリップがシステムによって閉じられます。

### <a name="return-value"></a>戻り値

成功した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

AVI リソースは、アニメーションコントロールを作成したモジュールから読み込まれます。

`Open`は、AVI クリップのサウンドをサポートしていません。サイレント AVI クリップのみを開くことができます。

アニメーションコントロールに`ACS_AUTOPLAY`スタイルが設定されている場合、アニメーションコントロールは、開いた直後にクリップの再生を自動的に開始します。 スレッドが実行を継続している間、バックグラウンドでクリップが再生され続けます。 クリップの再生が完了すると、自動的に繰り返されます。

アニメーションコントロールの`ACS_CENTER`スタイルがの場合、AVI クリップはコントロールの中央に配置され、コントロールのサイズは変更されません。 アニメーションコントロールに`ACS_CENTER`スタイルが設定されていない場合、avi クリップが avi クリップ内のイメージのサイズに開かれると、コントロールのサイズが変更されます。 コントロールの左上隅の位置は変更されず、コントロールのサイズのみになります。

アニメーションコントロールに`ACS_TRANSPARENT`スタイルが設定されている場合、最初のフレームは、アニメーションクリップで指定された背景色ではなく、透明な背景を使用して描画されます。

### <a name="example"></a>例

  [CAnimateCtrl:: CAnimateCtrl](#canimatectrl)の例を参照してください。

##  <a name="play"></a>  CAnimateCtrl::Play

アニメーションコントロールで AVI クリップを再生するには、この関数を呼び出します。

```
BOOL Play(
    UINT nFrom,
    UINT nTo,
    UINT nRep);
```

### <a name="parameters"></a>パラメーター

*n*<br/>
再生を開始するフレームの0から始まるインデックス。 値は65536未満である必要があります。 値0は、AVI クリップの最初のフレームから開始することを意味します。

*n*<br/>
再生が終了するフレームの0から始まるインデックス。 値は65536未満である必要があります。 値-1 は、AVI クリップの最後のフレームで終わることを意味します。

*nRep*<br/>
AVI クリップを再生する回数。 値-1 は、ファイルを無期限に再生することを意味します。

### <a name="return-value"></a>戻り値

成功した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

アニメーションコントロールは、スレッドの実行を継続しながら、バックグラウンドでクリップを再生します。 アニメーションコントロールにスタイルが`ACS_TRANSPARENT`設定されている場合は、アニメーションクリップで指定された背景色ではなく、透明な背景を使用して AVI クリップが再生されます。

### <a name="example"></a>例

  [CAnimateCtrl:: CAnimateCtrl](#canimatectrl)の例を参照してください。

##  <a name="seek"></a>  CAnimateCtrl::Seek

この関数を呼び出して、AVI クリップの1つのフレームを静的に表示します。

```
BOOL Seek(UINT nTo);
```

### <a name="parameters"></a>パラメーター

*n*<br/>
表示するフレームの0から始まるインデックス。 値は65536未満である必要があります。 値が0の場合は、AVI クリップの最初のフレームが表示されます。 値が-1 の場合は、AVI クリップの最後のフレームが表示されます。

### <a name="return-value"></a>戻り値

成功した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

アニメーションコントロールにスタイルが`ACS_TRANSPARENT`設定されている場合は、アニメーションクリップで指定された背景色ではなく、透明な背景を使用して AVI クリップが描画されます。

### <a name="example"></a>例

[CAnimateCtrl:: CAnimateCtrl](#canimatectrl)の例を参照してください。

##  <a name="stop"></a>CAnimateCtrl:: Stop

アニメーションコントロールで AVI クリップの再生を停止するには、この関数を呼び出します。

```
BOOL Stop();
```

### <a name="return-value"></a>戻り値

成功した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="example"></a>例

  [CAnimateCtrl:: CAnimateCtrl](#canimatectrl)の例を参照してください。

## <a name="see-also"></a>関連項目

[CWnd クラス](../../mfc/reference/cwnd-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CAnimateCtrl::Create](#create)<br/>
[ON_CONTROL](message-map-macros-mfc.md#on_control)
