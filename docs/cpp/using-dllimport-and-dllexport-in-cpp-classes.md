---
title: C++ クラスでの dllimport と dllexport の使用
ms.date: 11/04/2016
helpviewer_keywords:
- exporting classes [C++]
- declarations [C++], class
- exportable classes [C++]
- classes [C++], declaring
- classes [C++], exportable and inheritance
- inheritance [C++], exportable classes [C++]
- dllimport attribute [C++], classes
- declaring classes [C++]
- dllexport attribute [C++]
- dllexport attribute [C++], classes [C++]
ms.assetid: 8d7d1303-b9e9-47ca-96cc-67bf444a08a9
ms.openlocfilehash: b42ba7c1a88a4de28eb3385bbf6cad068abf1944
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857230"
---
# <a name="using-dllimport-and-dllexport-in-c-classes"></a>C++ クラスでの dllimport と dllexport の使用

**Microsoft 固有の仕様**

**Dllimport**属性またC++は**dllexport**属性を持つクラスを宣言できます。 これらの形式は、クラス全体がインポートまたはエクスポートされることを暗黙的に指定します。 この方法でエクスポートされたクラスは、エクスポート可能なクラスと呼ばれます。

次の例では、エクスポート可能なクラスを定義しています。 そのメンバー関数と静的データはすべてエクスポートされます。

```cpp
#define DllExport   __declspec( dllexport )

class DllExport C {
   int i;
   virtual int func( void ) { return 1; }
};
```

エクスポート可能なクラスのメンバーに対して**dllimport**属性と**dllexport**属性を明示的に使用することは禁止されています。

##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bdllexportclasses"></a>dllexport クラス

クラス**dllexport**を宣言すると、そのすべてのメンバー関数と静的データメンバーがエクスポートされます。 このようなすべてのメンバーは同じプログラム内で定義する必要があります。 定義しない場合は、リンカー エラーが生成されます。 この規則の例外は純粋仮想関数です。純粋仮想関数にはこのような明示的な定義は不要です。 ただし、抽象クラスのデストラクターは基底クラスのデストラクターによって常に呼び出されるため、純粋仮想デストラクターには常に明示的な定義が必要です。 これらの規則はエクスポート不可クラスに対しても同じであることに注意してください。

クラス型のデータまたはクラスを返す関数をエクスポートする場合、必ずそのクラスもエクスポートしてください。

##  <a name="_pluslang_dllexport_classesdllexportclasses"></a>dllimport クラス

**Dllimport**クラスを宣言すると、そのすべてのメンバー関数と静的データメンバーがインポートされます。 非クラス型での**dllimport**と**dllexport**の動作とは異なり、静的データメンバーは、 **dllimport**クラスが定義されている同じプログラム内で定義を指定することはできません。

##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2binheritanceandexportableclasses"></a>継承とエクスポート可能なクラス

エクスポート可能なクラスのすべての基底クラスはエクスポート可能である必要があります。 そうでない場合、コンパイラ警告が生成されます。 また、クラスでもあるアクセス可能なメンバーはすべてエクスポート可能である必要があります。 この規則により、 **dllexport**クラスは**dllimport**クラスを継承することが許可されます。また、この**クラスは、** **dllexport**クラスを継承することもできます (後者は推奨されません)。 一般的に、DLL のクライアントからアクセス可能な (C++ のアクセス規則に従って) すべてのものは、エクスポート可能なインターフェイスの一部である必要があります。 たとえば、インライン関数で参照されるプライベート データ メンバーなどです。

##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bselectivememberimportexport"></a>選択的メンバーのインポート/エクスポート

クラス内のメンバー関数と静的データは暗黙的に外部リンケージを持つため、クラス全体がエクスポートされない限り、 **dllimport**属性または**dllexport**属性を使用して宣言できます。 クラス全体をインポートまたはエクスポートする場合、 **dllimport**または**dllexport**としてメンバー関数とデータを明示的に宣言することは禁止されています。 クラス定義内で**dllexport**として静的データメンバーを宣言する場合、定義は、(非クラス外部リンケージと同様に) 同じプログラム内の任意の場所で実行する必要があります。

同様に、 **dllimport**属性または**dllexport**属性を使用してメンバー関数を宣言できます。 この場合は、同じプログラム内のどこかに**dllexport**定義を指定する必要があります。

選択的なメンバーのインポート/エクスポートには、次のいくつかの重要な点に注意してください。

- 選択的なメンバーのインポート/エクスポートは、より制限が厳しい、エクスポートされたクラス インターフェイスのバージョン (つまり、言語で許容されるよりも少ないパブリック機能およびプライベート機能を公開する DLL を設計できるバージョン) を提供する場合に最適です。 また、エクスポート可能なインターフェイスを最適化するためにも便利です。クライアントがプライベート データにアクセスできない場合は、もちろん、クラス全体をエクスポートする必要はありません。

- クラス内の 1 つの仮想関数をエクスポートする場合、それらの関数のすべてをエクスポートするか、少なくともクライアントが直接使用できるバージョンを提供する必要があります。

- 仮想関数で使用する選択的なメンバーのインポート/エクスポートを行うクラスがある場合、それらの関数はエクスポート可能なインターフェイスまたは定義済みインライン内 (クライアントから参照可能) にある必要があります。

- メンバーを**dllexport**として定義しても、クラス定義に含めない場合は、コンパイラエラーが生成されます。 クラスのヘッダーでメンバーを定義する必要があります。

- クラスメンバーの定義は**dllimport**または**dllexport**として許可されていますが、クラス定義で指定されているインターフェイスをオーバーライドすることはできません。

- 宣言したクラス定義の本体以外の場所でメンバー関数を定義した場合、関数が**dllexport**または**dllimport**として定義されている場合 (この定義がクラス宣言で指定されているものと異なる場合)、警告が生成されます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>参照

[dllexport、dllimport](../cpp/dllexport-dllimport.md)