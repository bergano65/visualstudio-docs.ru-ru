---
title: Совместимость версий для политик возврата с анализом кода | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 840a12e7f4c0e3853e885a803dea5a92e05a5a27
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49261486"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Совместимость версий для политик возврата анализа кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Если вам нужно создавать и возврат политик с использованием разных версий [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], необходимо обратить внимание на различия в том, как [!INCLUDE[vstsTfsOrcasLong](../includes/vststfsorcaslong-md.md)] и [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] оценки политик возврата.  
  
## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Совместимость версий для оценки политик возврата  
  
-   При вычислении политик возврата с анализом кода в [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], все правила, которые существовали в [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] , но не существуют в [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] игнорируются.  
  
-   При вычислении политик возврата с анализом кода в [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)], все новые правила, предназначенные исключительно для [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] игнорируются.  
  
-   Если политика возврата указывает сборки правил [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] пропускаются все правила, определяемые сборками, что он не распознает.  
  
-   Если политика возврата указывает сборки правил, [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] не распознает, отображается сообщение.  
  
## <a name="version-compatibility-for-authoring-check-in-policies"></a>Совместимость версий для создания политик возврата  
  
-   Если вы создали политику возврата с анализом кода с помощью [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] версии [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], нельзя использовать [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] версии [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] изменить его. Кроме того [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] невозможно вычислить политики.  
  
-   Если вы создали политику возврата с анализом кода с помощью [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] в [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)], можно использовать [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] в [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] изменить его, а также политики также можно оценить по [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)]. После внесения изменений в политику с помощью [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] в [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], больше не можете править политику с помощью [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] в [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)]. [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] может вычислить политики без проблем с рассогласованными строгими именами.  
  
-   Чтобы создать политику возврата с анализом кода с параметрами правил, которые применяются для обоих [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] и [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], необходимо создать политику в [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)], внести все необходимые изменения и сохранить политику. Если изменения правил существуют только в [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], изменить и сохранить политику в [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)].  
  
     После сохранения политики в [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], больше не можно изменить параметры для правил, которые существуют в [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] только.



