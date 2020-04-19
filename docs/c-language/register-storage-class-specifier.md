---
title: register ストレージ クラス指定子
ms.date: 11/04/2016
helpviewer_keywords:
- register variables
- register storage class
ms.assetid: 7577bf48-88ec-4191-873c-ef4217a4034e
ms.openlocfilehash: 0fac6db2254a909d0ec558a7e76f7ccf32aa7ac3
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147348"
---
# <a name="register-storage-class-specifier"></a>register ストレージ クラス指定子

**Microsoft 固有の仕様**

Microsoft C/C++ コンパイラは、レジスタ変数に対するユーザーの要求を考慮しません。 ただし、移植性を考慮して、**register** キーワードに関連付けられた他のセマンティクスは、すべてコンパイラによって実行されます。 たとえば、レジスタ オブジェクトに単項アドレス演算子 (**&**) を適用することはできず、配列で **register** キーワードを使用することもできません。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[内部レベル宣言のストレージ クラス指定子](../c-language/storage-class-specifiers-for-internal-level-declarations.md)
