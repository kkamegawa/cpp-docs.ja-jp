---
title: C++ コンソール アプリ プロジェクトを作成する
description: Visual C++ で Hello World コンソール アプリと電卓アプリを作成する
ms.custom: mvc
ms.date: 08/19/2019
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: ff1b5295f9fefd681ea76d09349415b59ceac1f2
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2019
ms.locfileid: "69631304"
---
# <a name="create-a-c-console-app-project"></a>C++ コンソール アプリ プロジェクトを作成する

::: moniker range=">=vs-2019"

C++ プログラマーにとってよくある出発点は、コマンド ラインで実行される "Hello, world!" アプリケーションです。 この記事でも、Visual Studio を利用してこのアプリを作成します。その後、もっと難しいアプリ、電卓アプリを作成します。

## <a name="prerequisites"></a>必須コンポーネント

- Visual Studio 2019 と、**C++ によるデスクトップ開発**ワークロードがコンピューターにインストールおよび実行されている必要があります。 まだインストールされていない場合は、[Visual Studio での C++ のインストール サポート](../build/vscpp-step-0-installation.md)に関するページを参照してください。

## <a name="create-your-app-project"></a>アプリのプロジェクトを作成する

Visual Studio では、"*プロジェクト*" を使用してアプリのコードを整理し、"*ソリューション*" を使用してプロジェクトを整理します。 プロジェクトには、アプリをビルドする場合に使用するすべてのオプション、構成、および規則が含まれています。 また、プロジェクトでは、プロジェクトのすべてのファイルと、外部のファイルとの間のリレーションシップも管理します。 アプリを作成するには、まず、新しいプロジェクトとソリューションを作成します。

1. Visual Studio を起動すると、Visual Studio 2019 ダイアログ ボックスが表示されます。 **[新しいプロジェクトの作成]** を選択して始めます。

   ![Visual Studio 2019 の最初のダイアログ](./media/calc-vs2019-initial-dialog.png "Visual Studio 2019 の最初のダイアログ")

   あるいは、Visual Studio のメニューバーで、 **[ファイル]** 、 **[新規作成]** 、 **[プロジェクト]** の順に選択します。 **[新しいプロジェクトの作成]** ウィンドウが開きます。

1. プロジェクト テンプレートの一覧で **[コンソール アプリ]** を選択し、 **[次へ]** を選択します。

   ![コンソール アプリ テンプレートを選択する](./media/calc-vs2019-choose-console-app.png "コンソール アプリ テンプレートを選択する")

   > [!Important]
   > 必ず、C++ バージョンの**コンソール アプリ** テンプレートを選択します。 **[C++]** 、 **[Windows]** 、および **[コンソール]** のタグと、アイコンの隅に "++" が表示されています。

1. **[新しいプロジェクトを構成します]** ダイアログ ボックスで、 **[プロジェクト名]** 編集ボックスを選択し、新しいプロジェクトに「*CalculatorTutorial*」という名前を付け、 **[作成]** を選択します。

   ![[新しいプロジェクトを構成します] ダイアログでプロジェクトに名前を付ける](./media/calc-vs2019-name-your-project.png "[新しいプロジェクトを構成します] ダイアログでプロジェクトに名前を付ける")

   空の C++ Windows コンソール アプリケーションが作成されます。 コンソール アプリケーションは Windows コンソール ウィンドウを使用して出力を表示し、ユーザー入力を受け付けます。 Visual Studio でエディター ウィンドウが開き、生成されたコードが表示されます。

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include <iostream>

    int main()
    {
        std::cout << "Hello World!\n";
    }

    // Run program: Ctrl + F5 or Debug > Start Without Debugging menu
    // Debug program: F5 or Debug > Start Debugging menu

    // Tips for Getting Started:
    //   1. Use the Solution Explorer window to add/manage files
    //   2. Use the Team Explorer window to connect to source control
    //   3. Use the Output window to see build output and other messages
    //   4. Use the Error List window to view errors
    //   5. Go to Project > Add New Item to create new code files, or Project > Add Existing Item to add existing code files to the project
    //   6. In the future, to open this project again, go to File > Open > Project and select the .sln file
    ```

## <a name="verify-that-your-new-app-builds-and-runs"></a>新しいアプリがビルドされ、動作することを確認する

新しい Windows コンソール アプリケーション用のテンプレートで、単純な C++ の "Hello World" アプリを作成します。 この時点で、作成したアプリを IDE から直接 Visual Studio でビルドおよび実行する方法を確認できます。

1. プロジェクトをビルドするには、 **[ビルド]** メニューの **[ソリューションのビルド]** を選択します。 **[出力]** ウィンドウに、ビルド プロセスの結果が表示されます。

   ![プロジェクトのビルド](./media/calc-vs2019-build-your-project.png "プロジェクトのビルド")

1. コードを実行するには、メニュー バーで **[デバッグ]** 、 **[デバッグなしで開始]** の順に選択します。

   ![プロジェクトの開始](./media/calc-vs2019-hello-world-console.png "プロジェクトの開始")

   コンソール ウィンドウが開き、アプリが実行されます。Visual Studio でコンソール アプリを起動すると、コードが実行され、「このウィンドウを閉じるには、どれかキーを押してください...」と表示されるので、出力を確認できます。おめでとうございます! 最初の "Hello, world!" コンソール アプリを Visual Studio で作成しました。

1. キーを押してコンソール ウィンドウを閉じ、Visual Studio に戻ります。

これで、変更を加えるたびにアプリをビルドして実行するツールを利用して、コードが期待どおりに機能することを確認できるようになりました。 機能しない場合にデバッグする方法については後述します。

## <a name="edit-the-code"></a>コードを編集する

次はこのテンプレートのコードを電卓アプリに変えましょう。

1. *CalculatorTutorial.cpp* ファイルで、この例に合わせてコードを編集します。

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include <iostream>

    using namespace std;

    int main()
    {
        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b"
            << endl;
        return 0;
    }

    // Run program: Ctrl + F5 or Debug > Start Without Debugging menu
    // Debug program: F5 or Debug > Start Debugging menu
    // Tips for Getting Started:
    //   1. Use the Solution Explorer window to add/manage files
    //   2. Use the Team Explorer window to connect to source control
    //   3. Use the Output window to see build output and other messages
    //   4. Use the Error List window to view errors
    //   5. Go to Project > Add New Item to create new code files, or Project > Add Existing Item to add existing code files to the project
    //   6. In the future, to open this project again, go to File > Open > Project and select the .sln file
    ```

   > コードの概要:
   >
   > - `#include` ステートメントを使用すると、他のファイル内のコードを参照できます。 ファイル名は、山かっこ ( **\<\>** ) で囲まれる場合や引用符 ( **" "** ) で囲まれる場合があります。 一般に、山かっこは C++ 標準ライブラリを参照するときに使用され、引用符は他のファイルに使用されます。
   > - `using namespace std;` 行は、このファイルに C++ 標準ライブラリの内容が使用されることを想定するようにコンパイラに指示します。 この行を含めない場合、ライブラリの各キーワードの前に `std::` を付けてそのスコープを示す必要があります。 たとえば、その行がない場合、`cout` への各参照は `std::cout` と記述する必要があります。 `using` ステートメントは、コードをわかりやすくするために追加されています。
   > - `cout` キーワードは、C++ の標準出力に出力するために使用されています。 **\<\<** 演算子は、その右側にあるものはすべて標準出力に送信するようにコンパイラに指示します。
   > - **endl** キーワードは Enter キーに似ています。つまり、その行を終了し、カーソルを次の行に移動します。 `endl` によって常にバッファーはフラッシュされ、プログラムのパフォーマンスが低下する可能性があるため、同じ処理を実行するには、("" で囲んで) 文字列内に `\n` を配置することをお勧めします。ただし、これは非常に小さなアプリなので、読みやすいように代わりに `endl` を使用します。
   > - すべての C++ ステートメントの末尾にはセミコロンを付ける必要があります。また、すべての C++ アプリケーションには `main()` 関数を含める必要があります。 この関数は、プログラムが最初に実行するものです。 使用するには、すべてのコードが `main()` からアクセスできる必要があります。

