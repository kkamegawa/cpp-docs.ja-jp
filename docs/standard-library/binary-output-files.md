---
title: バイナリ出力ファイル
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [C++], binary output files
- files [C++], binary output files
- binary data, binary output files
ms.assetid: 180954af-8cd6-444b-9a76-2f630a3389d8
ms.openlocfilehash: 4562f5c1167aeadc6689313e73545ed1ad9bbcf8
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2019
ms.locfileid: "68376334"
---
# <a name="binary-output-files"></a>バイナリ出力ファイル

ストリームは本来、テキスト向けとして設計されており、既定の出力モードはテキストです。 テキストモードでは、ラインフィード (改行) 文字が復帰と改行のペアに拡張されます。 この拡大は次のような問題を起こす可能性があります。

```cpp
// binary_output_files.cpp
// compile with: /EHsc
#include <fstream>
using namespace std;
int iarray[2] = { 99, 10 };
int main( )
{
    ofstream os( "test.dat" );
    os.write( (char *) iarray, sizeof( iarray ) );
}
```

このプログラムでは、{ 99, 0, 10, 0 } というバイト シーケンスの出力を想定していたところ、{ 99, 0, 13, 10, 0 } が出力されます。バイナリ入力を要求するプログラムで問題が起こります。 実際のバイナリ出力が必要な場合は、文字が変換されないように記述されている場合は`openmode` 、 [ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream)コンストラクター引数を使用してバイナリ出力を指定できます。

```cpp
// binary_output_files2.cpp
// compile with: /EHsc
#include <fstream>
using namespace std;
int iarray[2] = { 99, 10 };

int main()
{
   ofstream ofs ( "test.dat", ios_base::binary );

   // Exactly 8 bytes written
   ofs.write( (char*)&iarray[0], sizeof(int)*2 );
}
```

## <a name="see-also"></a>関連項目

[出力ストリーム](../standard-library/output-streams.md)
