---
title: "CA1044: свойства не должны быть доступны только на запись | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PropertiesShouldNotBeWriteOnly"
  - "CA1044"
helpviewer_keywords: 
  - "CA1044"
  - "PropertiesShouldNotBeWriteOnly"
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1044: свойства не должны быть доступны только на запись
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PropertiesShouldNotBeWriteOnly|  
|CheckId|CA1044|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Открытое или защищенное свойство имеет метод доступа set, но не имеет метода доступа get.  
  
## Описание правила  
 Методы доступа get предоставляют доступ на чтение свойства, а методы доступа set — на запись свойства.  Несмотря на то, что допустимо, а часто и необходимо иметь свойство, доступное только на чтение, рекомендации по разработке запрещают использование свойств, доступных только на запись.  Это обусловлено тем, что запрет на просмотр заданного пользователем значения не обеспечивает безопасность.  Кроме того, при отсутствии доступа на чтение нельзя просмотреть состояние общих объектов, что снижает их полезность.  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правило, добавьте для свойства метод доступа get.  Кроме того, если все же требуется свойство, доступное только для записи, можно преобразовать это свойство в метод.  
  
## Отключение предупреждений  
 Настоятельно рекомендуется не отключать предупреждение этого правила.  
  
## Пример  
 В следующем примере `BadClassWithWriteOnlyProperty` является типом со свойством только для записи.  Метод `GoodClassWithReadWriteProperty` содержит исправленный код.  
  
 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/VisualBasic/ca1044-properties-should-not-be-write-only_1.vb)]
 [!code-cs[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/CSharp/ca1044-properties-should-not-be-write-only_1.cs)]