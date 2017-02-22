---
title: "CA1804: удалите неиспользуемые локальные переменные | Microsoft Docs"
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
  - "CA1804"
  - "RemoveUnusedLocals"
helpviewer_keywords: 
  - "RemoveUnusedLocals"
  - "CA1804"
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1804: удалите неиспользуемые локальные переменные
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|RemoveUnusedLocals|  
|CheckId|CA1804|  
|Категория|Microsoft.Performance|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Метод объявляет локальную переменную, однако не использует ее. Эта переменная, возможно, является лишь получателем оператора присвоения.  Для анализа данного правила проверяемую сборку следует построить с отладочной информацией и связанный PDB\-файл должен быть доступен.  
  
## Описание правила  
 Неиспользуемые локальные переменные и ненужные присвоения увеличивают размер сборки и снижают производительность.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, удалите локальную переменную или используйте ее.  Обратите внимание, что компилятор C\#, который поставляется вместе с [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], удаляет все неиспользуемые переменные при компиляции с параметром `optimize`.  
  
## Отключение предупреждений  
 Если указанная переменная создана компилятором, предупреждение о нарушение данного правила можно отключить.  Кроме того, если производительность и удобство поддержки не входят в число основных приоритетов для кода, отключение такого рода предупреждений будет совершенно безопасно.  
  
## Пример  
 В следующем примере демонстрируется несколько неиспользуемых локальных переменных.  
  
 [!CODE [FxCop.Performance.UnusedLocals#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals#1)]  
  
## Связанные правила  
 [CA1809: избегайте чрезмерного использования локальных переменных](../code-quality/ca1809-avoid-excessive-locals.md)  
  
 [CA1811: не используйте невызываемый закрытый код](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: не создавайте внутренние классы без экземпляров](../Topic/CA1812:%20Avoid%20uninstantiated%20internal%20classes.md)  
  
 [CA1801: проверьте неиспользуемые параметры](../Topic/CA1801:%20Review%20unused%20parameters.md)