1. ファイルを保存するには、**Ctrl + S** キーを押すか、IDE の上部近くにある **[保存]** アイコン (メニュー バー下のツール バーのフロッピー ディスク アイコン) を選択します。

1. アプリケーションを実行するには、**Ctrl + F5** キーを押すか、 **[デバッグ]** メニューに移動して **[デバッグなしで開始]** を選択します。 コードで指定したテキストを表示するコンソール ウィンドウが出現するのを確認できます。

1. 完了したらコンソール ウィンドウを閉じます。

## <a name="add-code-to-do-some-math"></a>計算を実行するコードを追加する

いくつかの計算ロジックを追加しましょう。

### <a name="to-add-a-calculator-class"></a>Calculator クラスを追加するには

1. **[プロジェクト]** メニューの **[クラスの追加]** を選択します。 **[クラス名]** 編集ボックスに、「*Calculator*」と入力します。 **[OK]** をクリックします。 2 つの新しいファイルがプロジェクトに追加されます。 変更したファイルを一度にすべて保存するには、**Ctrl + Shift + S** キーを押します。 これは **[ファイル]**  >  **[すべて保存]** のキーボード ショートカットです。 **[保存]** ボタンの横にあるツール バーのボタン **[すべて保存]** (2 枚のフロッピー ディスクのアイコン) もあります。 一般に、保存時にファイルの漏れがないように、 **[すべて保存]** を頻繁に実行することをお勧めします。

   ![Calculator クラスの作成](./media/calc-vs2019-create-calculator-class.png "Calculator クラスの作成")

   クラスは、何かを実行するオブジェクトのブループリントのようなものです。 この例では、電卓とそれがどのように動作するかを定義します。 上で使用した **[クラスの追加]** ウィザードでは、クラスと同じ名前の .h ファイルと .cpp ファイルを作成しました。 IDE の横に表示される **[ソリューション エクスプローラー]** ウィンドウには、プロジェクト ファイルの完全な一覧が表示されます。 このウィンドウが表示されていない場合は、メニュー バーから開くことができます。 **[表示]**  >  **[ソリューション エクスプローラー]** を選択してください。

   ![ソリューション エクスプローラー](./media/calc-vs2019-solution-explorer.png "ソリューション エクスプローラー")

   これで、エディターに 3 つのタブが表示されます。*CalculatorTutorial.cpp*、*Calculator.h*、および *Calculator.cpp* です。 そのうちのいずれかを誤って閉じた場合は、 **[ソリューション エクスプローラー]** ウィンドウでダブルクリックして再度開くことができます。

1. ここでは不要なので、**Calculator.h** で、生成された `Calculator();` 行と `~Calculator();` 行を削除します。 次に、ファイルが以下のようになるように、次のコード行を追加します。

    ```cpp
    #pragma once
    class Calculator
    {
    public:
        double Calculate(double x, char oper, double y);
    };
    ```

   > コードの概要
   >
   > - 追加した行では `Calculate` という新しい関数を宣言しています。これは、加算、減算、乗算、除算の算術演算を実行するために使用します。
   > - C++ コードは、*ヘッダー* (.h) ファイルと*ソース* (.cpp) ファイルに編成されています。 さまざまなコンパイラが他のいくつかのファイル拡張子をサポートしていますが、これらは知っておくべき主な拡張子です。 通常、関数と変数は*宣言*されます。つまり、ヘッダー ファイルで名前と型が指定され、ソース ファイルで*実装*されるか定義が与えられます。 別のファイルで定義されているコードにアクセスするには、`#include "filename.h"` を使用できます。この 'filename.h' は、使用する変数または関数を宣言しているファイルの名前です。
   > - 削除した 2 行では、クラスの "*コンストラクター*" と "*デストラクター*" が宣言されていました。 このような単純なクラスの場合は、コンパイラによって自動的に作成されます。その使用方法は、このチュートリアルでは扱いません。
   > - コードは、処理内容に基づいて複数のファイルに編成することをお勧めします。こうすることで、後で必要なコードを簡単に見つけられます。 この例では、`main()` 関数を含むファイルとは別に `Calculator` クラスを定義しますが、`main()` 内から `Calculator` クラスを参照する予定です。

1. `Calculate` の下に緑色の波線が表示されます。 これは、.cpp ファイルで `Calculate` 関数を定義していないためです。 単語をポイントし、ポップアップ表示された電球 (今回はねじ回し) をクリックして、 **[Create definition of 'Calculate' in Calculator.cpp]\(Calculator.cpp で 'Calculate' の定義を作成\)** を選択します。

   ![Calculate の定義の作成](./media/calc-vs2019-create-definition.png "Calculate の定義の作成")

   ポップアップが表示され、他のファイルで行われたコード変更を確認できます。 コードが *Calculator.cpp* に追加されました。

   ![Calculate の定義を含むポップアップ](./media/calc-vs2019-pop-up-definition.png "Calculate の定義を含むポップアップ")

   現時点では単に 0.0 が返されます。 これを変えてみましょう。 **Esc** キーを押してポップアップを閉じます。

