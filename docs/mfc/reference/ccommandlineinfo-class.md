---
title: CCommandLineInfo クラス
ms.date: 11/04/2016
f1_keywords:
- CCommandLineInfo
- AFXWIN/CCommandLineInfo
- AFXWIN/CCommandLineInfo::CCommandLineInfo
- AFXWIN/CCommandLineInfo::ParseParam
- AFXWIN/CCommandLineInfo::m_bRunAutomated
- AFXWIN/CCommandLineInfo::m_bRunEmbedded
- AFXWIN/CCommandLineInfo::m_bShowSplash
- AFXWIN/CCommandLineInfo::m_nShellCommand
- AFXWIN/CCommandLineInfo::m_strDriverName
- AFXWIN/CCommandLineInfo::m_strFileName
- AFXWIN/CCommandLineInfo::m_strPortName
- AFXWIN/CCommandLineInfo::m_strPrinterName
- AFXWIN/CCommandLineInfo::m_strRestartIdentifier
helpviewer_keywords:
- CCommandLineInfo [MFC], CCommandLineInfo
- CCommandLineInfo [MFC], ParseParam
- CCommandLineInfo [MFC], m_bRunAutomated
- CCommandLineInfo [MFC], m_bRunEmbedded
- CCommandLineInfo [MFC], m_bShowSplash
- CCommandLineInfo [MFC], m_nShellCommand
- CCommandLineInfo [MFC], m_strDriverName
- CCommandLineInfo [MFC], m_strFileName
- CCommandLineInfo [MFC], m_strPortName
- CCommandLineInfo [MFC], m_strPrinterName
- CCommandLineInfo [MFC], m_strRestartIdentifier
ms.assetid: 3e313ddb-0a82-4991-87ac-a27feff4668c
ms.openlocfilehash: 6e4b535da00fdcecf4ce52fad696cb5d2bc55efa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408148"
---
# <a name="ccommandlineinfo-class"></a>CCommandLineInfo クラス

アプリケーション起動時のコマンド ライン解析を補助します。

## <a name="syntax"></a>構文

```
class CCommandLineInfo : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CCommandLineInfo::CCommandLineInfo](#ccommandlineinfo)|既定値を構築します`CCommandLineInfo`オブジェクト。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CCommandLineInfo::ParseParam](#parseparam)|個別のパラメーターを解析するには、このコールバックをオーバーライドします。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CCommandLineInfo::m_bRunAutomated](#m_brunautomated)|コマンドラインを示します`/Automation`オプションが見つかりました。|
|[CCommandLineInfo::m_bRunEmbedded](#m_brunembedded)|コマンドラインを示します`/Embedding`オプションが見つかりました。|
|[CCommandLineInfo::m_bShowSplash](#m_bshowsplash)|スプラッシュ スクリーンを表示するかどうかを示します。|
|[CCommandLineInfo::m_nShellCommand](#m_nshellcommand)|処理するシェル コマンドを示します。|
|[CCommandLineInfo::m_strDriverName](#m_strdrivername)|ドライバーを示す名前を印刷するには、シェル コマンドの場合それ以外の場合は空です。|
|[CCommandLineInfo::m_strFileName](#m_strfilename)|開くファイルまたは印刷されるファイル名を示します空の場合は、シェル コマンドは、新規または DDE です。|
|[CCommandLineInfo::m_strPortName](#m_strportname)|ポート名の場合、シェル コマンドを印刷するにはそれ以外の場合は空です。|
|[CCommandLineInfo::m_strPrinterName](#m_strprintername)|プリンターを示す名前を印刷するには、シェル コマンドの場合それ以外の場合は空です。|
|[CCommandLineInfo::m_strRestartIdentifier](#m_strrestartidentifier)|再起動マネージャーは、アプリケーションを再起動した場合、再起動マネージャーの一意の再起動の識別子を示します。|

## <a name="remarks"></a>Remarks

MFC アプリケーションがこのクラスでのローカル インスタンスを作成する通常の[InitInstance](../../mfc/reference/cwinapp-class.md#initinstance)アプリケーション オブジェクトの関数。 このオブジェクトに渡されます[CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline)、繰り返し呼び出す[ParseParam](#parseparam)を埋める、`CCommandLineInfo`オブジェクト。 `CCommandLineInfo`オブジェクトに渡されます[CWinApp::ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand)フラグ、コマンドライン引数を処理します。

このオブジェクトを使用すると、次のコマンド ライン オプションとパラメーターをカプセル化します。

|コマンド ライン引数|実行されたコマンド|
|----------------------------|----------------------|
|*app*|新しいファイルです。|
|*アプリ*ファイル名|ファイルを開く.|
|*アプリ*`/p`ファイル名|既定のプリンターにファイルを印刷します。|
|*アプリ*`/pt`ファイル名のプリンター ドライバーのポート|指定されたプリンターにファイルを印刷します。|
|*アプリ* `/dde`|起動し、DDE コマンドを待機します。|
|*アプリ* `/Automation`|OLE オートメーション サーバーとして起動します。|
|*アプリ* `/Embedding`|埋め込み OLE アイテムの編集を起動します。|
|*アプリ* `/Register`<br /><br /> *アプリ* `/Regserver`|登録タスクを実行するアプリケーションに通知します。|
|*アプリ* `/Unregister`<br /><br /> *アプリ* `/Unregserver`|任意の登録の解除タスクを実行するアプリケーションに通知します。|

新しいクラスを派生`CCommandLineInfo`他のフラグとパラメーター値を処理します。 オーバーライド[ParseParam](#parseparam)新しいフラグを処理します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CCommandLineInfo`

