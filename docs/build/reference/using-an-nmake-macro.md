---
title: NMAKE マクロの使用
ms.date: 11/04/2016
helpviewer_keywords:
- macros, NMAKE
- NMAKE macros, using
ms.assetid: 95c87fbc-76e6-48c0-8536-9bfe179f328e
ms.openlocfilehash: fb3b154ba8b30bbfc9a6c7c6b37720e5c60d6327
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317251"
---
# <a name="using-an-nmake-macro"></a>NMAKE マクロの使用

マクロを使用するには、ドル記号 ($) を次のように続くかっこ内の名前を囲みます。

## <a name="syntax"></a>構文

```
$(macroname)
```

## <a name="remarks"></a>Remarks

スペースは許可されません。 かっこは省略可能な場合は*macroname*は単一の文字。 定義の文字列に $ が置き換えられます (*macroname*)。 未定義のマクロは、null 文字列に置換されます。

## <a name="what-do-you-want-to-know-more-about"></a>さらに詳しくは次のトピックをクリックしてください

[マクロでの代入](macro-substitution.md)

## <a name="see-also"></a>関連項目

[マクロと NMAKE](macros-and-nmake.md)
