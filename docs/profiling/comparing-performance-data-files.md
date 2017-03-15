---
title: "Сравнение файлов данных о производительности | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling tools, comparing profiling tools report files
- profiling tools reports, comparing
ms.assetid: e6fda144-f21d-4912-9d16-1b8d3555a210
caps.latest.revision: 12
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
ms.openlocfilehash: 9a0b4dcb86aa4241d223dd4a1172267dd8ec20da
ms.lasthandoff: 02/22/2017

---
# <a name="comparing-performance-data-files"></a>Сравнение файлов данных о производительности
Функция сравнения файлов данных средств профилирования позволяет выбрать два файла отчетов (VSP или VSPS) и создать отчет, в котором будут показаны различия и случаи снижения и повышения производительности в двух последовательных сеансах профилирования.  
  
 В отчете о сравнении файлов данных средств профилирования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] сравниваются результаты анализа в одном файле данных профилирования с базовыми результатами анализа в другом файле данных. Оба файла данных необходимо создавать с помощью одного и того же метода профилирования. Отчет о таком сравнении сохраняется в VSPS-файле.  
  
 В отчете о сравнении измененные данные представляются в табличном виде. В таблице показаны изменившиеся данные или отклонение от базового значения. Это отклонение вычисляется на основе разности между старым (базовым) значением и результатом нового анализа.  
  
 Сравнение данных профилирования может выполняться на основе функций кода, модулей приложения, строк, указателей инструкций и типов.  
  
 Доступные для сравнения данные профилирования включают сведения, отображаемые в столбцах. Определения имен этих столбцов см. в статье [Performance Report Views](../profiling/performance-report-views.md) (Представления отчетов о производительности).  
  
 Для снижения шума и фильтрации данных в строках таблицы сравнения, которые не изменились по сравнению с указанным значением, можно установить порог.  
  
## <a name="in-this-section"></a>Содержание  
 [Практическое руководство. Сравнение файлов данных о производительности](../profiling/how-to-compare-performance-data-files.md)
