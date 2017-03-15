---
title: "CA1017: помечайте сборки атрибутом ComVisibleAttribute | Microsoft Docs"
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
  - "CA1017"
  - "MarkAssembliesWithComVisible"
helpviewer_keywords: 
  - "MarkAssembliesWithComVisible"
  - "CA1017"
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1017: помечайте сборки атрибутом ComVisibleAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAssembliesWithComVisible|  
|CheckId|CA1017|  
|Категория|Microsoft.Design|  
|Критическое изменение|Не критическое|  
  
## Причина  
 К сборке не применен атрибут <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>.  
  
## Описание правила  
 Атрибут <xref:System.Runtime.InteropServices.ComVisibleAttribute> определяет, как клиенты COM получают доступ к управляемому коду.  Для правильной разработки сборки должны явным образом указывать видимость COM.  Можно задать видимость COM для всей сборки, а затем переопределить ее для отдельных типов и элементов типов.  Если атрибут отсутствует, содержимое сборки будет видимым клиентам COM.  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правила, добавьте атрибут к сборке.  Если требуется, чтобы сборка не была видимой клиентам COM, примените атрибут и присвойте ему значение `false`.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  Чтобы сделать сборку видимой, примените атрибут и присвойте ему значение `true`.  
  
## Пример  
 В следующем примере демонстрируется сборка с примененным атрибутом <xref:System.Runtime.InteropServices.ComVisibleAttribute>, который делает ее невидимой для клиентов COM.  
  
 [!code-cpp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CPP/ca1017-mark-assemblies-with-comvisibleattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/VisualBasic/ca1017-mark-assemblies-with-comvisibleattribute_1.vb)]
 [!code-cs[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CSharp/ca1017-mark-assemblies-with-comvisibleattribute_1.cs)]  
  
## См. также  
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Qualifying .NET Types for Interoperation](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)