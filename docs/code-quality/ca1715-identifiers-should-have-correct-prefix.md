---
title: "CA1715: идентификаторы должны иметь правильные префиксы | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1715"
  - "IdentifiersShouldHaveCorrectPrefix"
helpviewer_keywords: 
  - "IdentifiersShouldHaveCorrectPrefix"
  - "CA1715"
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
caps.latest.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 30
---
# CA1715: идентификаторы должны иметь правильные префиксы
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldHaveCorrectPrefix|  
|CheckId|CA1715|  
|Категория|Microsoft.Naming|  
|Критическое изменение|Критическое — если возникает в интерфейсах.<br /><br /> Не критическое — если происходит для параметров универсального типа.|  
  
## Причина  
 Имя доступного для внешнего кода интерфейса не начинается с заглавной буквы "I".  
  
 – или –  
  
 Имя параметра универсального типа в доступном для внешнего кода типе или методе не начинается с заглавной буквы "Т".  
  
## Описание правила  
 В соответствии с соглашением об именовании, имена некоторых элементов программирования начинаются с особого префикса.  
  
 Имена интерфейсов должны начинаться с прописной буквы "I", за которой следует другая прописная буква.  Данное правило сообщает о нарушениях именования интерфейсов, например в именах "MyInterface" и "IsolatedInterface".  
  
 Имена параметров универсального типа должны начинаться с заглавной "T", за которой может следовать другая прописная буква \(необязательно\).  Данное правило сообщает о нарушениях именования универсальных параметров\-типов, например в именах "V" и "Type".  
  
 Соглашения об именах обеспечивают единообразие библиотек, предназначенных для выполнения в среде CLR.  Это позволяет сократить время обучения, необходимое для освоения новых библиотек программного обеспечения, и укрепить уверенность клиента в том, что библиотека была разработана опытным разработчиком управляемого кода.  
  
## Устранение нарушений  
 Переименуйте идентификатор, чтобы он содержал правильный префикс.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример  
 **В следующем примере показан интерфейс с неправильным именем.**  
  
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_1.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_1.vb)]
 [!code-cs[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_1.cs)]  
  
## Пример  
 **В следующем примере нарушение устраняется посредством добавления к имени интерфейса префикса "I".**  
  
 [!code-cs[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_2.cs)]
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_2.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_2.vb)]  
  
## Пример  
 **В следующем примере показан универсальный параметр\-тип с неправильным именем.**  
  
 [!CODE [FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1)]  
  
## Пример  
 **В следующем примере нарушение устраняется посредством добавления к имени универсального параметра\-типа префикса "Т".**  
  
 [!CODE [FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1)]  
  
## Связанные правила  
 [CA1722: идентификаторы не должны иметь неверные префиксы](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)