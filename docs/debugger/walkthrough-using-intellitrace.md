---
title: Просмотр событий с помощью IntelliTrace | Документы Microsoft
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
ms.openlocfilehash: 3fd43297dcf6a15e7d064809a5c4b5091f51ac63
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="view-events-with-intellitrace-in-visual-studio"></a>Просмотр событий с помощью IntelliTrace в Visual Studio
IntelliTrace можно использовать для сбора сведений о конкретных событиях или категориях событий, а также об отдельных вызовах функций в дополнение к событиям. Процедура приведена ниже.  
  
 IntelliTrace можно использовать в выпуске Visual Studio Enterprise, но не в выпусках Professional или Community.  
  
##  <a name="GettingStarted"></a> Настройка Intellitrace  
 Вы можете попробовать выполнить отладку только с помощью событий IntelliTrace. События IntelliTrace — это события отладчика, исключения, события .NET Framework и другие системные события. До начала отладки следует включить или отключить определенные события в зависимости от того, должно ли их записывать средство IntelliTrace. Дополнительные сведения см. в разделе [возможности IntelliTrace](../debugger/intellitrace-features.md).  
  
 - Включите событие IntelliTrace для доступа к файлам. Последовательно выберите пункты **Сервис > Параметры > IntelliTrace > события IntelliTrace** и разверните **файл** категории. Установите флажок напротив категории событий **Файл** . Будут проверены все события, связанные с файлами (доступ, закрытие, удаление).

## <a name="create-your-app"></a>Создание приложения
  
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

## <a name="start-debugging-and-view-intellitrace-events"></a>Начните отладку и просмотреть события IntelliTrace
  
1.  Запустите отладку обычным образом. (Нажмите клавишу **F5** или нажмите кнопку **Отладка > Начать отладку**.  
  
    > [!TIP]
    >  Сохранить **локальные** и **видимые** открытыми во время отладки, чтобы просматривать и записывать значения в этих окнах.  
  
2.  Выполнение прекратится в точке останова. Если вы не видите **средства диагностики** окно, нажмите кнопку **Отладка > Windows > события IntelliTrace**.  
  
     В окне **Средства диагностики** найдите вкладку **События** (должны появиться три вкладки: **События**, **Использование памяти**и **Использование ЦП**). На вкладке **События** показан хронологический список событий, заканчивающийся последним событием перед завершением выполнения отладчика. Должно иметься событие **Доступ к WordSearchInputs.txt**.  
  
     Приведенный ниже снимок экрана сделан в Visual Studio 2015 с обновлением 1.  
  
     ![IntelliTrace&#45;Update1](../debugger/media/intellitrace-update1.png "IntelliTrace-Update1")  
  
3.  Выберите событие и просмотрите подробности о нем.  
  
     Приведенный ниже снимок экрана сделан в Visual Studio 2015 с обновлением 1.  
  
     ![IntelliTraceUpdate1&#45;SingleEvent](../debugger/media/intellitraceupdate1-singleevent.png "IntelliTraceUpdate1 SingleEvent")  
  
     Вы можете щелкнуть ссылку пути, чтобы открыть файл. Если полный путь недоступен, откроется диалоговое окно **Открыть файл** .  
  
     Нажмите кнопку **Активировать отладку с ведением журнала**, присваивающего в контексте отладчика время, когда выбранное событие было собрано данные журнала **стек вызовов**, **Локальныепеременные** и других отобразятся окна отладчика. Если исходный код доступен, Visual Studio перемещает указатель на соответствующий код в окне источника, чтобы вы могли его изучить.  
  
     Приведенный ниже снимок экрана сделан в Visual Studio 2015 с обновлением 1.  
  
     ![HistoricalDebugging&#45;обновление 1](../debugger/media/historicaldebugging-update1.png "обновление 1 HistoricalDebugging")  
  
4.  Если ошибка не найдена, попробуйте изучить другие события, которые предположительно ее вызвали. Вы также можете просмотреть сведения о вызове записи IntelliTrace и выполнить вызовы функций по шагам. 
  
## <a name="next-steps"></a>Следующие шаги

Можно использовать некоторые расширенные функции IntelliTrace отладки с ведением журнала:

 - Просмотреть моментальные снимки [моментальных снимков с помощью IntelliTrace шаг обратного просмотра](../debugger/how-to-use-intellitrace-step-back.md)
 - Чтобы узнать, как для проверки переменных и перемещаться по коду, см. [проверки приложения отладки с ведением журнала](../debugger/historical-debugging-inspect-app.md)