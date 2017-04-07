---
title: "_spawnv、_wspawnv | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wspawnv"
  - "_spawnv"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-process-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "wspawnv"
  - "_spawnv"
  - "_wspawnv"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "wspawnv 関数"
  - "プロセス、作成"
  - "_spawnv 関数"
  - "プロセス、実行 (新規)"
  - "プロセス作成"
  - "_wspawnv 関数"
  - "spawnv 関数"
ms.assetid: 72360ef4-dfa9-44c1-88c1-b3ecb660aa7d
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# _spawnv、_wspawnv
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

新しいプロセスを作成して実行します。  
  
> [!IMPORTANT]
>  この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳しくは、「[\/ZW でサポートされない CRT 関数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)」をご覧ください。  
  
## 構文  
  
```  
intptr_t _spawnv(  
   int mode,  
   const char *cmdname,  
   const char *const *argv   
);  
intptr_t _wspawnv(  
   int mode,  
   const wchar_t *cmdname,  
   const wchar_t *const *argv   
);  
```  
  
#### パラメーター  
 `mode`  
 呼び出しプロセスの実行モード。  
  
 `cmdname`  
 実行されるファイルのパス。  
  
 `argv`  
 引数へのポインターの配列。`argv`\[0\] 引数は、通常、リアル モードのパスまたは保護モードのプログラム名へのポインターです。`argv`\[1\] 引数～ `argv`\[`n`\] 引数は、新しい引数リストを形成する文字列へのポインターです。 引数リストの末尾を示すために、`argv`\[`n`\+1\] 引数は `NULL` ポインターである必要があります。  
  
## 戻り値  
 同期 `_spawnv` または `_wspawnv` \(`_P_WAIT` 向けに指定された `mode`\) からの戻り値が新しいプロセスの終了ステータスです。 非同期 `_spawnv` または `_wspawnv`\(`_P_NOWAIT` 向けに指定された `_P_NOWAITO` または `mode`\) からの戻り値がプロセス ハンドルです。 プロセスが正常に終了した場合、終了ステータスは 0 です。 起動されたプロセスで、0 以外の引数を指定して `exit` ルーチンを明示的に呼び出すと、終了ステータスを 0 以外の値に設定できます。 新しいプロセスが明示的に終了ステータスを正の値に設定しなかった場合、正の値の終了ステータスは中止または割り込みによる異常終了を示します。 戻り値 –1 はエラーを示します \(新しいプロセスは開始されません\)。 この場合、`errno` は次のいずれかの値に設定されます。  
  
 `E2BIG`  
 引数リストが 1024 バイトを超えています。  
  
 `EINVAL`  
 `mode` 引数が無効です。  
  
 `ENOENT`  
 ファイルまたはパスが見つかりません。  
  
 `ENOEXEC`  
 指定されたファイルが実行可能ファイルでないか、無効な実行可能ファイル形式です。  
  
 `ENOMEM`  
 新しいプロセスを実行するのに十分なメモリがありません。  
  
 リターン コードの詳細については、「[\_doserrno、errno、\_sys\_errlist、および \_sys\_nerr](../Topic/errno,%20_doserrno,%20_sys_errlist,%20and%20_sys_nerr.md)」を参照してください。  
  
## 解説  
 これらの各関数は新しいプロセスを作成して実行し、コマンド ライン引数へのポインターの配列を渡します。  
  
 これらの関数では、パラメーターの検証が行われます。`cmdname` または `argv` が null ポインターの場合、または `argv` が null ポインターをポイントしている場合、または `argv[0]` が空の文字列の場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」に説明されているように、無効パラメーターのハンドラーが呼び出されます。 実行の継続が許可された場合、これらの関数は `errno` を `EINVAL` に設定し、\-1 を返します。 新しいプロセスは起動されません。  
  
## 必要条件  
  
|ルーチン|必須ヘッダー|  
|----------|------------|  
|`_spawnv`|\<stdio.h\> または \<process.h\>|  
|`_wspawnv`|\<stdio.h\> または \<wchar.h\>|  
  
 互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。  
  
## 使用例  
 「[\_spawn 系関数と \_wspawn 系関数](../Topic/_spawn,%20_wspawn%20Functions.md)」の使用例を参照してください。  
  
## 同等の .NET Framework 関数  
  
-   [System::Diagnostics::Process クラス](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)  
  
-   [System::Diagnostics::ProcessStartInfo クラス](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)  
  
## 参照  
 [プロセス制御と環境制御](../../c-runtime-library/process-and-environment-control.md)   
 [\_spawn 系関数と \_wspawn 系関数](../Topic/_spawn,%20_wspawn%20Functions.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [\_exec、\_wexec 系関数](../../c-runtime-library/exec-wexec-functions.md)   
 [終了、\_Exit、\_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [\_flushall](../../c-runtime-library/reference/flushall.md)   
 [\_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [\_onexit、\_onexit\_m](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [\_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [system、\_wsystem](../../c-runtime-library/reference/system-wsystem.md)