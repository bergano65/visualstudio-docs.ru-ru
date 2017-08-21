---
title: "PerfTips | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 509d2d4f-48a5-4cdf-acad-6f7b75421303
caps.latest.revision: 6
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
ms.translationtype: HT
ms.sourcegitcommit: 8a544bd1e1242bb6fabe00f7842ac33ed9d9d444
ms.openlocfilehash: b19a309f403daa0a3881ec154aa4cd3f5e4d97dc
ms.contentlocale: ru-ru
ms.lasthandoff: 08/14/2017

---
# <a name="perftips"></a>PerfTips
С помощью подсказок *PerfTips* , отображаемых в отладчике Visual Studio, а также встроенных в отладчик **средств диагностики** вы можете отслеживать и анализировать производительность вашего приложения во время отладки.  
  
 Несмотря на то, что встроенные в отладчик средства диагностики — это отличный способ оценить производительность приложения во время разработки, работа отладчика может существенно сказаться на показателях программы. Чтобы получить более точные данные о производительности, попробуйте дополнительно проанализировать программу с помощью средств диагностики Visual Studio, не встроенных в отладчик. См. статью [Running Profiling Tools with or without the Debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md) (Выполнение средств профилирования с отладчиком или без него).  
  
## <a name="perftips"></a>PerfTips  
 При остановке выполнения отладчика на точке останова или при завершения шага в окне редактора отображается время, прошедшее от предыдущей точки останова до прерывания. Дополнительные сведения см. в записи блога [PerfTips: информация о производительности при отладке с помощью Visual Studio](http://blogs.msdn.com/b/visualstudioalm/archive/2014/08/18/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio.aspx).  
  
 ![PerfTip](../profiling/media/dbgdiag_perf_perftip.png "DBGDIAG_PERF_PerfTip")  
  
## <a name="diagnostics-tools-window"></a>Окно "Средства диагностики"  
 Точки останова и связанные с ними данные о времени отображаются в окне "Средства диагностики".  
  
 На рисунке ниже показано окно "Средства диагностики в Visual Studio 2015 с обновлением 1.  
  
 ![DiagnosticTools: обновление 1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")  
  
-   На временной шкале **События прерывания** отмечаются точки останова, достигнутые за сеанс отладки. Щелкните событие, чтобы выбрать его в списке сведений **отладчика** .  
  
-   Граф **Использование ЦП** отображает изменения нагрузки на все ядра ЦП во время сеанса отладки.  
  
-   В списке **События** , расположенном в области сведений **отладчика** , отображаются все события прерывания.  
  
-   В столбце **Длительность** для каждого события прерывания отображается время, прошедшее до него от последней точки останова.  
  
## <a name="turn-perftips-on-or-off"></a>Включение и отключение PerfTips  
 Чтобы включить или отключить подсказки PerfTips, сделайте следующее:  
  
1.  В меню **Отладка** выберите пункт **Параметры**.  
  
2.  Установите или снимите флажок **Показывать подсказку с затраченным временем при отладке**.  
  
## <a name="turn-the-diagnostic-tools-window-on-or-off"></a>Включение и отключение окна "Средства диагностики"  
 Чтобы включить или отключить окно "Средства диагностики", сделайте следующее:  
  
1.  В меню **Отладка** выберите пункт **Параметры**.  
  
2.  Установите или снимите флажок **Включить средства диагностики при отладке**.

## <a name="see-also"></a>См. также
 [Профилирование в Visual Studio](../profiling/index.md) [Обзор возможностей профилирования](../profiling/profiling-feature-tour.md)

