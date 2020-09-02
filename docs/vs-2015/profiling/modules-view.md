---
title: Представление "Модули" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.modules
helpviewer_keywords:
- Modules view
- profiling tools reports, Modules view
- profiling tools, Modules view
ms.assetid: 4314a404-2120-425b-be42-180cd4bac840
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d396aec92b43aebca9b398c6d481962138354e0e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195609"
---
# <a name="modules-view"></a>Представление "Модули"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В представлении "Модули" перечисляются модули данных профилирования. Каждый модуль представляет собой корневой узел иерархического дерева. Профилируемые функции модуля указываются в узле модуля. Если данные профилирования собирались с помощью метода выборки, сведения о строке указываются в узле функции, а данные указателя на инструкцию — в узле строки.  
  
 Чтобы отобразить или свернуть данные о производительности модуля, следует отобразить или закрыть имя модуля.  
  
 Чтобы добавить или удалить столбцы, щелкните правой кнопкой мыши в окне отчета и выберите команду **Добавить или удалить столбцы**. Щелкнув имя столбца, можно сортировать данные. Дополнительные сведения см. в статье [How to: Customize Report View Columns](../profiling/how-to-customize-report-view-columns.md) (Практическое руководство. Настройка столбцов представлений отчета).  
  
 Столбцы, доступные в представлении "Модули", зависят от метода профилирования (выборка или инструментирование), использовавшегося для сбора данных, а также от того, были ли собраны данные памяти .NET в ходе сеанса профилирования.  
  
## <a name="see-also"></a>См. также:  
 [Представление "модули"](../profiling/modules-view-sampling-data.md)   
 [Представление "модули"](../profiling/modules-view-instrumentation-data.md)   
 [Представление "модули" — инструментирование](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Представление "модули" — выборка](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Представление "Модули"](../profiling/modules-view-contention-data.md)
