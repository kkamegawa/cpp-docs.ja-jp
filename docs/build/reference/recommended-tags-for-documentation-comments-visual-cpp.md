---
title: ドキュメント コメント (C++ のドキュメントのコメント) 用の推奨タグ
ms.date: 11/04/2016
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
ms.openlocfilehash: 2a6a2c3983c10579a6cd96b69be81aa7df8b8ee7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319149"
---
# <a name="recommended-tags-for-documentation-comments"></a>ドキュメント コメントとして推奨されるタグ

MSVC コンパイラがコードのドキュメントのコメントを処理し、各のコンパイル単位の .xdc ファイルを作成し、xdcmake.exe は .xml ファイルに .xdc ファイルを処理します。 .xml ファイルを加工してドキュメントを作成することは、自分のサイトで実行する必要がある項目です。

型や型メンバーなどのコンストラクトでタグが処理されます。

タグは型やメンバーの直前に置く必要があります。

> [!NOTE]
>  ドキュメント コメントは名前空間に適用できず、プロパティやイベントのアウトオブライン定義に置くことはできません。ドキュメント コメントは、クラス内宣言に置く必要があります。

コンパイラは、有効な XML のタグをすべて処理します。 次のタグによって、ユーザー ドキュメントで一般的に使用される機能が与えられます。

||||
|-|-|-|
|[\<c>](c-visual-cpp.md)|[\<code>](code-visual-cpp.md)|[\<example>](example-visual-cpp.md)|
|[\<exception>](exception-visual-cpp.md)1|[\<include>](include-visual-cpp.md)1|[\<list>](list-visual-cpp.md)|
|[\<para>](para-visual-cpp.md)|[\<param>](param-visual-cpp.md)1|[\<paramref>](paramref-visual-cpp.md)1|
|[\<permission>](permission-visual-cpp.md)1|[\<remarks>](remarks-visual-cpp.md)|[\<returns>](returns-visual-cpp.md)|
|[\<see>](see-visual-cpp.md)1|[\<seealso>](seealso-visual-cpp.md)1|[\<summary>](summary-visual-cpp.md)|
|[\<value>](value-visual-cpp.md)|||

1. コンパイラによって構文が検証されます。

現在のリリースでは、MSVC コンパイラがサポートされていません`<paramref>`、他の Visual Studio コンパイラでサポートされているタグ。 Visual C++ では、将来のリリースで `<paramref>` がサポートされる可能性があります。

## <a name="see-also"></a>関連項目

[XML に関するドキュメント](xml-documentation-visual-cpp.md)