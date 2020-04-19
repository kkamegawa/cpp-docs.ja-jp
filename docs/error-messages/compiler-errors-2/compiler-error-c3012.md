---
title: コンパイラ エラー C3012
ms.date: 11/04/2016
f1_keywords:
- C3012
helpviewer_keywords:
- C3012
ms.assetid: cc7040b1-b3fb-4da6-a474-877914d30332
ms.openlocfilehash: 9fe0ac7d3637cad3a5571c4631345dac1a0021bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386734"
---
# <a name="compiler-error-c3012"></a>コンパイラ エラー C3012

> '*組み込み*': 組み込み関数は、並行領域内で直接許可されていません

 [コンパイラ組み込み関数](../../intrinsics/compiler-intrinsics.md) は、 `omp parallel` 領域では使用できません。 この問題を修正するには、組み込み関数をリージョンの外に移動または非組み込みと同等に置き換えます。

## <a name="example"></a>例

次の例では、C3012 を生成し、その修正方法を示しています。

```cpp
// C3012.cpp
// compile with: /openmp
#ifdef __cplusplus
extern "C" {
#endif
void* _ReturnAddress();
#ifdef __cplusplus
}
#endif

int main()
{
   #pragma omp parallel
   {
      _ReturnAddress();   // C3012
   }
   _ReturnAddress();      // OK
}
```