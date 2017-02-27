---
title: "CA2242: правильно выполняйте проверку NaN | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TestForNaNCorrectly"
  - "CA2242"
helpviewer_keywords: 
  - "CA2242"
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA2242: правильно выполняйте проверку NaN
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TestForNaNCorrectly|  
|CheckId|CA2242|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Выражение проверяет значение на равенство <xref:System.Single.Nan?displayProperty=fullName> или <xref:System.Double.Nan?displayProperty=fullName>.  
  
## Описание правила  
 Значение <xref:System.Double.NaN?displayProperty=fullName>, представляющее не число, возвращается, если арифметическая операция не определена.  Любое выражение, которое проверяет равенство значения и <xref:System.Double.NaN?displayProperty=fullName>, всегда возвращает `false`.  Любое выражение, которое проверяет неравенство значения и <xref:System.Double.NaN?displayProperty=fullName>, всегда возвращает `true`.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила и точно сравнить значение с <xref:System.Double.NaN?displayProperty=fullName>, используйте для проверки этого значения метод <xref:System.Single.IsNan%2A?displayProperty=fullName> или <xref:System.Double.IsNan%2A?displayProperty=fullName>.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример  
 В следующем пример показаны два выражения, которые неправильно сравнивают значение с <xref:System.Double.NaN?displayProperty=fullName>, и еще одно выражение, правильно использующее метод <xref:System.Double.IsNaN%2A?displayProperty=fullName> для проверки значения.  
  
 [!code-vb[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/VisualBasic/ca2242-test-for-nan-correctly_1.vb)]
 [!code-cs[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/CSharp/ca2242-test-for-nan-correctly_1.cs)]