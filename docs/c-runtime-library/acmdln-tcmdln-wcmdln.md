---
title: _acmdln, _tcmdln, _wcmdln
ms.date: 11/04/2016
api_name:
- _wcmdln
- _acmdln
api_location:
- msvcrt.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _acmdln
- acmdln
- _wcmdln
- wcmdln
- _tcmdln
- tcmdln
helpviewer_keywords:
- _wcmdln global variable
- wcmdln global variable
- _acmdln global variable
- _tcmdln global variable
- tcmdln global variable
- acmdln global variable
ms.assetid: 4fc0a6a0-3f93-420a-a19f-5276061ba539
ms.openlocfilehash: 07061244e06256341a6da7d04e5487e81c4b9378
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940612"
---
# <a name="_acmdln-_tcmdln-_wcmdln"></a>_acmdln, _tcmdln, _wcmdln

内部 CRT グローバル変数。 コマンド ライン。

## <a name="syntax"></a>構文

```
char * _acmdln;
wchar_t * _wcmdln;

#ifdef WPRFLAG
   #define _tcmdln _wcmdln
#else
   #define _tcmdln _acmdln
```

## <a name="remarks"></a>解説

これらの CRT 内部変数には、完全なコマンド ラインが格納されます。 これらは CRT のエクスポートされたシンボルで公開されていますが、コードでの使用が目的ではありません。 `_acmdln` には、データは文字列として格納されます。 `_wcmdln` には、データはワイド文字列として格納されます。 `_tcmdln` は、どちらが適切かに応じて `_acmdln` または`_wcmdln` として定義できます。

## <a name="see-also"></a>関連項目

[グローバル変数](../c-runtime-library/global-variables.md)
