---
title: 1 つの引数 (int または long) を使用する出力ストリーム マニピュレーター
ms.date: 11/04/2016
helpviewer_keywords:
- output streams, int or long argument manipulators
ms.assetid: 338f3164-b5e2-4c5a-a605-7d9dc3629ca1
ms.openlocfilehash: 93e4de25323514eb4105814b565dc3ddc3fbb737
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453010"
---
# <a name="output-stream-manipulators-with-one-argument-int-or-long"></a>1 つの引数 (int または long) を使用する出力ストリーム マニピュレーター

iostream クラス ライブラリには、パラメーター化したマニピュレーターを作成するためのマクロ セットが用意されています。 1つの**int**または**long**引数を持つマニピュレーターは特殊なケースです。 単一の**int**または**long**引数 (など`setw`) を受け入れる出力ストリームマニピュレーターを作成するには、iomanip > で\<定義されている _Smanip マクロを使用する必要があります。 次の例では、指定した数の空白をストリームに挿入する `fillblank` マニピュレーターを定義します。

## <a name="example"></a>例

```cpp
// output_stream_manip.cpp
// compile with: /GR /EHsc
#include <iostream>
#include <iomanip>
using namespace std;

void fb( ios_base& os, int l )
{
   ostream *pos = dynamic_cast<ostream*>(&os);
   if (pos)
   {
      for( int i=0; i < l; i++ )
      (*pos) << ' ';
   };
}

_Smanip<int>
   __cdecl fillblank(int no)
   {
   return (_Smanip<int>(&fb, no));
   }

int main( )
{
   cout << "10 blanks follow" << fillblank( 10 ) << ".\n";
}
```

## <a name="see-also"></a>関連項目

[引数を使用するカスタム マニピュレーター](../standard-library/custom-manipulators-with-arguments.md)
