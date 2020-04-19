---
title: コンパイラ エラー C2299
ms.date: 11/04/2016
f1_keywords:
- C2299
helpviewer_keywords:
- C2299
ms.assetid: d001c2bc-f6fd-47aa-8e42-0eb824d6441d
ms.openlocfilehash: 009a441ec610053176e79126d9f2663f29b26bc6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759049"
---
# <a name="compiler-error-c2299"></a>コンパイラ エラー C2299

' function ': 動作の変更: 明示的な特殊化をコピーコンストラクターまたはコピー代入演算子にすることはできません

このエラーは、Visual Studio 2005 で実行されたコンパイラ準拠作業の結果として生成されることもC++あります。以前のバージョンのビジュアルでは、コピーコンストラクターまたはコピー代入演算子に対して明示的に特殊化されています。

C2299 を解決するには、コピーコンストラクターまたは代入演算子をテンプレート関数ではなく、クラス型を受け取るテンプレートではない関数を作成しないようにします。 テンプレート引数を明示的に指定してコピーコンストラクターまたは代入演算子を呼び出すコードでは、テンプレート引数を削除する必要があります。

次の例では、C2299 が生成されます。

```cpp
// C2299.cpp
// compile with: /c
class C {
   template <class T>
   C (T t);

   template <> C (const C&);   // C2299
   C (const C&);   // OK
};
```
