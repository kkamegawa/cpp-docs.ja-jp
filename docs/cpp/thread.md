---
title: スレッド
ms.date: 05/07/2019
f1_keywords:
- thread_cpp
helpviewer_keywords:
- thread local storage (TLS)
- thread __declspec keyword
- TLS (thread local storage), compiler implementation
- __declspec keyword [C++], thread
ms.assetid: 667f2a77-6d1f-4b41-bee8-05e67324fab8
ms.openlocfilehash: cc21602764a9a3c2584bdd7da62c75974ffdd5fb
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301289"
---
# <a name="thread"></a>スレッド

**Microsoft 固有の仕様**

スレッド**の拡張ストレージ**クラス修飾子は、スレッドローカル変数を宣言するために使用されます。 C++ 11 以降の移植可能なものについては、移植可能なコードには[thread_local](../cpp/storage-classes-cpp.md#thread_local)ストレージクラス指定子を使用します。 Windows **thread_local**は **__declspec (スレッド)** を使用して実装されます。

## <a name="syntax"></a>構文

**__declspec (スレッド)** *宣言子*

## <a name="remarks"></a>コメント

スレッド ローカル ストレージ (TLS) は、特定のマルチスレッド プロセスの各スレッドが、スレッド固有のデータを格納するための場所を割り当てる機能です。 標準のマルチスレッド プログラムでは、データは特定のプロセスのすべてのスレッド間で共有されますが、スレッド ローカル ストレージはスレッドごとのデータを割り当てるための機能です。 スレッドの詳細については、「[マルチスレッド](../parallel/multithreading-support-for-older-code-visual-cpp.md)」を参照してください。

スレッドローカル変数の宣言では、[拡張属性構文](../cpp/declspec.md)と、 **thread**キーワードで **__declspec**キーワードを使用する必要があります。 たとえば、次に示すコードは、整数型のスレッド ローカル変数を宣言して特定の値に初期化します。

```cpp
__declspec( thread ) int tls_i = 1;
```

動的に読み込まれるライブラリでスレッドローカル変数を使用する場合は、スレッドローカル変数が正しく初期化されない原因となる要因に注意する必要があります。

1. 変数が関数呼び出し (コンストラクターを含む) で初期化された場合、この関数は、バイナリ/DLL がプロセスに読み込まれる原因となったスレッド、およびバイナリ/DLL が読み込まれた後に起動したスレッドに対してのみ呼び出されます。 DLL が読み込まれたときに既に実行されていた他のスレッドに対しては、初期化関数は呼び出されません。 動的な初期化は DLL_THREAD_ATTACH の DllMain 呼び出しで発生しますが、dll がスレッドの起動時にプロセスに含まれていない場合、DLL はそのメッセージを取得しません。

1. 定数値を使用して静的に初期化されるスレッドローカル変数は、通常、すべてのスレッドで適切に初期化されます。 ただし、2017年12月以降、Microsoft C++コンパイラには、 **constexpr**変数が静的初期化ではなく動的に受け取るという既知の準拠の問題があります。

   注: これらの問題はどちらも、コンパイラの今後の更新で修正される予定です。

さらに、スレッドローカルオブジェクトと変数を宣言するときは、次のガイドラインに従う必要があります。

- **Thread**属性は、クラスおよびデータの宣言と定義にのみ適用できます。**スレッド**を関数の宣言または定義で使用することはできません。

- 指定することができます、**thread**静的ストレージ存続期間のデータ項目にのみ属性。 これには、グローバルなデータ オブジェクトが含まれます (どちらも**static**と**extern**)、ローカルな静的オブジェクト、およびクラスの静的データ メンバー。 **Thread**属性を使用して自動データオブジェクトを宣言することはできません。

- 宣言と定義が同じファイルと個別のファイルのどちらで発生するかにかかわらず、スレッドローカルオブジェクトの宣言と定義には**thread**属性を使用する必要があります。

- **スレッド**属性を型修飾子として使用することはできません。

- **Thread**属性を使用するオブジェクトの宣言は許可されているので、次の2つの例は意味的に等価です。

    ```cpp
    // declspec_thread_2.cpp
    // compile with: /LD
    __declspec( thread ) class B {
    public:
       int data;
    } BObject;   // BObject declared thread local.

    class B2 {
    public:
       int data;
    };
    __declspec( thread ) B2 BObject2;   // BObject2 declared thread local.
    ```

- 標準 C では、オブジェクトまたは変数を、それ自体への参照を含む式で初期化することができますが、非静的オブジェクトに対してのみ使用できます。 C++通常、このようなオブジェクトは、それ自体への参照を含む式を使用して動的に初期化できますが、この種の初期化はスレッドローカルオブジェクトでは許可されません。 例:

   ```cpp
   // declspec_thread_3.cpp
   // compile with: /LD
   #define Thread __declspec( thread )
   int j = j;   // Okay in C++; C error
   Thread int tls_i = sizeof( tls_i );   // Okay in C and C++
   ```

   初期化されるオブジェクトを含む**sizeof**式は、それ自体への参照を構成せず、C C++およびでも使用できます。

**END Microsoft 固有の仕様**

## <a name="see-also"></a>関連項目

[__declspec](../cpp/declspec.md)<br/>
[キーワード](../cpp/keywords-cpp.md)<br/>
[スレッド ローカル ストレージ (TLS: Thread Local Storage)](../parallel/thread-local-storage-tls.md)