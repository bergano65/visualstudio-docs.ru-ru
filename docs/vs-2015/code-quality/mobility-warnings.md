---
title: Предупреждения мобильности | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.MobilityRules
helpviewer_keywords:
- managed code analysis warnings, mobility warnings
- mobility warnings
- warnings, mobility
ms.assetid: 9808054c-593b-4fc3-92cc-1fc45f41569c
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c9f5606540d55c0a2c4257ff397ad77cc55624b4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655978"
---
# <a name="mobility-warnings"></a>предупреждения мобильности
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Предупреждения мобильности поддерживают эффективное энергопотребление.

## <a name="in-this-section"></a>Содержание

|Правило|Описание|
|----------|-----------------|
|[CA1600: не используйте приоритет процессов в состоянии ожидания](../code-quality/ca1600-do-not-use-idle-process-priority.md)|Не задавайте для приоритета процесса значение Idle. Процессы с приоритетом System.Diagnostics.ProcessPriorityClass.Idle будут занимать ЦП, который иначе простаивал бы, и тем самым блокировать работу в режиме ожидания.|
|[CA1601: не используйте таймеры, препятствующие изменению состояния электропитания](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|Повышение частоты периодических действий приводит к дополнительной нагрузке на ЦП и препятствует работе таймеров энергосберегающих режимов, которые отключают монитор и жесткие диски.|
