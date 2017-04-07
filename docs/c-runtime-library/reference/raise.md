---
title: raise | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- raise
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- Raise
dev_langs:
- C++
helpviewer_keywords:
- signals, sending to executing programs
- raise function
- signals
- programs [C++], sending signals to executing programs
ms.assetid: a3ccd3ad-f68f-4a7b-a005-c3ebfb217e8b
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: ff8b387b81487e0c39ba5018487a1b8045bd0574
ms.lasthandoff: 02/24/2017

---
# <a name="raise"></a>raise
実行中のプログラムにシグナルを送信します。  
  
> [!NOTE]
>  テスト シナリオまたはデバッグ シナリオの場合を除き、この方法を使用して [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] アプリをシャットダウンしないでください。 プログラムや UI によって [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] アプリを終了する方法は、「[Windows 8 アプリの認定の要件](http://go.microsoft.com/fwlink/?LinkId=262889)」のセクション 3.6 により許可されていません。 詳細については、[アプリケーションのライフサイクル (Windows ストア アプリ)](http://go.microsoft.com/fwlink/?LinkId=262853) に関するページをご覧ください。  
  
## <a name="syntax"></a>構文  
  
```  
  
      int raise(  
int sig   
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 *sig*  
 発生するシグナル。  
  
## <a name="return-value"></a>戻り値  
 正常に終了した場合、**raise** は 0 を返します。 それ以外の場合は、0 以外の値を返します。  
  
## <a name="remarks"></a>コメント  
 **raise** 関数は実行中のプログラムに *sig* を送信します。 **signal** への前回の呼び出しが *sig* の通知処理関数を組み込んでいた場合、**raise** はその関数を実行します。 ハンドラー関数がインストールされていない場合、シグナル値 *sig* に関連付けられた既定のアクションは、次のように取得されます。  
  
|シグナル|説明|Shared|  
|------------|-------------|-------------|  
|`SIGABRT`|異常終了|コード 3 で呼び出し元のプログラムを終了する|  
|`SIGFPE`|浮動小数点エラー|呼び出し元のプログラムを終了します。|  
|`SIGILL`|無効な命令|呼び出し元のプログラムを終了します。|  
|`SIGINT`|Ctrl + C 割り込み|呼び出し元のプログラムを終了します。|  
|`SIGSEGV`|ストレージへの無効なアクセス|呼び出し元のプログラムを終了します。|  
|`SIGTERM`|プログラムに送信される終了要求|シグナルを無視する|  
  
 上で指定したように、引数が有効なシグナルでない場合、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」に説明されているように、無効なパラメーター ハンドラーが呼び出されます。 ハンドルされない場合、関数は `errno` を `EINVAL` に設定し、0 以外の値を返します。  
  
## <a name="requirements"></a>要件  
  
|ルーチン|必須ヘッダー|  
|-------------|---------------------|  
|**raise**|\<signal.h>|  
  
 互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。  
  
## <a name="libraries"></a>ライブラリ  
 [C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のすべてのバージョン。  
  
## <a name="net-framework-equivalent"></a>同等の .NET Framework 関数  
 該当なし。 標準 C 関数を呼び出すには、 `PInvoke`を使用します。 詳細については、「[プラットフォーム呼び出しの例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 [プロセス制御と環境制御](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [signal](../../c-runtime-library/reference/signal.md)