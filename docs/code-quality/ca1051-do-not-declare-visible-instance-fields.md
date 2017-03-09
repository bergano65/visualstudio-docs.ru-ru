---
title: "CA1051: не объявляйте видимые поля экземпляров | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1051"
  - "DoNotDeclareVisibleInstanceFields"
helpviewer_keywords: 
  - "CA1051"
  - "DoNotDeclareVisibleInstanceFields"
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1051: не объявляйте видимые поля экземпляров
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareVisibleInstanceFields|  
|CheckId|CA1051|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 В типе, видимом снаружи, есть видимое снаружи поле экземпляра.  
  
## Описание правила  
 Поля главным образом следует использовать для данных реализации.  Поля должны быть помечены как `private` или `internal` и должны раскрываться с помощью свойств.  Доступ к свойству так же прост, как и доступ к полю, а код в методах доступа к свойству может измениться по мере расширения компонентов типа без критических изменений.  Свойства, возвращающие только значение закрытого или внутреннего поля, оптимизированы для выполнения наряду с доступом к полю; использование внешне видимых полей вместо свойств дает минимальный прироста производительности.  
  
 Внешняя видимость относится к уровням доступности `public`, `protected` и `protected internal` \(`Public`, `Protected` и `Protected Friend` в Visual Basic\).  
  
## Устранение нарушений  
 Для устранения нарушения этого правила сделайте поле `private` или `internal` и раскройте его с помощью свойства внешней видимости.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  Внешне видимые поля не предлагают каких\-либо преимуществ, которых нет в свойствах.  Кроме того, открытые поля не могут быть защищены [Link Demands](../Topic/Link%20Demands.md).  См. раздел [CA2112: защищенные типы не должны предоставлять поля](../code-quality/ca2112-secured-types-should-not-expose-fields.md).  
  
## Пример  
 В следующем примере показан тип \(`BadPublicInstanceFields`\), который нарушает данное правило.  `GoodPublicInstanceFields` показывает исправленный код.  
  
 [!code-cs[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]  
  
## Связанные правила  
 [CA2112: защищенные типы не должны предоставлять поля](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
## См. также  
 [Link Demands](../Topic/Link%20Demands.md)