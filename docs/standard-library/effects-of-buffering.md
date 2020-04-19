---
title: バッファリングの効果
ms.date: 11/04/2016
helpviewer_keywords:
- buffers, effects of buffering
- buffering, effects of
ms.assetid: 5d544812-e95e-4f28-b15a-edef3f3414fd
ms.openlocfilehash: 1f28748f1e7a837ad87ef1cfcebc56d3410d0fd2
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458909"
---
# <a name="effects-of-buffering"></a>バッファリングの効果

次に、バッファリングの効果を示す例を示します。 `please wait`を出力して 5 秒待ってから先に進むプログラムを想定することができますが、 必ずしもそのとおりに動作するとは限りません。これは、出力がバッファリングされるためです。

```cpp
// effects_buffering.cpp
// compile with: /EHsc
#include <iostream>
#include <time.h>
using namespace std;

int main( )
{
   time_t tm = time( NULL ) + 5;
   cout << "Please wait...";
   while ( time( NULL ) < tm )
      ;
   cout << "\nAll done" << endl;
}
```

プログラムを論理的に動作させるには、メッセージが表示されたときに `cout` オブジェクトがそれ自体を空にする必要があります。 `ostream` オブジェクトをフラッシュするには、それを `flush` マニピュレーターに送信します。

```cpp
cout <<"Please wait..." <<flush;
```

この手順ではバッファーがフラッシュされるため、必ず待機の前にメッセージが出力されます。 また、 `endl`マニピュレーターを使用して、バッファーをフラッシュし、キャリッジリターンラインフィードを出力します。または、 `cin`オブジェクトを使用することもできます。 通常、このオブジェクト (および `cerr` または `clog` オブジェクト) は `cout` オブジェクトに関連付けられています。 そのため、 `cin` (あるいは `cerr` または `clog` オブジェクト) を使用すると、 `cout` オブジェクトがフラッシュされます。

## <a name="see-also"></a>関連項目

[出力ストリーム](../standard-library/output-streams.md)
