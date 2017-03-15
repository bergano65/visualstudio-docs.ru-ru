---
title: "CA1814: используйте ступенчатые массивы вместо многомерных | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PreferJaggedArraysOverMultidimensional"
  - "CA1814"
helpviewer_keywords: 
  - "CA1814"
  - "PreferJaggedArraysOverMultidimensional"
ms.assetid: b1ccf563-2ec8-42e5-b89c-731a9de1ea1d
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA1814: используйте ступенчатые массивы вместо многомерных
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PreferJaggedArraysOverMultidimensional|  
|CheckId|CA1814|  
|Категория|Microsoft.Performance|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Член объявлен как многомерный массив.  
  
## Описание правила  
 Массив массивов — это массив, элементы которого сами являются массивами.  Массивы, которые составляют элементы, могут иметь различные размеры, что позволяет экономить пространство для некоторых наборов данных.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, преобразуйте многомерный массив в массив массивов.  
  
## Отключение предупреждений  
 Если использование многомерного пространства не приводит к чрезмерному использованию пространства, предупреждения о нарушении данного правила можно отключить.  
  
## Пример  
 В следующем примере демонстрируется объявления массива массивов и многомерного массива.  
  
 [!code-vb[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/VisualBasic/ca1814-prefer-jagged-arrays-over-multidimensional_1.vb)]
 [!code-cs[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/CSharp/ca1814-prefer-jagged-arrays-over-multidimensional_1.cs)]