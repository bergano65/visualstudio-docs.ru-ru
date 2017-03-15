---
title: "CA1308: строки следует нормализовать в верхнем регистре | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1308"
  - "NormalizeStringsToUppercase"
helpviewer_keywords: 
  - "NormalizeStringsToUppercase"
  - "CA1308"
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA1308: строки следует нормализовать в верхнем регистре
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|NormalizeStringsToUppercase|  
|CheckId|CA1308|  
|Категория|Microsoft.Globalization|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Операция нормализует строку в нижний регистр.  
  
## Описание правила  
 Строки следует нормализовать в верхний регистр.  Существует небольшая группа символов, которые после преобразования в нижний регистр не могут участвовать в круговом перемещении.  Выполнение кругового пути подразумевает преобразование символов из одного языкового стандарта в другой, в котором символьные данные представляются иначе, а затем точное извлечение исходных символов из преобразованных.  
  
## Устранение нарушений  
 Измените операции, преобразующие строки в нижний регистр, чтобы строки преобразовывались в верхний регистр.  Например, измените `String.ToLower(CultureInfo.InvariantCulture)` на `String.ToUpper(CultureInfo.InvariantCulture)`.  
  
## Отключение предупреждений  
 Можно отключать предупреждение, если от результата не зависит решение в области безопасности, например когда он отображается в пользовательском интерфейсе.  
  
## См. также  
 [Предупреждения глобализации](../code-quality/globalization-warnings.md)