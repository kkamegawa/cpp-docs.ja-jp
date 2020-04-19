---
title: コンパイラの警告 (レベル 4) C4062
ms.date: 04/05/2019
f1_keywords:
- C4062
helpviewer_keywords:
- C4062
ms.assetid: 36d1c6ae-c917-4b08-bf30-2eb49ee94169
ms.openlocfilehash: 79658afc31565b708cdbd8a88f49b887cdd10cf3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401411"
---
# <a name="compiler-warning-level-4-c4062"></a>コンパイラの警告 (レベル 4) C4062

> 列挙子 '*識別子*'列挙型のスイッチは' in*列挙*' はハンドルされません

列挙子*識別子*に関連付けられていないが`case`でハンドラーを`switch`ステートメントがあるとありません`default`ラベルがそれをキャッチできます。 不足している場合は、監視機能があります、コード内の潜在的なエラーです。 使用されていない列挙子に関連する警告の`switch`を持つステートメントを`default`場合は、「」を参照[C4061](compiler-warning-level-4-c4061.md)します。

既定では、この警告はオフに設定されています。 既定で無効になっている警告を有効にする方法の詳細については、次を参照してください。[コンパイラの警告を Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)します。

## <a name="example"></a>例

次の例は、C4062 が生成され、その修正方法を示しています。

```cpp
// C4062.cpp
// compile with: /EHsc /W4
#pragma warning(default : 4062)
enum E { a, b, c };
void func ( E e ) {
   switch(e) {
      case a:
      case b:
   // case c:  // to fix, uncomment this line
      break;   // no default label
   }   // C4062, enumerator 'c' not handled
}

int main() {
}
```

## <a name="see-also"></a>関連項目

[コンパイラの警告 (レベル 4) C4061](compiler-warning-level-4-c4061.md)
