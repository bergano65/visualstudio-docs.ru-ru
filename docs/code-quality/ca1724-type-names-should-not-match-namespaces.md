---
title: "CA1724. Имена типов не должны совпадать с именами пространства имен | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TypeNamesShouldNotMatchNamespaces"
  - "CA1724"
helpviewer_keywords: 
  - "TypeNamesShouldNotMatchNamespaces"
  - "CA1724"
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1724. Имена типов не должны совпадать с именами пространства имен
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypeNamesShouldNotMatchNamespaces|  
|CheckId|CA1724|  
|Категория|Microsoft.Naming|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Имя типа совпадает с пространством имен [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] при сравнении без учета регистра.  
  
## Описание правила  
 Имена типов не должны совпадать с именами пространств имен, определенными в библиотеке классов [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Нарушение этого правила приводит к уменьшению функциональности библиотеки.  
  
## Устранение нарушений  
 Выберите имя типа, которое не совпадает ни с одним из пространств имен библиотеки класса [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## Отключение предупреждений  
 При разработке нового кода случаи, когда необходимо отключать предупреждения о нарушении данного правила, неизвестны.  Прежде чем отключить предупреждения, тщательно продумать, как пользователи библиотеки могут быть запутаны одинаковым именем.  В случае поставки библиотек подобные предупреждения, возможно, необходимо отключать.