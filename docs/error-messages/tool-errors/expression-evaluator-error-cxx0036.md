---
title: 式エバリュエーター エラー CXX0036
ms.date: 11/04/2016
f1_keywords:
- CXX0036
helpviewer_keywords:
- CXX0036
- CAN0036
ms.assetid: 383404be-df5b-4eec-b113-df21bb5d269d
ms.openlocfilehash: d7961d92760cc5ac325b4bc9f187d4ee2298479a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397030"
---
# <a name="expression-evaluator-error-cxx0036"></a>式エバリュエーター エラー CXX0036

bad context {...} specification

このメッセージは、コンテキスト演算子の使用中のいくつかのエラーのいずれかで生成されることができます (**{}**)。

- コンテキスト演算子の構文 (**{}**) 指定されました。

   コンテキスト演算子の構文です。

     {*function*,*module*,*dll*}*expression*

   コンテキストを指定しますこの*式*します。 コンテキスト演算子は、型キャストと同じ優先順位と使用状況が。

   末尾のコンマは省略できます。 いずれか*関数*、*モジュール*、または*dll*リテラルのコンマを含む名前全体をかっこで囲む必要があります。

- 関数名の綴りが間違って、または、指定されたモジュールまたはダイナミック リンク ライブラリに存在しません。

   C は大文字小文字を区別する言語のため*関数*ソースで定義されている大文字小文字の区別で指定する必要があります。

- モジュールまたは DLL が見つかりませんでした。

   指定されたモジュールまたは DLL の完全なパス名を確認します。

このエラーは、can0036 と同じものと同じです。