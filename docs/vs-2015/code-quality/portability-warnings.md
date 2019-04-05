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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7c8f195f2219cfa2c81b24a3e04ddc559dc98a06
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58991248"
---
# <a name="portability-warnings"></a>предупреждения переносимости
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Предупреждения переносимости поддерживают возможность переноса для различных операционных систем.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Правило|Описание|  
|----------|-----------------|  
|[CA1900: Поля типа значения должны быть переносимыми](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Это правило проверяет правильность выравнивания структур, объявленных с помощью атрибута явной разметкой, при маршалировании в неуправляемый код на 64-разрядных операционных системах.|  
|[CA1901: Объявления P/Invoke должны быть переносимыми](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Это правило вычисляет размер каждого параметра и возвращаемого значения вызова P/Invoke и проверяет правильность их размера при маршалировании в неуправляемый код в 32-разрядных и 64-разрядных операционных системах.|  
|[CA1903: Используйте API-Интерфейс только из целевой версии .NET framework](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Член или тип использует член или тип, который был впервые представлен в пакете обновления, не включенном в целевую среду проекта.|
