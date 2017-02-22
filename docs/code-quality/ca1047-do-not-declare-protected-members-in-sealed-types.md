---
title: "CA1047: не объявляйте защищенные элементы в запечатанных типах | Microsoft Docs"
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
  - "DoNotDeclareProtectedMembersInSealedTypes"
  - "CA1047"
helpviewer_keywords: 
  - "CA1047"
  - "DoNotDeclareProtectedMembersInSealedTypes"
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1047: не объявляйте защищенные элементы в запечатанных типах
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|  
|CheckId|CA1047|  
|Категория|Microsoft.Design|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Открытый тип имеет атрибут `sealed` \(`NotInheritable` в Visual Basic\) и объявляет защищенный член или защищенный вложенный тип.  Это правило не учитывает нарушения для методов <xref:System.Object.Finalize%2A>, для которых такой шаблон обязателен.  
  
## Описание правила  
 Типы объявляют защищенный члены таким образом, чтобы наследующие типы могли получить доступ к члену или переопределить его.  По определению наследование запечатанного типа невозможно, это означает, что вызов защищенных методов для запечатанных типов невозможен.  
  
 Компилятор C\# выдает предупреждение для этой ошибки.  
  
## Устранение нарушений  
 Чтобы исправить нарушение этого правила, измените уровень доступа члена на закрытый или сделайте тип наследуемым.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  Если оставить тип в текущем состоянии, могут возникнуть проблемы обслуживания, а никаких преимуществ это не даст.  
  
## Пример  
 В следующем примере показан тип, который нарушает данное правило.  
  
 [!code-vb[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/VisualBasic/ca1047-do-not-declare-protected-members-in-sealed-types_1.vb)]
 [!code-cs[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/CSharp/ca1047-do-not-declare-protected-members-in-sealed-types_1.cs)]