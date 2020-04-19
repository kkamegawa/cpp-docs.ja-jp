---
title: C++ Interop (暗黙の PInvoke) の使用
ms.date: 11/04/2016
helpviewer_keywords:
- blittable types [C++]
- platform invoke [C++], implicit
- interop [C++], features
- data marshaling [C++], C++ Interop features
- porting [C++], C++ native to .NET
- COM interfaces [C++]
- implicit platform invoke
- examples [C++], interoperability
- types [C++], blittable
- marshaling [C++], C++ Interop features
- platform invoke [C++], examples
- interoperability [C++]
- C++ Interop
- interoperability [C++], Implicit PInvoke
- C++, interop
- C++ COM Interop
- .NET [C++], porting C++ native to
ms.assetid: 5f710bf1-88ae-4c4e-8326-b3f0b7c4c68a
ms.openlocfilehash: aaa07373b7dd22807290ceefa9197b4013c61fe5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384518"
---
# <a name="using-c-interop-implicit-pinvoke"></a>C++ Interop (暗黙の PInvoke) の使用

その他の .NET 言語とは異なり、Visual C には相互運用性サポートと同じファイルであっても、同じアプリケーション内に存在するマネージ コードとアンマネージ コードを許可する (で、[マネージ、アンマネージ](../preprocessor/managed-unmanaged.md)プラグマ)。 これにより、Visual C++ 開発者は、他のアプリケーションの動作を妨げることなく、既存の Visual C++ アプリケーションに .NET 機能を統合できます。

使用して、マネージ コンパイル単位からアンマネージ関数を呼び出すことができますも[dllexport、dllimport](../cpp/dllexport-dllimport.md)します。

関数パラメーターのマーシャリング方法を指定したり、DllImportAttribute を明示的に呼び出す際に指定できるその他の詳細設定を行ったりする必要がない場合は、暗黙の PInvoke を使用すると便利です。

Visual C++ では、マネージド関数とアンマネージド 関数を相互運用するために 2 つの方法があります。

- [C++ での明示的な PInvoke (DllImport 属性) の使用方法](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)

明示的な PInvoke は、.NET Framework でサポートされており、ほとんどの .NET 言語で使用できます。 ただし、その名前からわかるように、C++ Interop は Visual C++ 固有の機能です。

## <a name="c-interop"></a>C++ Interop

明示的な PInvoke よりも C++ Interop を使用することをお勧めします。C++ Interop は、より優れたタイプセーフを提供し、通常、実装も容易で、アンマネージ API が変更された場合もより柔軟に対処できるからです。また、明示的な PInvoke では不可能なパフォーマンスの向上も実現できます。 ただし、C++ Interop では、この非管理対象のソース コードが使用できない場合は、ことはできません。

## <a name="c-com-interop"></a>C++ COM Interop

Visual C++ がサポートしている相互運用機能は、COM コンポーネントとの相互運用性において、他の .NET 言語に比べ特に優れた効果を発揮します。 .NET Framework の制限にとらわれることがなく[Tlbimp.exe (タイプ ライブラリ インポーター)](/dotnet/framework/tools/tlbimp-exe-type-library-importer)、C++ 相互運用機能により、COM などのデータ型とすべての COM インターフェイスのすべてのメンバーの必須の露出を制限付きサポートアクセスするコンポーネントでは、個別の相互運用機能アセンブリは必要ありません。 Visual Basic とは異なり、 C#、Visual C は、通常の COM メカニズムを使用して直接 COM オブジェクトを使用できます (など**CoCreateInstance**と**QueryInterface**)。 これは、マネージとアンマネージ関数から移動し、再度遷移コードを自動的に挿入するコンパイラの原因になる C++ Interop 機能により、発生します。

C++ Interop を使用して、COM コンポーネントできますように通常使用されているか、C++ のクラス内にラップできます。 これらのラッパー クラスはカスタム ランタイム呼び出し可能ラッパーと呼ばれるまたは Crcw、およびそれらに直接アプリケーション コードで COM を使用する場合より 2 つの利点があります。

- 結果として得られるクラスは、Visual C 以外の言語から使用できます。

- 管理されたクライアント コードから COM インターフェイスの詳細を非表示にできます。 .NET データ型は、ネイティブな型の代わりに使用できるし、CRCW 内に、データのマーシャ リングの詳細を透過的に実行できます。

COM を使用する直接または、CRCW 経由かどうか、単純で、blittable 型以外の引数の型をマーシャ リングする必要があります。

## <a name="blittable-types"></a>blittable 型

