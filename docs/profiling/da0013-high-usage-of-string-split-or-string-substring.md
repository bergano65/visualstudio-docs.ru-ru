---
title: "DA0013: интенсивное использование String.Split или String.Substring | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.13"
  - "vs.performance.rules.DAAvoidStringSubstr"
  - "vs.performance.DA0013"
  - "vs.performance.rules.DA0013"
helpviewer_keywords: 
  - "vs.performance.13"
  - "vs.performance.rules.DA0013"
ms.assetid: f501f423-bef9-4e08-bf96-c9ac9957e5a2
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0013: интенсивное использование String.Split или String.Substring
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Идентификатор правила|DA0013|  
|Категория|Руководство по использованию .NET Framework|  
|Методы профилирования|Дискретизация|  
|Сообщение|Рекомендуется снизить использование функций String.Split и String.Substring.|  
|Тип правила|Предупреждение|  
  
## Причина  
 Вызовы методов System.String.Split или System.String.Substring составляют значительную часть данных профилирования.  Если выполняется проверка на наличие в строке подстроки, рекомендуется воспользоваться System.String.IndexOf или System.String.IndexOfAny.  
  
## Описание правила  
 Метод Split оперирует со строковым объектом и возвращает новый массив строк, содержащий подстроки исходного.  Функция выделяет память для объекта возвращаемого массива и выделяет новый объект строкового типа для каждого найденного элемента массива.  Аналогичным образом, метод Substr оперирует объектом String и возвращает новый объект String, эквивалентный запрошенной подстроке.  
  
 Если в приложении важно управление выделением памяти, следует рассмотреть возможность использования альтернатив методам String.Split и String.Substr.  Например можно использовать метод IndexOf или IndexOfAny для поиска конкретной подстроки в строке символов \(String\) без создания нового экземпляра класса String.  
  
## Анализ предупреждения  
 Дважды щелкните сообщение в окне со списком ошибок, чтобы перейти к [Представление сведений о функции](../profiling/function-details-view.md) данных примера профиля.  Проверьте функции вызова, чтобы найти секции программы, которые наиболее часто используют методы System.String.Split или System.String.Substr.  Если это возможно, следует использовать метод IndexOf или IndexOfAny для поиска конкретной подстроки в строке символов \(String\) без создания нового экземпляра класса String.