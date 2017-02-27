---
title: "CA1504: проверьте имена полей, которые могут ввести в заблуждение | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ReviewMisleadingFieldNames"
  - "CA1504"
helpviewer_keywords: 
  - "CA1504"
  - "ReviewMisleadingFieldNames"
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1504: проверьте имена полей, которые могут ввести в заблуждение
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewMisleadingFieldNames|  
|CheckId|CA1504|  
|Категория|Microsoft.Maintainability|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Имя поля экземпляра начинается с "s\_"; имя поля с модификатором `static` \(`Shared` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) начинается с "m\_".  
  
## Описание правила  
 Многие пользователи связывают имена полей, начинающиеся с "s\_", со статическими данными.  Аналогичным образом, имена полей, начинающиеся с "m\_", связываются о данными экземпляра \(члена — member\).  Для упрощения поддержки кода следует следовать общепринятым соглашениями об именовании.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, измените префикс имени поля.  Можно также сделать поле соответствующим его текущему префиксу, добавив или удалив модификатор `static`.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.