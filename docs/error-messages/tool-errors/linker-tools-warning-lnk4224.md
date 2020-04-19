---
title: リンカー ツールの警告 LNK4224
ms.date: 11/04/2016
f1_keywords:
- LNK4224
helpviewer_keywords:
- LNK4224
ms.assetid: 8624b70e-0b93-43cf-b457-834d38632d0b
ms.openlocfilehash: eb0a019cc80e5218a52697b8bcd5e91b811d04d3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160394"
---
# <a name="linker-tools-warning-lnk4224"></a>リンカー ツールの警告 LNK4224

> *オプション*はサポートされていません無視されます。

## <a name="remarks"></a>Remarks

無効な古いリンカー オプションが指定され、無視されます。

たとえば、LNK4224 発生する可能性が/comment ディレクティブが表示される場合 .obj。経由で追加された/comment ディレクティブ、[コメント (C/C++)](../../preprocessor/comment-c-cpp.md)プラグマ、非推奨の exestr オプションを使用します。 Dumpbin を使用して、 [/all](../../build/reference/all.md)リンカー ディレクティブを .obj ファイルの表示にします。

可能であれば、.obj ファイルのソースを変更し、プラグマを削除します。 この警告を無視する場合、.executable コンパイルされている可能性があります **/clr: 純粋な**は期待どおりに実行されません。 **/Clr: 純粋な**コンパイラ オプションは Visual Studio 2015 で非推奨とされ、Visual Studio 2017 でサポートされていません。

## <a name="example"></a>例

次の例では、LNK4224 が生成されます。

```cpp
// LNK4224.cpp
// compile with: /c /Zi
// post-build command: link LNK4224.obj /debug /debugtype:map
int main () {
   return 0;
}
```