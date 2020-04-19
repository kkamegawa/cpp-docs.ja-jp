---
title: __declspec(dllimport) を使った関数呼び出しのインポート
ms.date: 11/04/2016
f1_keywords:
- __declspec
- dllimport
helpviewer_keywords:
- importing function calls [C++]
- dllimport attribute [C++], function call imports
- __declspec(dllimport) keyword [C++]
- function calls [C++], importing
ms.assetid: 6b53c616-0c6d-419a-8e2a-d2fff20510b3
ms.openlocfilehash: 8635cf5d389f72972f471a4fd53ed56c3497bfe9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188796"
---
# <a name="importing-function-calls-using-declspecdllimport"></a>__declspec(dllimport) を使った関数呼び出しのインポート

次のコード例は、使用する方法を示しています。 **_declspec(dllimport)** DLL から関数呼び出しをアプリケーションにインポートします。 ある`func1`関数を含む .exe ファイルとは別の DLL に存在するは、**メイン**関数。

せず **_declspec**、このコードを指定します。

```
int main(void)
{
   func1();
}
```

コンパイラでは、次のようなコードが生成されます。

```
call func1
```

リンカーは、次のように呼び出しを変換します。

```
call 0x4000000         ; The address of 'func1'.
```

場合`func1`内に存在する別の DLL リンカーを直接解決することはできませんのアドレスを知る方法があるないため`func1`です。 16 ビットの環境では、リンカーは、このコードのアドレスをローダーは、正しいアドレスが実行時に修正プログラムは .exe ファイルの一覧に追加します。 32 ビットおよび 64 ビット環境では、リンカーは、アドレスを通知するサンクを生成します。 32 ビット環境では、サンクは、ようになります。

```
0x40000000:    jmp DWORD PTR __imp_func1
```

ここで`imp_func1`のアドレス、 `func1` .exe ファイルのインポート アドレス テーブル内のスロット。 すべてのアドレスはこのため、リンカーに認識します。 ローダーは、のみ、正常に動作するすべての読み込み時に、.exe ファイルのインポート アドレス テーブルを更新する必要があります。

したがってを使用して **_declspec**が必要ない場合、リンカーがサンクを生成しませんのでお勧めします。 サンクを指定するためのコードは大きく (RISC システムでは、ことができますいくつかの手順) と、キャッシュのパフォーマンスが低下することができます。 DLL 内の関数がコンパイラに指示はの間接呼び出しを生成できます。

これでこのコード:

```
__declspec(dllimport) void func1(void);
int main(void)
{
   func1();
}
```

この命令が生成されます。

```
call DWORD PTR __imp_func1
```

存在しないサンク`jmp`命令、コード サイズが小さく、高速化するようにします。

その一方で、DLL 内の関数呼び出し、たくない間接呼び出しを使用する必要があります。 関数のアドレスがわかっています。 読み込みし、間接的な呼び出しの前に関数のアドレスを格納するのには、時間と領域が必要なため、直接呼び出しは常に高速で小さい。 使用する **_declspec** DLL 自体の外部から DLL 関数を呼び出すとき。 使用しない **_declspec**その DLL を作成するときに、DLL 内の関数にします。

## <a name="see-also"></a>関連項目

[アプリケーションへのインポート](importing-into-an-application.md)
