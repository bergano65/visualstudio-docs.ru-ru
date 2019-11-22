---
title: IntelliTrace Features | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
caps.latest.revision: 73
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dc16094c98a912d073bd6b873ecb3d1b3b411d1e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298951"
---
# <a name="intellitrace-features"></a>Функции IntelliTrace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliTrace можно использовать для записи событий и вызовов методов, что позволяет проверять состояние приложения (стек вызовов и значения локальных переменных) на различных этапах выполнения. Just start debugging as usual - IntelliTrace is turned on by default, and you can see the information IntelliTrace is recording in the new **Diagnostic Tools** window under the **Events** tab. Select an event and click **Activate Historical Debugging** to see the call stack and locals recorded for this event.  
  
 Пошаговое описание см. в разделе [Пошаговое руководство: Использование IntelliTrace](../debugger/walkthrough-using-intellitrace.md).  
  
 Средство IntelliTrace доступно в выпуске Visual Studio Enterprise, но не в выпусках Visual Studio Professional или Community.  
  
 To confirm that IntelliTrace is turned on, open the **Tools / Options / IntelliTrace** options page. Параметр **Включить IntelliTrace** должен быть выбран по умолчанию.  
  
> [!NOTE]
> Все параметры на странице параметров **IntelliTrace** охватывают Visual Studio как единое целое, а не распространяются на отдельные проекты или решения. Изменение этих параметров применяется ко всем экземплярам Visual Studio, всем сеансам отладки и всем проектам и решениям.  
  
## <a name="ChooseEvents"></a> Choose the events that IntelliTrace records  
 Можно включить или отключить запись определенных событий IntelliTrace.  
  
 Если выполняется отладка, остановите ее. Go to **Tools / Options / IntelliTrace / IntelliTrace Events**. Выберите события, которые будет записывать IntelliTrace.  
  
## <a name="GoingFurther"></a> Collect IntelliTrace events and call information  
 Эта возможность не включена по умолчанию, но IntelliTrace может записывать вызовы методов вместе с событиями. To enable collection of method calls go to **Tools / Options / IntelliTrace / General**, and select **IntelliTrace events and call information**.  
  
 Это позволит увидеть журнал стека вызовов и переходить по вызовам в вашем коде. IntelliTrace записывает такие данные, как имена методов, точки входа и выхода методов и определенные значения параметров, а также возвращаемые значения.  
  
