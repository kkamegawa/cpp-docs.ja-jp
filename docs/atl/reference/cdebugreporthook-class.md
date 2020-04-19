---
title: CDebugReportHook クラス
ms.date: 11/04/2016
f1_keywords:
- CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook::CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook::CDebugReportHookProc
- ATLUTIL/ATL::CDebugReportHook::RemoveHook
- ATLUTIL/ATL::CDebugReportHook::SetHook
- ATLUTIL/ATL::CDebugReportHook::SetPipeName
- ATLUTIL/ATL::CDebugReportHook::SetTimeout
helpviewer_keywords:
- CDebugReportHook class
ms.assetid: 798076c3-6e63-4286-83b8-aa1bbcd0c20c
ms.openlocfilehash: 7187448b2ba2c9d3ab0399aa3e75ce8d757bfec1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496770"
---
# <a name="cdebugreporthook-class"></a>CDebugReportHook クラス

このクラスを使用して、デバッグレポートを名前付きパイプに送信します。

## <a name="syntax"></a>構文

```
class CDebugReportHook
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CDebugReportHook:: CDebugReportHook](#cdebugreporthook)|[Setpipename](#setpipename)、 [SetTimeout](#settimeout)、および[sethook](#sethook)を呼び出します。|
|[CDebugReportHook:: ~ CDebugReportHook](#dtor)|[Cdebugreporthook:: RemoveHook](#removehook)を呼び出します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CDebugReportHook:: CDebugReportHookProc](#cdebugreporthookproc)|雑音C ランタイムデバッグレポートプロセスにフックされるカスタムレポート関数。|
|[CDebugReportHook::RemoveHook](#removehook)|名前付きパイプへのデバッグレポートの送信を停止し、以前のレポートフックを復元するには、このメソッドを呼び出します。|
|[CDebugReportHook:: SetHook](#sethook)|このメソッドを呼び出して、名前付きパイプへのデバッグレポートの送信を開始します。|
|[CDebugReportHook:: SetPipeName](#setpipename)|このメソッドを呼び出して、デバッグレポートが送信されるパイプのコンピューターと名前を設定します。|
|[CDebugReportHook:: SetTimeout](#settimeout)|このメソッドを呼び出して、名前付きパイプが使用可能になるのをこのクラスが待機する時間をミリ秒単位で設定します。|

## <a name="remarks"></a>Remarks

サービスまたはアプリケーションのデバッグビルドで、このクラスのインスタンスを作成して、名前付きパイプにデバッグレポートを送信します。 デバッグレポートは、 [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)を呼び出すか、または[atltrace](debugging-and-error-reporting-macros.md#atltrace)マクロや[ATLASSERT](debugging-and-error-reporting-macros.md#atlassert)マクロなどのこの関数のラッパーを使用して生成されます。

このクラスを使用すると、対話型でない[ウィンドウステーション](/windows/win32/winstation/window-stations)で実行されているコンポーネントを対話的にデバッグできます。

デバッグレポートは、スレッドの基になるセキュリティコンテキストを使用して送信されることに注意してください。 偽装は一時的に無効になっているので、web アプリケーションなど、低い特権のユーザーの権限借用が発生している状況でデバッグレポートを表示することができます。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlutil. h

##  <a name="cdebugreporthook"></a>CDebugReportHook:: CDebugReportHook

[Setpipename](#setpipename)、 [SetTimeout](#settimeout)、および[sethook](#sethook)を呼び出します。

```
CDebugReportHook(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe",
    DWORD dwTimeout = 20000) throw();
```

### <a name="parameters"></a>パラメーター

*szMachineName*<br/>
デバッグ出力の送信先となるコンピューターの名前。 既定値はローカルコンピューターです。

*szPipeName*<br/>
デバッグ出力の送信先となる名前付きパイプの名前。

*dwTimeout*<br/>
名前付きパイプが使用可能になるのをこのクラスが待機する時間 (ミリ秒単位)。

##  <a name="dtor"></a>CDebugReportHook:: ~ CDebugReportHook

[Cdebugreporthook:: RemoveHook](#removehook)を呼び出します。

```
~CDebugReportHook() throw();
```

##  <a name="cdebugreporthookproc"></a>  CDebugReportHook::CDebugReportHookProc

C ランタイムデバッグレポートプロセスにフックされるカスタムレポート関数。

```
static int __cdecl CDebugReportHookProc(
    int reportType,
    char* message,
    int* returnValue) throw();
```

### <a name="parameters"></a>パラメーター

*reportType*<br/>
レポートの種類 (_CRT_WARN、_CRT_ERROR、または _CRT_ASSERT)。

*message*<br/>
メッセージ文字列。

*returnValue*<br/>
[_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)によって返される値。

### <a name="return-value"></a>戻り値

フックが問題のメッセージを完全に処理して、それ以上のレポートが必要ない場合は、FALSE を返します。 が通常の`_CrtDbgReport`方法でメッセージを報告する場合は TRUE を返します。

### <a name="remarks"></a>Remarks

レポート関数は、名前付きパイプを開いて、もう一方の側のプロセスと通信しようとします。 パイプがビジー状態の場合、レポート関数はパイプが解放されるか、タイムアウトが経過するまで待機します。 タイムアウトは、コンストラクターまたは[Cdebugreporthook:: SetTimeout](#settimeout)の呼び出しによって設定できます。

この関数のコードは、呼び出し元のスレッドの基になるセキュリティコンテキストで実行されます。つまり、この関数の間は偽装が無効になります。

##  <a name="removehook"></a>  CDebugReportHook::RemoveHook

名前付きパイプへのデバッグレポートの送信を停止し、以前のレポートフックを復元するには、このメソッドを呼び出します。

```
void RemoveHook() throw();
```

### <a name="remarks"></a>Remarks

[_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md)を呼び出して、以前のレポートフックを復元します。

##  <a name="sethook"></a>CDebugReportHook:: SetHook

このメソッドを呼び出して、名前付きパイプへのデバッグレポートの送信を開始します。

```
void SetHook() throw();
```

### <a name="remarks"></a>Remarks

[_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md)を呼び出して、 [Cdebugreporthookproc](#cdebugreporthookproc)経由で名前付きパイプにルーティングされるデバッグレポートを作成します。 このクラスは、 [Removehook](#removehook)が呼び出されたときに復元できるように、前のレポートフックを追跡します。

##  <a name="setpipename"></a>CDebugReportHook:: SetPipeName

このメソッドを呼び出して、デバッグレポートが送信されるパイプのコンピューターと名前を設定します。

```
BOOL SetPipeName(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe") throw();
```

### <a name="parameters"></a>パラメーター

*szMachineName*<br/>
デバッグ出力の送信先となるコンピューターの名前。

*szPipeName*<br/>
デバッグ出力の送信先となる名前付きパイプの名前。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、失敗した場合は FALSE を返します。

##  <a name="settimeout"></a>  CDebugReportHook::SetTimeout

このメソッドを呼び出して、名前付きパイプが使用可能になるのをこのクラスが待機する時間をミリ秒単位で設定します。

```
void SetTimeout(DWORD dwTimeout);
```

### <a name="parameters"></a>パラメーター

*dwTimeout*<br/>
名前付きパイプが使用可能になるのをこのクラスが待機する時間 (ミリ秒単位)。

## <a name="see-also"></a>関連項目

[クラス](../../atl/reference/atl-classes.md)
