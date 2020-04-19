---
title: 有効期間
ms.date: 11/04/2016
helpviewer_keywords:
- local variables, lifetime
- variables, automatic
- storage classes, lifetime
- variables, lifetime
- automatic storage class
- automatic storage class, duration
- storage class specifiers, storage duration
- memory allocation, dynamic allocation
- functions [C++], lifetime
- storage duration
- dynamic memory allocation
- memory allocation, dynamic
- lifetime
- global variables, lifetime
ms.assetid: ff0b42cb-3f0f-49a3-a94f-d1d825d8ddfe
ms.openlocfilehash: 962e5ef4cae1be142091d2a209b4c60c0b789e74
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149441"
---
# <a name="lifetime"></a>有効期間

「有効期間」は、変数または関数が存在するプログラムが実行中である期間です。 識別子のストレージ存続期間でその有効期間が決まります。

*storage-class-specifier* **static** で宣言された識別子には、静的ストレージ存続期間があります。 静的ストレージ存続期間 ("グローバル" とも呼ばれます) のある識別子は、プログラムの実行期間中、ストレージと定義済みの値を持っています。 ストレージは予約されているため、識別子に格納されている値はプログラムの起動前に一度だけ初期化されます。 外部または内部リンケージで宣言される識別子には、静的ストレージ存続期間があります (「[リンケージ](../c-language/linkage.md)」を参照してください)。

**static** ストレージ クラス指定子なしで宣言される識別子には、関数の内部で宣言されている場合は自動ストレージ存続期間があります。 自動ストレージ存続期間のある識別子 ("ローカル識別子") は、識別子が定義または宣言されたブロック内でのみストレージと定義済みの値を持っています。 自動識別子は、プログラムがそのブロックに入るたびに新しいストレージが割り当てられ、プログラムがブロックを終了するとストレージ (および値) を失います。 リンケージのない関数で宣言された識別子にも、自動ストレージ存続期間があります。

次の規則で、識別子にグローバル (静的) な有効期間とローカル (自動的) な有効期間のどちらがあるかが指定されます。

- すべての関数には静的な有効期間があります。 したがって、関数はプログラムの実行中は常に存在しています。 外部レベル (つまり、関数定義と同じレベルのプログラム内のすべてのブロックの外側) で宣言された識別子にも、常にグローバル (静的) な有効期間があります。

- ローカル変数に初期化子がある場合、その変数は作成されるたびに初期化されます (**static** として宣言されていない場合)。 関数パラメーターには、ローカルな有効期間もあります。 宣言に **static** ストレージ クラス指定子を含めることにより、ブロック内の識別子のグローバルな有効期間を指定できます。 **static** として宣言されると、変数はブロックの 1 つのエントリから次のエントリまでその値を保持します。

グローバルな有効期間がある識別子は、ソース プログラムの実行中に常に存在していますが (たとえば、外部で宣言された変数や **static** キーワードで宣言されたローカル変数)、プログラムのすべての部分に表示されない場合があります。 可視性については、「[スコープと可視性](../c-language/scope-and-visibility.md)」を参照してください。非終端要素の *storage-class-specifier* については、「[ストレージ クラス](../c-language/c-storage-classes.md)」を参照してください。

`malloc` などの特別なライブラリ ルーチンを使用して作成された場合は、必要に応じて (動的に) メモリを割り当てることができます。 動的メモリ割り当てはライブラリ ルーチンを使用するため、言語の一部とは見なされません。 「*ランタイム ライブラリ リファレンス*」の [malloc](../c-runtime-library/reference/malloc.md) 関数を参照してください。

## <a name="see-also"></a>関連項目

[有効期間、スコープ、可視性、およびリンケージ](../c-language/lifetime-scope-visibility-and-linkage.md)