> [!TIP]
> Этот параметр не включен по умолчанию, поскольку он связан со значительными издержками. IntelliTrace позволяет не только перехватывать каждый вызов метода, осуществляемый приложением, но и обрабатывать наборы данных значительного размера в случае необходимости их отображения на экране или сохранения на диск.  
>   
> Чтобы снизить издержки на производительность, можно ограничить список событий, записываемых IntelliTrace, и поддерживать минимальное количество собираемых модулей. Дополнительные сведения см. в разделе [Управление объемом сведений о вызовах, записываемых IntelliTrace](../debugger/intellitrace-features.md#ControlCallData).  
  
### <a name="using-the-navigation-gutter"></a>Использование области навигации  
 Можно использовать области навигации, которая отображается слева от окна кода. If you don't see the navigation gutter, go to **Tools / Options / IntelliTrace / Advanced**, and select **Display the navigation gutter while in debug mode**.  
  
 В области навигации в режиме отладки с ведением журнала можно перемещаться вперед и назад по вызовам методов и событиям. Дополнительные сведения об отладке с ведением журнала см. в разделе [Отладка с ведением журнала](../debugger/historical-debugging.md). Здесь доступен ряд команд.  
  
|||  
|-|-|  
|**Задать контекст отладчика здесь**|Задает контексту отладки временной интервал вызова, в котором он отображается.<br /><br /> Значок отображается только на текущем стеке вызовов.|  
|**Возврат к месту вызова**|Перемещает указатель и контекст отладки назад в тот момент, где была вызвана текущая функция.<br /><br /> Если вы находитесь в динамическом режиме отладки, эта команда включает отладку с ведением журнала. Если перейти в исходное место прерывания выполнения, отладка с ведением журнала отключается и включается режим динамической отладки.|  
|**Перейти к предыдущему вызову или событию IntelliTrace**|Перемещает указатель и контекст отладки назад к предыдущему вызову или событию.<br /><br /> Если вы находитесь в динамическом режиме отладки, эта команда включает отладку с ведением журнала.|  
|**Шаг с заходом**|Выполняет шаг с заходом в текущую выбранную функцию.<br /><br /> Эта команда доступна только в режиме отладки с ведением журнала.|  
|**Перейти к следующему вызову или событию IntelliTrace**|Перемещает указатель и контекст отладки к следующему вызову или событию, для которого имеются данные IntelliTrace.<br /><br /> Эта команда доступна только в режиме отладки с ведением журнала.|  
|**Перейти в динамический режим**|Возврат в динамический режим отладки.|  
  
### <a name="search-for-a-line-or-method-in-intellitrace"></a>Найти строку или метод в IntelliTrace  
 Поиск методов можно осуществлять только в том случае, если были включены сведения о вызовах метода. Можно выполнить поиск конкретной строки или метода в журнале IntelliTrace. Во время приостановки выполнения отладчика щелкните правой кнопкой мыши в теле функции, чтобы открыть контекстное меню, и выберите **Найти эту строку в IntelliTrace** или **Найти этот метод в IntelliTrace**.  
  
### <a name="ControlCallData"></a> Управление объемом сведений о вызовах, записываемых IntelliTrace  
 По умолчанию IntelliTrace записывает сведения для всех модулей, используемых в решении. IntelliTrace можно настроить для записи сведений о вызовах только в представляющих интерес модулях. In **Tools / Options / IntelliTrace / Modules**, You can specify the modules to include or the modules to exclude from IntelliTrace. IntelliTrace будет собирать только события, источниками которых являются указанные модули, и вызовы методов, выполненные в представляющих интерес модулях.  
  
 Чтобы добавить несколько модулей, используйте подстановочный знак * в начале или конце строки. В качестве имени модуля используйте имя файла, а не имя сборки. Пути к файлам не принимаются.  
  
 Попытайтесь свести число модулей к минимуму. Поскольку в этом случае уменьшается объем собираемых данных, уровень производительности повышается. Кроме того, в пользовательском интерфейсе снижается уровень шума.  
  
## <a name="SaveSession"></a> Saving IntelliTrace data to file  
 You can save the data that IntelliTrace has collected going to **Debug / IntelliTrace / Save IntelliTrace Session** while you are debugging and the application is in a break state. Если приложение все еще выполняется или отладка остановлена, пункт меню будет отключен и сохранить данные, собранные IntelliTrace, будет невозможно.  
  
 You can configure IntelliTrace to automatically save to a file by going to **Tools / Options / IntelliTrace / Advanced** and selecting **Store IntelliTrace recordings in this directory**. Можно также настроить размер набора для созданного файла, по достижении которого IntelliTrace перезаписывает старые данные при нехватке свободного пространства. Visual Studio создает два файла для каждого сеанса IntelliTrace, если файлы сохраняются автоматически и процесс размещения Visual Studio (vshost.exe) включен.  
  
> [!TIP]
> Для экономии места на диске отключите автоматическое сохранение файлов, когда они больше не нужны. Существующие файлы не удалятся. Всегда можно сохранить файл по запросу из контекстного меню.  
  
 При сохранении данных IntelliTrace в файл вы получаете один ITRACE-файл для каждого процесса, из которого IntelliTrace собрал данные. You can then open the .itrace file in Visual Studio by going to **File / Open / File** and selecting the .itrace file from the Open File dialog. Дополнительные сведения см. в разделе [Использование сохраненных данных IntelliTrace](../debugger/using-saved-intellitrace-data.md).  
  
## <a name="blogs"></a>Блоги  
 [IntelliTrace в Visual Studio Enterprise 2015](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-ultimate-2015/)  
  
 [Walkthrough of Live Debugging using IntelliTrace in Visual Studio 2015 (Text Editor)](https://devblogs.microsoft.com/devops/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-text-editor/)  
  
 [Walkthrough of Live Debugging using IntelliTrace in Visual Studio 2015 (Social Club)](https://devblogs.microsoft.com/devops/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-social-club/)  
  
 [IntelliTrace in Visual Studio Enterprise 2015 now supports attach!](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-enterprise-2015-now-supports-attach/)  
  
 [Collect data from a windows service using the IntelliTrace Standalone Collector](https://devblogs.microsoft.com/devops/collect-data-from-a-windows-service-using-the-intellitrace-standalone-collector/)  
  
 [Editing the IntelliTrace collection plan](https://devblogs.microsoft.com/devops/editing-the-intellitrace-collection-plan/)  
  
 [Custom TraceSource and debugging using IntelliTrace](https://devblogs.microsoft.com/devops/custom-tracesource-and-debugging-using-intellitrace/)  
  
 [IntelliTrace Standalone Collector and Application Pools running under Active Directory accounts](https://devblogs.microsoft.com/devops/intellitrace-standalone-collector-and-application-pools-running-under-active-directory-accounts/)  
  
## <a name="forums"></a>Форумы  
 [Отладчик Visual Studio](https://go.microsoft.com/fwlink/?LinkId=262263)  
  
## <a name="videos"></a>Видеоролики  
 [IntelliTrace Experience](https://channel9.msdn.com/Series/Visual-Studio-2015-Enterprise-Videos/IntelliTrace-Experience)  
  
 [Отладка с ведением журнала с помощью IntelliTrace в Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/events/Ignite/2015/BRK3716)
