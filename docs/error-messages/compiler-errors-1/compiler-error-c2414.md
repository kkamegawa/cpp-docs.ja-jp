---
title: コンパイラ エラー C2414
ms.date: 11/04/2016
f1_keywords:
- C2414
helpviewer_keywords:
- C2414
ms.assetid: bbe94e03-862e-4990-b15e-544ae464727d
ms.openlocfilehash: 84fa715c8bd567770f361552e203a37c44ffdde4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402984"
---
# <a name="compiler-error-c2414"></a>コンパイラ エラー C2414

オペランドの数が正しくありません。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>次のような原因をチェックして問題を解決するには

1. オペコードに使われているオペランドの数が正しくありません。 アセンブリ言語のリファレンス マニュアルで、正しいオペランド数を調べてください。

1. 最近のプロセッサでは、オペランド数が異なる命令もサポートされます。 調整、 [/arch (最小限の CPU アーキテクチャ)](../../build/reference/arch-minimum-cpu-architecture.md)それ以降のプロセッサを使用するオプション。