---
title: '方法: PInvoke を使用してマネージ コードからネイティブ Dll を呼び出す'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- platform invoke [C++], calling native DLLs
- interop [C++], calling native DLLs
- marshaling [C++], calling native DLLs
- data marshaling [C++], calling native DLLs
ms.assetid: 3273eb4b-38d1-4619-92a6-71bda542be72
ms.openlocfilehash: e51e094cc013250fc254a09e279745f1f9c108ac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222812"
---
# <a name="how-to-call-native-dlls-from-managed-code-using-pinvoke"></a>方法: PInvoke を使用してマネージ コードからネイティブ Dll を呼び出す

アンマネージ Dll に実装されている関数は、Platform Invoke (P/invoke) 機能を使用してマネージ コードから呼び出すことができます。 DLL のソース コードを使用できない場合の相互運用の唯一のオプションは、P/invoke します。 ただし、Visual C は、他の .NET 言語とは異なり、P/invoke の代替を提供します。 詳細については、次を参照してください。[を使用して C++ Interop (暗黙の PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)します。

## <a name="example"></a>例

次のコード例は、Win32 を使用して[GetSystemMetrics](/windows/desktop/api/winuser/nf-winuser-getsystemmetrics) (ピクセル単位)、画面の現在の解像度を取得します。

関数の引数として組み込み型のみを使用すると、戻り値の場合に余分な作業は必要ありません。 関数ポインター、配列、および構造体などの他のデータ型には、適切なデータのマーシャ リングすることを確認する追加属性が必要です。

必須ではありませんが、この例のように、グローバル名前空間に存在しないように P/invoke 宣言の値クラスの静的メンバーを作成するようにを勧めします。

```
// pinvoke_basic.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

value class Win32 {
public:
   [DllImport("User32.dll")]
   static int GetSystemMetrics(int);

   enum class SystemMetricIndex {
      // Same values as those defined in winuser.h.
      SM_CXSCREEN = 0,
      SM_CYSCREEN = 1
   };
};

int main() {
   int hRes = Win32::GetSystemMetrics( safe_cast<int>(Win32::SystemMetricIndex::SM_CXSCREEN) );
   int vRes = Win32::GetSystemMetrics( safe_cast<int>(Win32::SystemMetricIndex::SM_CYSCREEN) );
   Console::WriteLine("screen resolution: {0},{1}", hRes, vRes);
}
```

## <a name="see-also"></a>関連項目

[C++ での明示的な PInvoke (DllImport 属性) の使用方法](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
