---
title: 関数本体または変数の未定義
ms.date: 11/04/2016
helpviewer_keywords:
- function body
- variables, missing
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
ms.openlocfilehash: 5e3436054d69da7fb67c240c1d684585734635c3
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857157"
---
# <a name="missing-function-body-or-variable"></a>関数本体または変数の未定義

関数プロトタイプだけでは、コンパイラがエラーを発生させず続行できますが、関数コードまたは予約された変数の領域がないために、リンカーがアドレスへの呼び出しを解決することはできません。 リンカーを解決する必要があります関数への呼び出しを作成するまでに、このエラーを表示はされません。

## <a name="example"></a>例

メインの関数呼び出しは、プロトタイプにより、関数の存在を考慮するため、lnk2019 エラーが発生します。  リンカーは、しないことを検出します。

```cpp
// LNK2019_MFBV.cpp
// LNK2019 expected
void DoSomething(void);
int main() {
   DoSomething();
}
```

## <a name="example"></a>例

C++ では、クラス定義でクラスをプロトタイプだけでなく、特定の関数の実装を含めることを確認します。 ヘッダー ファイルの外部でクラスを定義する場合は、関数の前にクラス名を含めることを確認する (`Classname::memberfunction`)。

```cpp
// LNK2019_MFBV_2.cpp
// LNK2019 expected
struct A {
   static void Test();
};

// Should be void A::Test() {}
void Test() {}

int main() {
   A AObject;
   AObject.Test();
}
```

## <a name="see-also"></a>関連項目

[リンカー ツール エラー LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)