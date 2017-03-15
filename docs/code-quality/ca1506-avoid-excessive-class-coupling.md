---
title: "CA1506: избегайте чрезмерного соединения классов | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidExcessiveClassCoupling"
  - "CA1506"
helpviewer_keywords: 
  - "AvoidExcessiveClassCoupling"
  - "CA1506"
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# CA1506: избегайте чрезмерного соединения классов
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidExcessiveClassCoupling|  
|CheckId|CA1506|  
|Категория|Microsoft.Maintainability|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Тип или метод соединен с несколькими другими типами.  
  
## Описание правила  
 Данное правило измеряет соединение классов посредством подсчета количества уникальных ссылок на типы, содержащихся в типе или методе.  
  
 Типы и методы с высокой степенью соединения классов могут затруднять поддержку.  Рекомендуется использовать типы и методы с низкой степенью соединения и высокой степенью связанности.  
  
## Устранение нарушений  
 Для устранения нарушения данного правила попробуйте изменить тип или метод, чтобы снизить количество соединенных с ним типов.  
  
## Отключение предупреждений  
 Это предупреждение можно отключить, если тип и метод остается поддерживаемым несмотря на большое количество зависимостей от других типов.  
  
## См. также  
 [Предупреждения удобства обслуживания](../code-quality/maintainability-warnings.md)   
 [Оценка сложности и удобства сопровождения управляемого кода](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)