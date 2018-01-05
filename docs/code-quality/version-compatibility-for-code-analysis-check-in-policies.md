---
title: "Совместимость версий для политик возврата с анализом кода | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 323024cdb420d48c40b7a676bc4e698af7622b67
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Совместимость версий для политик возврата анализа кода
Если вам нужно создавать и возврат политик с использованием разных версий [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], необходимо обратить внимание на различия в том, как [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] и [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] оценки политик возврата.  
  
## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Совместимость версий для проверки политик возврата  
  
-   При проверке политик возврата с анализом кода в [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], все правила, которые существовали в [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] , но не существуют в [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] игнорируются.  
  
-   При проверке политик возврата с анализом кода в [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], все новые правила, предназначенные исключительно для [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] игнорируются.  
  
-   Если политика возврата указывает сборки правил [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] пропускаются все правила, определяемые сборками, что он не распознает.  
  
-   Если политика возврата указывает сборки правил, [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] не распознает, отображается сообщение.  
  
## <a name="version-compatibility-for-authoring-check-in-policies"></a>Совместимость версий для создания политик возврата  
  
-   Если вы создали политику возврата с анализом кода с помощью [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] версии [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], нельзя использовать [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] версии [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] для внесения изменений. Кроме того [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] нельзя вычислять политику.  
  
-   Если вы создали политику возврата с анализом кода с помощью [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] в [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], можно использовать [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] в [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] для изменения и политику также можно оценить по [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]. После изменения политики с помощью [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] в [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], больше не может изменить политики с помощью [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] в [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]. [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] может вычислить политики без проблем с рассогласованными строгими именами.  
  
-   Чтобы создать политику возврата с анализом кода с параметрами правил, которые применяются для обоих [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] и [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], необходимо создать политику в [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], внести все необходимые изменения и сохранить политику. Если изменения правил существуют только в [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], изменить и сохранить политику в [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)].  
  
     После сохранения политики в [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], больше не можно изменить параметры для правил, которые существуют в [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] только.