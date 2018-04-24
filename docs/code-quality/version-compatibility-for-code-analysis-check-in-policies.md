---
title: Совместимость версий для политик возврата анализа кода
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 25e8ee0bf46840d420f5537a2ca28965522dea43
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
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