1. エディター ウィンドウで *Calculator.cpp* ファイルに切り替えます。 (.h ファイルの場合と同様に) `Calculator()` セクションと `~Calculator()` セクションを削除し、次のコードを `Calculate()` に追加します。

    ```cpp
    #include "Calculator.h"

    double Calculator::Calculate(double x, char oper, double y)
    {
        switch(oper)
        {
            case '+':
                return x + y;
            case '-':
                return x - y;
            case '*':
                return x * y;
            case '/':
                return x / y;
            default:
                return 0.0;
        }
    }
    ```

   > コードの概要
   >
   > - 関数 `Calculate` では、数値、演算子、および 2 番目の数値を使用してから、その数字に対して要求された操作を実行します。
   > - switch ステートメントでは、指定された演算子を確認し、その演算に対応する case のみを実行します。 既定値: case は、ユーザーが受け入れられない演算子を入力した場合のフォールバックです。そのためプログラムは中断しません。 一般に、より洗練された方法で無効なユーザー入力を処理することが最善ですが、このチュートリアルでは扱いません。
   > - `double` キーワードは、小数をサポートする数値の種類を表します。 このようにすると、電卓は小数の計算と整数の計算の両方を扱うことができます。 `Calculate` 関数は、コードの先頭に `double` があるため、常にこのような数値を返す必要があります (これは関数の戻り型を表します)。そのため、既定の case でも 0.0 が返される理由です。
   > - .h ファイルは、関数の*プロトタイプ*を宣言します。これは、必要なパラメーターと、それから返される戻り値の型をコンパイラに事前に通知するものです。 .cpp ファイルには、関数の実装に関する詳細がすべて含まれています。

この時点でコードをビルドし、もう一度実行すると、実行する操作を問われた後に終了となります。 次に、いくつかの計算を行うように `main` 関数を修正します。

### <a name="to-call-the-calculator-class-member-functions"></a>Calculator クラスのメンバー関数を呼び出すには

1. それでは、*CalculatorTutorial.cpp* の `main` 関数を更新しましょう。

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include <iostream>
    #include "Calculator.h"

    using namespace std;

    int main()
    {
        double x = 0.0;
        double y = 0.0;
        double result = 0.0;
        char oper = '+';

        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b"
             << endl;

        Calculator c;
        while (true)
        {
            cin >> x >> oper >> y;
            result = c.Calculate(x, oper, y);
            cout << "Result is: " << result << endl;
        }

        return 0;
    }
    ```

   > コードの概要
   >
   > - C++ プログラムは常に `main()` 関数から始まり、そこから他のコードを呼び出す必要があるため、`#include` ステートメントが必要です。
   > - 一部の初期変数 `x`、`y`、`oper`、および `result` は、それぞれ最初の数値、2 番目の数値、演算子、および最終結果を格納するために宣言されています。 未定義の動作を回避するために、この例のように、何らかの初期値を指定しておくことを常にお勧めします。
   > - `Calculator c;` 行は、`Calculator` クラスのインスタンスとして 'c' というオブジェクトを宣言しています。 このクラス自体は、電卓がどのように機能するかを示す単なるブループリントです。オブジェクトは計算を実行する特定の電卓です。
   > - `while (true)` ステートメントはループです。 `()` 内の条件を満たしている限り、ループ内のコードは繰り返し実行されます。 条件は単に `true` と指定されているため、常に true になり、ループは永遠に実行されます。 プログラムを閉じるには、ユーザーは手動でコンソール ウィンドウを閉じる必要があります。 それ以外の場合、プログラムは常に新しい入力を待機します。
   > - `cin` キーワードは、ユーザーからの入力を受け付けるために使用されます。 コンソール ウィンドウに入力されたテキストの行を処理し、ユーザー入力が必要な仕様に一致すると想定して、列挙された各変数の内側に順番に配置するのであれば、この入力ストリームで十分です。 この行を変更して、たとえば 2 つを超える数値など、さまざまな種類の入力を受け入れることができますが、この処理には `Calculate()` 関数も更新する必要があります。
   > - `c.Calculate(x, oper, y);` 式は、前に定義した`Calculate` 関数を呼び出し、入力された値を提供します。 次に、関数は `result` に格納された数値を返します。
   > - 最後に、`result` がコンソールに出力されるので、ユーザーには計算結果が表示されます。

### <a name="build-and-test-the-code-again"></a>コードのビルドとテストの再実行

それでは、もう一度プログラムをテストして、すべてが正しく機能することを確認します。

1. **Ctrl + F5** キーを押してアプリをビルドして起動します。

1. 「`5 + 5`」と入力し、**Enter** キーを押します。 結果が 10 であることを確認してください。

   ![5 + 5 の結果](./media/calc-vs2019-five-plus-five.png "5 + 5 の結果")

## <a name="debug-the-app"></a>アプリをデバッグする

ユーザーはコンソール ウィンドウに自由に入力できるので、電卓が一部の入力を想定どおりに処理するようにしましょう。 プログラムを実行するのではなく、代わりにデバッグして、実行内容を詳細に確認することができます。

### <a name="to-run-the-app-in-the-debugger"></a>デバッガーでアプリを実行するには

1. ユーザーが入力を求められた直後に、`result = c.Calculate(x, oper, y);` 行にブレークポイントを設定します。 ブレークポイントを設定するには、行の横の、エディター ウィンドウの左端に沿った灰色の縦線をクリックします。 赤い点が表示されます。

   ![ブレークポイントを設定する](./media/calc-vs2019-set-breakpoint.png "ブレークポイントを設定する")

   プログラムをデバッグするときは、常にその行で実行が一時停止されます。 単純なケースではプログラムが動作することが既に大体わかっています。 実行を毎回一時停止させないために、条件付きのブレークポイントを設定しましょう。

1. ブレークポイントを表す赤丸を右クリックし、 **[条件]** を選択します。 条件の編集ボックスに「`(y == 0) && (oper == '/')`」と入力します。 完了したら、 **[閉じる]** ボタンを選択します。 条件は自動的に保存されます。

   ![条件付きブレークポイントの設定](./media/calc-vs2019-conditional-breakpoint.png "条件付きブレークポイントの設定")

   これで、ゼロ除算が試行された場合に、ブレークポイントで実行が一時停止されます。

1. プログラムをデバッグするには、**F5** キーを押すか、緑色の矢印アイコンがあるツール バーのボタン **[ローカル Windows デバッガー]** を選択します。 コンソール アプリで、「5 - 0」のように入力した場合、プログラムは正常に動作し、実行が継続されます。 ただし、「10/0」と入力すると、ブレークポイントで一時停止されます。 演算子と数値の間には任意の数のスペースを入れることもできます。`cin` で、入力を適切に解析できます。

   ![条件付きブレークポイントの一時停止](./media/calc-vs2019-debug-breakpoint.png "条件付きブレークポイントの一時停止")

### <a name="useful-windows-in-the-debugger"></a>デバッガーの便利なウィンドウ

