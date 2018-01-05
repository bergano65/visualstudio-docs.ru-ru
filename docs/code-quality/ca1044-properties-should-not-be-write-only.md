---
title: "CA1044: Свойства не должны быть доступны только для записи | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PropertiesShouldNotBeWriteOnly
- CA1044
helpviewer_keywords:
- CA1044
- PropertiesShouldNotBeWriteOnly
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: cdb3ac5479193236b146c7c2607e5a27727695a3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044: свойства не должны быть доступны только на запись
|||  
|-|-|  
|TypeName|PropertiesShouldNotBeWriteOnly|  
|CheckId|CA1044|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Свойства открытый или защищенный метод доступа set, но не метод доступа get.  
  
## <a name="rule-description"></a>Описание правила  
 Получение доступа предоставляют доступ на чтение к свойству и методы доступа set обеспечивают доступ на запись. Несмотря на то, что допустимо, а часто и необходимо иметь свойство, доступное только на чтение, рекомендации по разработке запрещают использование свойств, доступных только на запись. Это так, как позволить пользователю задать значение, а затем запретить пользователю просмотр значение обеспечивает безопасность. Кроме того, при отсутствии доступа на чтение нельзя просмотреть состояние общих объектов, что снижает их полезность.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, добавьте в метод доступа get свойства. Если необходимо поведение свойства только для записи, рассмотрите возможность преобразовать это свойство в метод.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Настоятельно рекомендуется не отключайте предупреждение из этого правила.  
  
## <a name="example"></a>Пример  
 В следующем примере `BadClassWithWriteOnlyProperty` — это тип со свойством только для записи. `GoodClassWithReadWriteProperty`содержит Исправленный код.  
  
 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/VisualBasic/ca1044-properties-should-not-be-write-only_1.vb)]
 [!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/CSharp/ca1044-properties-should-not-be-write-only_1.cs)]