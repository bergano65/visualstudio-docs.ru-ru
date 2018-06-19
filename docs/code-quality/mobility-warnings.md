---
title: предупреждения мобильности
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- vs.codeanalysis.MobilityRules
helpviewer_keywords:
- managed code analysis warnings, mobility warnings
- mobility warnings
- warnings, mobility
ms.assetid: 9808054c-593b-4fc3-92cc-1fc45f41569c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8f40803e4e491382e958c1954d2608cb712ad82b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31919668"
---
# <a name="mobility-warnings"></a>предупреждения мобильности
Предупреждения мобильности поддерживают эффективное энергопотребление.

## <a name="in-this-section"></a>В этом разделе

|Правило|Описание|
|----------|-----------------|
|[CA1600: не используйте приоритет процессов в состоянии ожидания](../code-quality/ca1600-do-not-use-idle-process-priority.md)|Не задавайте для приоритета процесса значение Idle. Процессы с приоритетом System.Diagnostics.ProcessPriorityClass.Idle будут занимать ЦП, который иначе простаивал бы, и тем самым блокировать работу в режиме ожидания.|
|[CA1601: не используйте таймеры, препятствующие изменению состояния электропитания](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|Повышение частоты периодических действий приводит к дополнительной нагрузке на ЦП и препятствует работе таймеров энергосберегающих режимов, которые отключают монитор и жесткие диски.|