コードをデバッグするたびに、新しいウィンドウがいくつか表示されることに注意してください。 これらは、デバッグ エクスペリエンスを支援するウィンドウです。 **[自動]** ウィンドウを見てください。 **[自動]** ウィンドウには、3 行以上前から現在の行までに使用されている変数の現在の値が表示されます。 その関数のすべての変数を確認するには、 **[ローカル]** ウィンドウに切り替えます。 このような変数の値をデバッグ中に実際に変更して、プログラムにどのような影響があるかを確認できます。 この例では、そのままにします。

   ![[ローカル] ウィンドウ](./media/calc-vs2019-debug-locals.png "[ローカル] ウィンドウ")

また、コード内の変数をポイントして、実行が一時停止されている現在の値を確認することもできます。 まずエディター ウィンドウをクリックして、フォーカスを切り替えます。

   ![ポイントして現在の変数値を表示](./media/calc-vs2019-hover-tooltip.png "ポイントして現在の変数値を表示")

### <a name="to-continue-debugging"></a>デバッグを続行するには

1. 左側の黄色の線は、現在の実行ポイントを示します。 現在の行で `Calculate` を呼び出すため、**F11** キーを押して関数の **[ステップ イン]** を行います。 `Calculate` 関数の本文が表示されます。 **[ステップ イン]** は気を付けて使ってください。実行しすぎると、多くの時間を無駄にする場合があります。 これを使うと、標準ライブラリの関数を含めて、現在の行で使っているすべてのコードを調査します。

1. 実行ポイントが `Calculate` 関数の先頭になったら、**F10** キーを押してプログラムの実行内の次の行に移動します。 **F10** キーは **[ステップ オーバー]** とも呼ばれます。 **[ステップ オーバー]** を使用すると、行の各部分で発生していることを詳しく調べることなく、行から行へ移動できます。 一般に、(実行して `Calculate` の本文に達したので) 別の場所から呼び出されたコードを詳しく掘り下げる場合を除き、 **[ステップ イン]** ではなく **[ステップ オーバー]** を使用することをお勧めします。

1. もう一方のファイルの `main()` 関数に戻るまで繰り返し **F10** キーを押して各行の **[ステップ オーバー]** を行い、`cout` 行で停止します。

   プログラムは期待どおりに動作しているように見えます。最初の数字を受け取り、それを 2 番目の数字で割ります。 `cout` 行の `result` 変数をポイントするか、 **[自動]** ウィンドウの `result` を確認します。 その値は "inf" として表示されます。これは正しくないようなので、修正しましょう。 `cout` 行は、`result` に格納されている値をそのまま出力するため、**F10** キーを使用してもう 1 行進むと、コンソール ウィンドウに次が表示されます。

   ![ゼロ除算の結果](./media/calc-vs2019-divide-by-zero-fail.png "ゼロ除算の結果")

   この結果は、ゼロ除算が定義されていないために発生します。そのため、プログラムは要求された操作に対して数値の答えを得られません。

### <a name="to-fix-the-divide-by-zero-error"></a>"ゼロ除算" エラーを修正するには

ユーザーが問題を理解できるように、ゼロ除算をより適切に処理しましょう。

1. *CalculatorTutorial.cpp* に次の変更を加えます ( **[エディット コンティニュ]** というデバッガー機能のおかげで、編集中にプログラムを実行したままにすることができます)。

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include <iostream>
    #include "Calculator.h"

    using namespace std;

    int main()
    {
        double x = 0.0;
        double y = 0.0;
        double result = 0.0;
        char oper = '+';

        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b" << endl;

        Calculator c;
        while (true)
        {
            cin  >> x  >> oper  >> y;
            if (oper == '/' && y == 0)
            {
                cout << "Division by 0 exception" << endl;
                continue;
            }
            else
            {
                result = c.Calculate(x, oper, y);
            }
            cout << "Result is: " << result << endl;
        }

        return 0;
    }
    ```

1. 次に **F5** キーを一度押します。 ユーザー入力を求めるために一時停止する必要があるまで、プログラムの実行が継続されます。 もう一度「`10 / 0`」と入力します。 今度はより役に立つメッセージが表示されます。 ユーザーはさらに入力を求められ、プログラムは通常どおり実行が継続されます。

   ![変更後の最終的な結果](./media/calc-vs2019-final-verification.png "変更後の最終的な結果")

   > [!Note]
   > デバッグ モードでコードを編集すると、コードが古くなる危険性があります。 これは、デバッガーがまだ古いコードを実行していて、まだ変更が反映されていない場合に発生します。 このような状況になると、デバッガーによってダイアログがポップアップ表示されます。 **F5** キーを押して実行中のコードを更新する必要がある場合があります。 特に、実行ポイントが関数内にあるときに関数内に変更を加えた場合は、関数からステップ アウトし、ステップ インして更新されたコードを取得する必要があります。 それが何らかの理由でうまくいかず、エラー メッセージが表示される場合は、IDE の上部にあるメニューの下にあるツール バーの赤色の四角をクリックしてデバッグを中止し、**F5** キーを押してデバッグを再開します。または、ツール バーの停止ボタンの横にある緑色の [再生] 矢印を選択します。

   > [実行] と [デバッグ] のショートカットの概要
   >
   > - **F5** キーを押すと (または **[デバッグ]**  >  **[デバッグの開始]** )、デバッグ セッションがまだアクティブでない場合は開始され、プログラムが実行され、ブレークポイントにヒットするか、ユーザー入力が必要になると停止されます。 ユーザー入力が不要で、ヒットするブレークポイントがない場合、プログラムは終了します。プログラムの実行が完了すると、コンソール ウィンドウは自動的に閉じます。 "Hello World" のようなプログラムを実行する場合は、**F5** キーを押す前 **Ctrl + F5** キーを押すか、ブレークポイントを設定してウィンドウを開いたままにします。
   > - **Ctrl + F5** キーを押すと (または **[デバッグ]**  >  **[デバッグなしで開始]** )、デバッグ モードに移行せずにアプリケーションを実行します。 これはデバッグよりもわずかに速く、プログラムの実行が完了した後もコンソール ウィンドウは開いたままです。
   > - **F10** キー ( **[ステップ オーバー]** と呼ばれます) を使用すると、コードを 1 行ずつ繰り返し実行し、コードの実行方法と各実行手順での変数値を視覚化できます。
   > - **F11** キー ( **[ステップ イン]** と呼ばれます) を使用すると、 **[ステップ オーバー]** と同様に機能しますが、実行中の行で呼び出される関数にステップ インする点が異なります。 たとえば、実行中の行が関数を呼び出す場合、**F11** キーを押すと、ポインターが関数の本文に移動するので、開始した行に戻る前に実行中の関数のコードに従うことができます。 **F10** キーを押すと、関数呼び出しがステップ オーバーされ、次の行に移動します。関数呼び出しはまだ行われますが、実行内容を示すためにプログラムは一時停止しません。

### <a name="close-the-app"></a>アプリを閉じる

- まだ実行中の場合は、電卓アプリのコンソール ウィンドウを閉じます。

## <a name="the-finished-app"></a>完成したアプリ

おめでとうございます! 電卓アプリのコードを完成し、Visual Studio でビルドしてデバッグしました。

## <a name="next-steps"></a>次の手順

[Visual Studio for C++ の詳細](https://blogs.msdn.microsoft.com/vcblog/2017/04/21/getting-started-with-visual-studio-for-c-and-cpp-development/)

::: moniker-end

::: moniker range="<vs-2019"

C++ プログラマーにとってよくある出発点は、コマンド ラインで実行される "Hello, world!" アプリケーションです。 この記事でも、Visual Studio を利用してこのアプリを作成します。その後、もっと難しいアプリ、電卓アプリを作成します。

## <a name="prerequisites"></a>必須コンポーネント

- Visual Studio 2019 と、**C++ によるデスクトップ開発**ワークロードがコンピューターにインストールおよび実行されている必要があります。 まだインストールされていない場合は、[Visual Studio での C++ のインストール サポート](../build/vscpp-step-0-installation.md)に関するページを参照してください。

## <a name="create-your-app-project"></a>アプリのプロジェクトを作成する

Visual Studio では、"*プロジェクト*" を使用してアプリのコードを整理し、"*ソリューション*" を使用してプロジェクトを整理します。 プロジェクトには、アプリをビルドする場合に使用するすべてのオプション、構成、および規則が含まれています。 また、プロジェクトでは、プロジェクトのすべてのファイルと、外部のファイルとの間のリレーションシップも管理します。 アプリを作成するには、まず、新しいプロジェクトとソリューションを作成します。

1. Visual Studio のメニューバーで、 **[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** の順に選択します。 **[新しいプロジェクト]** ウィンドウが開きます。

2. 左側のサイドバーで **[Visual C++]** が選択されていることを確認します。 中央にある **[Windows コンソール アプリケーション]** を選択します。

3. 下部にある **[名前]** 編集ボックスで、新しいプロジェクトに「*CalculatorTutorial*」と名前を付け、 **[OK]** を選択します。

   ![[新しいプロジェクト] ダイアログ](./media/calculator-new-project-dialog.png "[新しいプロジェクト] ダイアログ")

   空の C++ Windows コンソール アプリケーションが作成されます。 コンソール アプリケーションは Windows コンソール ウィンドウを使用して出力を表示し、ユーザー入力を受け付けます。 Visual Studio でエディター ウィンドウが開き、生成されたコードが表示されます。

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include "pch.h"
    #include <iostream>

    int main()
    {
        std::cout << "Hello World!\n"; 
    }

    // Run program: Ctrl + F5 or Debug > Start Without Debugging menu
    // Debug program: F5 or Debug > Start Debugging menu

    // Tips for Getting Started: 
    //   1. Use the Solution Explorer window to add/manage files
    //   2. Use the Team Explorer window to connect to source control
    //   3. Use the Output window to see build output and other messages
    //   4. Use the Error List window to view errors
    //   5. Go to Project > Add New Item to create new code files, or Project > Add Existing Item to add existing code files to the project
    //   6. In the future, to open this project again, go to File > Open > Project and select the .sln file
    ```

