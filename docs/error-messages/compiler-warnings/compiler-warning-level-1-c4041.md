---
title: コンパイラの警告 (レベル 1) C4041
ms.date: 11/04/2016
f1_keywords:
- C4041
helpviewer_keywords:
- C4041
ms.assetid: 107ee9fd-4b88-4f22-a18f-a20726831095
ms.openlocfilehash: 6e1f2a2396447038f6a117f66d4002bea7fd7486
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151319"
---
# <a name="compiler-warning-level-1-c4041"></a>コンパイラの警告 (レベル 1) C4041

コンパイラの制限 : ブラウザーの出力を中止します。

ブラウザー情報がコンパイラの制限を超えました。

この警告は、 [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) (ローカル変数を含めたブラウザー情報) でコンパイルすると発生することがあります。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>修復の可能性がある解決策

1. /Fr (ローカル変数を含まないブラウザー情報) でコンパイルします。

1. ブラウザーの出力 (/FR や /Fr なしのコンパイル) を無効にします。