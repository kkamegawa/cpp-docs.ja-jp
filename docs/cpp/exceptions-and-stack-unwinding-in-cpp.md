---
title: C++ での例外とスタック アンワインド
ms.date: 11/19/2019
ms.assetid: a1a57eae-5fc5-4c49-824f-3ce2eb8129ed
ms.openlocfilehash: 11657206e86dbc81eb62c1e11b49fd87777f11d8
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246568"
---
# <a name="exceptions-and-stack-unwinding-in-c"></a>C++ での例外とスタック アンワインド

C++ 例外の機能では、制御は throw ステートメントから、スローされる型を処理できる最初の catch ステートメントに移動します。 Catch ステートメントに到達すると、throw ステートメントと catch ステートメントの間のスコープ内にあるすべての自動変数は、*スタックアンワインド*と呼ばれるプロセスで破棄されます。 スタック アンワインドでは、次のように実行されます。

1. 制御は通常の順次実行によって**try**ステートメントに到達します。 **Try**ブロック内の保護されたセクションが実行されます。

1. 保護されたセクションの実行中に例外がスローされなかった場合、 **try**ブロックに続く**catch**句は実行されません。 実行は、関連付けられ**ている try**ブロックの後にある最後の**catch**句の後のステートメントから続行されます。

1. 保護されたセクションの実行中、または保護されたセクションが直接または間接的に呼び出したルーチンで例外がスローされた場合は、 **throw**オペランドによって作成されたオブジェクトから例外オブジェクトが作成されます。 (これは、コピーコンストラクターが関係している可能性があることを意味します)。この時点で、コンパイラは、スローされた型の例外を処理できる上位の実行コンテキスト、または任意の種類の例外を処理できる**catch**ハンドラーに対して、 **catch**句を検索します。 **Catch**ハンドラーは、 **try**ブロックの後に表示されます。 適切なハンドラーが見つからない場合は、次に動的に囲む**try**ブロックが検査されます。 このプロセスは、最も外側にある**try**ブロックが検査されるまで続行されます。

1. 一致するハンドラーが見つからない場合、またはアンワインド処理中に例外が発生した場合でも、ハンドラーが制御を取得する前であれば、定義済みのランタイム関数 `terminate` が呼び出されます。 例外がスローされた後でも、アンワインドが開始される前に例外が発生した場合は、`terminate` が呼び出されます。

1. 一致する**catch**ハンドラーが見つかり、値渡しでキャッチした場合、その仮パラメーターは例外オブジェクトをコピーすることによって初期化されます。 参照によってキャッチする場合、例外オブジェクトを示すためにパラメーターが初期化されます。 正式なパラメーターが初期化されると、スタックをアンワインドするプロセスが開始されます。 これには、**キャッチ**ハンドラーに関連付けられ**ている try**ブロックの先頭と例外の throw サイトの間で完全に構築されていてもまだ破棄されていないすべての自動オブジェクトが破棄されます。 破棄は、構築の逆順に発生します。 **Catch**ハンドラーが実行され、最後のハンドラー (つまり、 **catch**ハンドラーではない最初のステートメントまたはコンストラクト) の後にプログラムが実行を再開します。 Control**ステートメント内の** **goto**ステートメントまたは**case**ラベルを使用しないで、スローされた例外を使用して**キャッチ**ハンドラーにのみ入力できます。

## <a name="stack-unwinding-example"></a>スタックアンワインドの例

次の例では、例外がスローされたときにスタックをアンワインドする方法を示します。 スレッド上で実行すると、`C` の throw ステートメントから `main` の catch ステートメントにジャンプし、その途中の各関数をアンワインドします。 `Dummy` オブジェクトが作成され、スコープ外として破棄される順序に注意してください。 関数が catch ステートメントを含む `main` なしで完了しないことにも注意してください。 関数 `A` はその `B()` の呼び出しから戻りません。`B` はその `C()` の呼び出しから戻りません。 `Dummy` ポインターの定義と対応する DELETE ステートメントをコメントから外してプログラムを実行すると、ポインターは削除されなくなります。 これは、関数が例外の保証を提供しない場合に発生することがある問題を示しています。 詳細については、「方法: 例外に対してデザインする」を参照してください。 catch ステートメントをコメント アウトすると、未処理の例外によってプログラムが終了するときの動作が示されます。

```cpp
#include <string>
#include <iostream>
using namespace std;

class MyException{};
class Dummy
{
    public:
    Dummy(string s) : MyName(s) { PrintMsg("Created Dummy:"); }
    Dummy(const Dummy& other) : MyName(other.MyName){ PrintMsg("Copy created Dummy:"); }
    ~Dummy(){ PrintMsg("Destroyed Dummy:"); }
    void PrintMsg(string s) { cout << s  << MyName <<  endl; }
    string MyName;
    int level;
};

void C(Dummy d, int i)
{
    cout << "Entering FunctionC" << endl;
    d.MyName = " C";
    throw MyException();

    cout << "Exiting FunctionC" << endl;
}

void B(Dummy d, int i)
{
    cout << "Entering FunctionB" << endl;
    d.MyName = "B";
    C(d, i + 1);
    cout << "Exiting FunctionB" << endl;
}

void A(Dummy d, int i)
{
    cout << "Entering FunctionA" << endl;
    d.MyName = " A" ;
  //  Dummy* pd = new Dummy("new Dummy"); //Not exception safe!!!
    B(d, i + 1);
 //   delete pd;
    cout << "Exiting FunctionA" << endl;
}

int main()
{
    cout << "Entering main" << endl;
    try
    {
        Dummy d(" M");
        A(d,1);
    }
    catch (MyException& e)
    {
        cout << "Caught an exception of type: " << typeid(e).name() << endl;
    }

    cout << "Exiting main." << endl;
    char c;
    cin >> c;
}

/* Output:
    Entering main
    Created Dummy: M
    Copy created Dummy: M
    Entering FunctionA
    Copy created Dummy: A
    Entering FunctionB
    Copy created Dummy: B
    Entering FunctionC
    Destroyed Dummy: C
    Destroyed Dummy: B
    Destroyed Dummy: A
    Destroyed Dummy: M
    Caught an exception of type: class MyException
    Exiting main.

*/
```
