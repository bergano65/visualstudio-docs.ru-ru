---
title: "Возможности IntelliTrace | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliTrace, debugging with events
- IntelliTrace, recording execution history
- debugging [Visual Studio ALM], recording execution history
- IntelliTrace, turn off
- IntelliTrace, navigating event and call history
- IntelliTrace, saving your session
- IntelliTrace, enabling
- IntelliTrace, start debugging
- IntelliTrace, debugging with events and call information
- IntelliTrace, disabling
- IntelliTrace, turn on
- debugging [Visual Studio ALM], IntelliTrace
ms.assetid: 5ccc059c-6097-46b4-9d4b-34236c02d549
caps.latest.revision: "67"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f2ad259a116b1679f1e619dc9d281c114fa086cf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="intellitrace-features"></a>Возможности IntelliTrace
IntelliTrace можно использовать для записи событий и вызовов методов, что позволяет проверять состояние приложения (стек вызовов и значения локальных переменных) на различных этапах выполнения. Просто запустите отладку обычным образом — средство IntelliTrace включено по умолчанию, и вы увидите данные, записываемые IntelliTrace в новом **средства диагностики** под **события** вкладки. Выберите событие и нажмите кнопку **Активировать отладку с ведением журнала** для просмотра стека вызовов и локальные переменные, записанные для этого события.  
  
 Пошаговое описание см. в разделе [Пошаговое руководство: использование IntelliTrace](../debugger/walkthrough-using-intellitrace.md).  
  
 Средство IntelliTrace доступно в выпуске Visual Studio Enterprise, но не в выпусках Visual Studio Professional или Community.  
  
 Чтобы убедиться, что средство IntelliTrace включено, откройте **Сервис > Параметры > IntelliTrace** страница "Параметры". **Включить IntelliTrace** должен быть установлен по умолчанию.  
  
> [!NOTE]
>  Все параметры на область **IntelliTrace** страница "Параметры" — Visual Studio как единое целое, не для отдельных проектов или решений. Изменение этих параметров применяется ко всем экземплярам Visual Studio, всем сеансам отладки и всем проектам и решениям.  
  
##  <a name="ChooseEvents"></a>Выбор событий, записываемых IntelliTrace  
 Можно включить или отключить запись определенных событий IntelliTrace.  
  
 Если выполняется отладка, остановите ее. Последовательно выберите пункты **Сервис > Параметры > IntelliTrace > события IntelliTrace**. Выберите события, которые будет записывать IntelliTrace.  
  
## <a name="Snapshots"></a>Собирать события и моментальные снимки  
 Эта возможность не включена по умолчанию, но IntelliTrace можно делать моментальные снимки для каждой точки останова отладчика шаг события и приложения можно просмотреть эти моментальные снимки в сеанс отладки по журналу. Моментальный снимок позволяет получить представление состояния всего приложения. Для включения отслеживания моментальных снимков, перейдите к **Сервис > Параметры > IntelliTrace > Общие**и выберите **IntelliTrace события и моментальные снимки**. Дополнительные сведения см. в разделе [моментальных снимков с помощью IntelliTrace шаг обратного просмотра](../debugger/how-to-use-intellitrace-step-back.md)

 Моментальные снимки доступны в Visual Studio Enterprise 2017 г. версия 15,5 и более поздних версий и требует Юбилейного обновления Windows 10 или более поздней версии.  Моментальные снимки в настоящее время недоступны для приложений .NET Core и ASP.NET Core.

##  <a name="GoingFurther"></a>Сбор событий IntelliTrace и сведений о вызовах  
 Эта возможность не включена по умолчанию, но IntelliTrace может записывать вызовы методов вместе с событиями. Включить коллекцию методов, последовательно щелкните вызовы **Сервис > Параметры > IntelliTrace > Общие**и выберите **события IntelliTrace и сведений о вызовах**.

 Сведения о вызовах в настоящее время недоступен для приложений .NET Core и ASP.NET Core. 
  
 Это позволит увидеть журнал стека вызовов и переходить по вызовам в вашем коде. IntelliTrace записывает такие данные, как имена методов, точки входа и выхода методов и определенные значения параметров, а также возвращаемые значения.  
  
