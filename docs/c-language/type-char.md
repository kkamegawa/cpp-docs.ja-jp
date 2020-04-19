---
title: char 型
ms.date: 11/04/2016
helpviewer_keywords:
- type char
- unsigned char keyword [C]
- char keyword [C]
ms.assetid: a5da0866-e780-4793-be87-15a8426e7ea0
ms.openlocfilehash: bc8d3bef85b82d5bb5c2575b3bc6c6d8a4887140
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152210"
---
# <a name="type-char"></a>char 型

`char` 型は、表現できる文字セットのメンバーの整数値を格納するために使用されます。 この整数値は、特定の文字に対応する ASCII コードです。

**Microsoft 固有の仕様**

`unsigned char` 型の文字値の範囲は、16 進数で 0 から 0xFF までです。 **signed char** には 0x80 から 0x7F までの範囲があります。 これらの範囲は、0 から 255 の 10 進数と -128 から +127 の 10 進数にそれぞれ変換されます。 /J コンパイラ オプションは、既定値を **signed** から `unsigned` に変更します。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[基本型の格納](../c-language/storage-of-basic-types.md)
