---
title: パス名の指定
ms.date: 11/04/2016
helpviewer_keywords:
- names [C++], compiler output files
- cl.exe compiler, output files
- output files, specifying pathnames
ms.assetid: 7a6595ce-3383-44ae-957a-466bfa29c343
ms.openlocfilehash: dcff3610255c40f4e06201e52a53eb5dd965a4be
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317940"
---
# <a name="specifying-the-pathname"></a>パス名の指定

各出力ファイルのオプションを受け入れる、 *pathname*場所と出力ファイルの名前を指定する引数。 引数には、ドライブ名、ディレクトリ、およびファイル名を含めることができます。 オプションと引数の間にスペースは許可されません。

場合*pathname*ファイル名を含む、拡張子のない、コンパイラは、出力、既定の拡張子。 場合*pathname*ディレクトリがないファイル名が含まれています、コンパイラは、指定したディレクトリ内の既定の名前でファイルを作成します。 既定の名前は、ソース ファイルと出力ファイルの種類に基づいて既定の拡張機能の基本名に基づきます。 のままにする場合*pathname*既定のディレクトリに既定の名前と完全にコンパイラがファイルを作成します。

または、 *pathname*引数は、ファイル名ではなくデバイスの名前 (AUX、CON、PRN、または NUL) を指定できます。 デバイス名の一部として、オプションや、デバイス名、コロンの間にスペースを使わないでください。

|デバイス名|表現|
|-----------------|----------------|
|AUX|補助デバイス|
|CON|コンソール|
|PRN|プリンター|
|NUL|Null デバイス (ファイルが作成された)|

## <a name="example"></a>例

次のコマンド ラインでは、マップ ファイルをプリンターに送信します。

```
CL /FmPRN HELLO.CPP
```

## <a name="see-also"></a>関連項目

[出力ファイル (/F) オプション](output-file-f-options.md)<br/>
[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
