---
title: 'DA0501: средняя загрузка ЦП профилируемым процессом. | Документы Майкрософт'
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
- vs.performance.rules.DA0501
- vs.performance.DA0501
- vs.performance.501
ms.assetid: b01946b4-75e3-47d5-a1a1-cebfae66a3af
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 076afd65d356f319357221c0d33489895311dcc3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51759550"
---
# <a name="da0501-average-cpu-consumption-by-the-process-being-profiled"></a>DA0501: средняя загрузка ЦП профилируемым процессом.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ИД правила | DA501 |  
| Категория | Наблюдение за ресурсами |  
| Метод профилирования | Все |  
| Сообщение | Среднее использование ЦП профилируемым процессом. |  
| Тип правила | Сведения |  
  
 При профилировании с помощью выборки, памяти .NET или методов разрешения конфликтов ресурсов необходимо собрать минимум 10 выборок, чтобы активировать это правило.  
  
## <a name="rule-description"></a>Описание правила  
 Это сообщение указывает долю времени, когда процессор был занят выполнением инструкций, поступающих из приложения. Содержащееся в отчете значение является средним по всем интервалам измерения, в которых профилируемый процесс был активным. Значение может быть больше 100 % на компьютере с несколькими процессорами.  
  
## <a name="how-to-use-rule-data"></a>Использование данных правила  
 Значение правила используется для сравнения производительности разных версий или сборок программы или для анализа производительности приложения в различных сценариях тестирования.



