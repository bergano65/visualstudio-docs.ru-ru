---
title: "CA1707: идентификаторы не должны содержать знак подчеркивания | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IdentifiersShouldNotContainUnderscores"
  - "CA1707"
helpviewer_keywords: 
  - "CA1707"
  - "IdentifiersShouldNotContainUnderscores"
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA1707: идентификаторы не должны содержать знак подчеркивания
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldNotContainUnderscores|  
|CheckId|CA1707|  
|Категория|Microsoft.Naming|  
|Критическое изменение|Breaking — для сборок<br /><br /> Не критическое — если вызывается для параметров типов|  
  
## Причина  
 Имя идентификатора содержит знак подчеркивания \(\_\).  
  
## Описание правила  
 В соответствии с соглашением имена идентификаторов не могут содержать знак подчеркивания \(\_\).  Правило проверяет пространства имен, типы, члены и параметра.  
  
 Соглашения об именах обеспечивают единообразие библиотек, предназначенных для выполнения в среде CLR.  Это позволяет сократить время обучения, необходимое для освоения новых библиотек программного обеспечения, и укрепить уверенность клиента в том, что библиотека была разработана опытным разработчиком управляемого кода.  
  
## Устранение нарушений  
 Удалите из имени все знаки подчеркивания.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Связанные правила  
 [CA1709: идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: идентификаторы должны отличаться не только регистром](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)