## <a name="verify-that-your-new-app-builds-and-runs"></a>新しいアプリがビルドされ、動作することを確認する

新しい Windows コンソール アプリケーション用のテンプレートで、単純な C++ の "Hello World" アプリを作成します。 この時点で、作成したアプリを IDE から直接 Visual Studio でビルドおよび実行する方法を確認できます。

1. プロジェクトをビルドするには、 **[ビルド]** メニューの **[ソリューションのビルド]** を選択します。 **[出力]** ウィンドウに、ビルド プロセスの結果が表示されます。

   ![プロジェクトのビルド](./media/calculator-initial-build-output.png "プロジェクトのビルド")

1. コードを実行するには、メニュー バーで **[デバッグ]** 、 **[デバッグなしで開始]** の順に選択します。

   ![プロジェクトの開始](./media/calculator-hello-world-console.png "プロジェクトの開始")

   コンソール ウィンドウが開き、アプリが実行されます。 Visual Studio でコンソール アプリを起動すると、コードが実行され、"続行するには何かキーを押してください . " と表示されるので、出力を確認できます。 おめでとうございます! 最初の "Hello, world!" コンソール アプリを Visual Studio で作成しました。

1. キーを押してコンソール ウィンドウを閉じ、Visual Studio に戻ります。

これで、変更を加えるたびにアプリをビルドして実行するツールを利用して、コードが期待どおりに機能することを確認できるようになりました。 機能しない場合にデバッグする方法については後述します。

## <a name="edit-the-code"></a>コードを編集する

次はこのテンプレートのコードを電卓アプリに変えましょう。

1. *CalculatorTutorial.cpp* ファイルで、この例に合わせてコードを編集します。

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include "pch.h"
    #include <iostream>

    using namespace std;

    int main()
    {
        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b"
            << endl;
        return 0;
    }

    // Run program: Ctrl + F5 or Debug > Start Without Debugging menu
    // Debug program: F5 or Debug > Start Debugging menu
    // Tips for Getting Started:
    //   1. Use the Solution Explorer window to add/manage files
    //   2. Use the Team Explorer window to connect to source control
    //   3. Use the Output window to see build output and other messages
    //   4. Use the Error List window to view errors
    //   5. Go to Project > Add New Item to create new code files, or Project > Add Existing Item to add existing code files to the project
    //   6. In the future, to open this project again, go to File > Open > Project and select the .sln file
    ```

   > コードの概要:
   >
   > - `#include` ステートメントを使用すると、他のファイル内のコードを参照できます。 ファイル名は、山かっこ ( **\<\>** ) で囲まれる場合や引用符 ( **" "** ) で囲まれる場合があります。 一般に、山かっこは C++ 標準ライブラリを参照するときに使用され、引用符は他のファイルに使用されます。
   > - `#include "pch.h"` (Visual Studio 2017 以前では `#include "stdafx.h"`) 行は、プリコンパイル済みヘッダーと呼ばれるものを参照しています。 これらはコンパイル時間を短縮するためにプロのプログラマーがよく使用しますが、このチュートリアルでは扱いません。
   > - `using namespace std;` 行は、このファイルに C++ 標準ライブラリの内容が使用されることを想定するようにコンパイラに指示します。 この行を含めない場合、ライブラリの各キーワードの前に `std::` を付けてそのスコープを示す必要があります。 たとえば、その行がない場合、`cout` への各参照は `std::cout` と記述する必要があります。 `using` ステートメントは、コードをわかりやすくするために追加されています。
   > - `cout` キーワードは、C++ の標準出力に出力するために使用されています。 **\<\<** 演算子は、その右側にあるものはすべて標準出力に送信するようにコンパイラに指示します。
   > - **endl** キーワードは Enter キーに似ています。つまり、その行を終了し、カーソルを次の行に移動します。 `endl` によって常にバッファーはフラッシュされ、プログラムのパフォーマンスが低下する可能性があるため、同じ処理を実行するには、("" で囲んで) 文字列内に `\n` を配置することをお勧めします。ただし、これは非常に小さなアプリなので、読みやすいように代わりに `endl` を使用します。
   > - すべての C++ ステートメントの末尾にはセミコロンを付ける必要があります。また、すべての C++ アプリケーションには `main()` 関数を含める必要があります。 この関数は、プログラムが最初に実行するものです。 使用するには、すべてのコードが `main()` からアクセスできる必要があります。

