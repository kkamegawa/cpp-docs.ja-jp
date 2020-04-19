---
title: コンパイラ エラー C2316
ms.date: 07/08/2019
f1_keywords:
- C2316
helpviewer_keywords:
- C2316
ms.assetid: 9ad08eb5-060b-4eb0-8d66-0dc134f7bf67
ms.openlocfilehash: 5a3d9052775a5e1cbedfd58ccaaf0ff039a8475d
ms.sourcegitcommit: 07b34ca1c1fecced9fadc95de15dc5fee4f31e5a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2019
ms.locfileid: "67693442"
---
# <a name="compiler-error-c2316"></a>コンパイラ エラー C2316

> '*class_type*': デストラクターまたはコピー コンス トラクターがアクセスできないか削除としてキャッチできない、

値渡しまたは参照はコピー コンス トラクター、代入演算子で例外が検出されましたまたは両方にアクセスできませんでした。

## <a name="remarks"></a>Remarks

Visual Studio 2015 の準拠に関する変更は、このエラーから派生した MFC 例外の不適切な catch ステートメントに適用を行った`CException`します。 `CException`継承されたプライベート コピー コンス トラクター、クラスとその派生クラスはコピー可能なされ、それらの値によってキャッチできないことも意味値によって渡すことができません。 MFC 例外をキャッチして、実行時に例外がキャッチされていない値でステートメントをキャッチします。 ここでコンパイラは正しくこのような状況を識別し、エラー C2316 が報告します。 この問題を解決するには、する MFC TRY/CATCH マクロを使用して作成するよりも、独自の例外ハンドラーを勧めします。 しない場合は、コードの適切な場合、代わりに参照によって MFC 例外をキャッチします。

## <a name="example"></a>例

次の例では、C2316 を生成し、その修正方法を示しています。

```cpp
// C2316.cpp
// compile with: /EHsc
#include <stdio.h>

struct B
{
public:
    B() {}
    // Delete the following line to resolve.
private:
    // copy constructor
    B(const B&) {}
};

void f(const B&)
{
}

int main()
{
    try
    {
        B aB;
        f(aB);
    }
    catch (B b)    // C2316
    {
        printf_s("Caught an exception!\n");
    }
}
```
