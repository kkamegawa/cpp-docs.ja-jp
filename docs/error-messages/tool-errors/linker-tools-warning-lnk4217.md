---
title: リンカー ツールの警告 LNK4217
ms.date: 07/23/2019
f1_keywords:
- LNK4217
helpviewer_keywords:
- LNK4217
ms.assetid: 280dc03e-5933-4e8d-bb8c-891fbe788738
ms.openlocfilehash: 1301dd53f71c616d7b7af346923a54c42903c9fd
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450854"
---
# <a name="linker-tools-warning-lnk4217"></a>リンカー ツールの警告 LNK4217

> '*filename_1*' で定義されたシンボル '*symbol*' は、関数 '*function*' の '*filename_2*' によってインポートされています

シンボルが同じイメージ内のオブジェクトファイルで定義されているにもかかわらず、シンボルに[__declspec (dllimport)](../../cpp/dllexport-dllimport.md)が指定されました。 この警告`__declspec(dllimport)`を解決するには、修飾子を削除します。

## <a name="remarks"></a>Remarks

*symbol*は、イメージ内で定義されているシンボル名です。 *関数*は、シンボルをインポートする関数です。

この警告は、 [/clr](../../build/reference/clr-common-language-runtime-compilation.md)オプションを使用してコンパイルした場合には表示されません。

LNK4217 は、2つのモジュールをリンクしようとした場合にも発生する可能性があります。代わりに、最初のモジュールのインポートライブラリを使用して2番目のモジュールをコンパイルする必要があります。

```cpp
// main.cpp
__declspec(dllimport) void func();

int main()
{
    func();
    return 0;
}

```

この場合、次のようになります。

```cpp
// tt.cpp
// compile with: /c
void func() {}
```

次に示すように、これら2つのモジュールをコンパイルしようとすると、LNK4217 が発生します。

```cmd
cl.exe /c main.cpp tt.cpp
link.exe main.obj tt.obj
```

このエラーを解決するには、2つのファイルをコンパイルした後、.tt に .tt を渡して .lib ファイルを作成し、次に示すように、.tt を使用して .obj をリンクします。

```cmd
cl.exe /c main.cpp tt.cpp
lib.exe tt.obj /export:func /def
link.exe main.obj tt.lib
```

## <a name="see-also"></a>関連項目

[リンカーツールの警告 LNK4049](linker-tools-warning-lnk4049.md) \
[リンカーツールの警告 LNK4286](linker-tools-warning-lnk4286.md) \
[dllexport、dllimport](../../cpp/dllexport-dllimport.md)