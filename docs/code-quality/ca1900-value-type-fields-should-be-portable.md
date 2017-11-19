---
title: "CA1900: Поля типа значения должны быть переносимыми | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7f2d948d78f6b12352a3e4cfcb28aab41db3e873
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900: поля типа значения должны быть переносимыми
|||  
|-|-|  
|TypeName|ValueTypeFieldsShouldBePortable|  
|CheckId|CA1900|  
|Категория|Microsoft.Portability|  
|Критическое изменение|Критическое, если поле может отображаться за пределами сборки.<br /><br /> Не критическое — если поле не отображается за пределами сборки.|  
  
## <a name="cause"></a>Причина  
 Это правило проверяет правильность выравнивания структур, объявленных с явной разметкой, при маршалировании в неуправляемый код на 64-разрядных операционных системах. Обращается к памяти и процесса произойдет сбой, если не будет устранена, это нарушение запрещены IA-64.  
  
## <a name="rule-description"></a>Описание правила  
 Структуры, имеющие явно заданный макет, который содержит неправильно выровненные поля могут привести к сбоям в 64-разрядных операционных системах.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Все поля, которые меньше, чем 8 байт должны иметь смещения, кратные их размера и поля размером 8 байт или более должны иметь смещения, кратные 8. Другим решением является использование `LayoutKind.Sequential` вместо `LayoutKind.Explicit`, если слишком много.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Это предупреждение следует отключать только в том случае, если оно возникает в ошибке.