---
title: クイック リファレンス (C++/CX)
ms.date: 12/30/2016
ms.assetid: ba457195-26e5-43aa-b99d-24a871e550f4
ms.openlocfilehash: 2826105f7ec4a680208965fcc18a548c6ec4b795
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740917"
---
# <a name="quick-reference-ccx"></a>クイック リファレンス (C++/CX)

Windows ランタイムは、信頼できるオペレーティングシステム環境でのみ実行され、承認された機能、データ型、およびデバイスを使用し、Microsoft Store 経由で配布されるユニバーサル Windows プラットフォーム (UWP) アプリをサポートしています。 C++/Cx を使用すると、Windows ランタイムのアプリを簡単に作成できます。 この記事はクイックリファレンスです。詳細なドキュメントについては、「[型システム](../cppcx/type-system-c-cx.md)」を参照してください。

コマンドラインでビルドする場合は、 **/ZW**コンパイラオプションを使用して UWP アプリまたは Windows ランタイムコンポーネントをビルドします。 Windows ランタイムメタデータ (winmd) ファイルで定義されている Windows ランタイム宣言にアクセスするには`#using` 、ディレクティブまたは **/fu**コンパイラオプションを指定します。 UWP アプリ用のプロジェクトを作成すると、Visual Studio は既定でこれらのオプションを設定し、すべての Windows ランタイムライブラリへの参照を追加します。

## <a name="quick-reference"></a>クイック リファレンス

