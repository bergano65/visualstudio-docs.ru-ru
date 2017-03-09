---
title: "CA1014: помечайте сборки атрибутом CLSCompliantAttribute | Microsoft Docs"
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
  - "CA1014"
  - "MarkAssembliesWithClsCompliant"
helpviewer_keywords: 
  - "CA1014"
  - "MarkAssembliesWithClsCompliant"
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1014: помечайте сборки атрибутом CLSCompliantAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAssembliesWithClsCompliant|  
|CheckId|CA1014|  
|Категория|Microsoft.Design|  
|Критическое изменение|Не критическое|  
  
## Причина  
 К сборке не применен атрибут <xref:System.CLSCompliantAttribute?displayProperty=fullName>.  
  
## Описание правила  
 Спецификация среды CLS определяет ограничения по именованию, типам данных и правилам, которым должны соответствовать сборки, предназначенные для использования в нескольких языках программирования.  Для всех сборок нужно явным образом указывать совместимость с CLS, для этого служит атрибут <xref:System.CLSCompliantAttribute>.  Если атрибут отсутствует у сборки, она не является совместимой.  
  
 Сборка, совместимая с CLS, может содержать несовместимые типы или члены типов.  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правила, добавьте атрибут к сборке.  Вместо того, чтобы помечать всю сборку как несовместимую, нужно определить, какие типы или члены типов не являются совместимыми и пометить их.  Если это возможно, то для всех несовместимых членов следует предоставить замену, совместимую с CLS.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  Если не требуется, чтобы сборка была совместимой, примените этот атрибут и установите для него значение `false`.  
  
## Пример  
 В следующем примере кода показана сборка с атрибутом <xref:System.CLSCompliantAttribute?displayProperty=fullName>, объявляющим ее совместимой с CLS.  
  
 [!code-cs[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CSharp/ca1014-mark-assemblies-with-clscompliantattribute_1.cs)]
 [!code-cpp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CPP/ca1014-mark-assemblies-with-clscompliantattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/VisualBasic/ca1014-mark-assemblies-with-clscompliantattribute_1.vb)]  
  
## См. также  
 <xref:System.CLSCompliantAttribute?displayProperty=fullName>   
 [Независимость от языка и независимые от языка компоненты](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)