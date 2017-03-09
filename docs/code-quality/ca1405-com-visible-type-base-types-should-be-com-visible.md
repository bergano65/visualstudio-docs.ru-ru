---
title: "CA1405: базовые типы, относящиеся к типу видимых COM-клиенту, должны быть видимыми для COM | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1405"
  - "ComVisibleTypeBaseTypesShouldBeComVisible"
helpviewer_keywords: 
  - "CA1405"
  - "ComVisibleTypeBaseTypesShouldBeComVisible"
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1405: базовые типы, относящиеся к типу видимых COM-клиенту, должны быть видимыми для COM
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|  
|CheckId|CA1405|  
|Категория|Microsoft.Interoperability|  
|Критическое изменение|DependsOnFix|  
  
## Причина  
 Видимый тип модели COM наследует от типа, который не является видимым для COM.  
  
## Описание правила  
 Если тип, видимый для COM, добавляет члены в новую версию, то, чтобы не нарушить работу COM\-клиентов, связанных с текущей версией, необходимо строго следовать определенным правилам.  Для типов, невидимых для COM, следование правилам управления версиями COM при добавлении новых членов не требуется.  Однако, если видимый для COM тип наследует от невидимого для COM типа и предоставляет интерфейс класса <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> или <xref:System.Runtime.InteropServices.ClassInterfaceType> \(по умолчанию\), все открытые члены базового типа \(если только они не помечены как невидимые для COM, что было бы избыточным\) предоставляются клиентам COM.  Если базовый тип добавляет новые члены в последующую версию, работа всех клиентов COM, связанных с интерфейсом класса производного типа, может быть нарушена.  Чтобы снизить вероятность нарушения работы COM\-клиентов, видимые для COM типы должны наследовать только от видимых для COM типов.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, сделайте базовые типы видимыми для COM или производный тип невидимым для COM.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример  
 В следующем примере показан тип, который нарушает данное правило.  
  
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
 [!code-cs[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]  
  
## См. также  
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>   
 [Introducing the Class Interface](http://msdn.microsoft.com/ru-ru/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)