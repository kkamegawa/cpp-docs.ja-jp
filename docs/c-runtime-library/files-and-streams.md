---
title: ファイルとストリーム
ms.date: 11/04/2016
helpviewer_keywords:
- files [C++]
- streams
ms.assetid: f61e712b-eac9-4c28-bb18-97c3786ef387
ms.openlocfilehash: ea11ea76ade8a68c2d8a92e08d3652035c996d3d
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750794"
---
# <a name="files-and-streams"></a>ファイルとストリーム

プログラムは、ファイルを読み書きすることによって対象の環境と通信します。 ファイルには次のものがあります。

- 繰り返し読み書きできるデータ セット。

- プログラム (パイプラインなど) によって生成されるバイト ストリーム。

- 周辺デバイスとの間で送受信されるストリーム バイト。

最後の 2 つの項目は対話型ファイルです。 一般的に、ファイルはプログラムと相互に作用するための主要な手段です。 ライブラリ関数を呼び出すことによって、ほぼ同じ方法でこれらすべての種類のファイルを操作できます。 これらの関数の大半を宣言するには、標準ヘッダー STDIO.H をインクルードします。

ファイルで多くの操作を実行する前に、ファイルを開く必要があります。 ファイルを開くことによって、各種ファイル間の多くの違いが無視される標準 C ライブラリ内のデータ構造であるストリームと、ファイルが関連付けられます。 ライブラリでは、各ストリームの状態が FILE 型のオブジェクトで維持されます。

対象の環境では、プログラムの起動前に 3 つのファイルを開きます。 2 つの引数を使用してライブラリ関数 [fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md) を呼び出すことによってファイルを開くことができます。 (`fopen` 関数は非推奨とされます。代わりに [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md) を使用してください。)1 つ目の引数は、ファイル名です。 2 つ目の引数は、次を指定する C 文字列です。

- ファイルからデータを読み込む、ファイルにデータを書き込む、または両方を行うかどうか。

- ファイルの新しい内容を生成する (またはファイルが存在していなかった場合はファイルを作成する)、または既存の内容をそのままにするかどうか。

- ファイルへの書き込みによって既存の内容が変更される、またはファイルの終端にバイトが追加されるのみかどうか。

- テキスト ストリームまたはバイナリ ストリームを操作するかどうか。

ファイルが正常に開いたら、ストリームがバイト指向 (バイト ストリーム) かワイド指向 (ワイド ストリーム) かを決めることができます。 ストリームは、初期状態ではバインドされていません。 ストリームで操作する特定の関数を呼び出すとバイト指向になり、特定の他の関数を呼び出すとワイド指向になります。 いったん確立すると、[fclose](../c-runtime-library/reference/fclose-fcloseall.md) または [freopen](../c-runtime-library/reference/freopen-wfreopen.md) への呼び出しによってファイルが閉じるまで、ストリームの指向は保持されます。

© 1989-2001 by P.J. Plauger and Jim Brodie. All rights reserved.

## <a name="see-also"></a>関連項目

[テキスト ストリームとバイナリ ストリーム](../c-runtime-library/text-and-binary-streams.md)<br/>
[バイト ストリームとワイド ストリーム](../c-runtime-library/byte-and-wide-streams.md)<br/>
[ストリームの制御](../c-runtime-library/controlling-streams.md)<br/>
[ストリームの状態](../c-runtime-library/stream-states.md)
