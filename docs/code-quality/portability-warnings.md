---
title: предупреждения переносимости
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 072858a9faafe312fd7c8314e7f25cf581c40844
ms.sourcegitcommit: e95dd8cedcd180e0bce6a75c86cf861757918290
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2019
ms.locfileid: "72163072"
---
# <a name="portability-warnings"></a>предупреждения переносимости
Предупреждения переносимости поддерживают переносимость в разных операционных системах.

## <a name="in-this-section"></a>в этом разделе

|Правило|Описание|
|----------|-----------------|
|@NO__T 0CA1900: Поля типа значения должны быть переносимыми @ no__t-0|Это правило проверяет, должны ли структуры, объявленные с помощью явного атрибута макета, правильно выстроиться при маршалировании в неуправляемый код в 64-разрядных операционных системах.|
|@NO__T 0CA1901: Объявления P/Invoke должны быть переносимыми @ no__t-0|Это правило оценивает размер каждого параметра и возвращаемое значение P/Invoke и проверяет правильность их размера при маршалировании в неуправляемый код в 32-разрядных и 64-разрядных операционных системах.|
|@NO__T 0CA1903: Использовать API только из целевой платформы @ no__t-0|Член или тип использует член или тип, который был впервые представлен в пакете обновления, не включенном в целевую среду проекта.|
