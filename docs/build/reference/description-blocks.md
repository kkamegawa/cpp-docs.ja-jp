---
title: 記述ブロック
description: NMAKE は、記述ブロックを使用して、メイクファイル内のターゲット、依存関係、およびコマンドを関連付けます。
ms.date: 10/29/2019
helpviewer_keywords:
- description blocks
- NMAKE program, description blocks
- blocks, description
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
ms.openlocfilehash: fb9cf4400c96b588e8704e972dd29ab27f41cae9
ms.sourcegitcommit: 6ed1bc5b26dc60a780c1fc5f2f19d57ba1dc47d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73144523"
---
# <a name="description-blocks"></a>記述ブロック

記述ブロックはメイクファイルの中核となります。 これらは、*ターゲット、* 作成するファイル、およびその*依存関係*(ターゲットの作成に必要なファイル) を記述します。 説明ブロックには、依存関係からターゲットを作成する方法を説明する*コマンド*を含めることができます。 説明ブロックは依存関係の行で、オプションでコマンドブロックを続けたものになります。

```makefile
targets... : dependents...
    commands...
```

## <a name="dependency-lines"></a>依存関係の行

*依存関係の線*は、1つ以上のターゲット、および0個以上の依存を指定します。 ターゲットが存在しない場合、または依存関係より前のタイムスタンプを持っている場合、NMAKE はコマンドブロック内のコマンドを実行します。 ターゲットが[pseudotarget](pseudotargets.md)の場合、NMAKE はコマンドブロックも実行します。 依存関係の行の例を次に示します。

```makefile
hi_bye.exe : hello.obj goodbye.obj helper.lib
```

この依存関係の行では、`hi_bye.exe` がターゲットです。 その依存関係は `hello.obj`、`goodbye.obj`、および `helper.lib`です。 依存関係の行は、`hello.obj`、`goodbye.obj`、`helper.lib` が `hi_bye.exe`よりも最近変更されたときに、ターゲットをビルドするように NMAKE に指示します。

