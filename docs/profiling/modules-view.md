---
title: Представление "Модули" | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.modules
helpviewer_keywords:
- Modules view
- profiling tools reports, Modules view
- profiling tools, Modules view
ms.assetid: 4314a404-2120-425b-be42-180cd4bac840
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e34640a06fb231aad0cf0a48ebc001ef7e1b597a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54979105"
---
# <a name="modules-view"></a>Представление "Модули"
В представлении "Модули" перечисляются модули данных профилирования. Каждый модуль представляет собой корневой узел иерархического дерева. Профилируемые функции модуля указываются в узле модуля. Если данные профилирования собирались с помощью метода выборки, сведения о строке указываются в узле функции, а данные указателя на инструкцию — в узле строки.  
  
 Чтобы отобразить или свернуть данные о производительности модуля, следует развернуть или скрыть имя модуля.  
  
 Чтобы добавить или удалить столбцы, щелкните правой кнопкой мыши в окне отчета и выберите команду **Добавить или удалить столбцы**. Щелкнув имя столбца, можно сортировать данные. Дополнительные сведения см. в разделе [Как Настройка столбцов представлений отчета](../profiling/how-to-customize-report-view-columns.md).  
  
 Столбцы, доступные в представлении "Модули", зависят от метода профилирования (выборка или инструментирование), использовавшегося для сбора данных, а также от того, были ли собраны данные памяти .NET в ходе сеанса профилирования.  
  
## <a name="see-also"></a>См. также  
 [Представление "Модули"](../profiling/modules-view-sampling-data.md)   
 [Представление "Модули"](../profiling/modules-view-instrumentation-data.md)   
 [Представление "Модули" — инструментирование](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Представление "Модули" — выборка](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Представление "Модули"](../profiling/modules-view-contention-data.md)