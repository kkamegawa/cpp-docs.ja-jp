---
title: バッチモード規則
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- NMAKE program, inference rules
- batch-mode inference rules in NMAKE
ms.assetid: 0650b547-ef19-4455-9bba-fa567dcf88f2
ms.openlocfilehash: f01866e347b2734b5adfd111e3ae9de4f9edcf9f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295020"
---
# <a name="batch-mode-rules"></a>バッチモード規則

```
{frompath}.fromext{topath}.toext::
   commands
```

バッチモード推論規則は、n 個のコマンドがこの推論規則を進めるときに推論規則の 1 つだけの呼び出しを提供します。 バッチモード推論のルールを含まない n 個のコマンドを呼び出すことが必要です。 N は、推論規則をトリガーする依存オブジェクトの数です。

バッチモード推論規則が含まれているメイクファイルには、NMAKE 1.62 以降のバージョンを使用する必要があります。 (Nmake の) バージョンを確認するには、1.62 以降 (nmake の) バージョンで使用可能な _NMAKE_VER マクロを実行します。 このマクロは、Visual C 製品のバージョンを表す文字列を返します。

標準の推論規則からのみ構文の違いは、バッチモード推論規則は 2 つのコロン (:) で終了されていることです。

> [!NOTE]
>  呼び出されているツールは、複数のファイルを処理できる必要があります。 バッチモード推論規則を使用する必要があります`$<`依存ファイルにアクセスするには、マクロとして。

バッチモード推論規則は、ビルド処理を高速化できます。 高速化のバッチでコンパイラにファイルを指定するためは、コンパイラ ドライバが 1 回だけ呼び出されます。 たとえば、C および C++ コンパイラは、処理中に常駐しているメモリを保持できるため、一連のファイルを処理するときより実行します。

次の例では、バッチ モードの推論のルールを使用する方法を示します。

```
#
# sample makefile to illustrate batch-mode inference rules
#
O = .
S = .
Objs = $O/foo1.obj $O/foo2.obj $O/foo2.obj $O/foo3.obj $O/foo4.obj
CFLAGS = -nologo

all : $(Objs)

!ifdef NOBatch
{$S}.cpp{$O}.obj:
!else
{$S}.cpp{$O}.obj::
!endif
   $(CC) $(CFLAGS) -Fd$O\ -c $<

$(Objs) :

#end of makefile
```

NMAKE では、バッチ モードの推論規則のない、次の出力が生成されます。

```
E:\tmp> nmake -f test.mak -a NOBatch=1

Microsoft (R) Program Maintenance Utility   Version 7.00.0000
Copyright (C) Microsoft Corp 1988-2001. All rights reserved.
        cl -nologo -Fd.\ -c .\foo1.cpp
foo1.cpp
        cl -nologo -Fd.\ -c .\foo2.cpp
foo2.cpp
        cl -nologo -Fd.\ -c .\foo3.cpp
foo3.cpp
        cl -nologo -Fd.\ -c .\foo4.cpp
foo4.cpp
```

Nmake の推論の規則をバッチ モードでは、次の結果。

```
E:\tmp> nmake -f test.mak -a

Microsoft (R) Program Maintenance Utility   Version 7.00.0000
Copyright (C) Microsoft Corp 1988-2001. All rights reserved.

        cl -nologo -Fd.\ -c .\foo1.cpp .\foo2.cpp .\foo3.cpp .\foo4.cpp
foo1.cpp
foo2.cpp
foo3.cpp
foo4.cpp
Generating Code...
```

## <a name="see-also"></a>関連項目

[推論規則](inference-rules.md)
