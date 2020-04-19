---
title: code_seg (__declspec)
ms.date: 11/04/2016
f1_keywords:
- code_seg_cpp
helpviewer_keywords:
- code_seg __declspec keyword
ms.assetid: ad3c1105-15d3-4e08-b7b9-e4bd9d7b6aa0
ms.openlocfilehash: a0b9c6dcd7ee19af59ac39a71498fe41bfc107ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62216555"
---
# <a name="codeseg-declspec"></a>code_seg (__declspec)

**Microsoft 固有の仕様**

**Code_seg**宣言の属性名、関数またはクラス メンバー関数のオブジェクト コードの格納される .obj ファイル内の実行可能なテキスト セグメント。

## <a name="syntax"></a>構文

```
__declspec(code_seg("segname")) declarator
```

## <a name="remarks"></a>Remarks

`__declspec(code_seg(...))` 属性では、メモリ内でそれぞれページングまたはロックできる個別の名前のセグメントにコードを格納できます。 この属性を使用して、インスタンス化されたテンプレートとコンパイラによって生成されたコードの格納場所を制御できます。

A*セグメント*単位としてメモリに読み込まれた .obj ファイル内のデータの名前付きブロックです。 A*テキスト セグメント*は実行可能コードを含むセグメントです。 用語*セクション*用いセグメントを持つ。

`declarator` が定義されているときに生成されるオブジェクト コードは、ナロー文字列リテラルである `segname` で指定されたテキスト セグメントに格納されます。 名前`segname`で指定する必要はありません、[セクション](../preprocessor/section.md)プラグマ、宣言で使用できる前にします。 既定では、`code_seg` が指定されていないと、オブジェクト コードは .text という名前のセグメントに格納されます。 A **code_seg**属性は、既存のすべてのよりも優先されます。 [#pragma code_seg](../preprocessor/code-seg.md)ディレクティブ。 A **code_seg**属性のメンバー関数に適用される上書きされます**code_seg**外側のクラスに適用される属性。

エンティティがある場合、 **code_seg**属性では、すべての宣言と同じエンティティの定義が同じあります**code_seg**属性。 基底クラスがある場合、 **code_seg**派生した属性クラスは、同じ属性を持つ必要があります。

ときに、 **code_seg**属性が名前空間スコープ関数またはメンバー関数に適用されて、その関数のオブジェクト コードは、指定されたテキスト セグメントに配置されます。 この属性がクラスに適用されると、そのクラスおよび入れ子にされたクラスのメンバー関数はすべて (コンパイラによって生成された特殊なメンバー関数も含めて)、指定されたセグメントに格納されます。 ローカルで定義されたクラス、メンバー関数の本体で定義されたクラスなど-を継承しません、 **code_seg**外側のスコープの属性。

ときに、 **code_seg**テンプレート クラスまたはテンプレート関数に属性が適用される、テンプレートのすべての暗黙的な特殊化は、指定されたセグメントに配置されます。 明示的または部分的な特殊化を継承しません、 **code_seg**プライマリ テンプレートからの属性。 同じ、または別に指定することがあります**code_seg**特殊化での属性。 A **code_seg**属性は、明示的なテンプレート インスタンス化に適用することはできません。

既定では、コンパイラによって生成されたコード (特殊なメンバー関数など) は .text セグメントに格納されます。 `#pragma code_seg` ディレクティブは、この既定をオーバーライドしません。 使用して、 **code_seg**クラス、クラス テンプレート、またはコンパイラによって生成されたコードの格納場所を制御する関数テンプレートでの属性。

ラムダの継承**code_seg**その外側のスコープからの属性。 ラムダのセグメントを指定するには、適用、 **code_seg**属性パラメーター宣言句の後と前に、変更可能な例外の指定、any 後続の戻り値の型指定や、ラムダの本体。 詳細については、次を参照してください。[ラムダ式の構文](../cpp/lambda-expression-syntax.md)します。 この例では、ラムダを PagedMem という名前のセグメントに定義しています。

```cpp
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };
```

特定のメンバー関数 (特に仮想メンバー関数) を異なるセグメントに格納するときには注意が必要です。 ページング セグメントに存在する派生クラスの仮想関数を定義する場合、基底クラスのメソッドが非ページング セグメントに存在すると、他の基底クラスのメソッドやユーザー コードは、仮想メソッドの呼び出しによりページ フォールトがトリガーされないと見なすことがあります。

## <a name="example"></a>例

この例ではどのように、 **code_seg**格納時に暗黙的なセグメントを属性の制御と明示的なテンプレート特殊化の使用します。

```cpp
// code_seg.cpp
// Compile: cl /EHsc /W4 code_seg.cpp

// Base template places object code in Segment_1 segment
template<class T>
class __declspec(code_seg("Segment_1")) Example
{
public:
   virtual void VirtualMemberFunction(T /*arg*/) {}
};

// bool specialization places code in default .text segment
template<>
class Example<bool>
{
public:
   virtual void VirtualMemberFunction(bool /*arg*/) {}
};

// int specialization places code in Segment_2 segment
template<>
class __declspec(code_seg("Segment_2")) Example<int>
{
public:
   virtual void VirtualMemberFunction(int /*arg*/) {}
};

// Compiler warns and ignores __declspec(code_seg("Segment_3"))
// in this explicit specialization
__declspec(code_seg("Segment_3")) Example<short>; // C4071

int main()
{
   // implicit double specialization uses base template's
   // __declspec(code_seg("Segment_1")) to place object code
   Example<double> doubleExample{};
   doubleExample.VirtualMemberFunction(3.14L);

   // bool specialization places object code in default .text segment
   Example<bool> boolExample{};
   boolExample.VirtualMemberFunction(true);

   // int specialization uses __declspec(code_seg("Segment_2"))
   // to place object code
   Example<int> intExample{};
   intExample.VirtualMemberFunction(42);
}
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[__declspec](../cpp/declspec.md)<br/>
[キーワード](../cpp/keywords-cpp.md)