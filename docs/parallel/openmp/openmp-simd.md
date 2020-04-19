---
title: SIMD 拡張機能
ms.date: 03/20/2019
helpviewer_keywords:
- SIMD
- OpenMP in Visual C++, new features
- explicit parallelization, new features
ms.openlocfilehash: 52402aa553c6d68d3073aba26ecac7b784522ee9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363272"
---
# <a name="simd-extension"></a>SIMD 拡張機能

Visual C++ Visual Studio 2019 は、SIMD 機能も提供しています。 ただし、現在、OpenMP 2.0 標準をサポートしています。

> [!NOTE]
> SIMD を使用するとコンパイル、`-openmp:experimental`スイッチを使用する場合は、使用できない追加の OpenMP の機能をできるようにする、`-openmp`スイッチします。
>
> `-openmp:experimental`スイッチ目的`-openmp`、すべて OpenMP 2.0 に含まれる機能の使用を意味します。

詳細については、次を参照してください。 [SIMD 拡張機能をC++Visual Studio で OpenMP](https://devblogs.microsoft.com/cppblog/simd-extension-to-c-openmp-in-visual-studio/)します。

## <a name="openmp-simd-in-visual-c"></a>ビジュアルで OpenMP SIMDC++

OpenMP SIMD、ベクトルが容易なループを作成するターゲット標準、OpenMP 4.0 で導入されました。 使用して、`simd`ディレクティブ、ループの前に、コンパイラできますベクターの依存関係を無視する、ループ、できるだけわかりやすいのベクターとしてを行い、複数のループの反復処理が同時に実行するユーザーの意図を尊重します。

```c
    #pragma omp simd
    for (i = 0; i < count; i++)
    {
        a[i] = a[i-1] + 1;
        b[i] = *c + 1;
        bar(i);
    }
```

VisualC++などのような非 OpenMP ループ プラグマは、`#pragma vector`と`#pragma ivdep`OpenMP の SIMD コンパイラ操作を実行できますの詳細などが。

- ベクターの依存関係の存在を無視するのには常に許可します。
- `/fp:fast` ループ内で有効です。
- 外側のループと関数の呼び出しでのループは、ベクターに適したです。
- 入れ子になったループは、1 つのループに 1 つにまとめし、ベクターに適したを行ったことができます。
- ハイブリッドでの高速化`#pragma omp for simd`粒度の粗いマルチ スレッド処理ときめ細かなベクトルを有効にします。  

For ループのベクターに適した、コンパイラは、ベクター サポート ログ スイッチを使用する場合を除き、サイレントは。

```cmd
    cl -O2 -openmp:experimental -Qvec-report:2 mycode.cpp
```

```Output
    mycode.cpp(84) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(90) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(96) : info C5001: Omp simd loop vectorized
```

ループのベクターわかりづらい場合、コンパイラは各メッセージ。

```cmd
    cl -O2 -openmp:experimental mycode.cpp
```

```Output
    mycode.cpp(84) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(90) : info C5002: Omp simd loop not vectorized due to reason '1200'
```

### <a name="clauses"></a>句

OpenMP SIMD ディレクティブは、ベクター サポートを強化するために、次の句をこともできます。

|ディレクティブ|説明|
|---|---|
|`simdlen(length)`|ベクターのレーン数を指定します。|
|`safelen(length)`|ベクターの依存関係の距離を指定します。|
|`linear(list[ : linear-step]`)|ループ誘導変数から配列のサブスクリプションへの線形のマッピング|
|`aligned(list[ : alignment])`|データの配置です。|
|`private(list)`|データをプライベート化を指定します。|
|`lastprivate(list)`|最後のイテレーションから最終的な値では、データをプライベート化を指定します。|
|`reduction(reduction-identifier:list)`|カスタマイズされた縮小操作を指定します。|
|`collapse(n)`|結合のループの入れ子。|

> [!NOTE]
> 非効果的な SIMD 句が解析され、警告と、コンパイラによって無視されます。
>
> 警告を次のコードの問題の例では、使用します。
>
> ```c
>    #pragma omp simd simdlen(8)
>    for (i = 0; i < count; i++)
>    {
>        a[i] = a[i-1] + 1;
>        b[i] = *c + 1;
>        bar(i);
>    }
> ```
>
> ```Output
>    warning C4849: OpenMP 'simdlen' clause ignored in 'simd' directive
> ```

### <a name="example"></a>例
  
OpenMP SIMD ディレクティブは、コンパイラの作成ループのベクターに適したを決定する方法をユーザーに提供します。 OpenMP SIMD ディレクティブを使用して、ループの注釈を付けることによって、ユーザーは複数のループの反復処理が同時に実行する予定です。

たとえば、OpenMP SIMD ディレクティブには、次のループが付きます。 旧バージョンと依存関係 [i] から [i-1] は、コンパイラは、1 つのベクター命令には、最初のステートメントの連続するイテレーションをパックし、実行を引き続き許可 SIMD ディレクティブが原因であるために、ループの反復の間で完全な並列処理はありません。並列にします。

```c
    #pragma omp simd
    for (i = 0; i < count; i++)
    {
        a[i] = a[i-1] + 1;
        b[i] = *c + 1;
        bar(i);
    }
```

そのため、ループの次の変換されたベクトルの形式は**法的**コンパイラは各元のループ反復のシーケンシャルな動作を保持しているためです。 つまり、`a[i]`は後に実行`a[-1]`、`b[i]`後`a[i]`への呼び出し`bar`が最後に実行します。

```c
    for (i = 0; i < count; i+=4)
    {
        a[i:i+3] = a[i-1:i+2] + 1;
        b[i:i+3] = *c + 1;
        bar(i);
        bar(i+1);
        bar(i+2);
        bar(i+3);
    }
```

**有効ではない**メモリ参照を移動する`*c`ことがありますエイリアスの場合、ループから`a[i]`または`b[i]`します。 シーケンシャルの依存関係を中断する場合、元の 1 つのイテレーション内のステートメントを並べ替えるには有効なことではありません。 たとえば、次の変換後のループは、法的するではありません。

```c
    c = b;
    t = *c;
    for (i = 0; i < count; i+=4)
    {
        a[i:i+3] = a[i-1:i+2] + 1;
        bar(i);            // illegal to reorder if bar[i] depends on b[i]
        b[i:i+3] = t + 1;  // illegal to move *c out of the loop
        bar(i+1);
        bar(i+2);
        bar(i+3);
    }
```

## <a name="see-also"></a>関連項目

[/openmp (OpenMP 2.0 サポートの有効化)](../../build/reference/openmp-enable-openmp-2-0-support.md)<br/>
