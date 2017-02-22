---
title: "CA1722: идентификаторы не должны иметь неверные префиксы | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IdentifiersShouldNotHaveIncorrectPrefix"
  - "CA1722"
helpviewer_keywords: 
  - "CA1722"
  - "IdentifiersShouldNotHaveIncorrectPrefix"
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1722: идентификаторы не должны иметь неверные префиксы
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|  
|CheckId|CA1722|  
|Категория|Microsoft.Naming|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Идентификатор имеет неверный префикс.  
  
## Описание правила  
 В соответствии с соглашением об именовании, только некоторые элементы программирования могут иметь имена, которые начинаются с особого префикса.  
  
 Имена типов не имеют особого префикса, и к ним не следует добавлять префикс "C".  Данное правило сообщает о нарушениях в таких именах типов, как «CMyClass», и не сообщает о нарушениях в таких именах типов, как «Cache».  
  
 Соглашения об именах обеспечивают единообразие библиотек, предназначенных для выполнения в среде CLR.  Это позволяет сократить время обучения, необходимое для освоения новых библиотек программного обеспечения, и укрепить уверенность клиента в том, что библиотека была разработана опытным разработчиком управляемого кода.  
  
## Устранение нарушений  
 Удалите префикс из идентификатора.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Связанные правила  
 [CA1715: идентификаторы должны иметь правильные префиксы](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)