---
title: 構造体と定数の定義
ms.date: 11/04/2016
ms.assetid: 1df7cf46-b853-4788-a257-100d5c37997f
ms.openlocfilehash: ea7aa1ec25bcd0e8531ef63848de26da164da668
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317862"
---
# <a name="structure-and-constant-definitions"></a>構造体と定数の定義

既定のヘルパー ルーチンでは、いくつかの構造を使用して、通信用のフック関数とすべての例外の中にします。 通知とエラー値、情報構造体、および、フックに渡されるフック関数へのポインター型を次に示します。

```
//
// Delay load import hook notifications
//
enum {
    dliStartProcessing,        // used to bypass or note helper only
    dliNotePreLoadLibrary,     // called just before LoadLibrary, can
                               //  override w/ new HMODULE return val
    dliNotePreGetProcAddress,  // called just before GetProcAddress, can
                               //  override w/ new FARPROC return value
    dliFailLoadLib,            // failed to load library, fix it by
                               //  returning a valid HMODULE
    dliFailGetProc,            // failed to get proc address, fix it by
                               //  returning a valid FARPROC
    dliNoteEndProcessing,      // called after all processing is done, no
                               //  bypass possible at this point except
                               //  by longjmp()/throw()/RaiseException.
    };

typedef struct DelayLoadProc {
    BOOL                fImportByName;
    union {
        LPCSTR          szProcName;
        DWORD           dwOrdinal;
        };
    } DelayLoadProc;

typedef struct DelayLoadInfo {
    DWORD           cb;         // size of structure
    PCImgDelayDescr pidd;       // raw form of data (everything is there)
    FARPROC *       ppfn;       // points to address of function to load
    LPCSTR          szDll;      // name of dll
    DelayLoadProc   dlp;        // name or ordinal of procedure
    HMODULE         hmodCur;    // the hInstance of the library we have loaded
    FARPROC         pfnCur;     // the actual function that will be called
    DWORD           dwLastError;// error received (if an error notification)
    } DelayLoadInfo, * PDelayLoadInfo;

typedef FARPROC (WINAPI *PfnDliHook)(
    unsigned        dliNotify,
    PDelayLoadInfo  pdli
    );

typedef struct ImgDelayDescr {
    DWORD        grAttrs;        // attributes
    RVA          rvaDLLName;     // RVA to dll name
    RVA          rvaHmod;        // RVA of module handle
    RVA          rvaIAT;         // RVA of the IAT
    RVA          rvaINT;         // RVA of the INT
    RVA          rvaBoundIAT;    // RVA of the optional bound IAT
    RVA          rvaUnloadIAT;   // RVA of optional copy of original IAT
    DWORD        dwTimeStamp;    // 0 if not bound,
                                 // O.W. date/time stamp of DLL bound to (Old BIND)
    } ImgDelayDescr, * PImgDelayDescr;
```

## <a name="see-also"></a>関連項目

[ヘルパー関数について](understanding-the-helper-function.md)
