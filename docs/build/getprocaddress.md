---
title: GetProcAddress
ms.date: 11/04/2016
f1_keywords:
- GetProcAddress
helpviewer_keywords:
- DLLs [C++], GetProcAddress
- ordinal exports [C++]
- GetProcAddress method
ms.assetid: 48d14ae0-47ea-4c5d-96b1-2c158f1a26af
ms.openlocfilehash: 2d322cfe7d3bd60d8d702a226e181eb7b4ede963
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493248"
---
# <a name="getprocaddress"></a>GetProcAddress

Dll に明示的にリンクしているプロセスは、DLL 内のエクスポートされた関数のアドレスを取得するために[GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress)を呼び出します。 返された関数ポインターを使って、DLL 関数を呼び出します。 **GetProcAddress**は、DLL モジュールハンドル ( **LoadLibrary**、 `AfxLoadLibrary`、または**GetModuleHandle**のいずれかによって返される) のパラメーターとしてを受け取り、呼び出す関数の名前または関数のエクスポート序数を受け取ります。

DLL 関数の呼び出しにはポインターが使われ、コンパイル時にデータ型はチェックされないため、関数へ渡すパラメーターが正しいことを確認してください。パラメーターが不正な場合、スタック上に割り当てられたメモリ域をオーバーしたり、アクセス違反を起こしたりすることがあります。 型をタイプセーフにする 1 つの方法は、エクスポート関数の関数プロトタイプを見て、関数ポインター用に対応する typedef を作成することです。 例えば:

```
typedef UINT (CALLBACK* LPFNDLLFUNC1)(DWORD,UINT);
...

HINSTANCE hDLL;               // Handle to DLL
LPFNDLLFUNC1 lpfnDllFunc1;    // Function pointer
DWORD dwParam1;
UINT  uParam2, uReturnVal;

hDLL = LoadLibrary("MyDLL");
if (hDLL != NULL)
{
   lpfnDllFunc1 = (LPFNDLLFUNC1)GetProcAddress(hDLL,
                                           "DLLFunc1");
   if (!lpfnDllFunc1)
   {
      // handle the error
      FreeLibrary(hDLL);
      return SOME_ERROR_CODE;
   }
   else
   {
      // call the function
      uReturnVal = lpfnDllFunc1(dwParam1, uParam2);
   }
}
```

**GetProcAddress**を呼び出すときに必要な関数を指定する方法は、DLL のビルド方法によって異なります。

リンク先の DLL がモジュール定義 (.def) ファイルでビルドされている場合、および DLL の .def ファイルの**export**セクションの関数と共に序数が列挙されている場合にのみ、エクスポート序数を取得できます。 関数名ではなく、エクスポート序数を使用して**GetProcAddress**を呼び出すと、エクスポート序数が dll のエクスポートテーブルへのインデックスとして機能するため、dll にエクスポートされた関数が多数ある場合は、少し高速になります。 エクスポート序数では、 **GetProcAddress**は、指定された名前を DLL の export テーブル内の関数名と比較するのではなく、関数を直接検索できます。 ただし、.def ファイル内のエクスポートされた関数に序数を割り当てることを制御できる場合にのみ、エクスポート序数を指定して**GetProcAddress**を呼び出す必要があります。

## <a name="what-do-you-want-to-do"></a>実行する操作

- [実行可能ファイルと DLL のリンク](linking-an-executable-to-a-dll.md#linking-implicitly)

- [実行可能ファイルと DLL のリンク](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>さらに詳しくは次のトピックをクリックしてください

- [LoadLibrary と AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)

- [FreeLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-freelibrary)

- [DEF ファイルを使った DLL からのエクスポート](exporting-from-a-dll-using-def-files.md)

## <a name="see-also"></a>関連項目

[Visual Studio での C/C++ Dll の作成](dlls-in-visual-cpp.md)
