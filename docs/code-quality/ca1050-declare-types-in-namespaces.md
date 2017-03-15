---
title: "CA1050: объявляйте типы в пространствах имен | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1050"
  - "DeclareTypesInNamespaces"
helpviewer_keywords: 
  - "CA1050"
  - "DeclareTypesInNamespaces"
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1050: объявляйте типы в пространствах имен
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DeclareTypesInNamespaces|  
|CheckId|CA1050|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Открытый или защищенный тип определен вне области именованного пространства имен.  
  
## Описание правила  
 Типы объявляются в пространствах имен во избежание конфликтов имен и с целью упорядочения связанных типов в иерархии объектов.  Типы, не входящие в именованные пространства имен, находятся в глобальном пространстве имен, на которое нельзя ссылаться в коде.  
  
## Устранение нарушений  
 Чтобы исправить нарушение этого правила, поместите тип в пространство имен.  
  
## Отключение предупреждений  
 Хотя нет необходимости отключать предупреждения этого правила, но это можно сделать в том случае, если сборка никогда не будет использована с другими сборками.  
  
## Пример  
 В следующих примерах показана библиотека с типом, неправильно объявленным вне пространства имен, и с одноименным типом, объявленным в пространстве имен.  
  
 [!code-cs[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_1.cs)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_1.vb)]  
  
## Пример  
 Следующее приложение использует библиотеку, которая была определена ранее.  Обратите внимание, что тип, объявленный вне пространства имен, создается, когда имя `Test` не является полным именем с пространством имен.  Также обратите внимание, что для доступа к `Test` в `Goodspace` требуется имя пространства имен.  
  
 [!CODE [FxCop.Design.TestTypesLive#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive#1)]