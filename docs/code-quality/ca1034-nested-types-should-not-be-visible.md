---
title: "CA1034: вложенные типы не должны быть видимыми | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "NestedTypesShouldNotBeVisible"
  - "CA1034"
helpviewer_keywords: 
  - "NestedTypesShouldNotBeVisible"
  - "CA1034"
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1034: вложенные типы не должны быть видимыми
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|NestedTypesShouldNotBeVisible|  
|CheckId|CA1034|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Видимый для внешнего кода тип содержит объявление видимого для внешнего кода типа.  Данное правило не распространяется на вложенные перечислители и защищенные типы.  
  
## Описание правила  
 Вложенный тип — это тип, объявленный внутри области видимости другого типа.  Вложенные типы удобно использовать для инкапсуляции закрытых сведений о реализациях содержащего их типа.  В силу этого вложенные типы не должны быть видимыми для внешнего кода.  
  
 Не следует использовать видимые для внешнего кода вложенные типы для логической группировки или с целью предотвращения конфликтов имен. Для эти целей лучше применять пространства имен.  
  
 Некоторые программисты не всегда имеют четкое представление о доступности членов вложенных типов.  
  
 Защищенные типы можно использовать в подклассах, а вложенные типы — в скриптах расширенной настройки.  
  
## Устранение нарушений  
 Если вложенный тип не предназначен для доступа со стороны внешнего кода, измените видимость этого типа.  В противном случае удалите вложенный тип из родительского типа.  Если целью вложения является категоризация вложенных типов, используйте для создания иерархии пространство имен.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример  
 В следующем примере показан тип, который нарушает данное правило.  
  
 [!code-cpp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CPP/ca1034-nested-types-should-not-be-visible_1.cpp)]
 [!code-cs[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CSharp/ca1034-nested-types-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/VisualBasic/ca1034-nested-types-should-not-be-visible_1.vb)]