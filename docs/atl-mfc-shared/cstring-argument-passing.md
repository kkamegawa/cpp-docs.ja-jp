---
title: CString 引数の渡し方
ms.date: 11/04/2016
helpviewer_keywords:
- strings [C++], as function input/output
- argument passing [C++]
- arguments [C++], passing
- functions [C++], strings as input/output
- argument passing [C++], C strings
- passing arguments, C strings
- CString objects, passing arguments
- string arguments
ms.assetid: a67bebff-edf1-4cf4-bbff-d1cc6a901099
ms.openlocfilehash: 1729167786d71c107fe6a4369d5a0c7e7c8594f1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62236386"
---
# <a name="cstring-argument-passing"></a>CString 引数の渡し方

この記事に渡す方法を説明します[CString](../atl-mfc-shared/reference/cstringt-class.md)オブジェクトを返す方法と関数を`CString`関数からのオブジェクト。

##  <a name="_core_cstring_argument.2d.passing_conventions"></a> CString 引数渡し規約

クラス インターフェイスを定義するときに、メンバー関数の引数渡し規約を決定する必要があります。 受け渡しおよび返却のいくつかの標準的なルールがある`CString`オブジェクト。 説明されている規則に従う場合[関数の入力として文字列](#_core_strings_as_function_inputs)と[文字列関数の出力として](#_core_strings_as_function_outputs)、効率的で適切なコードが必要です。

##  <a name="_core_strings_as_function_inputs"></a> 関数の入力として文字列

使用する最も効率的で安全な方法を`CString`呼び出された関数でオブジェクトが渡す、`CString`関数オブジェクト。 その名前にかかわらず、`CString`オブジェクト、として保存されません文字列内部的には null 終端文字を含む C スタイル文字列。 代わりに、`CString`オブジェクトを追跡がある文字の数。 ある`CString`少量の作業することが重要なは、常にそのコードがある場合になり、null で終わる文字列への LPCTSTR ポインターを提供します。 変更を加えたために、結果は一時的なもの、`CString`内容 LPCTSTR ポインターの古いコピーが無効になります。

場合によっては、C スタイル文字列を指定させることです。 たとえば、呼び出された関数が C で記述しでサポートされないオブジェクトの状況があります。 この場合、強制、 `CString` LPCTSTR、および関数にパラメーターは、C スタイルの null で終わる文字列を取得します。 他の方向を移動し、作成できます、`CString`オブジェクトを使用して、 `CString` C スタイル文字列パラメーターを受け取るコンス トラクター。

文字列の内容が、関数によって変更される場合は、宣言のパラメーターは非定数の`CString`参照 (`CString&`)。

##  <a name="_core_strings_as_function_outputs"></a> 文字列関数の出力として

通常に戻ることができます`CString`ために、関数からオブジェクト`CString`オブジェクトがプリミティブ型と同様に、値セマンティクスに従います。 読み取り専用文字列を取得するには、定数を使用`CString`参照 (`const CString&`)。 使用例を次に示します`CString`パラメーターと戻り値の型。

[!code-cpp[NVC_ATLMFC_Utilities#197](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_1.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#198](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_2.cpp)]

## <a name="see-also"></a>関連項目

[文字列 (ATL と MFC)](../atl-mfc-shared/strings-atl-mfc.md)
