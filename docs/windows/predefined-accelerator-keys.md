---
title: アクセラレータ キー (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.accelerator
helpviewer_keywords:
- accelerator keys
- keyboard shortcuts
- keyboard shortcuts [C++], predefined
- menus [C++], shortcut keys
- keyboard shortcuts [C++], menu association
ms.assetid: f234c5f2-4ec3-4c9e-834a-b5dd297625b9
ms.openlocfilehash: 1e87d80b8995760eecda34334dab702480bd9669
ms.sourcegitcommit: 5beace7dcc6bf0e8b8cc96a930e7424f9daa05cb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2019
ms.locfileid: "55232124"
---
# <a name="accelerator-keys-c"></a>アクセラレータ キー (C++)

マネージ プロジェクトにリソースを追加する方法については、次を参照してください。 [Resources in Desktop Apps](/dotnet/framework/resources/index)で、 *.NET Framework 開発者ガイド*します。

## <a name="predefined-accelerator-keys"></a>定義済みのアクセラレータ キー

Windows アプリケーション プロジェクトの一部として使用できるいくつかの定義済みのアクセラレータ キーがあります。 これらの仮想キーの一部は、Windows 環境用です。 その他の仮想キーは、ブラウザーや Unicode アプリケーションで使用できます。 どのアクセラレータでもこれらのキーを使用できます。

|キー|説明|
|---------|-----------------|
|VK_ACCEPT|IME 使用可能|
|VK_BROWSER_BACK|Windows の場合:ブラウザーの戻るキー|
|VK_BROWSER_FAVORITES|Windows の場合:ブラウザーのお気に入りキー|
|VK_BROWSER_FORWARD|Windows の場合:ブラウザーの進むキー|
|VK_BROWSER_HOME|Windows の場合:ブラウザーの起動とホーム キー|
|VK_BROWSER_REFRESH|Windows の場合:更新キー|
|VK_BROWSER_SEARCH|Windows の場合:ブラウザーの検索キー|
|VK_BROWSER_STOP|Windows の場合:ブラウザーの停止キー|
|VK_CONVERT|IME 変換|
|VK_FINAL|IME Final モード|
|VK_HANGUEL|IME ハングル モード (互換性のために残されています。VK_HANGUL を使用してください) |
|VK_HANGUL|IME ハングル モード|
|VK_HANJA|IME Hanja モード|
|VK_JUNJA|IME Junja モード|
|VK_KANA|IME かなモード|
|VK_KANJI|IME 漢字モード|
|VK_LAUNCH_APP1|Windows の場合:アプリケーション 1 のキーを開始します。|
|VK_LAUNCH_APP2|Windows の場合:アプリケーション 2 のキーを開始します。|
|VK_LAUNCH_MAIL|Windows の場合:メールのキーを開始します。|
|VK_LAUNCH_MEDIA_SELECT|Windows の場合:メディア キーを選択します。|
|VK_LCONTROL|左 Ctrl キー|
|VK_LMENU|左 Alt キー|
|VK_LSHIFT|左 Shift キー|
|VK_MEDIA_NEXT_TRACK|Windows の場合:次のトラック キー|
|VK_MEDIA_PLAY_PAUSE|Windows の場合:メディアの再生/一時停止キー|
|VK_MEDIA_PREV_TRACK|Windows の場合:前のトラック キー|
|VK_MEDIA_STOP|Windows の場合:メディア キーを停止します。|
|VK_MODECHANGE|IME モード変更要求|
|VK_NONCONVERT|IME 無変換|
|VK_OEM_1|Windows の場合:米国標準キーボードの ';:' キー|
|VK_OEM_102|Windows の場合:山かっこキーまたは RT 102 key キーボードの円記号キー|
|VK_OEM_2|Windows の場合:米国標準キーボードの「/?」 key|
|VK_OEM_3|Windows の場合:米国標準キーボードの ' ~' キー|
|VK_OEM_4|Windows の場合:米国標準キーボードの ' [{' キー|
|VK_OEM_5|Windows の場合:米国標準キーボードの '\\&#124;' キー|
|VK_OEM_6|Windows の場合:米国標準キーボードの ']}' キー|
|VK_OEM_7|Windows の場合:米国標準キーボードの"1 つの引用符と二重引用符"キー|
|VK_OEM_COMMA|Windows の場合:すべての国/地域、',' のキーの|
|VK_OEM_MINUS|Windows の場合:すべての国/地域、'-' キー|
|VK_OEM_PERIOD|Windows の場合:すべての国/地域、'.' キー|
|VK_OEM_PLUS|Windows の場合:すべての国/地域、'+' キー|
|VK_PACKET|Windows の場合:キーボード操作している場合に、Unicode 文字を渡すために使用します。|
|VK_RCONTROL|右 Ctrl キー|
|VK_RMENU|右 Alt キー|
|VK_RSHIFT|右 Shift キー|
|VK_SLEEP|コンピューターのスリープ キー|
|VK_VOLUME_DOWN|Windows の場合:音量下げるキー|
|VK_VOLUME_MUTE|Windows の場合:音量ミュート キー|
|VK_VOLUME_UP|Windows の場合:音量上げるキー|
|VK_XBUTTON1|Windows の場合:X1 マウス ボタン|
|VK_XBUTTON2|Windows の場合:X2 マウス ボタン|

## <a name="associating-an-accelerator-key-with-a-menu-item"></a>アクセラレータ キーとメニュー項目との関連付け

メニュー項目とキーボードの組み合わせで同じプログラム コマンドを発行したいと思うことはよくあります。 これを行うには、メニュー項目とアプリケーションのアクセラレータ テーブル内のエントリに同じリソース識別子 (ID) を割り当てます。 次に、メニュー項目のキャプションを編集して、アクセラレータの名前を表示します。 メニュー項目とアクセラレータ キーの詳細については、次を参照してください。[アクセラレータ キーとメニュー項目の関連付け](../windows/associating-a-menu-command-with-an-accelerator-key.md)します。

## <a name="requirements"></a>必要条件

Win32

## <a name="see-also"></a>関連項目

[アクセラレータ エディター](../windows/accelerator-editor.md)<br/>
[リソース エディター](../windows/resource-editors.md)
