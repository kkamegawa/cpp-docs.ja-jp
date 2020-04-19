---
title: コンパイラの警告 (レベル 3) C4278
ms.date: 08/27/2018
f1_keywords:
- C4278
helpviewer_keywords:
- C4278
ms.assetid: 4b6053fb-df62-4c04-b6c8-c011759557b8
ms.openlocfilehash: 8c5c15105581602566116d3ed82b89a6337435c9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402165"
---
# <a name="compiler-warning-level-3-c4278"></a>コンパイラの警告 (レベル 3) C4278

> '*識別子*': タイプ ライブラリ内の識別子'*tlb*' は既にマクロです 'rename' 修飾子。

使用する場合[#import](../../preprocessor/hash-import-directive-cpp.md)、インポートするタイプ ライブラリ内の識別子は、識別子を宣言しようとします。*識別子*します。 ただし、これは有効なシンボルでは既にします。

使用して、 `#import` **の名前を変更**属性をタイプ ライブラリ内のシンボルにエイリアスを割り当てます。