## <a name="requirements"></a>要件

**ヘッダー:** afxwin.h

##  <a name="ccommandlineinfo"></a>  CCommandLineInfo::CCommandLineInfo

このコンス トラクターを作成、`CCommandLineInfo`既定値を持つオブジェクト。

```
CCommandLineInfo();
```

### <a name="remarks"></a>Remarks

既定では、スプラッシュ スクリーンを表示 ( `m_bShowSplash=TRUE`) と、[ファイル] メニューで新しいコマンドを実行する ( `m_nShellCommand` **NewFile =**)。

アプリケーション フレームワーク[ParseParam](#parseparam)をこのオブジェクトのデータ メンバーを入力します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#54](../../mfc/codesnippet/cpp/ccommandlineinfo-class_1.cpp)]

##  <a name="m_brunautomated"></a>  CCommandLineInfo::m_bRunAutomated

示します、`/Automation`フラグがコマンドラインで見つかりました。

```
BOOL m_bRunAutomated;
```

### <a name="remarks"></a>Remarks

TRUE の場合、OLE オートメーション サーバーとして起動することを意味します。

##  <a name="m_brunembedded"></a>  CCommandLineInfo::m_bRunEmbedded

示します、`/Embedding`フラグがコマンドラインで見つかりました。

```
BOOL m_bRunEmbedded;
```

### <a name="remarks"></a>Remarks

TRUE の場合、埋め込み OLE アイテムを編集するために起動することを意味します。

##  <a name="m_bshowsplash"></a>  CCommandLineInfo::m_bShowSplash

スプラッシュ スクリーンを表示することを示します。

```
BOOL m_bShowSplash;
```

### <a name="remarks"></a>Remarks

つまり TRUE の場合、起動中にこのアプリケーションのスプラッシュ スクリーンを表示する必要があります。 既定の実装[ParseParam](#parseparam)場合に TRUE に、このデータ メンバーを設定[m_nShellCommand](#m_nshellcommand)と等しい`CCommandLineInfo::FileNew`します。

##  <a name="m_nshellcommand"></a>  CCommandLineInfo::m_nShellCommand

アプリケーションのこのインスタンスのシェル コマンドを示します。

```
m_nShellCommand;
```

### <a name="remarks"></a>Remarks

このデータ メンバーの型は、次の列挙型で定義されている、`CCommandLineInfo`クラス。

```
enum {
    FileNew,
    FileOpen,
    FilePrint,
    FilePrintTo,
    FileDDE,
    AppRegister,
    AppUnregister,
    RestartByRestartManager,
    FileNothing = -1
    };
```

これらの値の簡単な説明は、次の一覧を参照してください。

- `CCommandLineInfo::FileNew` コマンドラインにファイル名が見つかりませんだったことを示します。

- `CCommandLineInfo::FileOpen` コマンドラインでファイル名が見つかったことと、次のフラグのいずれもコマンドラインで検出されたことを示します: `/p`、 `/pt`、`/dde`します。

- `CCommandLineInfo::FilePrint` 示します、`/p`フラグがコマンドラインで見つかりました。

- `CCommandLineInfo::FilePrintTo` 示します、`/pt`フラグがコマンドラインで見つかりました。

- `CCommandLineInfo::FileDDE` 示します、`/dde`フラグがコマンドラインで見つかりました。

- `CCommandLineInfo::AppRegister` 示します、`/Register`または`/Regserver`フラグがコマンドラインで検出され、アプリケーションが登録するように要求されました。

- `CCommandLineInfo::AppUnregister` 示します、`/Unregister`または`/Unregserver`アプリケーションが登録を解除するように要求されました。

- `CCommandLineInfo::RestartByRestartManager` 再起動マネージャーによって、アプリケーションが再起動されたことを示します。

- `CCommandLineInfo::FileNothing` 起動時に新しい MDI 子ウィンドウの表示をオフにします。 仕様では、アプリケーション ウィザードで生成された MDI アプリケーションは起動時に新しい子ウィンドウを表示します。 この機能を無効にするには、アプリケーションで使用できます`CCommandLineInfo::FileNothing`シェル コマンドを呼び出すときとして[ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand)します。 `ProcessShellCommand` によって呼び出される、`InitInstance( )`すべて`CWinApp`クラスを派生します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#55](../../mfc/codesnippet/cpp/ccommandlineinfo-class_2.cpp)]

##  <a name="m_strdrivername"></a>  CCommandLineInfo::m_strDriverName

コマンドラインでは、3 番目のフラグではないパラメーターの値を格納します。

```
CString m_strDriverName;
```

### <a name="remarks"></a>Remarks

このパラメーターは、通常、印刷シェル コマンドのプリンタ ドライバの名前です。 既定の実装[ParseParam](#parseparam)データ メンバー場合のみ、この設定、`/pt`フラグがコマンドラインで見つかりました。

##  <a name="m_strfilename"></a>  CCommandLineInfo::m_strFileName

コマンドラインでは、最初のフラグではないパラメーターの値を格納します。

```
CString m_strFileName;
```

### <a name="remarks"></a>Remarks

このパラメーターは、通常、開くファイルの名前です。

##  <a name="m_strportname"></a>  CCommandLineInfo::m_strPortName

コマンドラインでは、4 番目のフラグではないパラメーターの値を格納します。

```
CString m_strPortName;
```

### <a name="remarks"></a>Remarks

このパラメーターは、通常、印刷シェル コマンドのプリンター ポートの名前です。 既定の実装[ParseParam](#parseparam)データ メンバー場合のみ、この設定、`/pt`フラグがコマンドラインで見つかりました。

##  <a name="m_strprintername"></a>  CCommandLineInfo::m_strPrinterName

コマンドラインでは、2 つ目の非フラグ パラメーターの値を格納します。

```
CString m_strPrinterName;
```

### <a name="remarks"></a>Remarks

このパラメーターは、通常、印刷シェル コマンドのプリンターの名前です。 既定の実装[ParseParam](#parseparam)データ メンバー場合のみ、この設定、`/pt`フラグがコマンドラインで見つかりました。

##  <a name="m_strrestartidentifier"></a>  CCommandLineInfo::m_strRestartIdentifier

コマンドラインで識別子を一意に再起動します。

```
CString m_strRestartIdentifier;
```

### <a name="remarks"></a>Remarks

再起動識別子は、アプリケーションの各インスタンスに対して一意です。

再起動マネージャーは、アプリケーションを終了するし、再起動するように構成、再起動マネージャーは、任意のパラメーターとしての再起動の識別子を使用してコマンドラインからアプリケーションを実行します。 再起動マネージャーは、再起動の識別子を使用する場合、アプリケーションが以前に開かれているドキュメントを再び開くし、自動保存されたファイルを回復することができます。

##  <a name="parseparam"></a>  CCommandLineInfo::ParseParam

フレームワークは、コマンドラインからの個々 のパラメーターの解析/解釈には、この関数を呼び出します。 最初から 2 番目のバージョンとは異なる Unicode プロジェクトでのみです。

```
virtual void ParseParam(
    const char* pszParam,
    BOOL bFlag,
    BOOL bLast);

virtual void ParseParam(
    const TCHAR* pszParam,
    BOOL bFlag,
    BOOL bLast);
```

### <a name="parameters"></a>パラメーター

*pszParam*<br/>
パラメーターまたはフラグ。

*bFlag*<br/>
示すかどうか*pszParam*パラメーターまたはフラグ。

*爆発*<br/>
これは最後のパラメーターまたはコマンドラインでフラグを示します。

### <a name="remarks"></a>Remarks

[CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline)呼び出し`ParseParam`1 回の各パラメーターまたはコマンドラインでフラグの引数を渡す*pszParam*します。 パラメーターの最初の文字がある場合、' **-**'または' **/**'、取り除かれますと*bFlag*が TRUE に設定します。 最後のパラメーターを解析するときに*爆発*が TRUE に設定します。

この関数の既定の実装は、次のフラグを認識: `/p`、 `/pt`、 `/dde`、 `/Automation`、および`/Embedding`次の表に示すように、します。

|コマンド ライン引数|実行されたコマンド|
|----------------------------|----------------------|
|*app*|新しいファイルです。|
|*アプリ*ファイル名|ファイルを開く.|
|*アプリ*`/p`ファイル名|既定のプリンターにファイルを印刷します。|
|*アプリ*`/pt`ファイル名のプリンター ドライバーのポート|指定されたプリンターにファイルを印刷します。|
|*アプリ* `/dde`|起動し、DDE コマンドを待機します。|
|*アプリ* `/Automation`|OLE オートメーション サーバーとして起動します。|
|*アプリ* `/Embedding`|埋め込み OLE アイテムの編集を起動します。|
|*アプリ* `/Register`<br /><br /> *アプリ* `/Regserver`|登録タスクを実行するアプリケーションに通知します。|
|*アプリ* `/Unregister`<br /><br /> *アプリ* `/Unregserver`|任意の登録の解除タスクを実行するアプリケーションに通知します。|

この情報が格納されている[m_bRunAutomated](#m_brunautomated)、 [m_bRunEmbedded](#m_brunembedded)、および[m_nShellCommand](#m_nshellcommand)します。 フラグによってマークされているか、スラッシュ ' **/**'、またはハイフン' **-**'。

既定の実装には、最初のフラグではないパラメーターは、 [m_strFileName](#m_strfilename)します。 場合、`/pt`フラグは、既定の実装は、2 番目に、3 番目と 4 番目のフラグではないパラメーター [m_strPrinterName](#m_strprintername)、 [m_strDriverName](#m_strdrivername)、および[m _strPortName](#m_strportname)、それぞれします。

既定の実装も設定[m_bShowSplash](#m_bshowsplash)を新しいファイルの場合にのみ TRUE にします。 新しいファイルの場合は、ユーザーをアプリケーション自体に関連するアクションとしました。 シェルを使用して既存のファイルを開くことを含め、その他のケースでは、ユーザーの操作は、ファイルを直接は。 スプラッシュ スクリーンは、ドキュメント中心の観点で、アプリケーションの起動を発表する必要はありません。

その他のフラグとパラメーターの値を処理するために、派生クラスでは、この関数をオーバーライドします。

## <a name="see-also"></a>関連項目

[CObject クラス](../../mfc/reference/cobject-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline)<br/>
[CWinApp::ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand)
