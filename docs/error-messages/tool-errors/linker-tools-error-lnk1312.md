---
title: リンカ ツール エラー LNK1312
ms.date: 11/04/2016
f1_keywords:
- LNK1312
helpviewer_keywords:
- LNK1312
ms.assetid: 48284abb-d849-43fc-ab53-45aded14fd8a
ms.openlocfilehash: e462d24f2eb54718ba73617146aab96bb14a66df
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990905"
---
# <a name="linker-tools-error-lnk1312"></a>リンカ ツール エラー LNK1312

ファイルが無効であるか壊れています: アセンブリをインポートできません

アセンブリをビルドするときに、 **/clr**でコンパイルされたモジュールまたはアセンブリ以外のファイルが、 **/assemblymodule**リンカーオプションに渡されました。  オブジェクトファイルを **/Dns モジュール**に渡した場合は、 **/assemblymodule**ではなく、直接リンカーにオブジェクトを渡します。

## <a name="example"></a>使用例

次の例では、.obj ファイルを作成しました。

```cpp
// LNK1312.cpp
// compile with: /clr /LD
public ref class A {
public:
   int i;
};
```

## <a name="example"></a>使用例

次の例では、LNK1312 が生成されます。

```cpp
// LNK1312_b.cpp
// compile with: /clr /LD /link /assemblymodule:LNK1312.obj
// LNK1312 error expected
public ref class M {};
```
