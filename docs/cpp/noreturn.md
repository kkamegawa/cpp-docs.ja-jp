---
title: noreturn
ms.date: 11/04/2016
f1_keywords:
- noreturn_cpp
helpviewer_keywords:
- __declspec keyword [C++], noreturn
- noreturn __declspec keyword
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
ms.openlocfilehash: f9ca61c9d734ccdd6b8d8374ed3a7c4128ee3d5e
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857373"
---
# <a name="noreturn"></a>noreturn

**Microsoft 固有の仕様**

この **__declspec**属性は、関数がを返さないことをコンパイラに指示します。 その結果、コンパイラは、 **__declspec (noreturn)** 関数の呼び出しに続くコードに到達できないことを認識します。

コンパイラで値を返さないコントロール パスの関数が検出されると、警告 (C4715) またはエラー メッセージ (C2202) が生成されます。 返されることのない関数によってコントロールパスに到達できない場合は、 **__declspec (noreturn)** を使用して、この警告またはエラーを回避できます。

> [!NOTE]
>  返されると予想される関数に **__declspec (noreturn)** を追加すると、未定義の動作が発生する可能性があります。

## <a name="example"></a>使用例

次の例では、 **else**句に return ステートメントが含まれていません。  `fatal` を **__declspec (noreturn)** として宣言すると、エラーまたは警告メッセージが表示されなくなります。

```cpp
// noreturn2.cpp
__declspec(noreturn) extern void fatal () {}

int main() {
   if(1)
     return 1;
   else if(0)
     return 0;
   else
     fatal();
}
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>参照

[__declspec](../cpp/declspec.md)<br/>
[キーワード](../cpp/keywords-cpp.md)