1. ファイルを保存するには、**Ctrl + S** キーを押すか、IDE の上部近くにある **[保存]** アイコン (メニュー バー下のツール バーのフロッピー ディスク アイコン) を選択します。

1. アプリケーションを実行するには、**Ctrl + F5** キーを押すか、 **[デバッグ]** メニューに移動して **[デバッグなしで開始]** を選択します。 **[このプロジェクトは最新ではありません]** というポップアップが表示された場合、 **[今後このダイアログを表示しない]** を選択してから、 **[はい]** を選択してアプリケーションをビルドできます。 コードで指定したテキストを表示するコンソール ウィンドウが出現するのを確認できます。

   ![アプリケーションのビルドと起動](./media/calculator-first-launch.gif "アプリケーションのビルドと起動")

1. 完了したらコンソール ウィンドウを閉じます。

## <a name="add-code-to-do-some-math"></a>計算を実行するコードを追加する

いくつかの計算ロジックを追加しましょう。

### <a name="to-add-a-calculator-class"></a>Calculator クラスを追加するには

1. **[プロジェクト]** メニューの **[クラスの追加]** を選択します。 **[クラス名]** 編集ボックスに、「*Calculator*」と入力します。 **[OK]** をクリックします。 2 つの新しいファイルがプロジェクトに追加されます。 変更したファイルを一度にすべて保存するには、**Ctrl + Shift + S** キーを押します。 これは **[ファイル]**  >  **[すべて保存]** のキーボード ショートカットです。 **[保存]** ボタンの横にあるツール バーのボタン **[すべて保存]** (2 枚のフロッピー ディスクのアイコン) もあります。 一般に、保存時にファイルの漏れがないように、 **[すべて保存]** を頻繁に実行することをお勧めします。

   ![Calculator クラスの作成](./media/calculator-create-class.gif "Calculator クラスの作成")

   クラスは、何かを実行するオブジェクトのブループリントのようなものです。 この例では、電卓とそれがどのように動作するかを定義します。 上で使用した **[クラスの追加]** ウィザードでは、クラスと同じ名前の .h ファイルと .cpp ファイルを作成しました。 IDE の横に表示される **[ソリューション エクスプローラー]** ウィンドウには、プロジェクト ファイルの完全な一覧が表示されます。 このウィンドウが表示されていない場合は、メニュー バーから開くことができます。 **[表示]**  >  **[ソリューション エクスプローラー]** を選択してください。

   ![ソリューション エクスプローラー](./media/calculator-solution-explorer.png "ソリューション エクスプローラー")

   これで、エディターに 3 つのタブが表示されます。*CalculatorTutorial.cpp*、*Calculator.h*、および *Calculator.cpp* です。 そのうちのいずれかを誤って閉じた場合は、 **[ソリューション エクスプローラー]** ウィンドウでダブルクリックして再度開くことができます。

1. ここでは不要なので、**Calculator.h** で、生成された `Calculator();` 行と `~Calculator();` 行を削除します。 次に、ファイルが以下のようになるように、次のコード行を追加します。

    ```cpp
    #pragma once
    class Calculator
    {
    public:
        double Calculate(double x, char oper, double y);
    };
    ```

   > コードの概要
   >
   > - 追加した行では `Calculate` という新しい関数を宣言しています。これは、加算、減算、乗算、除算の算術演算を実行するために使用します。
   > - C++ コードは、*ヘッダー* (.h) ファイルと*ソース* (.cpp) ファイルに編成されています。 さまざまなコンパイラが他のいくつかのファイル拡張子をサポートしていますが、これらは知っておくべき主な拡張子です。 通常、関数と変数は*宣言*されます。つまり、ヘッダー ファイルで名前と型が指定され、ソース ファイルで*実装*されるか定義が与えられます。 別のファイルで定義されているコードにアクセスするには、`#include "filename.h"` を使用できます。この 'filename.h' は、使用する変数または関数を宣言しているファイルの名前です。
   > - 削除した 2 行では、クラスの "*コンストラクター*" と "*デストラクター*" が宣言されていました。 このような単純なクラスの場合は、コンパイラによって自動的に作成されます。その使用方法は、このチュートリアルでは扱いません。
   > - コードは、処理内容に基づいて複数のファイルに編成することをお勧めします。こうすることで、後で必要なコードを簡単に見つけられます。 この例では、`main()` 関数を含むファイルとは別に `Calculator` クラスを定義しますが、`main()` 内の `Calculator` クラスを参照する予定です。

1. `Calculate` の下に緑色の波線が表示されます。 これは、.cpp ファイルで `Calculate` 関数を定義していないためです。 単語をポイントし、ポップアップ表示された電球をクリックして、 **[Create definition of 'Calculate' in Calculator.cpp]\(Calculator.cpp で 'Calculate' の定義を作成\)** を選択します。 ポップアップが表示され、他のファイルで行われたコード変更を確認できます。 コードが *Calculator.cpp* に追加されました。

   ![Calculate の定義の作成](./media/calculator-create-definition.gif "Calculate の定義の作成")

   現時点では単に 0.0 が返されます。 これを変えてみましょう。 **Esc** キーを押してポップアップを閉じます。

1. エディター ウィンドウで *Calculator.cpp* ファイルに切り替えます。 (.h ファイルの場合と同様に) `Calculator()` セクションと `~Calculator()` セクションを削除し、次のコードを `Calculate()` に追加します。

    ```cpp
    #include "pch.h"
    #include "Calculator.h"

    double Calculator::Calculate(double x, char oper, double y)
    {
        switch(oper)
        {
            case '+':
                return x + y;
            case '-':
                return x - y;
            case '*':
                return x * y;
            case '/':
                return x / y;
            default:
                return 0.0;
        }
    }
    ```

   > コードの概要
   >
   > - 関数 `Calculate` では、数値、演算子、および 2 番目の数値を使用してから、その数字に対して要求された操作を実行します。
   > - switch ステートメントでは、指定された演算子を確認し、その演算に対応する case のみを実行します。 既定値: case は、ユーザーが受け入れられない演算子を入力した場合のフォールバックです。そのためプログラムは中断しません。 一般に、より洗練された方法で無効なユーザー入力を処理することが最善ですが、このチュートリアルでは扱いません。
   > - `double` キーワードは、小数をサポートする数値の種類を表します。 このようにすると、電卓は小数の計算と整数の計算の両方を扱うことができます。 `Calculate` 関数は、コードの先頭に `double` があるため、常にこのような数値を返す必要があります (これは関数の戻り型を表します)。そのため、既定の case でも 0.0 が返される理由です。
   > - .h ファイルは、関数の*プロトタイプ*を宣言します。これは、必要なパラメーターと、それから返される戻り値の型をコンパイラに事前に通知するものです。 .cpp ファイルには、関数の実装に関する詳細がすべて含まれています。

