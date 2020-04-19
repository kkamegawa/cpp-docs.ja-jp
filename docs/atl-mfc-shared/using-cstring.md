---
title: CString の使用
ms.date: 06/18/2018
helpviewer_keywords:
- CString objects, C++ string manipulation
- CString objects, reference counting
- CString class (Visual C++)
ms.assetid: ed018aaf-8b10-46f9-828c-f9c092dc7609
ms.openlocfilehash: a84ae21b60d87971cb2f7b758dd369b4078607e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62199210"
---
# <a name="using-cstring"></a>CString の使用

このセクションのトピックでは、`CString` を使用したプログラミング方法について説明します。 に関するリファレンス ドキュメント、`CString`クラス、ドキュメントを参照して[CStringT](../atl-mfc-shared/reference/cstringt-class.md)します。

`CString` を使用するには、`atlstr.h` ヘッダーをインクルードします。

`CString`、 `CStringA`、および`CStringW`クラスと呼ばれるクラス テンプレートの特殊化は、 [CStringT](../atl-mfc-shared/reference/cstringt-class.md)サポートする、文字データの種類に基づきます。

A`CStringW`オブジェクトが含まれています、 **wchar_t**を入力し、Unicode 文字列がサポートされます。 A`CStringA`オブジェクトが含まれています、 **char**型、およびサポートするシングル バイト文字とマルチバイト (MBCS) 文字列。 A`CString`オブジェクトがサポートするか、 **char**型または`wchar_t`MBCS シンボルまたは UNICODE 記号はコンパイル時に定義されているかどうかに応じて、種類。

`CString` オブジェクトは、`CStringData` オブジェクトの文字データを保持します。 `CString` NULL で終わる C スタイルの文字列を受け入れます。 `CString` 文字列の追跡のパフォーマンスを向上させることが、長さも LPCWSTR への変換をサポートするために格納されている文字データに NULL 文字を保持します。 `CString` C スタイルの文字列をエクスポートする場合、null 終端文字が含まれます。 その他の場所に NULL を挿入できる、 `CString`、予期しない結果が生じる。

文字列クラス `CAtlString`、`CAtlStringA`、および `CAtlStringW` は、CRT サポートがある場合もない場合も、MFC ライブラリにリンクせずに使用できます。

`CString` は、ネイティブ プロジェクトで使用されます。 マネージ コード (C++/CLI) プロジェクトの場合は、`System::String` を使用します。

`CString`、`CStringA`、または `CStringW` で現在提供されているよりも多くの機能を追加するには、追加機能を含む `CStringT` のサブクラスを作成する必要があります。

次のコードは、`CString` を作成して標準出力に表示する方法を示しています。

```cpp
#include <atlstr.h>

int main() {
    CString aCString = CString(_T("A string"));
    _tprintf(_T("%s"), (LPCTSTR) aCString);
}
```

## <a name="in-this-section"></a>このセクションの内容

[CString の基本操作](../atl-mfc-shared/basic-cstring-operations.md)<br/>
C リテラル文字列からのオブジェクトの作成、`CString` 内の個々の文字へのアクセス、2 つのオブジェクトの連結、`CString` オブジェクトの比較など、`CString` の基本操作について説明します。

[文字列データ管理](../atl-mfc-shared/string-data-management.md)<br/>
`CString` での Unicode と MBCS の使用について説明します。

[CString セマンティクス](../atl-mfc-shared/cstring-semantics.md)<br/>
`CString` オブジェクトの使用方法について説明します。

[C スタイルの文字列に関連する CString の操作方法](../atl-mfc-shared/cstring-operations-relating-to-c-style-strings.md)<br/>
C スタイルの null で終わる文字列のように `CString` オブジェクトの内容を操作する方法について説明します。

[BSTR 用のメモリの割り当てと解放](../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md)<br/>
BSTR および COM オブジェクトのメモリの使用について説明します。

[CString の例外の後処理](../atl-mfc-shared/cstring-exception-cleanup.md)<br/>
MFC 3.0 以降で明示的な後処理が不要になったことについて説明します。

[CString 引数の渡し方](../atl-mfc-shared/cstring-argument-passing.md)<br/>
CString オブジェクトを関数に渡す方法と関数から `CString` オブジェクトを返す方法について説明します。

[Unicode とマルチバイト文字セット (MBCS: Multibyte Character Set) のサポート](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)<br/>
MFC で Unicode と MBCS をサポートできるようにする方法について説明します。

## <a name="reference"></a>参照

[CStringT](../atl-mfc-shared/reference/cstringt-class.md)<br/>
`CStringT` クラスに関するリファレンス情報を提供します。

[CSimpleStringT クラス](../atl-mfc-shared/reference/csimplestringt-class.md)<br/>
`CSimpleStringT` クラスに関するリファレンス情報を提供します。

## <a name="related-sections"></a>関連項目

[文字列 (ATL と MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
文字列データを管理する複数の方法について説明したトピックへのリンクが含まれています。

[文字列 (ATL と MFC)](../atl-mfc-shared/strings-atl-mfc.md)
