---
title: Ref クラスと構造体 (C++/CX)
ms.date: 01/22/2017
ms.assetid: 3d736b82-0bf0-48cf-bac1-cc9d110b70d1
ms.openlocfilehash: b58c5b64d8f4a60b418fdd2b11318055a8fb618e
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740895"
---
# <a name="ref-classes-and-structs-ccx"></a>Ref クラスと構造体 (C++/CX)

/Cx C++は、ユーザー定義の*ref クラス*と*ref 構造体*、およびユーザー定義の*値クラス*と*値構造体*をサポートしています。 これらのデータ構造は、/Cx が Windows ランタイムC++型システムをサポートする主なコンテナーです。 これらのコンテンツは特定の特定のルールに従ってメタデータに出力されます。これにより、または他の言語C++で記述された Windows ランタイムコンポーネントとユニバーサル Windows プラットフォームアプリ間でそれらのコンテンツを渡すことができます。

ref クラスまたは ref 構造体には、次のような固有の特徴があります。

- 名前空間内部で宣言される必要があり、名前空間のスコープ、およびその名前空間内で public または private のアクセシビリティを持つことができます。 パブリック型だけがメタデータに出力されます。 入れ子になったパブリック [列挙型](../cppcx/enums-c-cx.md) クラスを含め、入れ子になったパブリック クラス定義は使用できません。 詳細については、「[名前空間と型の可視性](../cppcx/namespaces-and-type-visibility-c-cx.md)」を参照してください。

- これには、ref C++クラス、値クラス、ref 構造体、値構造体、または null 許容値構造体を含む、/cx としてを含めることができます。 これには、float64 や bool などのスカラー型も含まれる場合があります。 また、パブリックでない限り `std::vector` やカスタム クラスなどの標準の C++ 型が含まれる場合もあります。 C++`public`/Cx コンストラクトは`private` `protected` `protected private` 、、、 、、またはアクセシビリティを持つことができます。`internal` `public` または `protected` のすべてのメンバーは、メタデータに出力されます。 標準 C++ の型は、 `private`、 `internal`、または `protected private` のアクセシビリティを持つ必要があります。これにより、それらの型がメタデータに出力されることが防止されます。

- 1 つ以上の *インターフェイス クラス* または *インターフェイス構造体*を実装することができます。

- 1 つの基底クラスから継承することができ、基底クラス自体に追加の制限があります。 パブリック ref クラス階層構造での継承には、private ref クラスでの継承によりも多くの制限があります。

- generic として宣言することはできません。 private アクセシビリティがある場合、テンプレートになることができます。

- その有効期間は、自動参照カウントによって管理されます。

## <a name="declaration"></a>宣言

次のコード片は `Person` ref クラスを宣言します。 プライベートメンバーではC++ `std::map`標準の型が使用されており、Windows ランタイム`IMapView`インターフェイスがパブリックインターフェイスで使用されていることに注意してください。 また、"^" が参照型の宣言に追加されることにも注意してください。