この時点でコードをビルドし、もう一度実行すると、実行する操作を問われた後に終了となります。 次に、いくつかの計算を行うように `main` 関数を修正します。

### <a name="to-call-the-calculator-class-member-functions"></a>Calculator クラスのメンバー関数を呼び出すには

1. それでは、*CalculatorTutorial.cpp* の `main` 関数を更新しましょう。

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include "pch.h"
    #include <iostream>
    #include "Calculator.h"

    using namespace std;

    int main()
    {
        double x = 0.0;
        double y = 0.0;
        double result = 0.0;
        char oper = '+';

        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b"
             << endl;

        Calculator c;
        while (true)
        {
            cin >> x >> oper >> y;
            result = c.Calculate(x, oper, y);
            cout << "Result is: " << result << endl;
        }

        return 0;
    }
    ```

   > コードの概要
   >
   > - C++ プログラムは常に `main()` 関数から始まり、そこから他のコードを呼び出す必要があるため、`#include` ステートメントが必要です。
   > - 一部の初期変数 `x`、`y`、`oper`、および `result` は、それぞれ最初の数値、2 番目の数値、演算子、および最終結果を格納するために宣言されています。 未定義の動作を回避するために、この例のように、何らかの初期値を指定しておくことを常にお勧めします。
   > - `Calculator c;` 行は、`Calculator` クラスのインスタンスとして 'c' というオブジェクトを宣言しています。 このクラス自体は、電卓がどのように機能するかを示す単なるブループリントです。オブジェクトは計算を実行する特定の電卓です。
   > - `while (true)` ステートメントはループです。 `()` 内の条件を満たしている限り、ループ内のコードは繰り返し実行されます。 条件は単に `true` と指定されているため、常に true になり、ループは永遠に実行されます。 プログラムを閉じるには、ユーザーは手動でコンソール ウィンドウを閉じる必要があります。 それ以外の場合、プログラムは常に新しい入力を待機します。
   > - `cin` キーワードは、ユーザーからの入力を受け付けるために使用されます。 コンソール ウィンドウに入力されたテキストの行を処理し、ユーザー入力が必要な仕様に一致すると想定して、列挙された各変数の内側に順番に配置するのであれば、この入力ストリームで十分です。 この行を変更して、たとえば 2 つを超える数値など、さまざまな種類の入力を受け入れることができますが、この処理には `Calculate()` 関数も更新する必要があります。
   > - `c.Calculate(x, oper, y);` 式は、前に定義した`Calculate` 関数を呼び出し、入力された値を提供します。 次に、関数は `result` に格納された数値を返します。
   > - 最後に、`result` がコンソールに出力されるので、ユーザーには計算結果が表示されます。

### <a name="build-and-test-the-code-again"></a>コードのビルドとテストの再実行

それでは、もう一度プログラムをテストして、すべてが正しく機能することを確認します。

1. **Ctrl + F5** キーを押してアプリをビルドして起動します。

1. 「`5 + 5`」と入力し、**Enter** キーを押します。 結果が 10 であることを確認してください。

   ![5 + 5 の結果](./media/calculator-five-plus-five.png "5 + 5 の結果")

## <a name="debug-the-app"></a>アプリをデバッグする

ユーザーはコンソール ウィンドウに自由に入力できるので、電卓が一部の入力を想定どおりに処理するようにしましょう。 プログラムを実行するのではなく、代わりにデバッグして、実行内容を詳細に確認することができます。

### <a name="to-run-the-app-in-the-debugger"></a>デバッガーでアプリを実行するには

1. ユーザーが入力を求められた直後に、`result = c.Calculate(x, oper, y);` 行にブレークポイントを設定します。 ブレークポイントを設定するには、行の横の、エディター ウィンドウの左端に沿った灰色の縦線をクリックします。 赤い点が表示されます。

   ![ブレークポイントを設定する](./media/calculator-set-breakpoint.gif "ブレークポイントを設定する")

   プログラムをデバッグするときは、常にその行で実行が一時停止されます。 単純なケースではプログラムが動作することが既に大体わかっています。 実行を毎回一時停止させないために、条件付きのブレークポイントを設定しましょう。

1. ブレークポイントを表す赤丸を右クリックし、 **[条件]** を選択します。 条件の編集ボックスに「`(y == 0) && (oper == '/')`」と入力します。 完了したら、 **[閉じる]** ボタンを選択します。 条件は自動的に保存されます。

   ![条件付きブレークポイントの設定](./media/calculator-conditional-breakpoint.gif "条件付きブレークポイントの設定")

   これで、ゼロ除算が試行された場合に、ブレークポイントで実行が一時停止されます。

1. プログラムをデバッグするには、**F5** キーを押すか、緑色の矢印アイコンがあるツール バーのボタン **[ローカル Windows デバッガー]** を選択します。 コンソール アプリで、「5 - 0」のように入力した場合、プログラムは正常に動作し、実行が継続されます。 ただし、「10/0」と入力すると、ブレークポイントで一時停止されます。 演算子と数値の間には任意の数のスペースを入れることもできます。`cin` で、入力を適切に解析できます。

   ![条件付きブレークポイントの一時停止](./media/calculator-debug-conditional.gif "条件付きブレークポイントの一時停止")

### <a name="useful-windows-in-the-debugger"></a>デバッガーの便利なウィンドウ

コードをデバッグするたびに、新しいウィンドウがいくつか表示されることに注意してください。 これらは、デバッグ エクスペリエンスを支援するウィンドウです。 **[自動]** ウィンドウを見てください。 **[自動]** ウィンドウには、3 行以上前から現在の行までに使用されている変数の現在の値が表示されます。

   ![[自動] ウィンドウ](./media/calculator-autos.png "[自動] ウィンドウ")

その関数のすべての変数を確認するには、 **[ローカル]** ウィンドウに切り替えます。 このような変数の値をデバッグ中に実際に変更して、プログラムにどのような影響があるかを確認できます。 この例では、そのままにします。

   ![[ローカル] ウィンドウ](./media/calculator-locals.png "[ローカル] ウィンドウ")

