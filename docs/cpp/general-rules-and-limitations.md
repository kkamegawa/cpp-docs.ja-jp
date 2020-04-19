---
title: 一般的な規則と制限事項
ms.date: 11/04/2016
ms.assetid: 6c48902d-4259-4761-95d4-e421d69aa050
ms.openlocfilehash: 3bd8956b08d3e5f2109c5574802a3a8a72fba537
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857529"
---
# <a name="general-rules-and-limitations"></a>一般的な規則と制限事項

**Microsoft 固有の仕様**

- **Dllimport**属性または**dllexport**属性を指定せずに関数またはオブジェクトを宣言した場合、その関数またはオブジェクトは DLL インターフェイスの一部とは見なされません。 したがって、関数またはオブジェクトの定義は、該当のモジュール内か、同じプログラムの別のモジュール内に存在している必要があります。 関数またはオブジェクトを DLL インターフェイスの一部にするには、他のモジュール内の関数またはオブジェクトの定義を**dllexport**として宣言する必要があります。 定義しない場合は、リンカー エラーが生成されます。

   **Dllexport**属性を使用して関数またはオブジェクトを宣言する場合、その定義は、同じプログラムの一部のモジュールに出現する必要があります。 定義しない場合は、リンカー エラーが生成されます。

- プログラム内の1つのモジュールに、同じ関数またはオブジェクトの**dllimport**宣言と**dllexport**宣言の両方が含まれている場合、 **dllexport**属性は**dllimport**属性よりも優先されます。 ただし、コンパイラの警告が生成されます。 例:

    ```cpp
    __declspec( dllimport ) int i;
    __declspec( dllexport ) int i;   // Warning; inconsistent;
                                     // dllexport takes precedence.
    ```

- でC++は、グローバルに宣言されたローカルデータポインターまたは静的ローカルデータポインター、または**dllimport**属性で宣言されたデータオブジェクトのアドレスで初期化できます。この場合、C ではエラーが生成されます。また、 **dllimport**属性で宣言された関数のアドレスを使用して、静的ローカル関数ポインターを初期化することもできます。 C では、このような代入で、関数のアドレスではなく、DLL インポート サンク (関数に制御を移すコード スタブ) のアドレスがポインターに設定されます。 C++ では、ポインターに関数のアドレスが設定されます。 例:

    ```cpp
    __declspec( dllimport ) void func1( void );
    __declspec( dllimport ) int i;

    int *pi = &i;                             // Error in C
    static void ( *pf )( void ) = &func1;     // Address of thunk in C,
                                              // function in C++

    void func2()
    {
       static int *pi = &i;                  // Error in C
       static void ( *pf )( void ) = &func1; // Address of thunk in C,
                                             // function in C++
    }
    ```

   ただし、オブジェクトの宣言に**dllexport**属性を含むプログラムは、プログラム内のどこかでそのオブジェクトの定義を提供する必要があるため、 **dllexport**関数のアドレスを使用してグローバルまたはローカルの静的関数ポインターを初期化することができます。 同様に、 **dllexport**データオブジェクトのアドレスを使用して、グローバルまたはローカルの静的データポインターを初期化できます。 たとえば、次のコードの場合、C または C++ でエラーは発生しません。

    ```cpp
    __declspec( dllexport ) void func1( void );
    __declspec( dllexport ) int i;

    int *pi = &i;                              // Okay
    static void ( *pf )( void ) = &func1;      // Okay

    void func2()
    {
        static int *pi = &i;                   // Okay
        static void ( *pf )( void ) = &func1;  // Okay
    }
    ```

- Dllexport としてマークされていない基底クラスを持つ標準クラスに**dllexport**を適用する**と、コンパイラ**は C4275 を生成します。

   クラス テンプレートの特殊化が基底クラスである場合、コンパイラでも同じ警告が発生します。 この問題を回避するには、基になるクラスを**dllexport**でマークします。 クラステンプレートの特殊化に関する問題は、 **__declspec (dllexport)** を配置する場所です。クラステンプレートをマークすることは許可されていません。 代わりに、クラステンプレートを明示的にインスタンス化し、この明示的なインスタンス化を**dllexport**でマークします。 例:

    ```cpp
    template class __declspec(dllexport) B<int>;
    class __declspec(dllexport) D : public B<int> {
    // ...
    ```

   この回避策は、テンプレート引数が派生クラスの場合は失敗します。 例:

    ```cpp
    class __declspec(dllexport) D : public B<D> {
    // ...
    ```

   これはテンプレートを使用した一般的なパターンなので、1つまたは複数の基底クラスを持つクラスに適用され、1つ以上の基底クラスがクラステンプレートの特殊化である場合に、 **dllexport**のセマンティクスが変更されました。 この場合、コンパイラは、クラステンプレートの特殊化に**dllexport**を暗黙的に適用します。 警告が表示されない場合は、次の操作を実行できます。

    ```cpp
    class __declspec(dllexport) D : public B<D> {
    // ...
    ```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>参照

[dllexport、dllimport](../cpp/dllexport-dllimport.md)