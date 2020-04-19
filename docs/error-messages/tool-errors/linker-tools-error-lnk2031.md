---
title: リンカ ツール エラー LNK2031
ms.date: 11/04/2016
f1_keywords:
- LNK2031
helpviewer_keywords:
- LNK2031
ms.assetid: 18ed4b6e-3e75-443c-bbd8-2f6030dc89ee
ms.openlocfilehash: 003b9a58bfb08130f034530f59e2de27efa2ae8d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298920"
---
# <a name="linker-tools-error-lnk2031"></a>リンカ ツール エラー LNK2031

> p/invoke を生成できません"*function_declaration*" *decorated_name*; 呼び出し規約がメタデータに見つかりません

## <a name="remarks"></a>Remarks

ネイティブ関数を純粋なイメージにインポートしようとすると、暗黙の呼び出し規約がネイティブと純粋なコンパイルの間で異なることに注意してください。 純粋なイメージの詳細については、次を参照してください。[純粋で検証可能なコード (C +/cli CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)します。

**/Clr: 純粋な**コンパイラ オプションは Visual Studio 2015 で非推奨とされ、Visual Studio 2017 でサポートされていません。

## <a name="example"></a>例

このコード サンプルには、呼び出し規約が暗黙的には、ネイティブ、エクスポートされた関数を使用したコンポーネントが生成されます[_ _cdecl](../../cpp/cdecl.md)します。

```cpp
// LNK2031.cpp
// compile with: /LD
extern "C" {
   __declspec(dllexport) int func() { return 3; }
};
```

## <a name="example"></a>例

次の例では、ネイティブ関数を使用する純粋なクライアントを作成します。 ただし、下の呼び出し規約 **/clr: 純粋な**は[_ _clrcall](../../cpp/clrcall.md)します。 次の例では、LNK2031 が生成されます。

```cpp
// LNK2031_b.cpp
// compile with: /clr:pure LNK2031.lib
// LNK2031 expected
extern "C" int func();

int main() {
   return func();
}
```

## <a name="example"></a>例

次の例では、純粋なイメージからネイティブ関数を使用する方法を示します。 明示的に注意してください **_ _cdecl**呼び出し元の規則の指定子。

```cpp
// LNK2031_c.cpp
// compile with: /clr:pure LNK2031.lib
extern "C" int __cdecl func();

int main() {
   return func();
}
```