---
title: DLL の読み込み中に発生しC++た例外コード (C/)
ms.date: 11/19/2019
f1_keywords:
- ERROR_MOD_NOT_FOUND
- vcppException
- ERROR_SEVERITY_ERROR
helpviewer_keywords:
- vcppException
- C++ exception handling, delayed loading of DLLs
- delayed loading of DLLs, exceptions
- ERROR_SEVERITY_ERROR exception
- ERROR_MOD_NOT_FOUND exception
ms.assetid: c03be05d-1c39-4f35-84cf-00c9af3bae9a
ms.openlocfilehash: f557fe736f45f8c3f5411d076a0be18f1d1b670e
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "74243847"
---
# <a name="exceptions-cc"></a>例外 (C/C++)

エラーが発生すると、次の2つの例外コードが生成されます。

- **LoadLibrary**エラーの場合

- **GetProcAddress**エラーの場合

例外情報を次に示します。

```
//
// Exception information
//
#define FACILITY_VISUALCPP  ((LONG)0x6d)
#define VcppException(sev,err)  ((sev) | (FACILITY_VISUALCPP<<16) | err)
```

スローされる例外コードは、標準の VcppException (ERROR_SEVERITY_ERROR、ERROR_MOD_NOT_FOUND) と VcppException (ERROR_SEVERITY_ERROR、ERROR_PROC_NOT_FOUND) の値です。 例外は、LPDWORD 値の**Delayloadinfo**構造体へのポインターを渡します。この値は、 [EXCEPTION_RECORD](/windows/win32/api/winnt/ns-winnt-exception_record) structure の exceptioninformation [0] フィールドの**getexceptioninformation**によって取得できます。

また、grAttrs フィールドで間違ったビットが設定されている場合は、例外 ERROR_INVALID_PARAMETER がスローされます。 この例外は、すべてのインテントと目的で致命的です。

詳細については[、「構造体と定数の定義](structure-and-constant-definitions.md)」を参照してください。

## <a name="see-also"></a>参照

[エラー処理と通知](error-handling-and-notification.md)
