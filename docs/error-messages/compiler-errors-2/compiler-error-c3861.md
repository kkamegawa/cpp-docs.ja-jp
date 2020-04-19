---
title: コンパイラ エラー C3861
ms.date: 03/23/2018
f1_keywords:
- C3861
helpviewer_keywords:
- C3861
ms.assetid: 0a1eee30-b3db-41b1-b1e5-35949c3924d7
ms.openlocfilehash: 4ebfd3b0129e25cf543cac803a3b33fb074f3d70
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302413"
---
# <a name="compiler-error-c3861"></a>コンパイラ エラー C3861

> '*識別子*': 識別子が見つかりません

コンパイラでは、引数依存の検索を使用しても、識別子への参照を解決できませんでした。

## <a name="remarks"></a>Remarks

このエラーを解決するには、使用を比較*識別子*大文字小文字とスペルの識別子の宣言にします。 いることを確認[スコープ解決演算子](../../cpp/scope-resolution-operator.md)と名前空間[ディレクティブを使用して](../../cpp/namespaces-cpp.md#using_directives)が正しく使用します。 識別子がヘッダー ファイルで宣言されている場合は、識別子が参照される前に、ヘッダーが含まれることを確認します。 識別子は、外部から参照するものでは、それを使用する任意のソース ファイルで宣言されていることを確認します。 識別子の宣言または定義をによって除外されていないことを確認も[条件付きコンパイル ディレクティブ](../../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)します。

変更を Visual Studio 2015 での C ランタイム ライブラリの廃止された関数を削除するには、C3861 可能性があります。 このエラーを解決するには、これらの関数への参照を削除するか、存在する場合、セキュリティで保護されたその代替手段で置き換えます。 詳細については、次を参照してください。[廃止された関数](../../c-runtime-library/obsolete-functions.md)します。

コンパイラの以前のバージョンからのプロジェクトの移行後にエラー C3861 が表示された場合は、サポートされている Windows バージョンに関連する問題があります。 Visual C++ では、Windows 95、Windows 98、Windows ME、Windows NT、および Windows 2000 がサポート対象外になりました。 **WINVER** マクロまたは **_WIN32_WINNT** マクロをこれらのいずれかのバージョンの Windows に割り当てている場合は、そのマクロを修正する必要があります。 詳細については、次を参照してください。 [WINVER および _win32_winnt の変更](../../porting/modifying-winver-and-win32-winnt.md)します。

## <a name="examples"></a>使用例

### <a name="undefined-identifier"></a>未定義の識別子です。

次の例では、識別子が定義されていないために、C3861 が生成されます。

```cpp
// C3861.cpp
void f2(){}
int main() {
   f();    // C3861
   f2();   // OK
}
```

### <a name="identifier-not-in-scope"></a>スコープではなく識別子

次の例では、識別子は、それを使用する他のソース ファイルで宣言されている場合を除き、のみ、その定義のファイル スコープで見えるために、C3861 が生成されます。

```cpp
// C3861_a1.cpp
// Compile with: cl /EHsc /W4 C3861_a1.cpp C3861_a2.cpp
#include <iostream>
// Uncomment the following line to fix:
// int f();  // declaration makes external function visible
int main() {
   std::cout << f() << std::endl;    // C3861
}
```

```cpp
// C3861_a2.cpp
int f() {  // declared and defined here
   return 42;
}
```

### <a name="namespace-qualification-required"></a>Namespace 認定が必要です。

C++ 標準ライブラリでの例外クラスが必要な`std`名前空間。

```cpp
// C3861_b.cpp
// compile with: /EHsc
#include <iostream>
int main() {
   try {
      throw exception("Exception");   // C3861
      // try the following line instead
      // throw std::exception("Exception");
   }
   catch (...) {
      std::cout << "caught an exception" << std::endl;
   }
}
```

### <a name="obsolete-function-called"></a>古い関数が呼び出されます

廃止された関数は、CRT ライブラリから削除されましたがあります。

```cpp
// C3861_c.cpp
#include <stdio.h>
int main() {
   char line[21]; // room for 20 chars + '\0'
   gets( line );  // C3861
   // Use gets_s instead.
   printf( "The line entered was: %s\n", line );
}
```

### <a name="adl-and-friend-functions"></a>ADL と friend 関数

コンパイラの引数依存の参照を使用できないために、次のサンプル生成 C3767 `FriendFunc`:

```cpp
namespace N {
   class C {
      friend void FriendFunc() {}
      friend void AnotherFriendFunc(C* c) {}
   };
}

int main() {
   using namespace N;
   FriendFunc();   // C3861 error
   C* pC = new C();
   AnotherFriendFunc(pC);   // found via argument-dependent lookup
}
```

エラーを解決するには、クラス スコープでフレンドを宣言および名前空間スコープで定義します。

```cpp
class MyClass {
   int m_private;
   friend void func();
};

void func() {
   MyClass s;
   s.m_private = 0;
}

int main() {
   func();
}
```
