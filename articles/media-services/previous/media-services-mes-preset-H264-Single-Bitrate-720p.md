---
title: H264 Single Bitrate 720p Media Encoder Standard プリセット - Azure | Microsoft Docs
description: この記事では、Media Encoder Standard "H264 Single Bitrate 720P" タスク プリセットの概要を説明します。
author: Juliako
manager: femila
editor: ''
services: media-services
documentationcenter: ''
ms.assetid: f66da66c-9f21-441d-8038-51e3094e9307
ms.service: media-services
ms.workload: media
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 03/19/2019
ms.author: juliako
ms.openlocfilehash: ee6356981f6d7dace7869c99f69b0719677c5513
ms.sourcegitcommit: 829d951d5c90442a38012daaf77e86046018e5b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/09/2020
ms.locfileid: "89261565"
---
# <a name="h264-single-bitrate-720p"></a>H264 Single Bitrate 720p

[!INCLUDE [media services api v2 logo](./includes/v2-hr.md)]

`Media Encoder Standard` は、エンコード ジョブの作成時に使用できる一連のエンコード プリセットを定義します。 `preset name`を使用して、メディア ファイルをエンコードする形式を指定することも、 (UTF-8 または UTF-16 エンコードを使用して) 独自の JSON または XML ベースのプリセットを作成することもできます。 その後、カスタム プリセットをエンコーダーに渡します。 この `Media Encoder Standard` エンコーダーでサポートされているすべてのプリセット名の一覧については、[Media Encoder Standard 用のタスク プリセット](media-services-mes-presets-overview.md)に関する記事を参照してください。  
  
 このトピックでは、XML 形式と JSON 形式の `H264 Single Bitrate 720p` を示します。  
  
 このプリセットにより、ビットレートが 4,500 kbps、音声が AAC ステレオである単一の MP4 ファイルが生成されます。 このプリセットのプロファイル、ビットレート、サンプリング レートなどの詳細については、下に定義されている XML または JSON を確認してください。 これらのプリセット内の各要素の意味と各要素に有効な値の説明については、「[Media Encoder Standard スキーマ](media-services-mes-schema.md)」を参照してください。  
  
 XML  
  
```  
<?xml version="1.0" encoding="utf-16"?>  
<Preset xmlns:xsd="https://www.w3.org/2001/XMLSchema" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" Version="1.0" xmlns="https://www.windowsazure.com/media/encoding/Preset/2014/03">  
  <Encoding>  
    <H264Video>  
      <KeyFrameInterval>00:00:02</KeyFrameInterval>  
      <SceneChangeDetection>true</SceneChangeDetection>  
      <H264Layers>  
        <H264Layer>  
          <Bitrate>4500</Bitrate>  
          <Width>1280</Width>  
          <Height>720</Height>  
          <FrameRate>0/1</FrameRate>  
          <Profile>Auto</Profile>  
          <Level>auto</Level>  
          <BFrames>3</BFrames>  
          <ReferenceFrames>3</ReferenceFrames>  
          <Slices>0</Slices>  
          <AdaptiveBFrame>true</AdaptiveBFrame>  
          <EntropyMode>Cabac</EntropyMode>  
          <BufferWindow>00:00:05</BufferWindow>  
          <MaxBitrate>4500</MaxBitrate>  
        </H264Layer>  
      </H264Layers>  
      <Chapters />  
    </H264Video>  
    <AACAudio>  
      <Profile>AACLC</Profile>  
      <Channels>2</Channels>  
      <SamplingRate>48000</SamplingRate>  
      <Bitrate>128</Bitrate>  
    </AACAudio>  
  </Encoding>  
  <Outputs>  
    <Output FileName="{Basename}_{Width}x{Height}_{VideoBitrate}.mp4">  
      <MP4Format />  
    </Output>  
  </Outputs>  
</Preset>  
```  
  
 JSON  
  
```  
{  
  "Version": 1.0,  
  "Codecs": [  
    {  
      "KeyFrameInterval": "00:00:02",  
      "SceneChangeDetection": true,  
      "H264Layers": [  
        {  
          "Profile": "Auto",  
          "Level": "auto",  
          "Bitrate": 4500,  
          "MaxBitrate": 4500,  
          "BufferWindow": "00:00:05",  
          "Width": 1280,  
          "Height": 720,  
          "BFrames": 3,  
          "ReferenceFrames": 3,  
          "AdaptiveBFrame": true,  
          "Type": "H264Layer",  
          "FrameRate": "0/1"  
        }  
      ],  
      "Type": "H264Video"  
    },  
    {  
      "Profile": "AACLC",  
      "Channels": 2,  
      "SamplingRate": 48000,  
      "Bitrate": 128,  
      "Type": "AACAudio"  
    }  
  ],  
  "Outputs": [  
    {  
      "FileName": "{Basename}_{Width}x{Height}_{VideoBitrate}.mp4",  
      "Format": {  
        "Type": "MP4Format"  
      }  
    }  
  ]  
}  
```
