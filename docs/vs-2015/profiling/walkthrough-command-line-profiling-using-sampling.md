---
title: Пошаговое руководство. Профилирование из командной строки с помощью выборки | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance tools, command-line tools
ms.assetid: 1d53972f-6f35-4842-8c74-1b627f18c70a
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b46af3a5485f896e1a5014c094646f364876d0d0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752492"
---
# <a name="walkthrough-command-line-profiling-using-sampling"></a>Пошаговое руководство. Профилирование из командной строки с помощью выборки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве показано, как выполнить профилирование приложения с помощью программ командной строки и выборки для выявления проблем производительности.  
  
 В руководстве приводится пошаговое описание процесса профилирования управляемого приложения с помощью программ командной строки. Для поиска и определения проблем производительности приложения используется выборка.  
  
 В этом пошаговом руководстве выполняются следующие действия:  
  
-   профилирование приложения с помощью программ командной строки и выборки;  
  
-   анализ результатов профилирования с выборкой для выявления и исправления проблем производительности.  
  
## <a name="prerequisites"></a>Предварительные требования  
  
-   [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]или [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
-   Средний уровень знания [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)].  
  
-   Средний уровень навыков работы с программами командной строки.  
  
-   Копия [примера PeopleTrax](../profiling/peopletrax-sample-profiling-tools.md).  
  
-   Для работы со сведениями, полученными при профилировании, рекомендуется включить отладочные символы.  
  
## <a name="command-line-profiling-using-the-sampling-method"></a>Профилирование из командной строки с помощью метода выборки  
 Выборка — это метод профилирования, при котором конкретный процесс периодически опрашивается с целью определения активной функции. Полученные данные показывают, как часто функция находилась на вершине стека вызовов при выборочном опросе процесса.  
  
> [!NOTE]
>  Программы командной строки средств профилирования расположены в подкаталоге \Team Tools\Performance Tools каталога установки Visual Studio. На 64-разрядных компьютерах доступны 64- и 32-разрядные версии этих программ. Для использования программ командной строки профилировщика необходимо добавить путь в переменную среды PATH окна командной строки или в саму команду. Дополнительные сведения см. в статье [Указание пути к средствам командной строки](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). PeopleTrax — это 32-разрядное приложение.  
  
#### <a name="to-profile-the-peopletrax-application-by-using-the-sampling-method"></a>Профилирование приложения PeopleTrax с помощью метода выборки  
  
1.  Установите пример приложения PeopleTrax и выполните сборку окончательной версии приложения.  
  
2.  Откройте командную строку и добавьте каталог средств профилирования в локальную переменную среды Path.  
  
3.  Измените рабочую папку на каталог, содержащий двоичные файлы PeopleTrax.  
  
4.  Установите соответствующие переменные среды с помощью следующей команды:  
  
    ```  
    VSPerfCLREnv /sampleon  
    ```  
  
5.  Начните профилирование, запустив файл VSPerfCmd.exe, который является программой командной строки для управления профилировщиком. Запуск приложения и профилировщика в режиме выборки выполняется следующей командой:  
  
    ```  
    VsPerfCmd /start:sample /output:PeopleTraxReport.vsp /launch:PeopleTrax.exe  
    ```  
  
     Процесс профилировщика запускается и присоединяется к процессу PeopleTrax.exe. Процесс профилировщика начинает запись собранных данных профилирования в файл отчета.  
  
6.  Щелкните **Get People** (Получить пользователей).  
  
7.  Щелкните **Export Data** (Экспорт данных).  
  
     В Блокноте откроется новый файл, содержащий данные, экспортированные из приложения **PeopleTrax**.  
  
8.  Закройте Блокнот и приложение **PeopleTrax**.  
  
9. Завершите работу профилировщика. Введите следующую команду:  
  
    ```  
    VSPerfCmd /shutdown  
    ```  
  
10. Сбросьте переменные среды с помощью следующей команды:  
  
    ```  
    VSPerfCLREnv /sampleoff  
    ```  
  
11. Данные профилирования хранятся в VSP-файле. Проанализировать результаты можно одним из указанных ниже способов.  
  
    -   Откройте VSP-файл в интегрированной среде разработки Visual Studio.  
  
         Или...  
  
    -   Создайте файл значений, разделенных запятыми (CSV), с помощью программы командной строки VSPerfReport.exe. Для создания отчетов с целью использования вне интегрированной среды разработки [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] используйте следующую команду:  
  
        ```  
        VSPerfReport <dir> PeopleTraxReport.vsp /output:<dir> /summary:all  
        ```  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о сеансе анализа производительности](../profiling/performance-session-overview.md)   
 [Профилирование из командной строки](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Общие сведения о значениях выборочных данных](../profiling/understanding-sampling-data-values.md)   
 [Представления отчетов о производительности](../profiling/performance-report-views.md)



