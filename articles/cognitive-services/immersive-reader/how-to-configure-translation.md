---
title: 翻訳を構成する
titleSuffix: Azure Cognitive Services
description: この記事では、翻訳のさまざまなオプションを構成する方法について説明します。
author: metanMSFT
manager: guillasi
ms.service: cognitive-services
ms.subservice: immersive-reader
ms.topic: conceptual
ms.date: 06/29/2020
ms.author: metang
ms.openlocfilehash: 0a6ed6ecea216a36cfc9da4ef36a2bddc69cc6a8
ms.sourcegitcommit: fb3c846de147cc2e3515cd8219d8c84790e3a442
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2020
ms.locfileid: "92633146"
---
# <a name="how-to-configure-translation"></a>翻訳を構成する方法

この記事では、イマーシブ リーダーの翻訳のさまざまなオプションを構成する方法について説明します。

## <a name="configure-translation-language"></a>翻訳言語の構成

`options` パラメーターには、翻訳を構成するために使用できるすべてのフラグが含まれています。 `language` パラメーターを翻訳先の言語に設定します。 サポートされている言語の完全な一覧については、[言語サポート](./language-support.md)を参照してください。

```typescript
const options = {
    translationOptions: {
        language: 'fr-FR'
    }
};

ImmersiveReader.launchAsync(YOUR_TOKEN, YOUR_SUBDOMAIN, YOUR_DATA, options);
```

## <a name="automatically-translate-the-document-on-load"></a>読み込み時にドキュメントを自動的に翻訳する

`autoEnableDocumentTranslation` を `true` に設定すると、イマーシブ リーダーの読み込み時にドキュメント全体が自動的に翻訳されます。

```typescript
const options = {
    translationOptions: {
        autoEnableDocumentTranslation: true
    }
};
```

## <a name="automatically-enable-word-translation"></a>単語の翻訳を自動的に有効にする

`autoEnableWordTranslation` を `true` に設定して、単一の単語の翻訳を有効にします。

```typescript
const options = {
    translationOptions: {
        autoEnableWordTranslation: true
    }
};
```

## <a name="next-steps"></a>次のステップ

* [イマーシブ リーダー SDK リファレンス](./reference.md)を参照する