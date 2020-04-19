---
title: component プラグマ
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.component
- component_CPP
helpviewer_keywords:
- component pragma
- pragmas, component
ms.assetid: 7b66355e-3201-4c14-8190-f4a2a81a604a
ms.openlocfilehash: 578c590bdb4223f173e0249c18d0eea4e78a18db
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220470"
---
# <a name="component-pragma"></a>component プラグマ

ソースファイル内の参照情報または依存関係情報の収集を制御します。

## <a name="syntax"></a>構文

> **#pragma コンポーネント (browser、** { **on** | **off** } [ **、** **references** [ **,** *name* ]] **)**  \
> **#pragma コンポーネント (minrebuild、** { **on** | **off** } **)**  \
> **#pragma コンポーネント (mintypeinfo、** { **on** | **off** } **)**

## <a name="remarks"></a>Remarks

### <a name="browser"></a>ブラウザー

情報収集のオン/オフを切り替えます。また特定の名前を指定して情報収集の際に無視できます。

on または off を使用して、このプラグマ以降のブラウザー情報の収集を制御します。 例えば:

```cpp
#pragma component(browser, off)
```

上のプラグマは、コンパイラによるブラウザー情報の収集を停止します。

> [!NOTE]
> このプラグマを使用してブラウザー情報の収集をオンにするには、[最初に参照情報を有効にする必要があり](../build/reference/building-browse-information-files-overview.md)ます。

**References**オプションは、 *name*引数と共に使用することも、指定せずに使用することもできます。 *名前*を指定せずに**参照**を使用すると、参照の収集がオンまたはオフになります (ただし、その他の参照情報は引き続き収集されます)。 例えば:

```cpp
#pragma component(browser, off, references)
```

このプラグマは、コンパイラによる参照情報の収集を停止します。

*Name*と**off**の**参照**を使用すると、[参照情報] ウィンドウに*名前*への参照が表示されなくなります。 この構文を使用して必要のない名前と型を無視することで、ブラウザー情報ファイルのサイズを縮小できます。 例えば:

```cpp
#pragma component(browser, off, references, DWORD)
```

その時点以降の DWORD への参照を無視します。 **On**のを使用して、DWORD への参照の収集をオンにすることができます。

```cpp
#pragma component(browser, on, references, DWORD)
```

これは、*名前*への参照の収集を再開する唯一の方法です。無効にした*名前*は、明示的に有効にする必要があります。

プリプロセッサによって*名前*が拡張されないようにするには (NULL を0に拡張するなど)、次のように引用符で囲みます。

```cpp
#pragma component(browser, off, references, "NULL")
```

### <a name="minimal-rebuild"></a>最小リビルド

非推奨の[/Gm (簡易リビルドの有効化)](../build/reference/gm-enable-minimal-rebuild.md)機能を使用するにはC++ 、コンパイラがクラスの依存関係情報を作成して格納する必要があります。これにより、ディスク領域が確保されます。 ディスク領域を節約するために、 `#pragma component( minrebuild, off )`依存関係情報を収集する必要がない場合 (たとえば、不変のヘッダーファイルで) を使用できます。 不変`#pragma component( minrebuild, on )`のクラスの後に挿入して、依存関係コレクションを再び有効にします。

### <a name="reduce-type-information"></a>型情報を減らす

オプション`mintypeinfo`を指定すると、指定した領域のデバッグ情報が減少します。 この情報は量が多く、.pdb ファイルと .obj ファイルに影響を与えます。 mintypeinfo 領域では、クラスと構造をデバッグできません。 mintypeinfo オプションを使用すると、次の警告を回避するのに役立ちます。

```cmd
LINK : warning LNK4018: too many type indexes in PDB "filename", discarding subsequent type information
```

詳細については、「 [/Gm (簡易リビルドを有効にする)](../build/reference/gm-enable-minimal-rebuild.md)コンパイラオプション」を参照してください。

## <a name="see-also"></a>関連項目

[プラグマディレクティブと __ プラグマキーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
