---
title: _purecall
ms.date: 11/04/2016
api_name:
- _purecall
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ntoskrnl.exe
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- purecall
- _purecall
helpviewer_keywords:
- _purecall function
- purecall function
ms.assetid: 56135d9b-3403-4e22-822d-e714523801cc
ms.openlocfilehash: 5d62ec30731ce26c4683afc88474d4bddb63a697
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70950166"
---
# <a name="_purecall"></a>_purecall

純粋仮想関数が呼び出された場合の、既定のエラー ハンドラーです。 純粋仮想メンバー関数が呼び出されると、コンパイラによってこの関数を呼び出すコードが生成されます。

## <a name="syntax"></a>構文

```C
extern "C" int __cdecl _purecall();
```

## <a name="remarks"></a>Remarks

この**関数は、microsoft** C++コンパイラの microsoft 固有の実装の詳細を示しています。 この関数はコードで直接呼び出されるものではなく、パブリック ヘッダー宣言がありません。 C ランタイム ライブラリのパブリック エクスポートであるため、ここで説明しています。

純粋仮想関数には実装がないため、この関数への呼び出しはエラーになります。 純粋仮想関数が呼び出されたときに、コンパイラによって、 **_ puリコール**エラーハンドラー関数を呼び出すコードが生成されます。 既定**では、プログラムが終了し**ます。 プロセスに対して設定されている場合、この関数は、終了する前に、**すべてのハンドラー**関数を呼び出し**ます (_a** )。 純粋仮想関数の呼び出し用に独自のエラー ハンドラー関数をインストールして呼び出しをキャッチし、デバッグまたはレポート作成に使用することができます。 独自のエラーハンドラーを使用するには、**ハンドラー**シグネチャを持つ関数を作成し、 [_set_purecall_handler](get-purecall-handler-set-purecall-handler.md)を使用してそれを現在のハンドラーにします。

## <a name="requirements"></a>必要条件

**_ Puリコール**関数には、ヘッダー宣言がありません。 Stdlib.h>**の typedef は**、> で\<定義されています。

## <a name="see-also"></a>関連項目

[関数リファレンス (アルファベット順)](crt-alphabetical-function-reference.md)<br/>
[_get_purecall_handler、_set_purecall_handler](get-purecall-handler-set-purecall-handler.md)<br/>
