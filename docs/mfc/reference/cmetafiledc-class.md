---
title: CMetaFileDC クラス
ms.date: 11/04/2016
f1_keywords:
- CMetaFileDC
- AFXEXT/CMetaFileDC
- AFXEXT/CMetaFileDC::CMetaFileDC
- AFXEXT/CMetaFileDC::Close
- AFXEXT/CMetaFileDC::CloseEnhanced
- AFXEXT/CMetaFileDC::Create
- AFXEXT/CMetaFileDC::CreateEnhanced
helpviewer_keywords:
- CMetaFileDC [MFC], CMetaFileDC
- CMetaFileDC [MFC], Close
- CMetaFileDC [MFC], CloseEnhanced
- CMetaFileDC [MFC], Create
- CMetaFileDC [MFC], CreateEnhanced
ms.assetid: ffce60fa-4181-4d46-9832-25e46fad4db4
ms.openlocfilehash: 61e8442c085a5be0a7266409daf973bf63f52a7f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505507"
---
# <a name="cmetafiledc-class"></a>CMetaFileDC クラス

イメージやテキストを自由に作成するための一連のグラフィック デバイス インターフェイス (GDI) コマンドを含む Windows のメタファイルを実装します。

## <a name="syntax"></a>構文

```
class CMetaFileDC : public CDC
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMetaFileDC:: CMetaFileDC](#cmetafiledc)|`CMetaFileDC` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMetaFileDC:: Close](#close)|デバイスコンテキストを閉じ、メタファイルハンドルを作成します。|
|[CMetaFileDC:: CloseEnhanced](#closeenhanced)|拡張メタファイルデバイスコンテキストを閉じ、拡張メタファイルハンドルを作成します。|
|[CMetaFileDC:: Create](#create)|Windows メタファイルデバイスコンテキストを作成し、 `CMetaFileDC`オブジェクトにアタッチします。|
|[CMetaFileDC::CreateEnhanced](#createenhanced)|拡張形式メタファイルのメタファイルデバイスコンテキストを作成します。|

## <a name="remarks"></a>Remarks

Windows メタファイルを実装するには、 `CMetaFileDC`最初にオブジェクトを作成します。 コンストラクターを呼び出し、[Create](#create) member 関数を呼び出します。これにより、Windows メタファイルデバイスコンテキストが作成さ`CMetaFileDC`れ、オブジェクトにアタッチされます。`CMetaFileDC`

次に、 `CMetaFileDC`オブジェクトを再生する CDC GDI コマンドのシーケンスを送信します。 出力を作成する GDI コマンド ( `MoveTo`や`LineTo`など) のみを使用できます。

目的のコマンドをメタファイルに送信した後、 `Close`メンバー関数を呼び出します。これにより、メタファイルデバイスコンテキストが閉じられ、メタファイルハンドルが返されます。 次に、 `CMetaFileDC`オブジェクトを破棄します。

[CDC::P](../../mfc/reference/cdc-class.md#playmetafile) $ metafile はメタファイルハンドルを使用して、メタファイルを繰り返し再生できます。 メタファイルは、ファイルをディスクにコピーする[Copymetafile](/windows/win32/api/wingdi/nf-wingdi-copymetafilew)などの Windows 関数によって操作することもできます。

メタファイルが不要になった場合は、 [DeleteMetaFile](/windows/win32/api/wingdi/nf-wingdi-deletemetafile) Windows 関数を使用して、メモリから削除します。

また、オブジェクトを実装`CMetaFileDC`して、出力呼び出しと、など`GetTextExtent`の属性 GDI 呼び出しの両方を処理できるようにすることもできます。 このようなメタファイルの方が柔軟性が高く、一般的な GDI コードを再利用しやすくなります。これは、多くの場合、出力と属性の呼び出しの組み合わせで構成されます。 クラス`CMetaFileDC`は、CDC からとと`m_hDC` `m_hAttribDC`いう2つのデバイスコンテキストを継承します。 デバイス`m_hDC`コンテキストはすべての[cdc](../../mfc/reference/cdc-class.md) gdi 出力呼び出しを処理`m_hAttribDC`し、デバイスコンテキストはすべての cdc gdi 属性呼び出しを処理します。 通常、これら2つのデバイスコンテキストは同じデバイスを参照します。 の`CMetaFileDC`場合、既定では、属性 DC は NULL に設定されます。

画面、プリンター、またはメタファイル以外のデバイスをポイントする2番目のデバイスコンテキストを作成し、 `SetAttribDC`メンバー関数を呼び出して、新しいデバイス`m_hAttribDC`コンテキストをに関連付けます。 情報の GDI 呼び出しは、新しい`m_hAttribDC`に送られるようになります。 出力 GDI 呼び出しは、メタ`m_hDC`ファイルを表すに送られます。

の`CMetaFileDC`詳細については、「[デバイスコンテキスト](../../mfc/device-contexts.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CMetaFileDC`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxext.h