ターゲットは、行の先頭にある必要があります。 スペースやタブでインデントすることはできません。 ターゲットを依存から分離するには、コロン (`:`) を使用します。 ターゲット、コロン区切り記号 (`:`)、および依存の間でスペースまたはタブを使用できます。 依存関係の行を分割するには、ターゲットまたは依存の後に円記号 (`\`) を使用します。

NMAKE は、コマンドブロックを実行する前に、すべての依存関係と適用可能な推論規則をスキャンして、*依存関係ツリー*を構築します。 依存関係ツリーは、ターゲットを完全に更新するために必要な手順を指定します。 NMAKE は、依存関係自体が別の依存関係リスト内のターゲットであるかどうかを再帰的に確認します。 依存関係ツリーをビルドした後、NMAKE はタイムスタンプをチェックします。 ツリー内の依存関係がターゲットより新しい場合、NMAKE はターゲットをビルドします。

## <a name="targets"></a> ターゲット

依存関係線のターゲットセクションは、1つ以上のターゲットを指定します。 ターゲットには、任意の有効なファイル名、ディレクトリ名、または[pseudotarget](pseudotargets.md)を指定できます。 複数のターゲットを分割するには、1つまたは複数のスペースまたはタブを使用します。 ターゲットでは大文字と小文字が区別されません。 パスは、ファイル名と共に使用できます。 ターゲットとそのパスは、256文字を超えることはできません。 コロンの前のターゲットが1文字の場合は、スペースを区切りにします。 それ以外の場合、NMAKE は文字のコロンの組み合わせをドライブ指定子として解釈します。

### <a name="multiple-targets"></a>複数のターゲット

NMAKE は、1つの依存関係にある複数のターゲットを、それぞれ別の説明ブロックで指定されているかのように評価します。

たとえば、次の規則を使用します。

```makefile
bounce.exe leap.exe : jump.obj
   echo Building...
```

は次のように評価されます。

```makefile
bounce.exe : jump.obj
   echo Building...

leap.exe : jump.obj
   echo Building...
```

### <a name="cumulative-dependencies"></a>累積的な依存関係

ターゲットが繰り返される場合、説明ブロックの中に依存関係が累積されます。

たとえば、次の一連のルールがあります。

```makefile
bounce.exe : jump.obj
bounce.exe : up.obj
   echo Building bounce.exe...
```

は次のように評価されます。

```makefile
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

1つの説明ブロック内の複数の依存関係行に複数のターゲットがある場合、NMAKE はそれぞれが個別の説明ブロックで指定されているかのように評価します。 ただし、最後の依存関係行のターゲットのみがコマンドブロックを使用します。 NMAKE は、他のターゲットに対して推論規則を使用しようとします。

たとえば、次の一連のルールがあります。

```makefile
leap.exe bounce.exe : jump.obj
bounce.exe climb.exe : up.obj
   echo Building bounce.exe...
```

は次のように評価されます。

```makefile
leap.exe : jump.obj
# invokes an inference rule

bounce.exe : jump.obj up.obj
   echo Building bounce.exe...

climb.exe : up.obj
   echo Building bounce.exe...
```

### <a name="targets-in-multiple-description-blocks"></a>複数の説明ブロック内のターゲット

異なるコマンドを使用して複数の説明ブロックのターゲットを更新するには、2つの連続するコロン (::) を指定します。ターゲットと依存の間。

```makefile
target.lib :: one.asm two.asm three.asm
    ml one.asm two.asm three.asm
    lib target one.obj two.obj three.obj
target.lib :: four.c five.c
    cl /c four.c five.c
    lib target four.obj five.obj
```

### <a name="dependency-side-effects"></a>依存関係の副作用

コロン (:) でターゲットを指定することもできます。異なる場所にある2つの依存関係行。 コマンドが1つの行の後にのみ表示される場合、NMAKE は、行が隣接しているか結合されているかのように依存関係を解釈します。 コマンドを含まない依存関係の推論規則は呼び出されません。 代わりに、NMAKE は依存関係が1つの説明ブロックに属しているものと見なし、他の依存関係で指定されたコマンドを実行します。 この一連のルールを考えてみましょう。

```makefile
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
```

は次のように評価されます。

```makefile
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

この効果は、2つのコロン (`::`) が使用されている場合には発生しません。 たとえば、次の規則のセットを使用します。

```makefile
bounce.exe :: jump.obj
   echo Building bounce.exe...

bounce.exe :: up.obj
```

は次のように評価されます。

```makefile
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
# invokes an inference rule
```

### <a name="pseudotargets"></a>擬似ターゲット

*Pseudotarget*は、依存関係の行にファイル名の代わりに使用されるラベルです。 存在しないファイルとして解釈されるため、最新ではありません。 NMAKE は、pseudotarget のタイムスタンプが、そのすべての依存の最新のものと同じであると想定しています。 依存関係がない場合は、現在の時刻が想定されます。 Pseudotarget がターゲットとして使用されている場合、そのコマンドは常に実行されます。 依存として使用される pseudotarget は、別の依存関係のターゲットとしても表示される必要があります。 ただし、その依存関係はコマンドブロックを持つ必要はありません。

Pseudotarget の名前は、ターゲットのファイル名の構文規則に従います。 ただし、名前に拡張子が付いていない場合は、ファイル名の8文字の制限を超えることができ、最大256文字まで使用できます。

擬似ターゲットは、NMAKE で複数のターゲットを自動的に作成する場合に便利です。 NMAKE は、コマンドラインで指定されたターゲットのみをビルドします。 また、コマンドラインターゲットが指定されていない場合は、メイクファイル内の最初の依存関係の最初のターゲットのみがビルドされます。 コマンドラインで個別に一覧表示せずに、複数のターゲットをビルドするように NMAKE に指示できます。 Pseudotarget を含む依存関係を持つ説明ブロックを作成し、その依存関係としてビルドするターゲットを一覧表示します。 次に、この説明ブロックをメイクファイルに追加するか、NMAKE のコマンドラインで pseudotarget を指定します。

この例では、UPDATE は pseudotarget です。

```makefile
UPDATE : *.*
!COPY $** c:\product\release
```

更新が評価されると、NMAKE は、現在のディレクトリにあるすべてのファイルを、指定したドライブとディレクトリにコピーします。

次のメイクファイルでは、コマンドラインで `all` または target が指定されていない場合、pseudotarget `all` は `project1.exe` と `project2.exe` の両方をビルドします。 Pseudotarget `setenv` は、`.exe` ファイルが更新される前に LIB 環境変数を変更します。

```makefile
all : setenv project1.exe project2.exe

project1.exe : project1.obj
    LINK project1;

project2.exe : project2.obj
    LINK project2;

setenv :
    set LIB=\project\lib
```

## <a name="dependents"></a>子

依存関係の行で、コロン (`:`) の後に0個以上の依存を指定するか、任意の有効な filename または[pseudotarget](pseudotargets.md)を使用して、2つのコロン (`::`) を指定します。 複数の依存を区切るには、1つまたは複数のスペースまたはタブを使用します。 依存関係では大文字と小文字が区別されません。 パスは、ファイル名と共に使用できます。

### <a name="inferred-dependents"></a>推定される依存

依存関係の行に明示的に一覧表示する依存関係と共に、NMAKE は、*推論に依存*するものと想定できます。 推論に依存するは推論規則から派生し、明示的な依存の前に評価されます。 推論された依存がターゲットと比較して古くなっている場合、NMAKE は依存関係のコマンドブロックを呼び出します。 推論された依存が存在しない場合、または独自の依存関係と比較して古くなっている場合、NMAKE は最初に、推論された依存を更新します。 推定される依存関係の詳細については、「[推論規則](inference-rules.md)」を参照してください。

### <a name="search-paths-for-dependents"></a>依存関係の検索パス

依存関係ごとに、オプションの検索パスを指定できます。 検索するディレクトリのセットを指定する構文を次に示します。

> **{** _ディレクトリ_\[ **;** _ディレクトリ_...] **}** _依存_

ディレクトリ名を中かっこ (`{ }`) で囲みます。 複数のディレクトリをセミコロン (`;`) で区切ります。 スペースやタブは使用できません。 NMAKE は、現在のディレクトリで最初に依存しているを検索し、次に指定された順序でディレクトリの一覧を検索します。 マクロを使用して、検索パスの一部またはすべてを指定できます。 指定された依存だけがこの検索パスを使用します。

#### <a name="directory-search-path-example"></a>ディレクトリ検索パスの例

この依存関係線は、検索のディレクトリ仕様を作成する方法を示しています。

```makefile
reverse.exe : {\src\omega;e:\repo\backwards}retro.obj
```

ターゲット `reverse.exe` には、依存する `retro.obj`が1つあります。 中かっこで囲まれたリストは、2つのディレクトリを指定します。 NMAKE は、まず現在のディレクトリ内の `retro.obj` を検索します。 存在しない場合は、NMAKE によって `\src\omega` ディレクトリ、`e:\repo\backwards` ディレクトリが検索されます。

## <a name="see-also"></a>関連項目

[NMAKE リファレンス](nmake-reference.md)
