---
title: "CA1011: попробуйте передать базовые типы в качестве параметров | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ConsiderPassingBaseTypesAsParameters"
  - "CA1011"
helpviewer_keywords: 
  - "CA1011"
  - "ConsiderPassingBaseTypesAsParameters"
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1011: попробуйте передать базовые типы в качестве параметров
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ConsiderPassingBaseTypesAsParameters|  
|CheckId|CA1011|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 В объявлении метода содержится формальный параметр, принадлежащий производному типу, тогда как метод вызывает только члены базового типа параметра.  
  
## Описание правила  
 Если в объявлении метода в качестве параметра указан базовый тип, любой тип, производный от базового, можно передать методу в качестве соответствующего аргумента.  Если аргумент используется в основной части метода, конкретное выполнение метода зависит от типа аргумента.  Если дополнительные функции, предоставляемые производным типом, не требуются, то использование базового типа позволит более широко применять данный метод.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, замените тип параметра на базовый тип.  
  
## Отключение предупреждений  
 Отключение предупреждений о нарушении этого правила является безопасным  
  
-   Если этот метод требует определенные функциональные возможности, предоставляемые производным типом  
  
     \- либо \-  
  
-   обеспечить, чтобы только производный тип или более производный тип передавался в метод.  
  
 В таких случаях код будет более устойчивым благодаря строгой проверке типов, обеспечиваемой компилятором и средой выполнения.  
  
## Пример  
 В следующем примере показан метод `ManipulateFileStream`, который может использоваться только с объектом <xref:System.IO.FileStream>, что нарушает данное правило.  Второй метод — `ManipulateAnyStream` — удовлетворяет правилу благодаря замене параметра <xref:System.IO.FileStream> на <xref:System.IO.Stream>.  
  
 [!code-cs[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CSharp/ca1011-consider-passing-base-types-as-parameters_1.cs)]
 [!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CPP/ca1011-consider-passing-base-types-as-parameters_1.cpp)]
 [!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1011-consider-passing-base-types-as-parameters_1.vb)]  
  
## Связанные правила  
 [CA1059: члены не должны предоставлять определенные устойчивые типы](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)