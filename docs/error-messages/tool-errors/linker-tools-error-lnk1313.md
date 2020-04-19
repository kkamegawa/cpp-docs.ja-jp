---
title: リンカ ツール エラー LNK1313
ms.date: 11/04/2016
f1_keywords:
- LNK1313
helpviewer_keywords:
- LNK1313
ms.assetid: 5df0b72e-bb3f-428c-8d84-6084238f9827
ms.openlocfilehash: 380df2bff305acc47e423d69ea702d77c4eafdfd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160433"
---
# <a name="linker-tools-error-lnk1313"></a>リンカ ツール エラー LNK1313

> ijw/ネイティブ モジュールが検出されました。純粋なモジュールとリンクできません。

## <a name="remarks"></a>Remarks

Visual C の現在のバージョンは、ネイティブまたは混合のマネージド/ネイティブ .obj ファイルでコンパイルされた .obj ファイルをリンクをサポートしていない **/clr: 純粋な**します。

**/Clr: 純粋な**コンパイラ オプションは Visual Studio 2015 で非推奨とされ、Visual Studio 2017 でサポートされていません。

## <a name="example"></a>例

```cpp
// LNK1313.cpp
// compile with: /c /clr:pure
// a pure module
int main() {}
```

## <a name="example"></a>例

```cpp
// LNK1313_b.cpp
// compile with: /c /clr
// an IJW module
void test(){}
```

## <a name="example"></a>例

次の例では lnk1313 エラーが生成されます。

```cpp
// LNK1313_c.cpp
// compile with: /link LNK1313.obj LNK1313_b.obj
// LNK1313 warning expected
```