---
title: "Предупреждения переносимости | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: efd2d56700c70b27771623e618f61675b174da01
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="portability-warnings"></a>предупреждения переносимости
Предупреждения переносимости поддерживают возможность переноса между разными операционными системами.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Правило|Описание:|  
|----------|-----------------|  
|[CA1900: поля типа значения должны быть переносимыми](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Это правило проверяет правильность выравнивания структур, объявленных с явным атрибутом разметки, при маршалировании в неуправляемый код на 64-разрядных операционных системах.|  
|[CA1901: Объявления P/Invoke должны быть переносимыми](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Это правило вычисляет размер каждого параметра и возвращаемого значения вызова P/Invoke и проверяет правильность их размера при маршалировании в неуправляемый код на 32-разрядных и 64-разрядных операционных системах.|  
|[CA1903: использовать API-интерфейс только из целевой исполняющей среды](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Член или тип использует член или тип, который был впервые представлен в пакете обновления, не включенном в целевую среду проекта.|