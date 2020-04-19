---
title: C サイズ設定された整数型
ms.date: 11/04/2016
helpviewer_keywords:
- sized integer types
ms.assetid: 0d6199b4-d0ab-4e8c-a769-785f5afb92eb
ms.openlocfilehash: 136065466d3adb4017cf18f2baf8c3387ffbd035
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56150689"
---
# <a name="c-sized-integer-types"></a>C サイズ設定された整数型

**Microsoft 固有の仕様**

Microsoft C の機能では、サイズ設定された整数型をサポートします。 __int*n* 型指定子を使用して、8 ビット、16 ビット、32 ビット、または 64 ビットの整数変数を宣言できます。ここで、*n* は、整数変数のビット単位のサイズです。 *n* の値は、8、16、32、64 のいずれかになります。 次の例は、サイズ設定された整数の 4 つの型のそれぞれに 1 つの変数を宣言しています。

```
__int8 nSmall;      // Declares 8-bit integer
__int16 nMedium;    // Declares 16-bit integer
__int32 nLarge;     // Declares 32-bit integer
__int64 nHuge;      // Declares 64-bit integer
```

サイズ設定された整数の最初の 3 つの型は、同じサイズを持つ ANSI 型のシノニムで、複数のプラットフォームで同じように動作する移植性のあるコードを作成する場合に便利です。 __int8 データ型は char 型と同じ意味であり、\___int16 は short 型と同じ意味であり \___int32 は int 型と同じ意味です。\___int64 型には、同等の ANSI 型はありません。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[基本型の格納](../c-language/storage-of-basic-types.md)