シンプルな組み込み型を使用するアンマネージ Api の (を参照してください[blittable 型と非 Blittable 型](/dotnet/framework/interop/blittable-and-non-blittable-types))、特別なコーディングは必要ありませんので、これらのデータ型、メモリ内で同じ表現であるより複雑なデータ型が必要です明示的なデータをマーシャ リングします。 例については、「[方法: PInvoke を使用してマネージ コードからネイティブ Dll を呼び出す](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md)します。

## <a name="example"></a>例

```cpp
// vcmcppv2_impl_dllimp.cpp
// compile with: /clr:pure user32.lib
using namespace System::Runtime::InteropServices;

// Implicit DLLImport specifying calling convention
extern "C" int __stdcall MessageBeep(int);

// explicit DLLImport needed here to use P/Invoke marshalling because
// System::String ^ is not the type of the first parameter to printf
[DllImport("msvcrt.dll", EntryPoint = "printf", CallingConvention = CallingConvention::Cdecl,  CharSet = CharSet::Ansi)]
// or just
// [DllImport("msvcrt.dll")]
int printf(System::String ^, ...);

int main() {
   // (string literals are System::String by default)
   printf("Begin beep\n");
   MessageBeep(100000);
   printf("Done\n");
}
```

```Output
Begin beep
Done
```

## <a name="in-this-section"></a>このセクションの内容

- [方法: C++ Interop を使用して ANSI 文字列をマーシャリングする](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

- [方法: C++ Interop を使用して Unicode 文字列をマーシャリングする](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [方法: C++ Interop を使用して COM 文字列をマーシャリングする](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

- [方法: C++ Interop を使用して構造体をマーシャリングする](../dotnet/how-to-marshal-structures-using-cpp-interop.md)

- [方法: C++ Interop を使用して配列をマーシャリングする](../dotnet/how-to-marshal-arrays-using-cpp-interop.md)

- [方法: C++ Interop を使用してコールバックおよびデリゲートをマーシャリングする](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)

- [方法: C++ Interop を使用して埋め込みポインターをマーシャリングする](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)

- [方法: System::String の文字にアクセスする](../dotnet/how-to-access-characters-in-a-system-string.md)

- [方法: char * 文字列を System::Byte 配列に変換する](../dotnet/how-to-convert-char-star-string-to-system-byte-array.md)

- [方法: System::string を wchar_t * または char に変換します。\*](../dotnet/how-to-convert-system-string-to-wchar-t-star-or-char-star.md)

- [方法: System::String を標準文字列に変換する](../dotnet/how-to-convert-system-string-to-standard-string.md)

- [方法: 標準文字列を System::String に変換する](../dotnet/how-to-convert-standard-string-to-system-string.md)

- [方法: バイト配列へのポインターを取得する](../dotnet/how-to-obtain-a-pointer-to-byte-array.md)

- [方法: アンマネージ リソースをバイト配列に読み込む](../dotnet/how-to-load-unmanaged-resources-into-a-byte-array.md)

- [方法: ネイティブ関数の参照クラスを変更する](../dotnet/how-to-modify-reference-class-in-a-native-function.md)

- [方法: イメージがネイティブであるか CLR であるかを確認する](../dotnet/how-to-determine-if-an-image-is-native-or-clr.md)

- [方法: ネイティブ DLL をグローバル アセンブリ キャッシュに追加する](../dotnet/how-to-add-native-dll-to-global-assembly-cache.md)

- [方法: 値型への参照をネイティブ型で保持する](../dotnet/how-to-hold-reference-to-value-type-in-native-type.md)

- [方法: アンマネージ メモリ内にオブジェクト参照を保持する](../dotnet/how-to-hold-object-reference-in-unmanaged-memory.md)

- [方法: /Clr のコンパイルを検出します。](../dotnet/how-to-detect-clr-compilation.md)

- [方法: System::Guid と _GUID の間で変換を行う](../dotnet/how-to-convert-between-system-guid-and-guid.md)

- [方法: out パラメーターを指定する](../dotnet/how-to-specify-an-out-parameter.md)

- [方法: /Clr のコンパイルでネイティブ型を使用します。](../dotnet/how-to-use-a-native-type-in-a-clr-compilation.md)

- [方法: ネイティブ型のハンドルを宣言する](../dotnet/how-to-declare-handles-in-native-types.md)

- [方法: ネイティブ クラスを C# で使用できるようにラップする](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)

相互運用機能のシナリオではデリゲートの使用方法の詳細については、次を参照してください。[デリゲート (C++ コンポーネント拡張)](../extensions/delegate-cpp-component-extensions.md)します。

## <a name="see-also"></a>関連項目

- [マネージド コードからのネイティブ関数の呼び出し](../dotnet/calling-native-functions-from-managed-code.md)
