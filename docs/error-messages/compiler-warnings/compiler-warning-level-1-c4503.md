---
title: コンパイラの警告 (レベル 1) C4503
ms.date: 05/14/2018
f1_keywords:
- C4503
helpviewer_keywords:
- C4503
ms.assetid: 7c5a98ae-5b6d-41d8-b881-12d3ffd5e392
ms.openlocfilehash: 94c88511d87c3adf3cf5687a94948c83ebc5b3d5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160979"
---
# <a name="compiler-warning-level-1-c4503"></a>コンパイラの警告 (レベル 1) C4503

> '*identifier*' : decorated name length exceeded, name was truncated

## <a name="remarks"></a>Remarks

このコンパイラの警告は廃止され、Visual Studio 2017 およびそれ以降のコンパイラでは生成されません。

装飾名は、コンパイラの制限 (4096) よりも長くなりますが、切り捨てられました。 この警告とを切り捨てを回避するには、引数の数または使用される識別子の名前の長さを減らしてください。 装飾の名を適用ハッシュを持ち、コンパイラの制限よりも長い名前の競合の危険性はありません。

この警告を発行するコードには、テンプレートが含まれている場合、古いバージョンの Visual Studio を使用する場合繰り返しテンプレートの特殊化します。 たとえば、マップ (C++ 標準ライブラリ) からマップします。 このような状況で行うことができます、typedef 型 (、**構造体**など)、マップを格納しています。

ただし、いないコードを再構築することができます。  C4503 を生成するアプリケーションを出荷することができますが、切り捨てられたシンボルで、リンク時のエラーが発生した場合、エラーのシンボルの種類を決定することが難しくできます。 月もデバッグことは困難です。デバッガーは難しいため、シンボル名を型名にマッピングがあります。 ただし、プログラムの正確性は切り捨てられた名前による影響ではありません。

## <a name="example"></a>例

次の例では、Visual Studio 2017 の以前のコンパイラで C4503 が生成されます。

```cpp
// C4503.cpp
// compile with: /W1 /EHsc /c
// C4503 expected
#include <string>
#include <map>

class Field{};

typedef std::map<std::string, Field> Screen;
typedef std::map<std::string, Screen> WebApp;
typedef std::map<std::string, WebApp> WebAppTest;
typedef std::map<std::string, WebAppTest> Hello;
Hello MyWAT;
```

このサンプルは、C4503 を解決するのには、コードを書き直す方法の 1 つを示しています。

```cpp
// C4503b.cpp
// compile with: /W1 /EHsc /c
#include <string>
#include <map>

class Field{};

struct Screen2 {
   std::map<std::string, Field> Element;
};

struct WebApp2 {
   std::map<std::string, Screen2> Element;
};

struct WebAppTest2 {
   std::map<std::string, WebApp2> Element;
};

struct Hello2 {
   std::map<std::string, WebAppTest2> Element;
};

Hello2 MyWAT2;
```