> [!TIP]
>  Этот параметр не включен по умолчанию, поскольку он связан со значительными издержками. IntelliTrace позволяет не только перехватывать каждый вызов метода, осуществляемый приложением, но и обрабатывать наборы данных значительного размера в случае необходимости их отображения на экране или сохранения на диск.  
>   
>  Чтобы снизить издержки на производительность, можно ограничить список событий, записываемых IntelliTrace, и поддерживать минимальное количество собираемых модулей. Дополнительные сведения см. в разделе [Управление объемом сведений о вызовах IntelliTrace записывает](../debugger/intellitrace-features.md#ControlCallData).  
  
### <a name="use-the-navigation-gutter"></a>Использовать области навигации  
 Можно использовать области навигации, которая отображается слева от окна кода. Если вы не видите области навигации, перейдите к **Сервис > Параметры > IntelliTrace > Дополнительно**и выберите **отображать область навигации в режиме отладки**.  
  
 В области навигации в режиме отладки с ведением журнала можно перемещаться вперед и назад по вызовам методов и событиям. Дополнительные сведения об отладке с ведением журнала см. в разделе [отладка с ведением журнала](../debugger/historical-debugging.md). Здесь доступен ряд команд.  
  
|||  
|-|-|  
|**Задать контекст отладчика здесь**|Задает контексту отладки временной интервал вызова, в котором он отображается.<br /><br /> Значок отображается только на текущем стеке вызовов.|  
|**Вернуться к месту вызова**|Перемещает указатель и контекст отладки назад в тот момент, где была вызвана текущая функция.<br /><br /> Если вы находитесь в динамическом режиме отладки, эта команда включает отладку с ведением журнала. Если перейти в исходное место прерывания выполнения, отладка с ведением журнала отключается и включается режим динамической отладки.|  
|**Перейти к предыдущему вызову или событию IntelliTrace**|Перемещает указатель и контекст отладки назад к предыдущему вызову или событию.<br /><br /> Если вы находитесь в динамическом режиме отладки, эта команда включает отладку с ведением журнала.|  
|**Шаг в**|Выполняет шаг с заходом в текущую выбранную функцию.<br /><br /> Эта команда доступна только в режиме отладки с ведением журнала.|  
|**Перейти к следующему вызову или событию IntelliTrace**|Перемещает указатель и контекст отладки к следующему вызову или событию, для которого имеются данные IntelliTrace.<br /><br /> Эта команда доступна только в режиме отладки с ведением журнала.|  
|**Перейти в динамический режим**|Возврат в динамический режим отладки.|  
  
### <a name="search-for-a-line-or-method-in-intellitrace"></a>Найти строку или метод в IntelliTrace  
 Поиск методов можно осуществлять только в том случае, если были включены сведения о вызовах метода. Можно выполнить поиск конкретной строки или метода в журнале IntelliTrace. Во время выполнения отладчик прерывается, щелкните правой кнопкой мыши в теле функции, чтобы открыть контекстное меню и выберите либо **поиск этой строки в IntelliTrace** или **поиска этот метод в IntelliTrace**.  
  
###  <a name="ControlCallData"></a>Управление объемом сведений о вызовах IntelliTrace записывает  
 По умолчанию IntelliTrace записывает сведения для всех модулей, используемых в решении. IntelliTrace можно настроить для записи сведений о вызовах только в представляющих интерес модулях. В **Сервис > Параметры > IntelliTrace > модули**, вы можете указать модули, включаемые или модулей, чтобы исключить из IntelliTrace. IntelliTrace будет собирать только события, источниками которых являются указанные модули, и вызовы методов, выполненные в представляющих интерес модулях.  
  
 Чтобы добавить несколько модулей, используйте подстановочный знак * в начале или конце строки. В качестве имени модуля используйте имя файла, а не имя сборки. Пути к файлам не принимаются.  
  
 Попытайтесь свести число модулей к минимуму. Поскольку в этом случае уменьшается объем собираемых данных, уровень производительности повышается. Кроме того, в пользовательском интерфейсе снижается уровень шума.  
  
##  <a name="SaveSession"></a>Сохранять данные IntelliTrace в файл  
 Можно сохранить данные, собранные IntelliTrace будет **Отладка > IntelliTrace > Сохранение сеанса IntelliTrace** во время отладки и приложение находится в состоянии разрыва. Если приложение все еще выполняется или отладка остановлена, пункт меню будет отключен и сохранить данные, собранные IntelliTrace, будет невозможно.  
  
 Можно настроить IntelliTrace для автоматического сохранения в файл, последовательно выбрав пункты **Сервис > Параметры > IntelliTrace > Дополнительно** и выбрав **хранить записи IntelliTrace в этом каталоге**. Можно также настроить размер набора для созданного файла, по достижении которого IntelliTrace перезаписывает старые данные при нехватке свободного пространства. Visual Studio создает два файла для каждого сеанса IntelliTrace, если файлы сохраняются автоматически и процесс размещения Visual Studio (vshost.exe) включен.  
  
> [!TIP]
>  Для экономии места на диске отключите автоматическое сохранение файлов, когда вы они больше не нужны. Существующие файлы не удалятся. Всегда можно сохранить файл по запросу из контекстного меню.  
  
 При сохранении данных IntelliTrace в файл вы получаете один ITRACE-файл для каждого процесса, из которого IntelliTrace собрал данные. Затем откройте ITRACE-файл в Visual Studio, перейдя **файл > Открыть > файл** и выбрав ITRACE-файл из диалогового окна открытия файла. Дополнительные сведения см. в разделе [использование сохраненных данных IntelliTrace](../debugger/using-saved-intellitrace-data.md).  
  
## <a name="blogs"></a>Блоги  
 [IntelliTrace в Visual Studio Enterprise 2015](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/intellitrace-in-visual-studio-ultimate-2015.aspx)  
  
 [Пошаговое руководство по динамической отладке с помощью IntelliTrace в Visual Studio 2015 (текстовый редактор)](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-text-editor.aspx)  
  
 [Пошаговое руководство по динамической отладке с помощью IntelliTrace в Visual Studio 2015 (Сообщество)](http://blogs.msdn.com/b/visualstudioalm/archive/2000/1/1/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-social-club.aspx)  
  
 [IntelliTrace в Visual Studio Enterprise 2015 теперь поддерживает присоединение!](http://blogs.msdn.com/b/visualstudioalm/archive/2015/05/14/intellitrace-in-visual-studio-enterprise-2015-now-supports-attach.aspx)  
  
 [Собирать данные из службы windows с помощью автономного сборщика IntelliTrace](http://blogs.msdn.com/b/visualstudioalm/archive/2015/05/14/collect-data-from-a-windows-service-using-the-intellitrace-standalone-collector.aspx)  
  
 [Изменение плана сбора IntelliTrace](http://blogs.msdn.com/b/visualstudioalm/archive/2015/03/09/editing-the-intellitrace-collection-plan.aspx)  
  
 [Пользовательский TraceSource и отладка с помощью IntelliTrace](http://blogs.msdn.com/b/visualstudioalm/archive/2014/12/17/custom-tracesource-and-debugging-using-intellitrace.aspx)  
  
 [Автономный сборщик IntelliTrace и пулы приложений выполняется с учетными записями Active Directory](http://blogs.msdn.com/b/visualstudioalm/archive/2014/12/22/intellitrace-standalone-collector-and-application-pools-running-under-active-directory-accounts.aspx)  
  
## <a name="forums"></a>Форумы  
 [Отладчик Visual Studio](http://go.microsoft.com/fwlink/?LinkId=262263)  
  
## <a name="videos"></a>Видеоролики  
 [Работа IntelliTrace](https://channel9.msdn.com/Series/Visual-Studio-2015-Enterprise-Videos/IntelliTrace-Experience)  
  
 [Отладка с ведением журнала с помощью IntelliTrace в Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/events/Ignite/2015/BRK3716)