また、コード内の変数をポイントして、実行が一時停止されている現在の値を確認することもできます。 まずエディター ウィンドウをクリックして、フォーカスを切り替えます。

   ![ポイントして現在の変数値を表示](./media/calculator-hover-tooltip.gif "ポイントして現在の変数値を表示")

### <a name="to-continue-debugging"></a>デバッグを続行するには

1. 左側の黄色の線は、現在の実行ポイントを示します。 現在の行で `Calculate` を呼び出すため、**F11** キーを押して関数の **[ステップ イン]** を行います。 `Calculate` 関数の本文が表示されます。 **[ステップ イン]** は気を付けて使ってください。実行しすぎると、多くの時間を無駄にする場合があります。 これを使うと、標準ライブラリの関数を含めて、現在の行で使っているすべてのコードを調査します。

1. 実行ポイントが `Calculate` 関数の先頭になったら、**F10** キーを押してプログラムの実行内の次の行に移動します。 **F10** キーは **[ステップ オーバー]** とも呼ばれます。 **[ステップ オーバー]** を使用すると、行の各部分で発生していることを詳しく調べることなく、行から行へ移動できます。 一般に、(実行して `Calculate` の本文に達したので) 別の場所から呼び出されたコードを詳しく掘り下げる場合を除き、 **[ステップ イン]** ではなく **[ステップ オーバー]** を使用することをお勧めします。

1. もう一方のファイルの `main()` 関数に戻るまで繰り返し **F10** キーを押して各行の **[ステップ オーバー]** を行い、`cout` 行で停止します。

   ![Calculate のステップ アウトと結果の確認](./media/calculator-undefined-zero.gif "Calculate のステップ アウトと結果の確認")

   プログラムは期待どおりに動作しているように見えます。最初の数字を受け取り、それを 2 番目の数字で割ります。 `cout` 行の `result` 変数をポイントするか、 **[自動]** ウィンドウの `result` を確認します。 その値は "inf" として表示されます。これは正しくないようなので、修正しましょう。 `cout` 行は、`result` に格納されている値をそのまま出力するため、**F10** キーを使用してもう 1 行進むと、コンソール ウィンドウに次が表示されます。

   ![ゼロ除算の結果](./media/calculator-divide-by-zero-fail.png "ゼロ除算の結果")

   この結果は、ゼロ除算が定義されていないために発生します。そのため、プログラムは要求された操作に対して数値の答えを得られません。

### <a name="to-fix-the-divide-by-zero-error"></a>"ゼロ除算" エラーを修正するには

ユーザーが問題を理解できるように、ゼロ除算をより適切に処理しましょう。

1. *CalculatorTutorial.cpp* に次の変更を加えます ( **[エディット コンティニュ]** というデバッガー機能のおかげで、編集中にプログラムを実行したままにすることができます)。

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include "pch.h"
    #include <iostream>
    #include "Calculator.h"

    using namespace std;

    int main()
    {
        double x = 0.0;
        double y = 0.0;
        double result = 0.0;
        char oper = '+';

        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b" << endl;

        Calculator c;
        while (true)
        {
            cin  >> x  >> oper  >> y;
            if (oper == '/' && y == 0)
            {
                cout << "Division by 0 exception" << endl;
                continue;
            }
            else
            {
                result = c.Calculate(x, oper, y);
            }
            cout << "Result is: " << result << endl;
        }

        return 0;
    }
    ```

1. 次に **F5** キーを一度押します。 ユーザー入力を求めるために一時停止する必要があるまで、プログラムの実行が継続されます。 もう一度「`10 / 0`」と入力します。 今度はより役に立つメッセージが表示されます。 ユーザーはさらに入力を求められ、プログラムは通常どおり実行が継続されます。

   ![変更後の最終的な結果](./media/calculator-final-verification.gif "変更後の最終的な結果")

   > [!Note]
   > デバッグ モードでコードを編集すると、コードが古くなる危険性があります。 これは、デバッガーがまだ古いコードを実行していて、まだ変更が反映されていない場合に発生します。 このような状況になると、デバッガーによってダイアログがポップアップ表示されます。 **F5** キーを押して実行中のコードを更新する必要がある場合があります。 特に、実行ポイントが関数内にあるときに関数内に変更を加えた場合は、関数からステップ アウトし、ステップ インして更新されたコードを取得する必要があります。 それが何らかの理由でうまくいかず、エラー メッセージが表示される場合は、IDE の上部にあるメニューの下にあるツール バーの赤色の四角をクリックしてデバッグを中止し、**F5** キーを押してデバッグを再開します。または、ツール バーの停止ボタンの横にある緑色の [再生] 矢印を選択します。
   
   > [実行] と [デバッグ] のショートカットの概要
   >
   > - **F5** キーを押すと (または **[デバッグ]**  >  **[デバッグの開始]** )、デバッグ セッションがまだアクティブでない場合は開始され、プログラムが実行され、ブレークポイントにヒットするか、ユーザー入力が必要になると停止されます。 ユーザー入力が不要で、ヒットするブレークポイントがない場合、プログラムは終了します。プログラムの実行が完了すると、コンソール ウィンドウは自動的に閉じます。 "Hello World" のようなプログラムを実行する場合は、**F5** キーを押す前 **Ctrl + F5** キーを押すか、ブレークポイントを設定してウィンドウを開いたままにします。
   > - **Ctrl + F5** キーを押すと (または **[デバッグ]**  >  **[デバッグなしで開始]** )、デバッグ モードに移行せずにアプリケーションを実行します。 これはデバッグよりもわずかに速く、プログラムの実行が完了した後もコンソール ウィンドウは開いたままです。
   > - **F10** キー ( **[ステップ オーバー]** と呼ばれます) を使用すると、コードを 1 行ずつ繰り返し実行し、コードの実行方法と各実行手順での変数値を視覚化できます。
   > - **F11** キー ( **[ステップ イン]** と呼ばれます) を使用すると、 **[ステップ オーバー]** と同様に機能しますが、実行中の行で呼び出される関数にステップ インする点が異なります。 たとえば、実行中の行が関数を呼び出す場合、**F11** キーを押すと、ポインターが関数の本文に移動するので、開始した行に戻る前に実行中の関数のコードに従うことができます。 **F10** キーを押すと、関数呼び出しがステップ オーバーされ、次の行に移動します。関数呼び出しはまだ行われますが、実行内容を示すためにプログラムは一時停止しません。

### <a name="close-the-app"></a>アプリを閉じる

- まだ実行中の場合は、電卓アプリのコンソール ウィンドウを閉じます。

## <a name="the-finished-app"></a>完成したアプリ

おめでとうございます! 電卓アプリのコードを完成し、Visual Studio でビルドしてデバッグしました。

## <a name="next-steps"></a>次の手順

[Visual Studio for C++ の詳細](https://blogs.msdn.microsoft.com/vcblog/2017/04/21/getting-started-with-visual-studio-for-c-and-cpp-development/)

::: moniker-end
