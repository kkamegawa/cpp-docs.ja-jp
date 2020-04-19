---
title: コンパイラの警告 (レベル 1) C4377
ms.date: 11/04/2016
f1_keywords:
- C4377
helpviewer_keywords:
- C4377
ms.assetid: a1c797b8-cd5e-4a56-b430-d07932e811cf
ms.openlocfilehash: 30e2ecb1d5e0de290c028cdfb53c7df831a732b4
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966459"
---
# <a name="compiler-warning-level-1-c4377"></a>コンパイラの警告 (レベル 1) C4377

ネイティブ型は、既定ではプライベートです。-d1PrivateNativeTypes は非推奨です

以前のリリースでは、アセンブリ内のネイティブ型は既定でパブリックになっており、非公開にするためにドキュメントに記載されていないコンパイラオプション ( **/d1PrivateNativeTypes**) が使用されていました。

ネイティブと CLR のすべての型は、アセンブリで既定でプライベートになったため、 **/d1PrivateNativeTypes**は不要になりました。

## <a name="example"></a>例

次の例では、C4377 が生成されます。

```cpp
// C4377.cpp
// compile with: /clr /d1PrivateNativeTypes /W1
// C4377 warning expected
int main() {}
```