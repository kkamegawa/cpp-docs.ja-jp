---
title: signbit
ms.date: 01/31/2019
f1_keywords:
- signbit
- math/signbit
helpviewer_keywords:
- signbit function
ms.openlocfilehash: ce2f632f11296bf71036011a57f242365951d7f2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356330"
---
# <a name="signbit"></a>signbit

浮動小数点値が負の値であるかどうかを判断します。

## <a name="syntax"></a>構文

```C
int signbit(
   /* floating-point */ x
); /* C-only macro */

inline bool signbit(
   float x
) throw(); /* C++-only overloaded function */

inline bool signbit(
   double x
) throw(); /* C++-only overloaded function */

inline bool signbit(
   long double x
) throw(); /* C++-only overloaded function */
```

### <a name="parameters"></a>パラメーター

*x*<br/>
テストする浮動小数点値。

## <a name="return-value"></a>戻り値

**signbit** 0 以外の値を返します (**true** C++ で) 場合、引数*x*負の値または負の無限大します。 0 を返します (**false** C++ の) 引数が負以外の正の無限大または NAN の場合。

## <a name="remarks"></a>Remarks

**signbit**マクロとして、C、C++ としてコンパイル時に、オーバー ロードされたインライン関数をコンパイルする場合。

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー (C)|必須ヘッダー (C++)|
|--------------|---------------------------|-------------------------------|
|**signbit**|\<math.h>|\<math.h> または \<cmath>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[isfinite、_finite、_finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
[_fpclass、_fpclassf](fpclass-fpclassf.md)<br/>
