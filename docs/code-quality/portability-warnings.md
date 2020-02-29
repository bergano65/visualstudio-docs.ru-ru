---
title: Portability Warnings
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f48cef7ffaf08fc26566fdd04bee15a3e3e1b85f
ms.sourcegitcommit: 1efb6b219ade7c35068b79fbdc573a8771ac608d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2020
ms.locfileid: "78167577"
---
# <a name="portability-warnings"></a>Portability Warnings
Предупреждения переносимости поддерживают переносимость в разных операционных системах.

## <a name="in-this-section"></a>в этом разделе

|Правило|Описание|
|----------|-----------------|
|[CA1900: поля типа значения должны быть переносимыми](../code-quality/ca1900.md)|Это правило проверяет, должны ли структуры, объявленные с помощью явного атрибута макета, правильно выстроиться при маршалировании в неуправляемый код в 64-разрядных операционных системах.|
|[CA1901: объявления P/Invoke должны быть переносимыми](../code-quality/ca1901.md)|Это правило оценивает размер каждого параметра и возвращаемое значение P/Invoke и проверяет правильность их размера при маршалировании в неуправляемый код в 32-разрядных и 64-разрядных операционных системах.|
|[CA1903: использовать API-интерфейс только из целевой исполняющей среды](../code-quality/ca1903.md)|Член или тип использует член или тип, который был впервые представлен в пакете обновления, не включенном в целевую среду проекта.|
