---
title: Предупреждения переносимости | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 932474143b4770e81d8bfca14ab05a6538ae84a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671166"
---
# <a name="portability-warnings"></a>предупреждения переносимости
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Предупреждения переносимости поддерживают переносимость в разных операционных системах.

## <a name="in-this-section"></a>в этом разделе

|Правило|Описание|
|----------|-----------------|
|[CA1900. Поля типов значений должны быть переносимыми](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Это правило проверяет, должны ли структуры, объявленные с помощью явного атрибута макета, правильно выстроиться при маршалировании в неуправляемый код в 64-разрядных операционных системах.|
|[CA1901: объявления P/Invoke должны быть переносимыми](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Это правило оценивает размер каждого параметра и возвращаемое значение P/Invoke и проверяет правильность их размера при маршалировании в неуправляемый код в 32-разрядных и 64-разрядных операционных системах.|
|[CA1903. Используйте API только из целевой рабочей среды](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Член или тип использует член или тип, который был впервые представлен в пакете обновления, не включенном в целевую среду проекта.|
