---
title: Практическое руководство. Инструментирование динамически скомпилированного веб-приложения ASP.NET и сбор данных по использованию памяти с помощью командной строки профилировщика | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2cdd9903-39db-47e8-93dd-5e6a21bc3435
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4693b7e1b0b274c9166bfa4f8d25531433a566bb
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2018
ms.locfileid: "48879311"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>Практическое руководство. Инструментирование динамически скомпилированного веб-приложения ASP.NET и сбор данных об использовании памяти с помощью командной строки профилировщика
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: инструментирование динамически скомпилированные веб-приложения ASP.NET и сбор данных памяти с помощью командной строки Profiler](https://docs.microsoft.com/visualstudio/profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line).  
  
В этом разделе описывается использование программ командной строки средств профилирования [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] для сбора подробных сведений о времени существования объектов и выделении памяти .NET для динамически скомпилированного веб-приложения [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] с помощью метода профилирования с инструментированием.  
  
> [!NOTE]
>  Программы командной строки средств профилирования расположены в подкаталоге \Team Tools\Performance Tools каталога установки [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. На 64-разрядных компьютерах доступны 64- и 32-разрядные версии этих программ. Для использования программ командной строки профилировщика необходимо добавить путь к программам в переменную среды PATH окна командной строки или в саму команду. Дополнительные сведения см. в статье [Указание пути к средствам командной строки](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Чтобы собрать данные о производительности из веб-приложения [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], следует изменить файл web.config для этого приложения, разрешив использование средства [VSInstr.exe](../profiling/vsinstr.md) для инструментирования динамически компилируемых файлов приложения. Затем с помощью программы [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) нужно настроить сервер, на котором размещено веб-приложение [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], и включить профилирование памяти .NET, задав соответствующие переменные среды, и перезагрузить компьютер.  
  
 Чтобы начать сбор данных, запустите профилировщик, а затем целевое приложение. Пока профилировщик присоединен к приложению, сбор данных можно приостанавливать и возобновлять. Собрав необходимые данные, закройте приложение, рабочий процесс служб IIS, а затем завершите работу профилировщика.  
  
 Когда работа по профилированию будет завершена, восстановите исходное состояние файла web.config и настроек веб-сервера.  
  
## <a name="configuring-the-aspnet-web-application-and-the-web-server"></a>Настройка веб-приложения ASP.NET и веб-сервера  
  
#### <a name="to-configure-the-aspnet-web-application-and-the-web-server"></a>Процедура настройки веб-приложения ASP.NET и веб-сервера  
  
1.  Измените файл web.config для целевого приложения. См. статью [How to: Modify Web.Config Files to Instrument and Profile Dynamically Compiled ASP.NET Web Applications](../profiling/how-to-modify-web-config-files-to-instrument-and-profile-dynamically-compiled-aspnet-web-applications.md) (Практическое руководство. Изменение файлов Web.Config для инструментирования и профилирования динамически скомпилированных веб-приложений ASP.NET).  
  
2.  Откройте окно командной строки на компьютере, на котором размещено веб-приложение.  
  
3.  Инициализируйте переменные среды профилирования. Тип:  
  
     **VSPerfClrEnv /globaltracegc**  
  
     - или -  
  
     **VSPerfClrEnv /globaltracegclife**  
  
    -   **/globaltracegc** включает сбор данных по выделению памяти.  
  
    -   **/globaltracegclife** включает сбор данных по выделению памяти и времени существования объектов.  
  
4.  Перезагрузите компьютер.  
  
## <a name="running-the-profiling-session"></a>Запуск сеанса профилирования  
  
#### <a name="to-profile-the-aspnet-web-application"></a>Профилирование веб-приложения ASP.NET  
  
1.  Запуск профилировщика. Тип:  
  
     **VSPerfCmd** [/start](../profiling/start.md) **:trace** [/output](../profiling/output.md) **:** `OutputFile` [`Options`]  
  
    -   Параметр **/start:trace** инициализирует профилировщик.  
  
    -   Параметр **/output**`OutputFile` является обязательным при использовании параметра **/start**. `OutputFile` указывает имя и расположение файла данных профилирования (VSP-файла).  
  
     С параметром **/start:trace** можно использовать любой из следующих параметров.  
  
    > [!NOTE]
    >  Параметры **/user** и **/crosssession** обычно являются обязательными для приложений ASP.NET.  
  
    |Параметр|Описание:|  
    |------------|-----------------|  
    |[/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Задает необязательный домен и имя пользователя учетной записи, которая является владельцем рабочего процесса [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Этот параметр является обязательным, если процесс выполняется от имени пользователя, отличного от вошедшего в систему. Имя указано в столбце "Имя пользователя" на вкладке "Процессы" диспетчера задач Windows.|  
    |[/crossession](../profiling/crosssession.md)|Включает профилирование процессов в других сеансах. Этот параметр является обязательным, если приложение выполняется в другом сеансе. Идентификатор сеанса указан в столбце "Идентификатор сеанса" на вкладке "Процессы" диспетчера задач Windows. **/CS** можно указать как краткую версию **/crosssession**.|  
    |[/globaloff](../profiling/globalon-and-globaloff.md)|Запускает профилировщик в состоянии приостановки сбора данных. Используйте параметр [/globalon](../profiling/globalon-and-globaloff.md) для возобновления профилирования.|  
    |[/counter](../profiling/counter.md) **:** `Config`|Собирает данные из счетчика производительности процессора, указанного в `Config`. Сведения счетчика добавляются в данные, собранные для каждого события профилирования.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Задает счетчик производительности Windows, данные которого будут собираться во время профилирования.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Используется с только с параметром **/wincounter**. Указывает время (в миллисекундах) между событиями сбора счетчика производительности Windows. Значение по умолчанию — 500 мс.|  
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Задает события трассировки событий для Windows (ETW), собираемые во время профилирования. События трассировки событий Windows собираются в отдельный ETL-файл.|  
  
2.  Запустите приложение [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] обычным образом.  
  
## <a name="controlling-data-collection"></a>Управление сбором данных  
 Пока выполняется целевое приложение, вы можете управлять сбором данных, останавливая и возобновляя процесс записи данных в файл данных профилировщика с помощью параметров **VSPerfCmd.exe**. Управление сбором данных позволяет собирать данные на конкретных этапах выполнения программы, например при запуске или завершении работы приложения.  
  
#### <a name="to-start-and-stop-data-collection"></a>Запуск и остановка сбора данных  
  
-   Следующие пары параметров запускают и останавливают сбор данных. Каждый параметр необходимо указывать в отдельной командной строке. Сбор данных можно включать и отключать несколько раз.  
  
    |Параметр|Описание:|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Запускает (**/globalon**) или останавливает (**/globaloff**) сбор данных для всех процессов.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Запускает (**/processon**) или останавливает (**/processoff**) сбор данных для процесса с указанным идентификатором процесса (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Запускает (**/threadon**) или останавливает (**/threadoff**) сбор данных для потока с указанным идентификатором потока (`TID`).|  
  
-   Можно также использовать параметр **VSPerfCmd.exe**[/mark](../profiling/mark.md) для добавления метки профилирования в файл данных. Команда **/mark** добавляет идентификатор, метку времени и необязательную определяемую пользователем текстовую строку. Метки можно использовать для фильтрации данных в представлениях отчетов и данных профилировщика.  
  
## <a name="ending-the-profiling-session"></a>Завершение сеанса профилирования  
 Для завершения сеанса профилирования закройте целевое веб-приложение [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], остановите службы IIS, чтобы остановить профилируемый процесс, и завершите работу профилировщика. Затем перезапустите службы IIS.  
  
#### <a name="to-end-a-profiling-session"></a>Завершение сеанса профилирования  
  
1.  Закройте веб-приложение [!INCLUDE[vstecasp](../includes/vstecasp-md.md)].  
  
2.  Закройте рабочий процесс [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], сбросив Internet Information Services (IIS). Тип:  
  
     **IISReset /stop**  
  
3.  Завершите работу профилировщика. Тип:  
  
     **VSPerfCmd** [/shutdown](../profiling/shutdown.md)  
  
4.  Перезапустите IIS. Тип:  
  
     **IISReset /start**  
  
## <a name="restoring-the-application-and-computer-configuration"></a>Восстановление конфигурации приложения и компьютера  
 По завершении всех операций профилирования замените файл web.config, удалите значения переменных среды, используемых для профилирования, и перезагрузите компьютер для восстановления исходного состояния сервера и приложения [!INCLUDE[vstecasp](../includes/vstecasp-md.md)].  
  
#### <a name="to-restore-the-application-and-computer-configuration"></a>Восстановление конфигурации приложения и компьютера  
  
1.  Замените файл web.config копией исходного файла.  
  
2.  (Необязательно). Очистите переменные среды, установленные для профилирования. Тип:  
  
     **VSPerfCmd /globaloff**  
  
3.  Перезагрузите компьютер.  
  
## <a name="see-also"></a>См. также  
 [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Представления данных в памяти .NET](../profiling/dotnet-memory-data-views.md)



