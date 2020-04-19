---
title: .NET および UWP 用のコンポーネントの拡張機能
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- what's new [C++], keywords
- what's new [C++], language features
- C++, keywords
- keywords [C++]
- Managed Extensions for C++, replacement syntax
ms.assetid: 1e400ee6-3ac9-4910-a608-9d3d5993e423
ms.openlocfilehash: cf123e54c633539c8e5bf8204344c842a21183ef
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "65516717"
---
# <a name="component-extensions-for-net-and-uwp"></a>.NET および UWP 用のコンポーネントの拡張機能

C++ 標準では、コンパイラ ベンダーがその言語に対して非標準の拡張機能を提供できます。 Microsoft では、ネイティブ C++ コードを .NET Framework またはユニバーサル Windows プラットフォーム (UWP) 上で実行されるコードに接続するために役立つ拡張機能を提供しています。 .NET 拡張機能は C++/CLI と呼ばれ、共通言語ランタイム (CLR) と呼ばれる .NET マネージド実行環境で実行されるコードを生成します。 UWP 拡張機能は C++/CX と呼ばれ、ネイティブ マシン コードを生成します。

> [!NOTE]
> 新しいアプリケーションでは、C++/CX ではなく C++/WinRT を使用することをお勧めします。 C++/WinRT は、Windows ランタイム API 用の新しい標準的な C++17 言語プロジェクションです。 C++/CX と WRL は引き続きサポートされますが、新しいアプリケーションでは C++/WinRT を使用することを強くお勧めします。 詳細については、「[C++/WinRT](/windows/uwp/cpp-and-winrt-apis/index)」を参照してください。

### <a name="two-runtimes-one-set-of-extensions"></a>2 つのランタイムに共通の拡張

