---
title: コンパイラの警告 (レベル 1) C4532
ms.date: 11/04/2016
f1_keywords:
- C4532
helpviewer_keywords:
- C4532
ms.assetid: 4e2a286a-d233-4106-9f65-29be1a94ca02
ms.openlocfilehash: b47eb192bc01e6fe2c6c9423ed2c672f16c6818f
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966246"
---
# <a name="compiler-warning-level-1-c4532"></a>コンパイラの警告 (レベル 1) C4532

' continue ': __finally/finally ブロックからジャンプすると、終了処理中に未定義の動作が発生します

コンパイラは、次のいずれかのキーワードを検出しました。

- [continue](../../cpp/continue-statement-cpp.md)

- [break](../../cpp/break-statement-cpp.md)

- [goto](../../cpp/goto-statement-cpp.md)

異常終了時に[__finally](../../cpp/try-finally-statement.md)または[finally](../../dotnet/finally.md)ブロックからジャンプする。

例外が発生したとき、終了ハンドラーの実行中にスタックがアンワインドされているとき (`__finally` または finally ブロック)、`__finally` ブロックが終了する前にコードが `__finally` ブロックからジャンプした場合、動作は未定義になります。 コントロールはアンワインドコードに戻らない場合があるため、例外が適切に処理されない可能性があります。

**__Finally**ブロックから移動する必要がある場合は、最初に異常終了を確認してください。

次の例では、C4532 が生成されます。警告を解決するには、ジャンプステートメントをコメントアウトするだけです。

```cpp
// C4532.cpp
// compile with: /W1
// C4532 expected
int main() {
   int i;
   for (i = 0; i < 10; i++) {
      __try {
      } __finally {
         // Delete the following line to resolve.
         continue;
      }

      __try {
      } __finally {
         // Delete the following line to resolve.
         break;
      }
   }
}
```