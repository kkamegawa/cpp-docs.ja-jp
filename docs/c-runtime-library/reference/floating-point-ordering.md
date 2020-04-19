---
title: isgreater、isgreaterequal、isless、islessequal、islessgreater、isunordered
ms.date: 01/31/2019
f1_keywords:
- isgreater
- math/isgreater
- isgreaterequal
- math/isgreaterequal
- isless
- math/isless
- islessequal
- math/islessequal
- islessgreater
- math/islessgreater
- isunordered
- math/isunordered
helpviewer_keywords:
- isgreater function
- isgreaterequal function
- isless function
- islessequal function
- islessgreater function
- isunordered function
ms.openlocfilehash: 748360cae1dd0ee43645dee369c60c835246ed03
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62333704"
---
# <a name="isgreater-isgreaterequal-isless-islessequal-islessgreater-isunordered"></a>isgreater、isgreaterequal、isless、islessequal、islessgreater、isunordered

2 つの浮動小数点値の順序付けの関係を決定します。

## <a name="syntax"></a>構文

```C
int isgreater(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int isgreaterequal(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int isless(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int islessequal(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int islessgreater(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int isunordered(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */
```

```C++
template <class FloatingType1, class FloatingType2>
inline bool isgreater(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool isgreaterequal(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool isless(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool islessequal(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool islessgreater(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool isunordered(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */
```

### <a name="parameters"></a>パラメーター

*x*、 *y*<br/>
比較対象の浮動小数点値。

## <a name="return-value"></a>戻り値

すべての比較では、無限大記号が同じは等しいと比較します。 負の無限大とは、有限値または正の無限大より小さいです。 正の無限大では、任意の有限値または負の無限大を超えています。 ゼロでは、符号に関係なく同じです。 Nan は、同じか、または別の NaN を含む、任意の値より大きいよりも小さいではありません。

どちらの引数が NaN の場合、順序付けのマクロが場合**isgreater**、 **isgreaterequal**、**isless**、および**islessequal**ゼロ以外の値を返します場合は値の間で、指定された順序付けリレーションシップ*x*と*y* true を保持します。 これらのマクロは、いずれかまたは両方の引数が Nan である場合、または注文のリレーションシップが false の場合に 0 を返します。 関数フォームは、同様に動作しますが、返す**true**または**false**します。

**Islessgreater**マクロは、両方に 0 以外の値を返します*x*と*y* 、Nan でないと*x*かよりも大きいか小さい*y*します。 いずれかまたは両方の引数が Nan の場合、または値が等しい場合は 0 を返します。 関数の形式は、同様に動作が返されます**true**または**false**します。

**Isunordered**マクロは、いずれかに 0 以外の値を返します*x*、 *y*、または両方に Nan です。 それ以外の場合は、0 を返します。 関数の形式は、同様に動作が返されます**true**または**false**します。

## <a name="remarks"></a>Remarks

これらの比較操作は、C および C++ としてコンパイルされるときに、テンプレート関数をインラインとしてコンパイルされるときにマクロとして実装されます。

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー (C)|必須ヘッダー (C++)|
|--------------|---------------------------|-------------------------------|
| **isgreater**、 **isgreaterequal**、**isless**、<br/>**islessequal**、 **islessgreater**、 **isunordered** | \<math.h> | \<math.h> または \<cmath> |

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[isfinite、_finite、_finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
[_fpclass、_fpclassf](fpclass-fpclassf.md)<br/>
