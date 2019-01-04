---
title: Совместимость версий для политик возврата анализа кода
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: d9c57b9e0afb443c8ec808dbd2908c1b8b7031aa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53892512"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Совместимость версий для политик возврата анализа кода

Если вам нужно создавать и возврат политик с использованием разных версий [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], необходимо обратить внимание на различия в том, как [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] и [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] оценки политик возврата.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Совместимость версий для оценки политик возврата

- При вычислении политик возврата с анализом кода в [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], все правила, которые существовали в [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] , но не существуют в [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] игнорируются.

- При вычислении политик возврата с анализом кода в [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], все новые правила, предназначенные исключительно для [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] игнорируются.

- Если политика возврата указывает сборки правил [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] пропускаются все правила, определяемые сборками, что он не распознает.

- Если политика возврата указывает сборки правил, [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] не распознает, отображается сообщение.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Совместимость версий для создания политик возврата

- Если вы создали политику возврата с анализом кода с помощью [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] версии [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], нельзя использовать [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] версии [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] изменить его. Кроме того [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] невозможно вычислить политики.

- Если вы создали политику возврата с анализом кода с помощью [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] в [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], можно использовать [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] в [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] изменить его, а также политики также можно оценить по [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]. После внесения изменений в политику с помощью [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] в [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], больше не можете править политику с помощью [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] в [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]. [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] может вычислить политики без проблем с рассогласованными строгими именами.

- Чтобы создать политику возврата с анализом кода с параметрами правил, которые применяются для обоих [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] и [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], необходимо создать политику в [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], внести все необходимые изменения и сохранить политику. Если изменения правил существуют только в [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], изменить и сохранить политику в [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)].

   После сохранения политики в [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], больше не можно изменить параметры для правил, которые существуют в [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] только.