---
title: runtime_checks プラグマ
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.runtime_checks
- runtime_checks_CPP
helpviewer_keywords:
- runtime_checks pragma
- pragmas, runtime_checks
ms.assetid: ae50b43f-f88d-47ad-a2db-3389e9e7df5b
ms.openlocfilehash: a1c8e6cca27e157818e6ec80182f8fefa112daf1
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216609"
---
# <a name="runtime_checks-pragma"></a>runtime_checks プラグマ

[/RTC](../build/reference/rtc-run-time-error-checks.md) 設定を無効化または復元します。

## <a name="syntax"></a>構文

> **#pragma runtime_checks ("** [ *runtime_checks* ] **",** { **restore** | **off** } **)**

## <a name="remarks"></a>Remarks

コンパイラオプションによって有効にされていないランタイムチェックを有効にすることはできません。 たとえば、コマンドラインでを指定`/RTCs`しない場合、を指定`#pragma runtime_checks( "s", restore)`してもスタックフレームの検証は有効になりません。

**Runtime_checks**プラグマは関数の外に記述する必要があり、プラグマが検出された後に定義された最初の関数で有効になります。 **restore** 引数と **off** 引数は **runtime_checks** で指定するオプションのオンとオフを切り替えます。

**runtime_checks** には、次の表に示すパラメーターの 0 個以上を指定できます。

### <a name="parameters-of-the-runtime_checks-pragma"></a>runtime_checks プラグマのパラメーター

| パラメーター | ランタイム チェックの種類 |
|--------------------|-----------------------------|
| **s** | スタック (フレーム) 検証を有効にします。 |
| **c** | より小さいデータ型に値が代入されてデータが失われる場合に報告します。 |
| **u** | 変数が定義される前に使用されたことを報告します。 |

これらのパラメーターは、 `/RTC`コンパイラオプションで使用されるものと同じです。 例えば:

```cpp
#pragma runtime_checks( "sc", restore )
```

空の文字列 ( **""** ) での**runtime_checks**プラグマの使用は、ディレクティブの特殊な形式です。

- **Off**パラメーターを使用すると、上記の表に一覧表示されているランタイムエラーチェックがオフになります。

- **Restore**パラメーターを使用すると、ランタイムエラーチェックが`/RTC`コンパイラオプションを使用して指定したものにリセットされます。

```cpp
#pragma runtime_checks( "", off )
/* runtime checks are off in this region */
#pragma runtime_checks( "", restore )
```

## <a name="see-also"></a>関連項目

[プラグマディレクティブと __ プラグマキーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