C++/CLI は ISO/ANSI C++ 規格を拡張したものであり、Ecma C++/CLI 規格で定義されています。 詳細については、「[C++/CLI による .NET プログラミング (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)」を参照してください。

C++/CX 拡張機能は、C++/CLI のサブセットです。 拡張構文はほとんどの場合は同じですが、生成されるコードは、UWP をターゲットする `/ZW` コンパイラ オプションまたは .NET をターゲットとする `/clr` オプションの指定に応じて異なります。 Visual Studio を使用してプロジェクトを作成すると、これらのスイッチが自動的に設定されます。

## <a name="data-type-keywords"></a>データ型のキーワード

これらの言語拡張には、空白で区切られた 2 つのトークンで構成される "*集計キーワード*" が含まれています。 これらのトークンは、単独で使用した場合と一緒に使用した場合で意味が異なることがあります。 たとえば、"ref" は通常の識別子であり、"class" はネイティブ クラスを宣言するキーワードです。 しかし、これらを組み合わせて **ref class** として使用した場合は、"*ランタイム クラス*" と呼ばれるエンティティを宣言する集計キーワードになります。

これらの拡張機能には、"*状況依存キーワード*" も含まれています。 キーワードが状況依存のキーワードとして扱われるかどうかは、キーワードを含むステートメントの種類と、そのステートメント内でのキーワードの配置で決まります。 たとえば、"property" というトークンは、識別子として使用されることもあれば、特殊なパブリック クラスのメンバーを宣言するために使用されることもあります。

次の表に、C++ 言語拡張のキーワードの一覧を示します。

|キーワード|状況依存|目的|関連項目|
|-------------|-----------------------|-------------|---------------|
|**ref class**<br /><br /> **ref struct**|いいえ|クラスを宣言します。|[クラスと構造体](classes-and-structs-cpp-component-extensions.md)|
|**value class**<br /><br /> **value struct**|いいえ|値クラスを宣言します。|[クラスと構造体](classes-and-structs-cpp-component-extensions.md)|
|**interface class**<br /><br /> **interface struct**|いいえ|インターフェイスを宣言します。|[interface class](interface-class-cpp-component-extensions.md)|
|**enum class**<br /><br /> **enum struct**|いいえ|列挙型を宣言します。|[enum class](enum-class-cpp-component-extensions.md)|
|**property**|はい|プロパティを宣言します。|[プロパティ](property-cpp-component-extensions.md)|
|**delegate**|はい|デリゲートを宣言します。|[delegate (C++/CLI および C++/CX)](delegate-cpp-component-extensions.md)|
|**event**|はい|イベントを宣言します。|[event](event-cpp-component-extensions.md)|

## <a name="override-specifiers"></a>オーバーライド指定子

次のキーワードは、派生のオーバーライド動作を修飾するために使用できます。 **new** キーワードは C++ の拡張機能ではありませんが、追加のコンテキストで使用できるキーワードとしてこの一覧に含めてあります。 一部の指定子は、ネイティブのプログラミングに対しても有効です。 詳細については、「[方法 :ネイティブ コンパイルでオーバーライド指定子を宣言する (C++/CLI)](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)」を参照してください。

|キーワード|状況依存|目的|関連項目|
|-------------|-----------------------|-------------|---------------|
|**abstract**|はい|関数またはクラスが抽象型であることを示します。|[abstract](abstract-cpp-component-extensions.md)|
|**new**|いいえ|関数が基底クラスのバージョンのオーバーライドでないことを示します。|[new (vtable の新しいスロット)](new-new-slot-in-vtable-cpp-component-extensions.md)|
|**override**|はい|メソッドが基底クラスのバージョンのオーバーライドでなければならないことを示します。|[override](override-cpp-component-extensions.md)|
|**sealed**|はい|クラスを基底クラスとして使用しないことを示します。|[sealed](sealed-cpp-component-extensions.md)|

## <a name="keywords-for-generics"></a>ジェネリックのキーワード

ジェネリック型をサポートするために追加されたキーワードを次に示します。 詳細については、「[ジェネリック](generics-cpp-component-extensions.md)」を参照してください。

|キーワード|状況依存|目的|
|-------------|-----------------------|-------------|
|**generic**|いいえ|ジェネリック型を宣言します。|
|**where**|はい|ジェネリック型パラメーターに適用される制約を指定します。|

## <a name="miscellaneous-keywords"></a>その他のキーワード

C++ 拡張に追加されたその他のキーワードを次に示します。

|キーワード|状況依存|目的|関連項目|
|-------------|-----------------------|-------------|---------------|
|**finally**|はい|例外処理の既定の動作を示します。|[例外処理](exception-handling-cpp-component-extensions.md)|
|**for each、in**|いいえ|コレクションの要素を列挙します。|[for each、in](../dotnet/for-each-in.md)|
|**gcnew**|いいえ|ガベージ コレクション ヒープに型を割り当てます。 **new** と **delete** の代わりに使用します。|[ref new、gcnew](ref-new-gcnew-cpp-component-extensions.md)|
|**ref new**|はい|Windows ランタイム型を割り当てます。 **new** と **delete** の代わりに使用します。|[ref new、gcnew](ref-new-gcnew-cpp-component-extensions.md)|
|**initonly**|はい|宣言または静的コンストラクターでしかメンバーを初期化できないことを示します。|[initonly (C++/CLI)](../dotnet/initonly-cpp-cli.md)|
|**name**|はい|リテラル変数を作成します。|[name](literal-cpp-component-extensions.md)|
|**nullptr**|いいえ|ハンドルまたはポインターでオブジェクトを参照しないことを示します。|[nullptr](nullptr-cpp-component-extensions.md)|

## <a name="template-constructs"></a>テンプレートの構成要素

次の言語構成要素は、キーワードとしてではなく、テンプレートとして実装されています。 `/ZW` コンパイラ オプションを指定した場合は `lang` 名前空間で定義され、 `/clr` コンパイラ オプションを指定した場合は `cli` 名前空間で定義され、

|キーワード|目的|関連項目|
|-------------|-------------|---------------|
|**array**|配列を宣言します。|[配列](arrays-cpp-component-extensions.md)|
|**interior_ptr**|(CLR のみ) 参照型でデータを参照します。|[interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md)|
|**pin_ptr**|(CLR のみ) CLR 参照型を参照して、ガベージ コレクション システムを一時的に無効にします。|[pin_ptr (C++/CLI)](pin-ptr-cpp-cli.md)|
|**safe_cast**|ランタイム型の最適なキャスト方法を特定して実行します。|[safe_cast](safe-cast-cpp-component-extensions.md)|
|**typeid**|(CLR のみ) 指定した型またはオブジェクトを表す <xref:System.Type?displayProperty=fullName> オブジェクトを取得します。|[typeid](typeid-cpp-component-extensions.md)|

## <a name="declarators"></a>宣言子

割り当てられたオブジェクトの有効期間と削除をランタイムで自動的に管理するように指定する型の宣言子を次に示します。

|演算子|目的|関連項目|
|--------------|-------------|---------------|
|`^`|オブジェクトを識別するハンドル (使用できなくなったときに自動的に削除される Windows ランタイム オブジェクトまたは CLR オブジェクトへのポインター) を宣言します。|[オブジェクト演算子 (^) へのハンドル](handle-to-object-operator-hat-cpp-component-extensions.md)|
|`%`|追跡参照 (使用できなくなったときに自動的に削除される Windows ランタイム オブジェクトまたは CLR オブジェクトへの参照) を宣言します。|[参照演算子の追跡](tracking-reference-operator-cpp-component-extensions.md)|

## <a name="additional-constructs-and-related-topics"></a>その他の構成要素と関連トピック

ここでは、その他のプログラミング構成要素と CLR の関連トピックを示します。

|トピック|説明|
|-----------|-----------------|
|[__identifier (C++/CLI)](identifier-cpp-cli.md)|(Windows ランタイムおよび CLR) キーワードを識別子として使用できるようにします。|
|[可変個引数リスト (...) (C++/CLI)](variable-argument-lists-dot-dot-dot-cpp-cli.md)|(Windows ランタイムおよび CLR) 関数で受け取ることができる引数の数を可変にします。|
|[C++ ネイティブ型と等価な .NET Framework ネイティブ型 (C++/CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)|C++ の整数型の代わりに使用される CLR 型を示します。|
|[appdomain](../cpp/appdomain.md) **__declspec** 修飾子|**__declspec** 修飾子は、appdomain ごとに静的変数とグローバル変数を必須にする修飾子です。|
|[C スタイル キャストと /clr (C++/CLI)](c-style-casts-with-clr-cpp-cli.md)|C スタイル キャストがどのように解釈されるかについて説明します。|
|[__clrcall](../cpp/clrcall.md) 呼び出し規則|CLR 準拠の呼び出し規則を示します。|
|`__cplusplus_cli`|[定義済みマクロ](../preprocessor/predefined-macros.md)|
|[カスタム属性](user-defined-attributes-cpp-component-extensions.md)|独自の CLR 属性を定義する方法について説明します。|
|[例外処理](exception-handling-cpp-component-extensions.md)|例外処理の概要を示します。|
|[明示的なオーバーライド](explicit-overrides-cpp-component-extensions.md)|メンバー関数で任意のメンバーをオーバーライドする方法を示します。|
|[フレンド アセンブリ (C++)](../dotnet/friend-assemblies-cpp.md)|クライアント アセンブリでアセンブリ コンポーネントのすべての型にアクセスする方法について説明します。|
|[ボックス化](boxing-cpp-component-extensions.md)|値型がボックス化される条件を示します。|
|[型の特徴のコンパイラ サポート](compiler-support-for-type-traits-cpp-component-extensions.md)|コンパイル時に型の特性を検出する方法について説明します。|
|[マネージド、アンマネージド](../preprocessor/managed-unmanaged.md) プラグマ|同じモジュールにマネージド 関数とアンマネージド 関数を共存させる方法を示します。|
|[process](../cpp/process.md) **__declspec** 修飾子|**__declspec** 修飾子は、プロセスごとに静的変数とグローバル変数を必須にする修飾子です。|
|[リフレクションの問題 (C++/CLI)](../dotnet/reflection-cpp-cli.md)|CLR バージョンのランタイム型情報を示します。|
|[String](string-cpp-component-extensions.md)|文字列リテラルから <xref:System.String> へのコンパイラによる変換について説明します。|
|[型の転送 (C++/CLI)](type-forwarding-cpp-cli.md)|クライアント コードを再コンパイルしなくても済むように、出荷時のアセンブリの型を別のアセンブリに移動できるようにします。|
|[ユーザー定義の属性](user-defined-attributes-cpp-component-extensions.md)|ユーザー定義の属性を示します。|
|[#using ディレクティブ](../preprocessor/hash-using-directive-cpp.md)|外部アセンブリをインポートします。|
|[XML に関するドキュメント](../build/reference/xml-documentation-visual-cpp.md)|[/doc (ドキュメント コメントの処理) (C/C++)](../build/reference/doc-process-documentation-comments-c-cpp.md) を使用した XML ベースのコード ドキュメントについて説明します。|

## <a name="see-also"></a>関連項目

[C++/CLI (Visual C++) による .NET プログラミング](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
[ネイティブと .NET の相互運用性](../dotnet/native-and-dotnet-interoperability.md)