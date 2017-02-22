---
title: "CA1802. Используйте литералы там, где возможно | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseLiteralsWhereAppropriate"
  - "CA1802"
helpviewer_keywords: 
  - "UseLiteralsWhereAppropriate"
  - "CA1802"
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1802. Используйте литералы там, где возможно
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseLiteralsWhereAppropriate|  
|CheckId|CA1802|  
|Категория|Microsoft.Performance|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Поле объявлено `static` и `readonly` \(`Shared` и `ReadOnly` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) и инициализировано со значением, вычисляемым во время компиляции.  
  
## Описание правила  
 Значение поля `static` `readonly` вычисляется во время выполнения при вызове статического конструктора для объявляющего типа.  Если поле `static` `readonly` инициализируется во время своего объявления и статический конструктор не объявлен явно, компилятор выдает статический конструктор для инициализации поля.  
  
 Значение поля `const` вычисляется во время компиляции и хранится в метаданных, что приводит к повышению производительности среды выполнения по сравнению с полем `static` `readonly`.  
  
 Поскольку значение, назначенное целевому полю, вычисляется во время компиляции, измените объявление на поле `const`, чтобы значение вычислялось не во время выполнения, а во время компиляции.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, замените модификаторы `static` и `readonly` на модификатор `const`.  
  
## Отключение предупреждений  
 Если вопрос производительности не критичен, можно отключить вывод предупреждения для данного правила или полностью отключить само правило.  
  
## Пример  
 В следующем примере показан тип `UseReadOnly`, который нарушает данное правило, и тип `UseConstant`, удовлетворяющий ему.  
  
 [!CODE [FxCop.Performance.UseLiterals#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals#1)]