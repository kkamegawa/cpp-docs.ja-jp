---
title: 廃止された呼び出し規約
ms.date: 11/04/2016
f1_keywords:
- __fortran
- __pascal
- __syscall
helpviewer_keywords:
- WINAPI [C++]
- __syscall keyword [C++]
- __pascal keyword [C++]
- __fortran keyword [C++]
- calling conventions, obsolete
ms.assetid: a91fc665-034a-48ce-b6bd-d27125f308a7
ms.openlocfilehash: 7f059afe02cbbad77920fd8c4a0e6cb7c958e992
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857360"
---
# <a name="obsolete-calling-conventions"></a>廃止された呼び出し規約

**Microsoft 固有の仕様**

**__Pascal**、 **__fortran**、および **__syscall**の呼び出し規約はサポートされなくなりました。 サポートされる呼び出し規則および適切なリンカー オプションの 1 つを使用して、それらの機能をエミュレートできます。

\<windows .h > では、WINAPI マクロがサポートされるようになりました。これは、ターゲットの適切な呼び出し規約に変換されます。 以前に PASCAL または **__far \__pascal**を使用した場合は、WINAPI を使用します。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>参照

[引数の渡し規則と名前付け規則](../cpp/argument-passing-and-naming-conventions.md)