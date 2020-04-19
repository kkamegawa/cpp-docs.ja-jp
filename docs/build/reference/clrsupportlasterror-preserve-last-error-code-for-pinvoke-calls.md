---
title: /CLRSUPPORTLASTERROR (PInvoke 呼び出しの最終エラー コードの保持)
ms.date: 11/04/2016
f1_keywords:
- /CLRSUPPORTLASTERROR
helpviewer_keywords:
- /CLRSUPPORTLASTERROR linker option
- -CLRSUPPORTLASTERROR linker option
ms.assetid: b7057990-4154-4b1d-9fc9-6236f7be7575
ms.openlocfilehash: 64948d81759d415245e741bc6152d56bb35480d2
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988353"
---
# <a name="clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls"></a>/CLRSUPPORTLASTERROR (PInvoke 呼び出しの最終エラー コードの保持)

既定でオンになっている **/CLRSUPPORTLASTERROR**は、P/Invoke 機構を通じて呼び出された関数の最後のエラーコードを保持します。これにより、 **/clr**でコンパイルされたコードから dll 内のネイティブ関数を呼び出すことができます。

## <a name="syntax"></a>構文

```
/CLRSUPPORTLASTERROR{:NO | SYSTEMDLL}
```

## <a name="remarks"></a>Remarks

最後のエラーコードを保持することは、パフォーマンスの低下を意味します。  最新のエラーコードを保持することによるパフォーマンスへの影響を避ける場合は、 **/CLRSUPPORTLASTERROR: NO**とリンクします。

**/CLRSUPPORTLASTERROR: SYSTEMDLL**とリンクすることで、パフォーマンスへの影響を最小限に抑えることができます。この場合、システム dll 内の関数の最後のエラーコードのみが保持されます。  システム DLL は、次のいずれかとして定義されます。

|||||
|-|-|-|-|
|ACLUI。DLL|ACTIVEDS.DLL|ADPTIF。DLL|ADVAPI32.DLL|
|ASYCFILT.DLL|承認.DLL|AVICAP32.DLL|AVIFIL32.DLL|
|キャビネット.DLL|CLUSAPI.DLL|COMCTL32.DLL.DLL|COMDLG32.LIB や KERNEL32.LIB.DLL|
|COMSVCS。DLL|CREDUI.DLL|CRYPT32.DLL.DLL|CRYPTNET。DLL|
|CRYPTUI.DLL.DLL|D3D8THK.DLL|DBGENG。DLL|DBGHELP.DLL.DLL|
|DCIMAN32.DLL|DNSAPI.DLL|DSPROP。DLL|DSUIEXT。DLL|
|GDI32.DLL|GLU32.DLL|HLINK.DLL.DLL|ICM32.DLL|
|IMAGEHLP.DLL.DLL|IMM32.DLL|IPHLPAPI.DLL|IPROP。DLL|
|KERNEL32.DLL.DLL|KSUSER。DLL|Loadperf」.DLL|LZ32.DLL|
|MAPI32.DLL|MGMTAPI.DLL|MOBSYNC.DLL|MPR.DLL|
|MPRAPI。DLL|MQRT。DLL|MSACM32.DLL|MSCMS.DLL|
|MSI.DLL|MSIMG32.DLL|MSRATING。DLL|MSTASK.DLL|
|MSVFW32.DLL|MSWSOCK。DLL|MTXEX.DLL|NDDEAPI。DLL|
|NETAPI32.DLL|NPPTOOLS。DLL|NTDSAPI.DLL|NTDSBCLI.DLL|
|NTMSAPI.DLL|ODBC32.DLL|ODBCBCP.DLL.DLL|OLE32.DLL|
|OLEACC。DLL|OLEAUT32.DLL.DLL|OLEDLG.DLL|OPENGL32.DLL|
|PDH.DLL|POWRPROF.DLL|QOSNAME。DLL|照会.DLL|
|RASAPI32.DLL|RASDLG。DLL|RASSAPI。DLL|RESUTILS.DLL|
|RICHED20.DLL.DLL|RPCNS4.DLL|RPCRT4.DLL|リリース.DLL|
|RTUTILS.DLL|SCシャード。DLL|SECUR32.DLL|SENSAPI。DLL|
|SETUPAPI.LOG.DLL|SFC.EXE.DLL|SHELL32.DLL.DLL|SHFOLDER.DLL が.DLL|
|SHLWAPI.DLL|SISBKUP.DLL|SNMPAPI.DLL|SRCLIENT。DLL|
|飛行.DLL|TAPI32.DLL|トラッフィック.DLL|先.DLL|
|URLMON.DLL|USER32.DLL.DLL|USERENV.DLL|USP10.DLL|
|UXTHEME.DLL|VDMDBG.DLL|バージョン。DLL|WINFAX.DLL|
|WINHTTP.DLL|WININET.DLL|WINMM.DLL.DLL|WINSCARD.DLL|
|WINTRUST。DLL|WLDAP32.DLL.DLL|WOW32.DLL|WS2_32 .DLL|
|WSNMP32.DLL.DLL|WSOCK32.DLL|WTSAPI32.DLL.DLL|XOLEHLP。DLL|

> [!NOTE]
>  同じモジュールで CLR コードによって使用されるアンマネージ関数では、最後のエラーの保持はサポートされていません。

- 詳細については、「[/clr (共通言語ランタイムのコンパイル)](clr-common-language-runtime-compilation.md)」を参照してください。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. **[リンカー]** フォルダーをクリックします。

1. **[コマンド ライン]** プロパティ ページをクリックします。

1. **[追加オプション]** ボックスにオプションを入力します。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>

## <a name="example"></a>使用例

次の例では、最後のエラーを変更するエクスポートされた関数を1つ持つネイティブ DLL を定義します。

```cpp
// CLRSUPPORTLASTERROR_dll.cpp
// compile with: /LD
#include <windows.h>
#include <math.h>

#pragma unmanaged
__declspec(dllexport) double MySqrt(__int64 n) {
   SetLastError(DWORD(-1));
   return sqrt(double(n));
}
```

## <a name="example"></a>使用例

次の例では、DLL を使用して、 **/CLRSUPPORTLASTERROR**の使用方法を示しています。

```cpp
// CLRSUPPORTLASTERROR_client.cpp
// compile with: /clr CLRSUPPORTLASTERROR_dll.lib /link /clrsupportlasterror:systemdll
// processor: x86
#include <windows.h>
#include <wininet.h>
#include <stdio.h>
#include <math.h>

#pragma comment(lib, "wininet.lib")

double MySqrt(__int64 n);

#pragma managed
int main() {
   double   d = 0.0;
   __int64 n = 65;
   HANDLE  hGroup = NULL;
   GROUPID groupID;
   DWORD   dwSet = 127, dwGet = 37;

   SetLastError(dwSet);
   d = MySqrt(n);
   dwGet = GetLastError();

   if (dwGet == DWORD(-1))
      printf_s("GetLastError for application call succeeded (%d).\n",
             dwGet);
   else
      printf_s("GetLastError for application call failed (%d).\n",
             dwGet);

   hGroup = FindFirstUrlCacheGroup(0, CACHEGROUP_SEARCH_ALL,
                           0, 0, &groupID, 0);
   dwGet = GetLastError();
   if (dwGet == 183)
      printf_s("GetLastError for system call succeeded (%d).\n",
             dwGet);
   else
      printf_s("GetLastError for system call failed (%d).\n",
             dwGet);
}
```

```Output
GetLastError for application call failed (127).
GetLastError for system call succeeded (183).
```

## <a name="see-also"></a>参照

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
