---
title: "CA1811: не используйте невызываемый закрытый код | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidUncalledPrivateCode"
  - "CA1811"
helpviewer_keywords: 
  - "CA1811"
  - "AvoidUncalledPrivateCode"
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 20
---
# CA1811: не используйте невызываемый закрытый код
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidUncalledPrivateCode|  
|CheckId|CA1811|  
|Категория|Microsoft.Performance|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Закрытый или внутренний член \(член уровня сборки\) не вызывается ни объектами сборки, ни средой CLR, ни делегатом.  Ниже перечислены методы, которые не проверяются данным правилом.  
  
-   Явные члены интерфейса.  
  
-   Статические конструкторы.  
  
-   Конструкторы сериализации.  
  
-   Методы, помеченные атрибутом <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> или <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>.  
  
-   Члены, которые являются переопределениями.  
  
## Описание правила  
 Данное правило может сообщать о ложных положительных результатах, если в коде имеются точки входа, которые в данный момент не обнаруживаются логикой правила.  Кроме того компилятор может выдавать невызываемый код в сборку.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, удалите невызываемый код или добавьте код, который может его вызвать.  
  
## Отключение предупреждений  
 Отключение предупреждений о нарушении этого правила является безопасным.  
  
## Связанные правила  
 [CA1812: не создавайте внутренние классы без экземпляров](../Topic/CA1812:%20Avoid%20uninstantiated%20internal%20classes.md)  
  
 [CA1801: проверьте неиспользуемые параметры](../Topic/CA1801:%20Review%20unused%20parameters.md)  
  
 [CA1804: удалите неиспользуемые локальные переменные](../code-quality/ca1804-remove-unused-locals.md)