[!code-cpp[cx_classes#03](../cppcx/codesnippet/CPP/classesstructs/class1.h#03)]

## <a name="implementation"></a>実装

このコード例は、 `Person` ref クラスの実装を示しています。

[!code-cpp[cx_classes#04](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#04)]

## <a name="usage"></a>使用法

次のコード例は、クライアント コードで `Person` ref クラスを使用する方法を示しています。

[!code-cpp[cx_classes#05](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#05)]

また、スタック セマンティクスを使用して ref クラスのローカル変数を宣言することもできます。 メモリはまだ動的に割り当てられますが、このようなオブジェクトはスタック ベースの変数のように動作します。 1 つの重要な違いは、スタック セマンティクスを使用して宣言されている変数に追跡参照 (%) を割り当てることができないことです。これにより、関数が終了したときに参照カウントが必ず 0 にデクリメントされます。 この例では、基本 ref クラス `Uri`、およびスタック セマンティクスでそれを使用する関数を示します。

[!code-cpp[cx_classes#06](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#06)]

## <a name="memory-management"></a>メモリ管理

ref クラスは、 `ref new` キーワードを使用して動的メモリに割り当てます。

[!code-cpp[cx_classes#01](../cppcx/codesnippet/CPP/classesstructs/class1.h#01)]

オブジェクトへのハンドル演算子 ^ は "キャレット" として知られ、基本的には C++ スマート ポインターです。 これが指すメモリは、最後のキャレットがスコープ外に出ると自動的に破棄されるか、明示的に `nullptr`に設定されます。

定義上、ref クラスには、参照セマンティクスがあります。 ref クラスの変数を代入した場合、代入されるのはコピーされるハンドルであり、オブジェクト自体ではありません。 次の例では、代入後に `myClass` と `myClass2` の両方が同じメモリ位置を指します。

[!code-cpp[cx_classes#02](../cppcx/codesnippet/CPP/classesstructs/class1.h#02)]

C++/CX ref クラスをインスタンス化する場合、コンストラクターを呼び出す前にメモリがゼロ初期化されます。したがって、プロパティを含む個々のメンバーをゼロ初期化する必要はありません。 C++/CX クラスが Windows ランタイム C++ ライブラリ (WRL) クラスから派生している場合、C++/CX 派生クラスの部分だけがゼロ初期化されます。

### <a name="members"></a>メンバー

ref クラスは、 `public`、 `protected`、および `private` の関数メンバーを格納できます。 `public` と `protected` のメンバーだけが、メタデータに出力されます。 入れ子になったクラスおよび ref クラスは許可されますが、 `public`になることはできません。 public フィールドは使用できません。public データ メンバーはプロパティとして宣言する必要があります。 プライベートまたはプロテクトの内部データ メンバーは、フィールドである場合があります。 既定では、ref クラスでは、すべてのメンバーのアクセシビリティは `private`です。

ref 構造体は ref クラスと同じですが、既定ではメンバーのアクセシビリティは `public` です。

`public` Ref クラスまたは ref 構造体はメタデータに出力されますが、他のユニバーサル Windows プラットフォームアプリおよび Windows ランタイムコンポーネントから使用できるようにするには、少なくとも1つのパブリックコンストラクターまたはプロテクトコンストラクターが必要です。 public コンストラクターを持つ public ref クラスは、アプリケーション バイナリ インターフェイス (ABI: Application Binary Interface) を介してさらに派生されることを防ぐために `sealed` としても宣言される必要があります。

Windows ランタイム型システムで const がサポートされていないため、パブリックメンバーを const として宣言することはできません。 静的なプロパティを使用して、定数値を持つパブリック データ メンバーを宣言することができます。

public の ref クラスまたは構造体が定義されると、コンパイラは必要な属性をクラスに適用し、その情報をアプリの .winmd ファイルに格納します。 ただし、パブリックに封印されていない ref クラスを定義`Windows::Foundation::Metadata::WebHostHidden`する場合は、属性を手動で適用して、クラスが JavaScript で記述されたユニバーサル Windows プラットフォームアプリに表示されないようにします。

ref クラスは、 `const` 型を含む標準 C++ の型を、 `private`、 `internal`、または `protected private` のあらゆるメンバーの中で使用することができます。

型パラメーターを持つパブリック ref クラスは許可されません。 ユーザー定義の generic ref クラスは許可されません。 private、internal、または protected private の ref クラスは、テンプレートになることができます。

## <a name="destructors"></a>デストラクター

/Cx C++では、 `delete`パブリックデストラクターでを呼び出すと、オブジェクトの参照カウントに関係なくデストラクターが呼び出されます。 この動作により、非 RAII リソースのカスタム クリーンアップを確定的な方法で実行できるデストラクターを定義できます。 ただし、この場合でも、オブジェクト自体はメモリから削除されません。 オブジェクトのメモリは、参照カウントがゼロに達した場合のみ解放されます。

クラスのデストラクターがパブリックでない場合は、参照カウントがゼロに達する場合にのみ、このデストラクターが呼び出されます。 プライベートデストラクターを`delete`持つオブジェクトに対してを呼び出すと、コンパイラによって警告 C4493 が発生します。これは、"型 > \<名のデストラクターに ' public ' アクセシビリティが設定されていないため、delete 式は無効です。" というメッセージが表示されます。

Ref クラスのデストラクターでは、次以外の宣言はできません。

- public および virtual (sealed または unsealed 型で使用できます)

- protected private と non-virtual (unsealed 型でのみ使用できます)

- private と non-virtual (sealed 型でのみ使用できます)

アクセシビリティ、仮想性、およびシールド性のこれ以外の組み合わせは使用できません。  デストラクターが明示的に宣言されない場合、型の基底クラスまたはメンバーに public デストラクターがあると、コンパイラは public virtual デストラクターを生成します。 それ以外の場合、コンパイラは unsealed 型には protected private non-virtual デストラクター、sealed 型には private non-virtual デストラクターを生成します。

デストラクターを既に実行しているクラスのメンバーにアクセスを試みたときの動作は不確定です。プログラムがクラッシュする可能性が高いと思われます。 public デストラクターがない型上で `delete t` を呼び出しても、何の効果もありません。 型の階層構造内から既知の `delete this` または `private` デストラクターを持つ型または基底クラス上で `protected private` を呼び出しても、何の効果もありません。

public デストラクターが宣言されると、コンパイラがコードを生成するので、ref クラスが `Platform::IDisposable` を実装し、デストラクターが `Dispose` メソッドを実装します。 `Platform::IDisposable`は、 C++の`Windows::Foundation::IClosable`/cx プロジェクションです。 これらのインターフェイスは、明示的に実装しないでください。

## <a name="inheritance"></a>継承

Platform::Object は、すべての ref クラスの汎用基底クラスです。 ref クラスは、いずれも Platform::Object に暗黙的に変換可能で、 [Object::ToString](../cppcx/platform-object-class.md#tostring)をオーバーライドできます。 ただし、Windows ランタイム継承モデルは、一般的な継承モデルとしては想定されていません。/Cx C++では、ユーザー定義のパブリック ref クラスを基底クラスとして使用することはできません。

XAML ユーザー コントロールを作成し、オブジェクトが依存関係プロパティ システムに参加している場合は、 `Windows::UI::Xaml::DependencyObject` を基底クラスとして使用できます。

`MyBase` から継承する unsealed クラス `DependencyObject`が定義されると、コンポーネントまたはアプリ内の他の public または private の ref クラスは `MyBase`から継承できるようになります。 public ref クラスの継承は、仮想メソッド、ポリモーフィック ID、およびカプセル化のオーバーライドをサポートする目的以外には実行しないでください。

private 基本 ref クラスがなくても、既存の unsealed クラスから派生できます。 独自のプログラム構造をモデル化するかまたはコードの再利用を有効にするために、オブジェクト階層構造を必要とする場合は、private または internal の ref クラスを使用するか、さらに優れた手法として標準 C++ クラスを使用してください。 public sealed ref クラス ラッパーを通じて、プライベート オブジェクト階層構造の機能を公開できます。

/Cx 内のC++public または protected コンストラクターを持つ ref クラスは、sealed として宣言されなければなりません。 この制限は、 C#やなどの他の言語で記述されたクラスが Visual Basic、/cxでC++記述された Windows ランタイムコンポーネントで宣言する型から継承する方法がないことを意味します。

/Cx でC++の継承に関する基本的な規則を次に示します。

- ref クラスは多くても 1 つの基本 ref クラスからしか直接継承できませんが、任意の数のインターフェイスを実装できます。

- あるクラスに public コンストラクターがある場合、さらに派生されることを防ぐために sealed として宣言する必要があります。

- 基底クラスが `Windows::UI::Xaml::DependencyObject`などの既存の unsealed 基底クラスから直接または間接的に派生する場合は、internal または protected private のコンストラクターを持つ public unsealed 基底クラスを作成できます。 .winmd ファイル間でのユーザー定義 ref クラスの継承はサポートされません。ただし、ref クラスは別の .winmd ファイルで定義されているインターフェイスから継承できます。 ユーザー定義の基本 ref クラスの派生クラスは、同じ Windows ランタイムコンポーネントまたはユニバーサル Windows プラットフォームアプリ内でのみ作成できます。

- ref クラスの場合、パブリック継承のみサポートされます。

   [!code-cpp[cx_classes#08](../cppcx/codesnippet/CPP/classesstructs/class1.h#08)]

次の例では、継承階層構造の他の ref クラスから派生する public ref クラスを公開する方法を示します。

[!code-cpp[cx_classes#09](../cppcx/codesnippet/CPP/classesstructs/class1.h#09)]

## <a name="see-also"></a>関連項目

[型システム](../cppcx/type-system-c-cx.md)<br/>
[値クラスと構造体](../cppcx/value-classes-and-structs-c-cx.md)<br/>
[C++/CX 言語リファレンス](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[名前空間参照](../cppcx/namespaces-reference-c-cx.md)
