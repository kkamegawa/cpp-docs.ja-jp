---
title: コンパイラの警告 C4936
ms.date: 11/04/2016
f1_keywords:
- C4936
helpviewer_keywords:
- C4936
ms.assetid: 6676de35-bf1b-4d0b-a70f-b5734130336c
ms.openlocfilehash: bbb69cccbf93be6e97d13db5008780f57e63f9da
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62280855"
---
# <a name="compiler-warning-c4936"></a>コンパイラの警告 C4936

> この __declspec は、/clr または /clr:pure でコンパイルされるときのみサポートされます

## <a name="remarks"></a>Remarks

**/Clr: 純粋な**コンパイラ オプションは Visual Studio 2015 で非推奨とされ、Visual Studio 2017 でサポートされていません。

`__declspec` 修飾子が使用されましたが、この `__declspec` 修飾子は、いずれかの [/clr](../../build/reference/clr-common-language-runtime-compilation.md) オプションでコンパイルされた場合にのみ有効です。

詳細については、「 [appdomain](../../cpp/appdomain.md) 」および「 [process](../../cpp/process.md)」を参照してください。

C4936 は、常にエラーとして表示されます。  [warning](../../preprocessor/warning.md) プラグマを使用して、C4936 を無効にすることができます。

## <a name="example"></a>例

次の例では C4936 が生成されます。

```cpp
// C4936.cpp
// compile with: /c
// #pragma warning (disable : 4936)
__declspec(process) int i;   // C4936
__declspec(appdomain) int j;   // C4936
```