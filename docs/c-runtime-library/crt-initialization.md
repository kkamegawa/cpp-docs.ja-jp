---
title: CRT の初期化
ms.date: 11/04/2016
helpviewer_keywords:
- CRT initialization [C++]
ms.assetid: e7979813-1856-4848-9639-f29c86b74ad7
ms.openlocfilehash: 03126b8fdf1c3824b114d822c269655c22e5ee9f
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446685"
---
# <a name="crt-initialization"></a>CRT の初期化

このトピックでは、CRT がネイティブ コードのグローバル状態を初期化する方法について説明します。

既定では、リンカーには、独自のスタートアップ コードを提供する CRT ライブラリが含まれています。 このスタートアップ コードは、CRT ライブラリを初期化し、グローバル初期化子を呼び出し、コンソール アプリケーション用のユーザー指定の `main` 関数を呼び出します。

## <a name="initializing-a-global-object"></a>グローバル オブジェクトの初期化

次のコードがあるとします。

```
int func(void)
{
    return 3;
}

int gi = func();

int main()
{
    return gi;
}
```

C と C++ の標準に従えば、`func()` は `main()` を実行する前に呼び出す必要があります。 では、呼び出し元は何でしょうか。

これを決定する 1 つの方法は、`func()` 内にブレークポイントを設定し、アプリケーションをデバッグし、スタックを調査することです。 これは Visual Studio に CRT ソース コードが含まれているから可能なことです。

スタック上の関数を参照すると、CRT が関数ポインターのリスト内をループしており、見つかるたびに 1 つの関数を呼び出していることがわかります。 これらの関数は `func()` またはクラス インスタンスのコンストラクターに似ています。

CRT では Microsoft C++ コンパイラから関数ポインターのリストが取得されます。 コンパイラがグローバル初期化子を確認すると、`.CRT$XCU` セクション内に動的初期化子を生成します (`CRT` はセクション名、`XCU` はグループ名です)。 これらの動的初期化子を取得するには、**dumpbin /all main.obj** コマンドを実行し、(main.cpp が C ファイルではなく C++ ファイルとしてコンパイルされるときに) `.CRT$XCU` セクションを検索します 。 これは次のようになります。

```
SECTION HEADER #6
.CRT$XCU name
       0 physical address
       0 virtual address
       4 size of raw data
     1F2 file pointer to raw data (000001F2 to 000001F5)
     1F6 file pointer to relocation table
       0 file pointer to line numbers
       1 number of relocations
       0 number of line numbers
40300040 flags
         Initialized Data
         4 byte align
         Read Only

RAW DATA #6
  00000000: 00 00 00 00                                      ....

RELOCATIONS #6
                                                Symbol    Symbol
Offset    Type              Applied To         Index     Name
--------  ----------------  -----------------  --------  ------
00000000  DIR32                      00000000         C  ??__Egi@@YAXXZ (void __cdecl `dynamic initializer for 'gi''(void))
```

CRT では、2 つのポインターを定義します。

- 『`__xc_a`』の「`.CRT$XCA`」

- 『`.CRT$XCZ`』の「`__xc_z`」

両グループとも、`__xc_a` と `__xc_z` を除いては、定義された他のシンボルはありません。

リンカーがさまざまな `.CRT` グループを読み取るとき、グループを 1 つのセクションに結合し、アルファベット順に並べ替えます。 つまり、ユーザー定義のグローバル初期化子 (Microsoft C++ コンパイラでは `.CRT$XCU` 内にあります) は常に `.CRT$XCA` の後にあり、`.CRT$XCZ` の前にあります。

セクションは次のようになります。

```
.CRT$XCA
            __xc_a
.CRT$XCU
            Pointer to Global Initializer 1
            Pointer to Global Initializer 2
.CRT$XCZ
            __xc_z
```

イメージが読み込まれたあとに初期化子がメモリに配置されるため、CRT ライブラリは `__xc_a` と `__xc_z` の両方を使用してグローバル初期化子リストの先頭と末尾を決定します。

## <a name="see-also"></a>関連項目

[CRT ライブラリの機能](../c-runtime-library/crt-library-features.md)
