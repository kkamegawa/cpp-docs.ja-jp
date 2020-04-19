---
title: 'C++ での明示的な PInvoke (DllImport 属性) の使用方法 '
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling [C++], platform invoke
- C++ Interop, platform invoke
- interop [C++], platform invoke
- platform invoke [C++], marshaling in C++
- data marshaling [C++], platform invoke
ms.assetid: 18e5218c-6916-48a1-a127-f66e22ef15fc
ms.openlocfilehash: ee9d77920f04f7eba5112c66a906b02b7fc4a658
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384427"
---
# <a name="using-explicit-pinvoke-in-c-dllimport-attribute"></a>C++ での明示的な PInvoke (DllImport 属性) の使用方法 

.NET Framework では、明示的なプラットフォーム呼び出し (PInvoke) 機能に、マネージド アプリケーションが DLL 内部にパッケージ化されているアンマネージド 関数を呼び出すことができるようにする `Dllimport` 属性を備えています。 明示的な PInvoke は、アンマネージ API が DLL としてパッケージ化され、ソース コードが利用できない場合に必要です。 たとえば、Win32 関数の呼び出しには、PInvoke が必要です。 それ以外の場合、使用して、暗黙の P {Invoke; を参照してください[を使用して C++ Interop (暗黙の PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)詳細については。

PInvoke を機能させるには、<xref:System.Runtime.InteropServices.DllImportAttribute> を使用します。 この属性は、その最初の引数として DLL 名を使用し、使用する各 DLL エントリ ポイントの関数宣言の前に置かれます。 関数のシグネチャは、DLL によってエクスポートされた関数名に一致する必要があります (ただし、型変換によっては、マネージド型を使用して `DllImport` 宣言を定義することで、暗黙的に実行できるものもあります)。

その結果、これは、必要な遷移コード (または、サンク) と単純データ変換を含む各ネイティブ DLL 関数のマネージド エントリ ポイントになります。 その後、マネージド関数は、これらのエントリ ポイントを介して DLL を呼び出します。 PInvoke の結果として、モジュールに挿入されたコードが完全に管理されます。

## <a name="in-this-section"></a>このセクションの内容

- [マネージド コードからのネイティブ関数の呼び出し](../dotnet/calling-native-functions-from-managed-code.md)

- [方法: PInvoke を使用してマネージド コードからネイティブ DLL を呼び出す](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md)

- [方法: PInvoke を使用して文字列をマーシャリングする](../dotnet/how-to-marshal-strings-using-pinvoke.md)

- [方法: PInvoke を使用して構造体をマーシャリングする](../dotnet/how-to-marshal-structures-using-pinvoke.md)

- [方法: PInvoke を使用して配列をマーシャリングする](../dotnet/how-to-marshal-arrays-using-pinvoke.md)

- [方法: PInvoke を使用して関数ポインターをマーシャリングする](../dotnet/how-to-marshal-function-pointers-using-pinvoke.md)

- [方法: PInvoke を使用して埋め込みポインターをマーシャリングする](../dotnet/how-to-marshal-embedded-pointers-using-pinvoke.md)

## <a name="see-also"></a>関連項目

[マネージド コードからのネイティブ関数の呼び出し](../dotnet/calling-native-functions-from-managed-code.md)
