---
title: 致命的なエラー C1128
ms.date: 11/04/2016
f1_keywords:
- C1128
helpviewer_keywords:
- C1128
ms.assetid: 6f9580fd-ecef-48be-9780-dcf666704279
ms.openlocfilehash: bb1d9af10084d6b3e75325450c7f13ea1683ee2e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62229047"
---
# <a name="fatal-error-c1128"></a>致命的なエラー C1128

セクションの数がオブジェクト ファイル形式の制限を超えています : /bigobj と共にコンパイルしてください

.obj ファイルが、許容されるセクション数である COFF オブジェクト ファイル形式制限を超えました。

このセクション制限に到達できるを使用した結果[/Gy](../../build/reference/gy-enable-function-level-linking.md)とデバッグ ビルドです。**/Gy**により、関数に独自の COMDAT セクションに移動します。 デバッグ ビルドには、各 COMDAT 関数のデバッグ情報セクションがあります。

C1128 エラーは、インライン関数が多すぎることが原因で発生することもあります。

このエラーを修正するには、ソース ファイルを複数のソース コード ファイルに分割、なしでコンパイル **/Gy**を使用してコンパイル[/bigobj (セクション数を増やすので。Obj ファイル)](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md)します。  せずにコンパイルする場合 **/Gy**、個別に、最適化を指定する必要がありますので **/O2**と **/O1**両方を意味 **/Gy**します。

可能であれば、デバッグ情報なしでコンパイルしてください。

また、テンプレートの固有のインスタンス化をコンパイラで出力するのではなく、別のソース コード ファイルにこれらを指定する必要もあります。

コードを移植するときに c1128 が最初に、x64 を使用する場合、コンパイラおよび x86 でコンパイラ。 x64 には、コンパイルされた各関数に関連付けられている少なくとも 4 つのセクションがある **/Gy**テンプレートまたはクラス インラインからインライン化: コード、pdata、およびデバッグ情報、および xdata の可能性があります。  X86 は pdata を持ちません。