---
title: предупреждения переносимости
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e6fe3bcd703d7fd58d5590b755a553d8ead4c0a9
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="portability-warnings"></a>предупреждения переносимости
Предупреждения переносимости поддерживают возможность переноса между разными операционными системами.

## <a name="in-this-section"></a>В этом разделе

|Правило|Описание|
|----------|-----------------|
|[CA1900: поля типа значения должны быть переносимыми](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Это правило проверяет правильность выравнивания структур, объявленных с явным атрибутом разметки, при маршалировании в неуправляемый код на 64-разрядных операционных системах.|
|[CA1901: Объявления P/Invoke должны быть переносимыми](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Это правило вычисляет размер каждого параметра и возвращаемого значения вызова P/Invoke и проверяет правильность их размера при маршалировании в неуправляемый код на 32-разрядных и 64-разрядных операционных системах.|
|[CA1903: использовать API-интерфейс только из целевой исполняющей среды](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Член или тип использует член или тип, который был впервые представлен в пакете обновления, не включенном в целевую среду проекта.|