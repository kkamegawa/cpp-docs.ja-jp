---
title: コンパイラ エラー C2393
ms.date: 11/04/2016
f1_keywords:
- C2393
helpviewer_keywords:
- C2393
ms.assetid: 4bd95728-e813-4ce8-844a-c6ebe235ca82
ms.openlocfilehash: 39ca693aed3f08e7b2df3d687f94d93384393f23
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302398"
---
# <a name="compiler-error-c2393"></a>コンパイラ エラー C2393

> '*シンボル*': appdomain ごとのシンボルをセグメントに割り当てることができない'*セグメント*'

## <a name="remarks"></a>Remarks

**/Clr: 純粋な**と **/clr:safe**コンパイラ オプションは Visual Studio 2015 で非推奨とされ、Visual Studio 2017 でサポートされていません。

使用[appdomain](../../cpp/appdomain.md)変数を使ってコンパイルすることを意味する **/clr: 純粋な**または **/clr:safe**、safe または純粋なイメージは、データ セグメントを含めることはできません。

参照してください[/clr (共通言語ランタイムのコンパイル)](../../build/reference/clr-common-language-runtime-compilation.md)詳細についてはします。

## <a name="example"></a>例

次の例では、C2393 が生成されます。 この問題を解決するには、データ セグメントを作成しないでください。

```cpp
// C2393.cpp
// compile with: /clr:pure /c
#pragma data_seg("myseg")
int n = 0;   // C2393
```