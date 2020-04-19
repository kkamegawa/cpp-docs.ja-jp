---
title: モジュール定義 (.def) ファイル
ms.date: 11/04/2016
helpviewer_keywords:
- def files
- module definition files
- .def files
ms.assetid: 08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8
ms.openlocfilehash: 0047f24722644cd9a68bbbf827ced26ad085d4c1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321229"
---
# <a name="module-definition-def-files"></a>モジュール定義 (.def) ファイル

モジュール定義 (.def) ファイルは、エクスポート、属性、およびその他の情報をリンクできるプログラムの詳細については、リンカーを提供します。 .Def ファイルは、DLL を構築する際に最も役立ちます。 あるため、 [MSVC リンカー オプション](linker-options.md)使用できるモジュール定義ステートメントではなく .def ファイルは通常必要ありません。 使用することも[方式](../exporting-from-a-dll-using-declspec-dllexport.md)エクスポートされた関数を指定する方法として。

リンカーのフェーズ中に .def ファイルを呼び出すことができます、 [/DEF (モジュール定義ファイルの指定)](def-specify-module-definition-file.md)リンカー オプション。

エクスポートを持たない .exe ファイルを作成する場合、.def ファイルを使用すると、出力ファイルの大規模かつ低速の読み込みが作成されます。

例については、次を参照してください。 [DEF ファイルを使用する DLL からエクスポート](../exporting-from-a-dll-using-def-files.md)します。

詳細については、次のセクションを参照してください。

- [モジュール定義ステートメントに関する規則](rules-for-module-definition-statements.md)

- [エクスポート](exports.md)

- [ヒープサイズ](heapsize.md)

- [ライブラリ](library.md)

- [NAME](name-c-cpp.md)

- [セクション](sections-c-cpp.md)

- [スタックサイズ](stacksize.md)

- [スタブ](stub.md)

- [バージョン](version-c-cpp.md)

- [予約語](reserved-words.md)

## <a name="see-also"></a>関連項目

[C/C++ ビルドのリファレンス](c-cpp-building-reference.md)<br/>
[MSVC リンカー オプション](linker-options.md)
