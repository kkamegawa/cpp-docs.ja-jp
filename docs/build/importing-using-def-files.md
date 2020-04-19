---
title: DEF ファイルを使ったインポート
ms.date: 11/04/2016
helpviewer_keywords:
- importing DLLs [C++], DEF files
- def files [C++], importing with
- .def files [C++], importing with
- dllimport attribute [C++], DEF files
- DLLs [C++], DEF files
ms.assetid: aefdbf50-f603-488a-b0d7-ed737bae311d
ms.openlocfilehash: 13a6a375d6200f73dd9845d057d1954c2b65485c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273418"
---
# <a name="importing-using-def-files"></a>DEF ファイルを使ったインポート

使用する場合 **_declspec**と共に、.def ファイルでは、定数の代わりにデータを使用して、コーディングの誤りによってが発生する問題を低減する .def ファイルを変更する必要があります。

```
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   DATA
```

次の表では、その理由を示します。

|キーワード|インポート ライブラリに出力します。|エクスポート|
|-------------|---------------------------------|-------------|
|`CONSTANT`|`_imp_ulDataInDll`, `_ulDataInDll`|`_ulDataInDll`|
|`DATA`|`_imp_ulDataInDll`|`_ulDataInDll`|

使用して **_declspec**し、両方の定数が一覧表示、`imp`バージョンと非装飾名 .lib DLL では、明示的なリンクを許可するために作成、ライブラリをインポートします。 使用して **_declspec**とデータのリストだけ`imp`バージョンの名前。

定数を使用する場合、次のコード コンストラクトのいずれかを使用できますにアクセスする`ulDataInDll`:

```
__declspec(dllimport) ULONG ulDataInDll; /*prototype*/
if (ulDataInDll == 0L)   /*sample code fragment*/
```

\- または -

```
ULONG *ulDataInDll;      /*prototype*/
if (*ulDataInDll == 0L)  /*sample code fragment*/
```

ただし、.def ファイルにデータを使用する場合、次の定義でコンパイルされたコードのみ変数アクセスできる`ulDataInDll`:

```
__declspec(dllimport) ULONG ulDataInDll;

if (ulDataInDll == 0L)   /*sample code fragment*/
```

余分なレベルの間接参照を使用することを忘れてしまった場合は、変数へのインポート アドレス テーブルのポインターを可能性のあるアクセスだったためよりリスクの高いは定数を使用して、変数自体ではありません。 インポート アドレス テーブルは、現在行われるため読み取り専用のコンパイラとリンカーで、この種の問題はアクセス違反としてマニフェスト多くの場合、ことができます。

現在、MSVC リンカーは、このケースに対応する .def ファイル内の定数が見つかる場合に警告を発行します。 定数を使用する唯一の理由がのかどうか、ヘッダー ファイルが一覧表示されませんいくつかのオブジェクト ファイルを再コンパイルすることはできません **_declspec**プロトタイプ。

## <a name="see-also"></a>関連項目

[アプリケーションへのインポート](importing-into-an-application.md)
