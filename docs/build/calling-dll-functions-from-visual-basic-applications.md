---
title: DLL 関数の Visual Basic アプリケーションからの呼び出し方
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++], calling DLL functions from Visual Basic
- DLL functions [C++]
- function calls [C++], DLL functions
- DLLs [C++], calling
- calling DLL functions from VB applications [C++]
- __stdcall keyword [C++]
- DLL functions [C++], calling
ms.assetid: 282f7fbf-a0f2-4b9f-b277-1982710be56c
ms.openlocfilehash: 23b5692e28b9ea5b70c492e2564b8bf5385b1815
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221199"
---
# <a name="calling-dll-functions-from-visual-basic-applications"></a>DLL 関数の Visual Basic アプリケーションからの呼び出し方

Visual Basic アプリケーション (または Pascal、Fortran などの他の言語でのアプリケーション) の C と C++ の DLL で関数を呼び出すの関数をエクスポート正しい呼び出し規則を使用して、コンパイラによって装飾された名前なし

`__stdcall` は、関数の正しい呼び出し規則を作成します。つまり、呼び出された関数がスタックをクリアし、パラメーターは右から左へ渡されます。ただし、関数名は異なる方法で装飾されます。 したがって、**方式**使用 DLL でエクスポートされた関数の装飾名がエクスポートされます。

`__stdcall`名前の装飾をアンダー スコアでシンボル名のプレフィックス ( **\_** ) のシンボルを追加し、アット マーク (**\@**) 文字の数が続く引数リスト (必要なスタック空間) のバイト数。 結果として、宣言時の関数は次のようになります。

```C
int __stdcall func (int a, double b)
```

装飾すると、`_func@12`出力します。

C の呼び出し規則 (`__cdecl`) による装飾では、名前は `_func` となります。

装飾名を取得する[/map](reference/map-generate-mapfile.md)します。 使用**方式**は次の処理します。

- C 呼び出し規則と関数をエクスポートするかどうか (`__cdecl`)、先頭にアンダー スコアを除去 ( **\_** ) 名前がエクスポートされます。

- エクスポートされる関数が C の呼び出し規則を使わない場合 (`__stdcall` など) は、装飾名がエクスポートされます。

スタックがクリアされた場所をオーバーライドする方法はないので、`__stdcall` を使う必要があります。 `__stdcall` を使って装飾を外すには、.def ファイルの EXPORTS セクションにエイリアスを使って、その名前を指定する必要があります。 関数宣言の例を次に示します。

```C
int  __stdcall MyFunc (int a, double b);
void __stdcall InitCode (void);
```

.DEF ファイルの内容は、次のとおりです。

```
EXPORTS
   MYFUNC=_MyFunc@12
   INITCODE=_InitCode@0
```

Visual Basic で書かれたプログラムから DLL を呼び出す場合は、ここで示したエイリアスの手法を .def ファイル内で使用する必要があります。 エイリアスが Visual Basic プログラムの中で宣言されている場合は、.def ファイル内でのエイリアスは不要です。 エイリアス句を追加することで、Visual Basic プログラムで行うことができます、 [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement)ステートメント。

## <a name="what-do-you-want-to-know-more-about"></a>さらに詳しくは次のトピックをクリックしてください

- [DLL からのエクスポート](exporting-from-a-dll.md)

- [使用して、DLL からエクスポートしています。DEF ファイル](exporting-from-a-dll-using-def-files.md)

- [関数を使った DLL からエクスポートします。](exporting-from-a-dll-using-declspec-dllexport.md)

- [C 言語の実行可能ファイルで使用するための C++ 関数をエクスポートします。](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [エクスポート方式の使用](determining-which-exporting-method-to-use.md)

- [装飾名](reference/decorated-names.md)

## <a name="see-also"></a>関連項目

[Visual Studio で C/C++ Dll を作成します。](dlls-in-visual-cpp.md)
