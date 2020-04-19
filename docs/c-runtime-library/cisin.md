---
title: _CIsin
ms.date: 04/10/2018
api_name:
- _CIsin
api_location:
- msvcr80.dll
- msvcr100.dll
- msvcrt.dll
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- CIsin
- _CIsin
helpviewer_keywords:
- _CIsin intrinsic
- CIsin intrinsic
ms.assetid: f215f39a-2341-4f1c-ba8e-cb522451ceb2
ms.openlocfilehash: 66f26e9fa4dd08d18b15deca4efa40c236e092c9
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944541"
---
# <a name="_cisin"></a>_CIsin

浮動小数点スタックのトップ値のサインを計算します。

## <a name="syntax"></a>構文

```C
void __cdecl _CIsin();
```

## <a name="remarks"></a>解説

この組み込みバージョンの [sin](../c-runtime-library/reference/sin-sinf-sinl.md) 関数には、コンパイラで認識される特殊な呼び出し規則があります。 コピーの生成を防ぎ、レジスタ割り当てが容易になるため、実行時間が短縮されます。

結果の値は、浮動小数点スタックのトップにプッシュされます。

## <a name="requirements"></a>必要条件

**プラットフォーム:** x86

## <a name="see-also"></a>関連項目

[関数リファレンス (アルファベット順)](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[sin、sinf、sinl](../c-runtime-library/reference/sin-sinf-sinl.md)<br/>
