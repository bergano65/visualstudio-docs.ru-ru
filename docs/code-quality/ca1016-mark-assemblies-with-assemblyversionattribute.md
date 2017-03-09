---
title: "CA1016: помечать сборки атрибутом AssemblyVersionAttribute | Microsoft Docs"
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
  - "MarkAssembliesWithAssemblyVersion"
  - "CA1016"
helpviewer_keywords: 
  - "CA1016"
  - "MarkAssembliesWithAssemblyVersion"
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1016: помечать сборки атрибутом AssemblyVersionAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAssembliesWithAssemblyVersion|  
|CheckId|CA1016|  
|Категория|Microsoft.Design|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Сборка не имеет номера версии.  
  
## Описание правила  
 Сборка идентифицируется следующими сведениями.  
  
-   Имя сборки  
  
-   Номер версии  
  
-   Язык и региональные параметры  
  
-   Открытый ключ \(для строго именованных сборок\).  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] использует номер версии для уникального обозначения сборки и для привязки к типам в сборках со строгими именами.  Номер версии используется наряду с политикой версий и издателя.  По умолчанию приложения выполняются только с версией сборки, которая использовалась для их построения.  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правила, добавьте номер версии к сборке с помощью атрибута <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName>.  См. следующий пример.  
  
## Отключение предупреждений  
 Не отключайте предупреждение из этого правила для сборок, используемых сторонними лицами или в производственной среде.  
  
## Пример  
 В следующем примере показана сборка с примененным параметром <xref:System.Reflection.AssemblyVersionAttribute>.  
  
 [!code-cs[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CSharp/ca1016-mark-assemblies-with-assemblyversionattribute_1.cs)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/VisualBasic/ca1016-mark-assemblies-with-assemblyversionattribute_1.vb)]
 [!code-cpp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CPP/ca1016-mark-assemblies-with-assemblyversionattribute_1.cpp)]  
  
## См. также  
 [Управление версиями сборок](../Topic/Assembly%20Versioning.md)   
 [Практическое руководство. Создание политики издателя](../Topic/How%20to:%20Create%20a%20Publisher%20Policy.md)