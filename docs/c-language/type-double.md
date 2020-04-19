---
title: double 型
ms.date: 11/04/2016
helpviewer_keywords:
- mantissas, floating-point variables
- type double
- portability [C++], type double
- double data type
ms.assetid: 17c85b24-1475-4d41-a03c-ddf2d6561d34
ms.openlocfilehash: 43e6cc444f4d6a973fc58b5ce550e468066aca1b
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151859"
---
# <a name="type-double"></a>double 型

double 型の倍精度浮動小数点値のサイズは 8 バイトです。 形式は、float 形式に似ています。ただし、エクセス 1023 形式の 11 ビット指数部と 52 ビット仮数部に、暗黙の上位 1 ビットを持ちます。 この形式では、およそ 1.7E-308 から 1.7E+308 の範囲を double 型で表現します。

**Microsoft 固有の仕様**

double 型は 64 ビットです。符号が 1 ビット、指数部が 11 ビット、仮数部が 52 ビットです。 その範囲は 15 桁以上の精度で、+/-1.7E308 です。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[基本型の格納](../c-language/storage-of-basic-types.md)
