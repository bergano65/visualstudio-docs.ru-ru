---
title: "Представление &quot;Строки&quot; | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.view.lines
helpviewer_keywords:
- profiling tools reports, Line view
- profiling tools, Line view
- Lines view
ms.assetid: 71ec0781-6031-4e17-af09-f50226018437
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 94bc996fa73de37fadf47fbfce7ff08380cbf85f
ms.lasthandoff: 02/22/2017

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
