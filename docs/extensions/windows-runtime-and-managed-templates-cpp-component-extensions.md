---
title: Windows ランタイムおよびマネージド テンプレート (C++/CLI および C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- templates, with CLR types
ms.assetid: cf59d16b-5514-448b-9a95-e0b4fcb616a6
ms.openlocfilehash: a8cc429763d042ba262d5543f4a2d85bbf8aa29a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515967"
---
# <a name="windows-runtime-and-managed-templates-ccli-and-ccx"></a>Windows ランタイムおよびマネージド テンプレート (C++/CLI および C++/CX)

テンプレートを使用して、Windows ランタイムまたは共通言語ランタイム型のプロトタイプを定義し、別のテンプレート型パラメーターを使用してその型のバリエーションをインスタンス化できます。

## <a name="all-runtimes"></a>すべてのランタイム

値型または参照型からテンプレートを作成できます。  値型または参照型の作成の詳細については、[クラスと構造体](classes-and-structs-cpp-component-extensions.md)に関する記事を参照してください。

標準 C++ クラス テンプレートの詳細については、「[Class Templates (クラス テンプレート)](../cpp/class-templates.md)」を参照してください。

## <a name="windows-runtime"></a>Windows ランタイム

(この言語機能には Windows ランタイムのみに適用される特記事項がありません。)

### <a name="requirements"></a>要件

コンパイラ オプション: `/ZW`

## <a name="common-language-runtime"></a>共通言語ランタイム

マネージド型からのクラス テンプレートの作成には、次のコード例で説明するいくつかの制限があります。

### <a name="requirements"></a>要件

コンパイラ オプション: `/clr`

### <a name="examples"></a>使用例

マネージド型テンプレート パラメーターを使用してジェネリック型をインスタンス化できますが、ジェネリック型テンプレート パラメーターを使用してマネージド テンプレートをインスタンス化することはできません。 これは、ジェネリック型は実行時に解決されるためです。 詳細については、「[Generics and Templates (C++/CLI) (ジェネリックとテンプレート (C++/CLI))](generics-and-templates-visual-cpp.md)」を参照してください。

```cpp
// managed_templates.cpp
// compile with: /clr /c

generic<class T>
ref class R;

template<class T>
ref class Z {
   // Instantiate a generic with a template parameter.
   R<T>^ r;    // OK
};

generic<class T>
ref class R {
   // Cannot instantiate a template with a generic parameter.
   Z<T>^ z;   // C3231
};
```

マネージド テンプレートでは、ジェネリック型または関数を入れ子にすることはできません。

```cpp
// managed_templates_2.cpp
// compile with: /clr /c

template<class T> public ref class R {
   generic<class T> ref class W {};   // C2959
};
```

C++/CLI 言語の構文では参照アセンブリに定義されているテンプレートにアクセスできませんが、リフレクションは使用できます。 テンプレートがインスタンス化されない場合、メタデータは生成されません。 テンプレートがインスタンス化される場合は、参照されているメンバー関数のみがメタデータ内に出現します。

```cpp
// managed_templates_3.cpp
// compile with: /clr

// Will not appear in metadata.
template<class T> public ref class A {};

// Will appear in metadata as a specialized type.
template<class T> public ref class R {
public:
   // Test is referenced, will appear in metadata
   void Test() {}

   // Test2 is not referenced, will not appear in metadata
   void Test2() {}
};

// Will appear in metadata.
generic<class T> public ref class G { };

public ref class S { };

int main() {
   R<int>^ r = gcnew R<int>;
   r->Test();
}
```

クラス テンプレートの部分的特殊化または明示的な特殊化内のクラスのマネージ修飾子を変更できます。

```cpp
// managed_templates_4.cpp
// compile with: /clr /c

// class template
// ref class
template <class T>
ref class A {};

// partial template specialization
// value type
template <class T>
value class A <T *> {};

// partial template specialization
// interface
template <class T>
interface class A<T%> {};

// explicit template specialization
// native class
template <>
class A <int> {};
```

## <a name="see-also"></a>関連項目

[.NET および UWP でのコンポーネント拡張](component-extensions-for-runtime-platforms.md)