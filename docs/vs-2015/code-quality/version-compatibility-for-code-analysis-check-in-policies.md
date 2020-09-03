---
title: Совместимость версий для политик возврата с анализом кода | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 075981569cbee05e90afe17b3afc9558d7bbb270
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72609318"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Совместимость версий для политик возврата анализа кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Если необходимо оценить и разработать политики возврата с анализом кода с использованием различных версий [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] , необходимо ознакомиться с различиями в области определения [!INCLUDE[vstsTfsOrcasLong](../includes/vststfsorcaslong-md.md)] [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] политик возврата и их вычисления.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Совместимость версий для оценки политик возврата

- При вычислении политик возврата с анализом кода [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] все правила, которые существовали в, [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] но не существуют в [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] , игнорируются.

- При вычислении политик возврата с анализом кода [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] все новые правила, которые являются эксклюзивными для, [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] игнорируются.

- Если политика возврата для анализа кода указывает сборки правил, [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] пропускает все правила, заданные нераспознаваемыми сборками.

- Если политика возврата с анализом кода указывает сборки правил, которые [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] не распознаются, выводится сообщение.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Совместимость версий для создания политик возврата

- Если вы создали политику возврата с анализом кода с помощью [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] версии [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] , ее нельзя изменить с помощью [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] версии [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] . Кроме того, [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] невозможно вычислить политику.

- Если вы создали политику возврата с анализом кода с помощью [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] в [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] , [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] для ее изменения можно использовать в [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] . Кроме того, политику можно вычислить с помощью [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] . После изменения политики с помощью [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] в [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] можно изменить политику с помощью [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] в [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] . [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] может оценивать политики без проблем с несовпадающими строгими именами.

- Чтобы создать политику возврата с анализом кода с параметрами правила, применяемыми для [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] и [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] , необходимо создать политику в [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] , внести все необходимые изменения и сохранить политику. Если изменения правил существуют только в [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] , вы изменяете и сохраняете политику в [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] .

     После сохранения политики в [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] вы больше не сможете изменять параметры правил, которые существуют [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] только в.
