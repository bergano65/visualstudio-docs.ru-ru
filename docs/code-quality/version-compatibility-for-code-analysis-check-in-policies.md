---
title: Совместимость версий для политик возврата анализа кода
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8385e2b36d09f029c4b8625e58cd99ecc06ea226
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649027"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Совместимость версий для политик возврата анализа кода

Если необходимо оценить и разработать политики возврата с анализом кода, используя разные версии [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], необходимо узнать о различиях в [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] и [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] оценке политик возврата.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Совместимость версий для оценки политик возврата

- При оценке политик возврата с анализом кода в [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] все правила, которые существовали [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] но не существуют в [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], игнорируются.

- При оценке политик возврата с анализом кода в [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] все новые правила, которые являются эксклюзивными для [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], игнорируются.

- Если политика возврата для анализа кода указывает сборки правил, [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] игнорирует все правила, заданные нераспознаваемыми сборками.

- Если политика возврата с анализом кода указывает сборки правил, которые [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] не распознаются, выводится сообщение.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Совместимость версий для создания политик возврата

- Если вы создали политику возврата с анализом кода с помощью [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] версии [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], для ее изменения нельзя использовать [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]ную версию [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]. Кроме того, [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] не может оценить политику.

- Если вы создали политику возврата с анализом кода с помощью [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] в [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], для ее изменения можно использовать [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] в [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]. Кроме того, можно оценить политику с помощью [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]. После изменения политики с помощью [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] в [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] вы больше не сможете изменять ее с помощью [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] в [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]. [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] может вычислить политики без проблем с рассогласованными строгими именами.

- Чтобы создать политику возврата с анализом кода с параметрами правил, которые применяются как для [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], так и для [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], необходимо создать политику в [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], внести все необходимые изменения и сохранить политику. Если изменения правил существуют только в [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], вы изменяете и сохраняете политику в [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)].

   После сохранения политики в [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] вы больше не сможете изменять параметры правил, которые существуют только в [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)].
