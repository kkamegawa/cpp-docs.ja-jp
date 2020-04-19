---
title: リンカ ツール エラー LNK2028
ms.date: 11/04/2016
f1_keywords:
- LNK2028
helpviewer_keywords:
- LNK2028
ms.assetid: e2b03293-6066-464d-a050-ce747bcf7f0e
ms.openlocfilehash: ed2dc1a95d4dd7c447b360da21b5046e20f79083
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298985"
---
# <a name="linker-tools-error-lnk2028"></a>リンカ ツール エラー LNK2028

"*exported_function*"(*decorated_name*) 関数で参照されている"*function_containing_function_call*"(*decorated_name*)

## <a name="remarks"></a>Remarks

ネイティブ関数を純粋なイメージにインポートしようとすると、暗黙の呼び出し規約がネイティブと純粋なコンパイルの間で異なることに注意してください。

**/Clr: 純粋な**コンパイラ オプションは Visual Studio 2015 で非推奨とされ、Visual Studio 2017 でサポートされていません。

## <a name="example"></a>例

このコード サンプルには、呼び出し規約が暗黙的には、ネイティブ、エクスポートされた関数を使用したコンポーネントが生成されます[_ _cdecl](../../cpp/cdecl.md)します。

```cpp
// LNK2028.cpp
// compile with: /LD
__declspec(dllexport) int func() {
   return 3;
}
```

## <a name="example"></a>例

次の例では、ネイティブ関数を使用する純粋なクライアントを作成します。 ただし、下の呼び出し規約 **/clr: 純粋な**は[_ _clrcall](../../cpp/clrcall.md)します。 次の例では、LNK2028 が生成されます。

```cpp
// LNK2028_b.cpp
// compile with: /clr:pure lnk2028.lib
// LNK2028 expected
int func();

int main() {
   return func();
}
```