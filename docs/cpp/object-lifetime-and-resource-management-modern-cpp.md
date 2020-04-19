---
title: オブジェクトの有効期間とリソースの管理 (RAII)
description: リソースリークを回避するためにC++ 、最新の RAII の原則に従います。
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 8aa0e1a1-e04d-46b1-acca-1d548490700f
ms.openlocfilehash: 01867ec0a71ba54bb6534da1b408cb0610d652a7
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303376"
---
# <a name="object-lifetime-and-resource-management-raii"></a>オブジェクトの有効期間とリソースの管理 (RAII)

マネージ言語とはC++異なり、には自動*ガベージコレクション*がありません。 これは、プログラムの実行時にヒープメモリおよびその他のリソースを解放する内部プロセスです。 C++プログラムは、取得したすべてのリソースをオペレーティングシステムに返す役割を担います。 未使用のリソースを解放できない場合は、*リーク*と呼ばれます。 リークしたリソースは、プロセスが終了するまで他のプログラムで使用できなくなります。 特にメモリリークは、C スタイルのプログラミングでのバグの一般的な原因です。

最新C++では、スタック上でオブジェクトを宣言することで、可能な限りヒープメモリを使用することを回避しています。 リソースが大きすぎてスタックを保持できない場合は、オブジェクトによって*所有*されている必要があります。 オブジェクトが初期化されると、そのオブジェクトが所有するリソースを取得します。 次に、オブジェクトは、デストラクターのリソースを解放します。 所有しているオブジェクト自体がスタックで宣言されています。 *オブジェクトがリソースを所有*するという原則は、"リソースの取得が初期化されています" または RAII とも呼ばれます。

リソース所有のスタックオブジェクトがスコープ外に出ると、そのデストラクターは自動的に呼び出されます。 このようにすると、のC++ガベージコレクションはオブジェクトの有効期間に密接に関連し、決定的なものになります。 リソースは、プログラム内の既知のポイントで常に解放され、制御できます。 では、メモリリソースとC++メモリ以外のリソースを同じように処理できます。

次の例は、単純なオブジェクト `w`を示しています。 これは関数スコープでスタック上で宣言され、関数ブロックの最後に破棄されます。 オブジェクト `w` が*リソース*(ヒープ割り当てメモリなど) を所有していません。 その唯一のメンバー `g` がスタックで宣言され、`w`と共にスコープ外に出ます。 `widget` デストラクターに特別なコードは必要ありません。

```cpp
class widget {
private:
    gadget g;   // lifetime automatically tied to enclosing object
public:
    void draw();
};

void functionUsingWidget () {
    widget w;   // lifetime automatically tied to enclosing scope
                // constructs w, including the w.g gadget member
    // ...
    w.draw();
    // ...
} // automatic destruction and deallocation for w and w.g
  // automatic exception safety,
  // as if "finally { w.dispose(); w.g.dispose(); }"
```

次の例では、`w` がメモリリソースを所有しているため、メモリを削除するには、デストラクターにコードを含める必要があります。
 
```cpp
class widget
{
private:
    int* data;
public:
    widget(const int size) { data = new int[size]; } // acquire
    ~widget() { delete[] data; } // release
    void do_something() {}
};

void functionUsingWidget() {
    widget w(1000000);   // lifetime automatically tied to enclosing scope
                        // constructs w, including the w.data member
    w.do_something();

} // automatic destruction and deallocation for w and w.data

```

C++ 11 以降では、標準ライブラリからスマートポインターを使用することにより、前の例を記述するより良い方法があります。 スマートポインターは、所有しているメモリの割り当てと削除を処理します。 スマートポインターを使用すると、`widget` クラスの明示的なデストラクターが不要になります。

```cpp
#include <memory>
class widget
{
private:
    std::unique_ptr<int> data;
public:
    widget(const int size) { data = std::make_unique<int>(size); }
    void do_something() {}
};

void functionUsingWidget() {
    widget w(1000000);   // lifetime automatically tied to enclosing scope
                // constructs w, including the w.data gadget member
    // ...
    w.do_something();
    // ...
} // automatic destruction and deallocation for w and w.data

```

メモリの割り当てにスマートポインターを使用すると、メモリリークの可能性を排除することができます。 このモデルは、ファイルハンドルやソケットなどの他のリソースに対して機能します。 独自のリソースは、クラス内で同様の方法で管理できます。 詳細については、「[スマートポインター](smart-pointers-modern-cpp.md)」を参照してください。

オブジェクトがスコープC++外に出ると、が確実に破棄されるように設計されています。 つまり、ブロックが終了したときに構築と逆の順序で破棄されます。 オブジェクトが破棄されると、その基底クラスとメンバーが特定の順序で破棄されます。 すべてのブロックの外側で宣言されたオブジェクトは、グローバルスコープで、問題の原因になる可能性があります。 グローバルオブジェクトのコンストラクターで例外がスローされた場合、デバッグが困難になることがあります。

## <a name="see-also"></a>参照

[に戻るC++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 言語リファレンス](../cpp/cpp-language-reference.md)<br/>
[C++ 標準ライブラリ](../standard-library/cpp-standard-library-reference.md)
