---
title: selectany
ms.date: 11/04/2016
f1_keywords:
- selectany_cpp
helpviewer_keywords:
- __declspec keyword [C++], selectany
- selectany __declspec keyword
ms.assetid: 9c353017-5a42-4f50-b741-bd13da1ce84d
ms.openlocfilehash: a6bf4076dfecbd29035716285f52c0a9faf81067
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62267298"
---
# <a name="selectany"></a>selectany

**Microsoft 固有の仕様**

宣言されたグローバル データ項目 (変数またはオブジェクト) が pick-any COMDAT (パッケージ化された関数) であることをコンパイラに指示します。

## <a name="syntax"></a>構文

```
__declspec( selectany ) declarator
```

## <a name="remarks"></a>Remarks

リンク時、COMDAT の複数の定義が見つかった場合、リンカーは 1 つを選択し、残りを破棄します。 場合、リンカー オプション[/OPT:REF](../build/reference/opt-optimizations.md) (最適化) が選択されている場合は、中間 COMDAT 除去が発生してリンカー出力のすべての参照されないデータ項目を削除し、します。

コンストラクター、および宣言におけるグローバル関数または静的メソッドによる代入は参照を作成しないため、/OPT:REF による削除が妨げられません。 このようなコードからの副作用は、データへの他の参照が存在しない時期によって決まりません。

動的に初期化されると、グローバル オブジェクト、 **selectany**未参照のオブジェクトの初期化コードもが破棄されます。

グローバル データ項目は、一度だけ EXE または DLL プロジェクトで正常に初期化できます。 **selectany** 1 つ以上のソース ファイルに同じヘッダーが表示されたら、ヘッダーで定義されたグローバル データの初期化に使用されることができます。 **selectany**は C および C++ の両方のコンパイラで使用できます。

> [!NOTE]
>  **selectany**は外部から参照するグローバル データ項目の実際の初期化にのみ適用できます。

## <a name="example"></a>例

このコードは、使用する方法を示します、 **selectany**属性。

```cpp
//Correct - x1 is initialized and externally visible
__declspec(selectany) int x1=1;

//Incorrect - const is by default static in C++, so
//x2 is not visible externally (This is OK in C, since
//const is not by default static in C)
const __declspec(selectany) int x2 =2;

//Correct - x3 is extern const, so externally visible
extern const __declspec(selectany) int x3=3;

//Correct - x4 is extern const, so it is externally visible
extern const int x4;
const __declspec(selectany) int x4=4;

//Incorrect - __declspec(selectany) is applied to the uninitialized
//declaration of x5
extern __declspec(selectany) int x5;

// OK: dynamic initialization of global object
class X {
public:
X(int i){i++;};
int i;
};

__declspec(selectany) X x(1);
```

## <a name="example"></a>例

このコードは、使用する方法を示します、 **selectany**データ COMDAT の圧縮も使用するとことを確認する属性、 [/OPT:ICF](../build/reference/opt-optimizations.md)リンカー オプション。 データをマークする必要がありますに注意してください。 **selectany**に置かれていると、 **const** (読み取り専用) セクション。 読み取り専用セクションを明示的に指定する必要があります。

```cpp
// selectany2.cpp
// in the following lines, const marks the variables as read only
__declspec(selectany) extern const int ix = 5;
__declspec(selectany) extern const int jx = 5;
int main() {
   int ij;
   ij = ix + jx;
}
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[__declspec](../cpp/declspec.md)<br/>
[キーワード](../cpp/keywords-cpp.md)