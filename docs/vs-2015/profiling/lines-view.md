---
title: Представление "Строки" | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.view.lines
helpviewer_keywords:
- profiling tools reports, Line view
- profiling tools, Line view
- Lines view
ms.assetid: 71ec0781-6031-4e17-af09-f50226018437
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fdf3249974f2e04cc3794c3437b0d31cef7b9ef9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49205144"
---
# <a name="lines-view"></a>Представление строк
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 [Представление "Строки"](../profiling/lines-view-contention-data.md)



