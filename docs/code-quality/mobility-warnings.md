---
title: Mobility Warnings
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.MobilityRules
helpviewer_keywords:
- managed code analysis warnings, mobility warnings
- mobility warnings
- warnings, mobility
ms.assetid: 9808054c-593b-4fc3-92cc-1fc45f41569c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6061b614442d7bcb2f3465b1c40f35d583626c45
ms.sourcegitcommit: 1efb6b219ade7c35068b79fbdc573a8771ac608d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2020
ms.locfileid: "78167589"
---
# <a name="mobility-warnings"></a>Mobility Warnings
Предупреждения мобильности поддерживают эффективное энергопотребление.

## <a name="in-this-section"></a>в этом разделе

|Правило|Описание|
|----------|-----------------|
|[CA1600: не используйте приоритет процессов в состоянии ожидания](../code-quality/ca1600.md)|Не задавайте для приоритета процесса значение Idle. Процессы с приоритетом System.Diagnostics.ProcessPriorityClass.Idle будут занимать ЦП, который иначе простаивал бы, и тем самым блокировать работу в режиме ожидания.|
|[CA1601: не используйте таймеры, препятствующие изменению состояния электропитания](../code-quality/ca1601.md)|Повышение частоты периодических действий приводит к дополнительной нагрузке на ЦП и препятствует работе таймеров энергосберегающих режимов, которые отключают монитор и жесткие диски.|