|概念|標準 C++|C++/CX|Remarks|
|-------------|--------------------|------------------------------------------------------------------|-------------|
|基本的な型|C++ の基本型。|C++Windows ランタイムで定義されている基本型を実装する/CX の基本型。|名前`default`空間にC++は、/cx 組み込みの基本型が含まれています。 コンパイラは、/Cx C++の基本型を標準C++型に暗黙的にマップします。<br /><br /> 名前`Platform`空間のファミリには、基本的な Windows ランタイム型を実装する型が含まれています。|
||`bool`|`bool`|8 ビットのブール値。|
||`__wchar_t`|`char16`|Unicode (UTF-16) コード ポイントを表す 16 ビットの数字以外の値。|
||`short`<br /><br /> `unsigned short`|`int16`<br /><br /> `uint16`|16 ビット符号付き整数。<br /><br /> 16 ビット符号なし整数。|
||`int`<br /><br /> `unsigned int`|`int`<br /><br /> `uint32`|32 ビット符号付き整数。<br /><br /> 32 ビット符号なし整数|
||`long long` または `__int64`<br /><br /> `unsigned long long`|`int64`<br /><br /> `uint64`|64 ビット符号付き整数。<br /><br /> 64 ビット符号なし整数。|
||`float, double`|`float32, float64`|32 ビットまたは 64 ビットの IEEE 754 浮動小数点数。|
||`enum {}`|`enum class {}`<br /><br /> \- または -<br /><br /> `enum struct {}`|32 ビット列挙体。|
||(該当なし)|`Platform::Guid`|`Platform` 名前空間での 128 ビット非数値 (GUID)。|
||`std::time_get`|`Windows::Foundation::DateTime`|日付と時刻の構造体。|
||(該当なし)|`Windows::Foundation::TimeSpan`|期間の構造体。|
||(該当なし)|`Platform::Object^`|Windows ランタイム型システムのC++ビューの参照カウントベースオブジェクト。|
||`std::wstring`<br /><br /> `L"..."`|`Platform::String^`|`Platform::String^` は、テキストを表す Unicode 文字列の、参照がカウントされて変更不可能なシーケンスです。|
|ポインター|オブジェクトへのポインター (`*`):<br /><br /> `std::shared_ptr`|オブジェクトへのハンドル (`^`、「ハット」と発音):<br /><br /> *T^ identifier*|すべての Windows ランタイムクラスは、オブジェクトへのハンドル修飾子を使用して宣言されます。 オブジェクトのメンバーにアクセスするには、矢印 (`->`) クラス メンバー アクセス演算子を使用します。<br /><br /> Hat 修飾子は、"自動的に参照カウントされる Windows ランタイムオブジェクトへのポインター" を意味します。 より厳密には、オブジェクトへのハンドルは、コンパイラが、オブジェクトの参照カウントを自動的に管理するためのコードを挿入する必要があること、および参照カウントがゼロになった場合にオブジェクトを削除する必要があることを宣言します。|
|参照|オブジェクトへの参照 (`&`):<br /><br /> *T* `&` *identifier*|トラッキング参照 (`%`):<br /><br /> *T* `%` *identifier*|追跡参照修飾子を使用して宣言できるのは、Windows ランタイム型だけです。 オブジェクトのメンバーにアクセスするには、ドット (`.`) クラス メンバー アクセス演算子を使用します。<br /><br /> 追跡参照は、"自動的に参照カウントされる Windows ランタイムオブジェクトへの参照" を意味します。 より厳密には、追跡参照は、コンパイラが、オブジェクトの参照カウントを自動的に管理するためのコードを挿入する必要があること、および参照カウントがゼロになった場合にオブジェクトを削除する必要があることを宣言します。|
|動的な型の宣言|`new`|`ref new`|Windows ランタイムオブジェクトを割り当て、そのオブジェクトへのハンドルを返します。|
|オブジェクトの有効期間の管理|`delete` *identifier*<br /><br /> `delete[]`  *identifier*|(デストラクターを呼び出します。)|有効期間は、参照カウントによって決まります。 削除への呼び出しはデストラクターを呼び出しますが、それ自体はメモリを解放しません。|
|配列の宣言|*T  identifier* `[]`<br /><br /> `std::array` *identifier*|`Array<` *T* `^>^` *identifier* `(` *size* `)`<br /><br /> \- または -<br /><br /> `WriteOnlyArray<` *T* `^>`  *identifier* `(` *size* `)`|T^ 型の、1 次元変更可能または書き込み専用の配列を宣言します。 配列自体も、オブジェクトへのハンドル修飾子を使用して宣言する必要がある、参照カウント オブジェクトです。<br /><br /> (配列宣言は、 `Platform` 名前空間にあるヘッダー テンプレート クラスを使用します。)|
|クラス宣言|`class`  *identifier* `{}`<br /><br /> `struct` *identifier* `{}`|`ref class` *identifier* `{}`<br /><br /> `ref struct` *identifier* `{}`|既定のプライベート アクセシビリティを持つランタイム クラスを宣言します。<br /><br /> 既定のパブリック アクセシビリティを持つランタイム クラスを宣言します。|
|構造体宣言|`struct` *identifier* `{}`<br /><br /> (つまり、PODS (Plain Old Data Structure))|`value class` *identifier* `{}`<br /><br /> `value struct` *identifier* `{}`|既定のプライベート アクセシビリティを持つ POD 構造体を宣言します。<br /><br /> 値のクラスは Windows メタデータで表現できますが、標準の C++ クラスは Windows メタデータで表現できません。<br /><br /> 既定のパブリック アクセシビリティを持つ POD 構造体を宣言します。<br /><br /> 値の構造体は Windows メタデータで表現できますが、標準 C++ 構造体は Windows メタデータで表現できません。|
|インターフェイス宣言|純粋仮想関数のみを含む抽象クラス。|`interface class` *identifier* `{}`<br /><br /> `interface struct` *identifier* `{}`|既定のプライベート アクセシビリティを持つインターフェイスを宣言します。<br /><br /> 既定のパブリック アクセシビリティを持つインターフェイスを宣言します。|
|delegate|`std::function`|`public delegate` *return-type* *delegate-type-identifier* `(` *[ parameters ]* `);`|関数呼び出しのように呼び出すことができるオブジェクトを宣言します。|
|event|(該当なし)|`event` *delegate-type-identifier* *event-identifier* `;`<br /><br /> *delegate-type-identifier* *delegate-identifier* = `ref new`*delegate-type-identifier*`( this` *[, parameters]* `);`<br /><br /> *event-identifier* `+=` *delegate-identifier* `;`<br /><br /> \- または -<br /><br /> `EventRegistrationToken` *token-identifier* = *obj*`.`*event-identifier*`+=`*delegate-identifier*`;`<br /><br /> \- または -<br /><br /> `auto`*トークン識別子* =  *obj*。*イベント識別子* *デリゲート-識別子* `::add(``);`<br /><br /> *obj* `.` *event-identifier* `-=` *token-identifier* `;`<br /><br /> \- または -<br /><br /> *obj* `.` *event-identifier* `::remove(` *token-identifier* `);`|イベント オブジェクトを宣言し、そこにイベントが発生したときに呼び出されるイベント ハンドラー (デリゲート) のコレクションを格納します。<br /><br /> イベント ハンドラーを作成します。<br /><br /> イベント ハンドラーを追加します。<br /><br /> イベント ハンドラーを追加すると、イベント トークン (*token-identifier*) が返されます。 明示的にイベント ハンドラーを削除することを意図している場合は、後で使用できるようにイベント トークンを保存する必要があります。<br /><br /> イベント ハンドラーを削除します。<br /><br /> イベント ハンドラーを削除するには、イベント ハンドラーが追加されたときに保存したイベント トークンを指定する必要があります。|
|property|(該当なし)|`property` *T* *identifier*;<br /><br /> `property` *T* *identifier* `[` *インデックス* `];`<br /><br /> `property` *T* `default[` *インデックス* `];`|クラス メンバー関数またはオブジェクト メンバー関数が、データ メンバーまたはインデックス付きの配列要素へのアクセスで使用されたのと同じ構文を使用してアクセスされることを宣言します。<br /><br /> クラス オブジェクト メンバー関数またはオブジェクト メンバー関数のインデックス付きプロパティを宣言します。<br /><br /> オブジェクト メンバー関数のインデックス付きプロパティを宣言します。<br /><br /> クラス メンバー関数のインデックス付きプロパティを宣言します。|
|パラメーター化された型|テンプレート|`generic <typename` *T* `> interface class` *identifier* `{}`<br /><br /> `generic <typename` *T* `> delegate` *[return-type]* *delegate-identifier* `() {}`|パラメーター化されたインターフェイス クラスを宣言します。<br /><br /> パラメーター化されたデリゲートを宣言します。|
|null 許容値型|`boost::optional<T>`|[Platform:: ibox \<T >](../cppcx/platform-ibox-interface.md)|スカラー型および値構造体の変数の値を `nullptr`にすることができます。|

## <a name="see-also"></a>関連項目

[C++/CX 言語リファレンス](../cppcx/visual-c-language-reference-c-cx.md)
