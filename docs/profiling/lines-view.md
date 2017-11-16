---
title: "Представление \"Строки\" | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.view.lines
helpviewer_keywords:
- profiling tools reports, Line view
- profiling tools, Line view
- Lines view
ms.assetid: 71ec0781-6031-4e17-af09-f50226018437
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fa6492447650be1b7ab9db1725b7146fa808ecc9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="lines-view"></a>Представление строк
Представление "Строки" доступно только для данных профилировщика, собранных с использованием метода выборки. Представление недоступно для данных, собранных с использованием инструментирования.  
  
 Для данных выборочного профиля представление "Строки" определяет оператор в функции, которая непосредственно выполнялась в момент получения выборки. Для данных памяти .NET представление "Строки" определяет операторы, выделяющие память.  
  
 В исходном файле оператор может занимать несколько строк, а одна строка может включать несколько операторов.  
  
 Оператор определяется следующими данными:  
  
-   исходным файлом, который содержит оператор функции;  
  
-   функцией, содержащей оператор;  
  
-   исходной строкой, с которой начинается оператор;  
  
-   знаком исходной строки, с которой начинается оператор;  
  
-   исходной строкой, которой заканчивается оператор;  
  
-   знаком исходной строки, которой заканчивается оператор.  
  
## <a name="see-also"></a>См. также  
 [Представление "Строки"](../profiling/lines-view-sampling-data.md)   
 [Представление "Строки" — выборка](../profiling/lines-view-dotnet-memory-sampling-data.md)   
 [Представление строк](../profiling/lines-view-contention-data.md)