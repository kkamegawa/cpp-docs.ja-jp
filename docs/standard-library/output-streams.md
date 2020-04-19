---
title: 出力ストリーム
ms.date: 11/04/2016
helpviewer_keywords:
- output streams
ms.assetid: b49410e3-5caa-4153-9d0d-c4266408dc83
ms.openlocfilehash: e650f9fd0bbc7ad483363706e632686e8ec3749e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450167"
---
# <a name="output-streams"></a>出力ストリーム

出力ストリーム オブジェクトは、バイトのターゲットです。 3 つの最も重要な出力ストリーム クラスは `ostream`、`ofstream`、および `ostringstream` です。

`ostream` クラスは、派生クラス `basic_ostream` を通して、事前定義されたストリーム オブジェクトをサポートしています。

- `cout`標準出力

- `cerr`制限バッファリングでの標準エラー

- `clog``cerr` に類似しているが、完全バッファリング

オブジェクトが `ostream` から構築されることはほとんどありません。一般的に事前定義オブジェクトが使用されます。 場合によっては、プログラムの起動後に事前定義オブジェクトを再割り当てすることができます。 `ostream` クラスは、バッファーあり、バッファーなしのいずれの操作にも構成できますが、連続したテキスト モードの出力に最適です。 基本クラスのすべての機能 `ios` は、`ostream` に含まれています。 `ostream` クラスのオブジェクトを構築する場合、コンストラクターへの `streambuf` オブジェクトを指定する必要があります。

`ofstream` クラスは、ディスク ファイルの出力をサポートしています。 出力専用のディスクが必要な場合は、`ofstream` クラスのオブジェクトを構築します。 `ofstream` オブジェクトを構築する場合、またはオブジェクトの `open` メンバー関数を呼び出す場合、`ofstream` オブジェクトでバイナリまたはテキスト モードのデータを受け入れるかどうかを指定することができます。 多くの書式設定オプションとメンバー関数が `ofstream` オブジェクトに適用されており、基本クラス `ios` および `ostream` のすべての機能が含まれています。

コンストラクターでファイル名を指定すると、オブジェクトの構築時にそのファイルが自動的に開きます。 あるいは、既定のコンストラクターを起動した後に `open` メンバー関数を使用します。

ランタイム関数 `sprintf_s` と同様に、`ostringstream` クラスはメモリ内の文字列への出力をサポートしています。 入出力ストリームの書式設定を使用して、メモリ内の文字列を作成するには、`ostringstream` クラスのオブジェクトを構築します。

## <a name="in-this-section"></a>このセクションの内容

[出力ストリーム オブジェクトの構築](../standard-library/constructing-output-stream-objects.md)

[挿入演算子と制御形式の使用](../standard-library/using-insertion-operators-and-controlling-format.md)

[出力ファイル ストリームのメンバー関数](../standard-library/output-file-stream-member-functions.md)

[バッファリングの効果](../standard-library/effects-of-buffering.md)

[バイナリ出力ファイル](../standard-library/binary-output-files.md)

[独自クラスのための << 演算子のオーバーロード](../standard-library/overloading-the-output-operator-for-your-own-classes.md)

[引数を使用しない独自マニピュレーターの作成](../standard-library/writing-your-own-manipulators-without-arguments.md)

## <a name="see-also"></a>関連項目

[ofstream](../standard-library/basic-ofstream-class.md)\
[ostringstream](../standard-library/basic-ostringstream-class.md)\
[iostream プログラミング](../standard-library/iostream-programming.md)
