---
title: 区切り記号 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- punctuators [C++]
ms.assetid: 1521564c-a977-488a-9490-068079897592
ms.openlocfilehash: cef34a17de99a189a590ac3f13c0db9563df643c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62244234"
---
# <a name="punctuators-c"></a>区切り記号 (C++)

C++ の区切り記号はコンパイラに対する構文上およびセマンティック上の意味を持ちますが、それ自体は値を生成する演算を指定しません。 一部の区切り記号 (単独または組み合わせ) は、C++ の演算子としても使用できたり、プリプロセッサで意味を持つことがあります。

次の文字が区切り記号と見なされます。

```
! % ^ & * ( ) - + = { } | ~
[ ] \ ; ' : " < > ? , . / #
```

区切り記号 **[]**、**に関するページ ()**、および **{}** 後に、ペアで使用する必要があります[変換フェーズ](../preprocessor/phases-of-translation.md)4 です。

## <a name="see-also"></a>関連項目

[構文規則](../cpp/lexical-conventions.md)