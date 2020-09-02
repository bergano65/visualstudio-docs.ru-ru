---
title: Представление "Строки" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.lines
helpviewer_keywords:
- profiling tools reports, Line view
- profiling tools, Line view
- Lines view
ms.assetid: 71ec0781-6031-4e17-af09-f50226018437
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ccdb211312a6f53e7f519b7fac0e3ac28aab2429
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145625"
---
# <a name="lines-view"></a>Представление строк
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Представление "Строки" доступно только для данных профилировщика, собранных с использованием метода выборки. Представление недоступно для данных, собранных с использованием инструментирования.  
  
 Для данных выборочного профиля представление "Строки" определяет оператор в функции, которая непосредственно выполнялась в момент получения выборки. Для данных памяти .NET представление "Строки" определяет операторы, выделяющие память.  
  
 В исходном файле оператор может занимать несколько строк, а одна строка может включать несколько операторов.  
  
 Оператор определяется следующими данными:  
  
- исходным файлом, который содержит оператор функции;  
  
- функцией, содержащей оператор;  
  
- исходной строкой, с которой начинается оператор;  
  
- знаком исходной строки, с которой начинается оператор;  
  
- исходной строкой, которой заканчивается оператор;  
  
- знаком исходной строки, которой заканчивается оператор.  
  
## <a name="see-also"></a>См. также:  
 [Представление "строки"](../profiling/lines-view-sampling-data.md)   
 [Представление "строки" — выборка](../profiling/lines-view-dotnet-memory-sampling-data.md)   
 [Представление строк](../profiling/lines-view-contention-data.md)
