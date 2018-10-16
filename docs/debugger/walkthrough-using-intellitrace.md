---
title: Просмотр событий с помощью IntelliTrace | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: e1c9c91a-0009-4c4e-9b4f-c9ab3a6022a7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f46113365b66a75d3f9e149181637c79068645ab
ms.sourcegitcommit: a749c287ec7d54148505978e8ca55ccd406b71ee
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/21/2018
ms.locfileid: "46542329"
---
# <a name="view-events-with-intellitrace-in-visual-studio"></a>Просмотр событий с помощью IntelliTrace в Visual Studio
IntelliTrace можно использовать для сбора сведений о конкретных событиях или категориях событий, а также об отдельных вызовах функций в дополнение к событиям. Процедура приведена ниже.  
  
 IntelliTrace можно использовать в выпуске Visual Studio Enterprise, но не выпуск Professional или Community.  
  
##  <a name="GettingStarted"></a> Настройка Intellitrace  
 Вы можете попробовать выполнить отладку только с помощью событий IntelliTrace. События IntelliTrace — это события отладчика, исключения, события .NET Framework и другие системные события. До начала отладки следует включить или отключить определенные события в зависимости от того, должно ли их записывать средство IntelliTrace. Дополнительные сведения см. в разделе [возможности IntelliTrace](../debugger/intellitrace-features.md).  
  
 - Включите событие IntelliTrace для доступа к файлам. Перейдите к **Сервис > Параметры > IntelliTrace > события IntelliTrace** странице, а затем разверните **файл** категории. Установите флажок напротив категории событий **Файл** . Будут проверены все события, связанные с файлами (доступ, закрытие, удаление).

## <a name="create-your-app"></a>Создание нового приложения
  
1.  Создайте консольное приложение C#. В файле Program.cs добавьте следующую инструкцию `using`:  
  
    ```csharp  
    using System.IO;  
    ```  
  
2.  Создайте <xref:System.IO.FileStream> в методе Main, выполните его считывание, закройте его и удалите файл. Добавьте еще одну строку, чтобы задать точку останова:  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        FileStream fs = File.Create("WordSearchInputs.txt");  
        fs.ReadByte();  
        fs.Close();  
        File.Delete("WordSearchInputs.txt");  
  
        Console.WriteLine("done");  
    }  
    ```  
  
3.  Задайте точку останова в `Console.WriteLine("done");`  

## <a name="start-debugging-and-view-intellitrace-events"></a>Начните отладку и просматривать события IntelliTrace
  
1.  Запустите отладку обычным образом. (Нажмите клавишу **F5** или нажмите кнопку **Отладка > Начать отладку**.  
  
    > [!TIP]
    >  Сохранить **"Локальные"** и **"Видимые"** windows открыть при отладке, чтобы просматривать и записывать значения в них.  
  
2.  Выполнение прекратится в точке останова. Если вы не видите **средства диагностики** окно, нажмите кнопку **Отладка > Windows > события IntelliTrace**.  
  
     В окне **Средства диагностики** найдите вкладку **События** (должны появиться три вкладки: **События**, **Использование памяти**и **Использование ЦП**). На вкладке **События** показан хронологический список событий, заканчивающийся последним событием перед завершением выполнения отладчика. Должно иметься событие **Доступ к WordSearchInputs.txt**.  
  
     Приведенный ниже снимок экрана сделан в Visual Studio 2015 с обновлением 1.  
  
     ![IntelliTrace&#45;Update1](../debugger/media/intellitrace-update1.png "IntelliTrace-Update1")  
  
3.  Выберите событие и просмотрите подробности о нем.  
  
     Приведенный ниже снимок экрана сделан в Visual Studio 2015 с обновлением 1.  
  
     ![IntelliTraceUpdate1&#45;SingleEvent](../debugger/media/intellitraceupdate1-singleevent.png "IntelliTraceUpdate1 SingleEvent")  
  
     Вы можете щелкнуть ссылку пути, чтобы открыть файл. Если полный путь недоступен, откроется диалоговое окно **Открыть файл** .  
  
     Нажмите кнопку **Активировать отладку с ведением журнала**, присваивающего контексте отладчика время выбранное событие собранные, данные журнала **стек вызовов**, **"Локальные"** и других отобразятся окна отладчика. Если исходный код доступен, Visual Studio перемещает указатель на соответствующий код в окне источника, чтобы вы могли его изучить.  
  
     Приведенный ниже снимок экрана сделан в Visual Studio 2015 с обновлением 1.  
  
     ![HistoricalDebugging&#45;Update1](../debugger/media/historicaldebugging-update1.png "HistoricalDebugging Update1")  
  
4.  Если ошибка не найдена, попробуйте изучить другие события, которые предположительно ее вызвали. Вы также можете просмотреть сведения о вызове записи IntelliTrace и выполнить вызовы функций по шагам. 
  
## <a name="next-steps"></a>Следующие шаги

Можно использовать некоторые расширенные возможности IntelliTrace отладки с ведением журнала:

 - Чтобы просмотреть моментальные снимки, см. в разделе [проверять предыдущих состояний приложения с помощью IntelliTrace](../debugger/view-historical-application-state.md)
 - Узнайте, как проверять значения переменных и навигации по коду, см. в разделе [проверить свое приложение с помощью отладки с ведением журнала](../debugger/historical-debugging-inspect-app.md)