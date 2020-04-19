---
title: _get_FMA3_enable、_set_FMA3_enable
ms.date: 04/05/2018
api_name:
- _get_FMA3_enable
- _set_FMA3_enable
api_location:
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
- math/_get_FMA3_enable
- math/_set_FMA3_enable
helpviewer_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
ms.assetid: 4c1dc4bc-e86b-451b-9211-5a2ba6c98ee4
ms.openlocfilehash: dee75bf5b16b5fe5b619444f7f2736010bb42a84
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857812"
---
# <a name="_get_fma3_enable-_set_fma3_enable"></a>_get_FMA3_enable、_set_FMA3_enable

超越 math 浮動小数点ライブラリ関数が、X64 プラットフォーム用にコンパイルされたコードで FMA3 命令を使用するかどうかを指定するフラグを取得または設定します。

## <a name="syntax"></a>構文

```C
int _set_FMA3_enable(int flag);
int _get_FMA3_enable();
```

### <a name="parameters"></a>パラメーター

*flag*<br/>
を1に設定すると、X64 プラットフォームでの超越 math 浮動小数点ライブラリ関数の FMA3 実装が有効になります。または、FMA3 命令を使用しない実装を使用する場合は0に設定されます。

## <a name="return-value"></a>戻り値

超越 math 浮動小数点ライブラリ関数の FMA3 実装が有効になっている場合は、0以外の値。 それ以外の場合は0。

## <a name="remarks"></a>Remarks

CRT ライブラリの超越 math 浮動小数点関数で FMA3 命令の使用を有効または無効にするには、 **_set_FMA3_enable**関数を使用します。 戻り値には、変更後に使用される実装が反映されます。 CPU で FMA3 命令がサポートされていない場合、この関数はライブラリで有効にすることができず、戻り値はゼロになります。 **_Get_FMA3_enable**を使用して、ライブラリの現在の状態を取得します。 既定では、X64 プラットフォームでは、CRT スタートアップコードは、CPU が FMA3 命令をサポートしているかどうかを検出し、ライブラリ内の FMA3 実装を有効または無効にします。

FMA3 の実装では異なるアルゴリズムが使用されているため、FMA3 の実装が有効または無効になっている場合、または FMA3 をサポートしていないコンピューターの場合は、計算結果の微妙な違いが観察される可能性があります。 詳細については、「[浮動小数点の移行に関する問題](../../porting/floating-point-migration-issues.md)」を参照してください。

## <a name="requirements"></a>要件

**_Set_FMA3_enable**および **_get_FMA3_enable**関数は、CRT の X64 バージョンでのみ使用できます。

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_set_FMA3_enable**、 **_get_FMA3_enable**| C: \<math.h><br />C++: \<cmath > または \<の数値演算 >|

**_Set_FMA3_enable**関数と **_get_FMA3_enable**関数は、Microsoft 固有の関数です。 互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>参照

[浮動小数点のサポート](../../c-runtime-library/floating-point-support.md)<br/>
[浮動小数点の移行に関する問題](../../porting/floating-point-migration-issues.md)<br/>
