---
title: ファイルを開く
ms.date: 11/04/2016
helpviewer_keywords:
- Open member functions [MFC]
- CFile class [MFC], variable
- opening files, in MFC
- Open calls [MFC]
- Open method, CFile class [MFC]
- examples [MFC], opening files
- opening files, handling exceptions
- exception handling [MFC], when opening files
- files [MFC], opening
- file objects [MFC]
- MFC, file operations
- opening files [MFC]
- exception handling [MFC], opening files
ms.assetid: a991b8ec-b04a-4766-b47e-7485b5dd0b01
ms.openlocfilehash: dab7a680d9b33a6e334da99a045b709fe00f215c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394482"
---
# <a name="opening-files"></a>ファイルを開く

Mfc では、ファイルを開く最も一般的な方法は、2 段階プロセスです。

#### <a name="to-open-a-file"></a>ファイルを開く

1. パスまたはアクセス許可フラグを指定せず、ファイル オブジェクトを作成します。

   宣言することで、通常、ファイル オブジェクトを作成する、 [CFile](../mfc/reference/cfile-class.md)スタック フレームで変数。

1. 呼び出す、[オープン](../mfc/reference/cfile-class.md#open)パスとアクセス許可フラグを指定して、ファイル オブジェクトのメンバー関数。

   戻り値`Open`ファイルが正常に開かれている場合、0 以外の値または 0 になる場合は、指定したファイルを開くことができませんでした。 `Open`メンバー関数は、次のようにプロトタイプ宣言。

   `virtual BOOL Open( LPCTSTR lpszFileName, UINT nOpenFlags, CFileException* pError = NULL );`

   フラグがなど、アクセス許可を指定するファイルの読み取り専用です。 内の列挙型定数として可能なフラグの値が定義されている、`CFile`で修飾されるため、クラス"`CFile::`"うに`CFile::modeRead`します。 使用して、`CFile::modeCreate`ファイルを作成する場合にフラグを設定します。

次の例では、(前のファイルはすべて同じパスに置き換えて)、読み取り/書き込み権限を持つ新しいファイルを作成する方法を示します。

[!code-cpp[NVC_MFCFiles#1](../atl-mfc-shared/reference/codesnippet/cpp/opening-files_1.cpp)]

> [!NOTE]
>  この例では、作成し、ファイルを開きます。 問題がある場合、`Open`呼び出しを返すことができます、`CFileException`次に示すように、最後のパラメーター オブジェクトします。 TRACE マクロは、ファイル名とエラーの理由を示すコードの両方を出力します。 呼び出すことができます、`AfxThrowFileException`エラー報告の詳細が必要な場合に機能します。

## <a name="see-also"></a>関連項目

[CFile クラス](../mfc/reference/cfile-class.md)<br/>
[CFile::Open](../mfc/reference/cfile-class.md#open)<br/>
[ファイル](../mfc/files-in-mfc.md)