##  <a name="close"></a>  CMetaFileDC::Close

メタファイルデバイスコンテキストを閉じ、 [CDC::P](../../mfc/reference/cdc-class.md#playmetafile)の $ metafile メンバー関数を使用してメタファイルを再生するために使用できる Windows メタファイルハンドルを作成します。

```
HMETAFILE Close();
```

### <a name="return-value"></a>戻り値

関数が成功した場合は有効な HMETAFILE。それ以外の場合は NULL。

### <a name="remarks"></a>Remarks

Windows メタファイルハンドルは、 [Copymetafile](/windows/win32/api/wingdi/nf-wingdi-copymetafilew)などの windows 関数でメタファイルを操作するためにも使用できます。

Windows [DeleteMetaFile](/windows/win32/api/wingdi/nf-wingdi-deletemetafile)関数を呼び出して、使用後にメタファイルを削除します。

##  <a name="closeenhanced"></a>CMetaFileDC:: CloseEnhanced

拡張メタファイルデバイスコンテキストを閉じ、拡張形式メタファイルを識別するハンドルを返します。

```
HENHMETAFILE CloseEnhanced();
```

### <a name="return-value"></a>戻り値

成功した場合は、拡張メタファイルのハンドル。それ以外の場合は NULL。

### <a name="remarks"></a>Remarks

アプリケーションでは、この関数によって返される拡張メタファイルハンドルを使用して、次のタスクを実行できます。

- 拡張メタファイルに格納されている画像を表示する

- 拡張メタファイルのコピーの作成

- 拡張メタファイル内の個々のレコードを列挙、編集、またはコピーする

- 拡張メタファイルヘッダーからメタファイルの内容のオプションの説明を取得します。

- 拡張メタファイルヘッダーのコピーを取得します。

- 拡張メタファイルのバイナリコピーを取得する

- オプションのパレットの色を列挙する

- 拡張形式メタファイルを Windows 形式のメタファイルに変換します。

アプリケーションが拡張メタファイルハンドルを必要としなくなった場合は、Win32 `DeleteEnhMetaFile`関数を呼び出すことによってハンドルを解放する必要があります。

##  <a name="cmetafiledc"></a>  CMetaFileDC::CMetaFileDC

2つ`CMetaFileDC`の手順でオブジェクトを構築します。

```
CMetaFileDC();
```

### <a name="remarks"></a>Remarks

まず、を`CMetaFileDC`呼び出し、を`Create`呼び出します。これにより、Windows メタファイルデバイスコンテキストが`CMetaFileDC`作成され、オブジェクトにアタッチされます。

##  <a name="create"></a>  CMetaFileDC::Create

2つ`CMetaFileDC`の手順でオブジェクトを構築します。

```
BOOL Create(LPCTSTR lpszFilename = NULL);
```

### <a name="parameters"></a>パラメーター

*lpszFilename*<br/>
は、null で終わる文字列を指します。 作成するメタファイルのファイル名を指定します。 *Lpszfilename*が NULL の場合、新しいメモリ内メタファイルが作成されます。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

まず、コンストラクター `CMetaFileDC`を呼び出し、次に`Create`を呼び出します。これにより、Windows メタファイルデバイスコンテキスト`CMetaFileDC`が作成され、オブジェクトにアタッチされます。

##  <a name="createenhanced"></a>  CMetaFileDC::CreateEnhanced

拡張形式メタファイルのデバイスコンテキストを作成します。

```
BOOL CreateEnhanced(
    CDC* pDCRef,
    LPCTSTR lpszFileName,
    LPCRECT lpBounds,
    LPCTSTR lpszDescription);
```

### <a name="parameters"></a>パラメーター

*pDCRef*<br/>
拡張メタファイルの参照デバイスを識別します。

*lpszFileName*<br/>
は、null で終わる文字列を指します。 作成する拡張メタファイルのファイル名を指定します。 このパラメーターが NULL の場合、拡張メタファイルはメモリベースであり、オブジェクトが破棄されたとき、また`DeleteEnhMetaFile`は Win32 関数が呼び出されたときに、その内容が失われます。

*lpBounds*<br/>
拡張メタファイルに格納される画像の HIMETRIC 単位 (0.01 mm 単位) の大きさを指定する[RECT](/windows/win32/api/windef/ns-windef-rect)データ構造体または[CRect](../../atl-mfc-shared/reference/crect-class.md)オブジェクトを指します。

*lpszDescription*<br/>
画像を作成したアプリケーションの名前と画像のタイトルを指定する、0で終わる文字列を指します。

### <a name="return-value"></a>戻り値

成功した場合は、拡張メタファイルのデバイスコンテキストのハンドル。それ以外の場合は NULL。

### <a name="remarks"></a>Remarks

この DC は、デバイスに依存しない画像を格納するために使用できます。

Windows では、 *Pdcref*パラメーターによって識別される参照デバイスを使用して、画像がもともと表示されていたデバイスの解像度と単位を記録します。 *Pdcref*パラメーターが NULL の場合、参照に現在の表示デバイスが使用されます。

`RECT` *LpBounds*パラメーターが指すデータ構造体の左側と上位のメンバーは、それぞれ right メンバーと bottom メンバーより小さくする必要があります。 四角形の端に沿った点が画像に含まれます。 *LpBounds*が NULL の場合、グラフィックスデバイスインターフェイス (GDI) は、アプリケーションによって描画された画像を囲むことができる最小の四角形の大きさを計算します。 可能な場合は、 *lpBounds*パラメーターを指定する必要があります。

*Lpszdescription*パラメーターが指す文字列には、アプリケーション名と画像名の間に null 文字が含まれている必要があり、2つの null 文字で終了する必要があります (例: "XYZ Graphics Editor\0Bald Eagle\0\0")。 \ 0 はを表します。null 文字。 *Lpszdescription*が NULL の場合は、拡張メタファイルヘッダーに対応するエントリがありません。

アプリケーションでは、この関数によって作成された DC を使用して、拡張メタファイルにグラフィックス画像を格納します。 この DC を識別するハンドルを任意の GDI 関数に渡すことができます。

アプリケーションは、拡張メタファイルに画像を格納した後、 `CDC::PlayMetaFile`関数を呼び出して、任意の出力デバイスに画像を表示できます。 画像を表示する場合、 *lpBounds*パラメーターによって示される四角形と、参照デバイスからの解像度データを使用して、画像の配置とスケーリングを行います。 この関数によって返されるデバイスコンテキストには、新しい DC に関連付けられているのと同じ既定の属性が含まれています。

アプリケーションでは、拡張`GetWinMetaFileBits`メタファイルを古い Windows メタファイル形式に変換するために、Win32 関数を使用する必要があります。

拡張メタファイルのファイル名には、を使用する必要があります。EMF 拡張。

## <a name="see-also"></a>関連項目

[CDC クラス](../../mfc/reference/cdc-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)
