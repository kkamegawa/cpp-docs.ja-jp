---
title: コンパイラ エラー C3005
ms.date: 11/04/2016
f1_keywords:
- C3005
helpviewer_keywords:
- C3005
ms.assetid: 30bad565-e79f-4c3f-82cb-a74bd0baab8f
ms.openlocfilehash: b260879dfafbe40ab13d14f7208f1ffbc90b9826
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302160"
---
# <a name="compiler-error-c3005"></a>コンパイラ エラー C3005

'error_text' : OpenMP 'directive' ディレクティブでは予期しないトークンです

OpenMP ディレクティブの形式が正しくありません。

次の例では C3005 が生成されます。

```c
// C3005.c
// compile with: /openmp
int main()
{
   #pragma omp parallel + for   // C3005
}
```

プラグマと同じ行で始め中かっこを使用した場合も、C3005 が発生します。

```c
// C3005b.c
// compile with: /openmp
int main() {
   #pragma omp parallel {   // C3005 put open brace on next line
   lbl2:;
   }
   goto lbl2;
}
```
