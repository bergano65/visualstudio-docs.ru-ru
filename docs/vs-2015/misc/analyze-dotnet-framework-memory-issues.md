---
title: Analyze .NET Framework memory issues | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.diagnostics.managedmemoryanalysis
ms.assetid: 43341928-9930-48cf-a57f-ddcc3984b787
caps.latest.revision: 9
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e94edbeac381ac634171507766126ab954153eb1
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295896"
---
# <a name="analyze-net-framework-memory-issues"></a>Анализ проблем с памятью .NET Framework
С помощью анализатора управляемой памяти Visual Studio вы можете найти утечки памяти и определить неэффективное использование памяти в коде .NET Framework. Минимальная версия .NET Framework целевого кода — .NET Framework 4.5.  
  
 The memory analysis tool analyzes information in *dump files with heap data* that a copy of the objects in an app's memory. Вы можете собрать файлы дампа (DMP) в среде Visual Studio или с помощью других системных средств.  
  
- Можно проанализировать один мгновенный снимок, чтобы понять относительное влияние типов объектов на использование памяти и найти код в приложении, который использует память неэффективно.  
  
- You can also compare (*diff*) two snapshots of an app to find areas in your code that cause the memory use to increase over time.  
  
  For a walkthrough of the managed memory analyzer, see [Using Visual Studio 2013 to Diagnose .NET Memory Issues in Production](https://devblogs.microsoft.com/devops/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production/) on the Visual Studio ALM + Team Foundation Server blog .  
  
## <a name="BKMK_Contents"></a> Описание  
 [Memory use in .NET Framework apps](#BKMK_Memory_use_in__NET_Framework_apps)  
  
 [Identify a memory issue in an app](#BKMK_Identify_a_memory_issue_in_an_app)  
  
 [Collect memory snapshots](#BKMK_Collect_memory_snapshots)  
  
 [Analyze memory use](#BKMK_Analyze_memory_use)  
  
## <a name="BKMK_Memory_use_in__NET_Framework_apps"></a> Memory use in .NET Framework apps  
 .NET Framework — это среда выполнения со сборкой мусора, поэтому в большинстве приложений использование памяти не вызывает проблем. Но в долго работающих приложениях, таких как веб-службы и приложения, и на устройствах с ограниченным объемом памяти, накопление объектов в памяти может снизить производительность приложения и устройства. Избыточное использование памяти может привести к дефициту ресурсов, если сборщик мусора будет запускаться слишком часто или операционной системе приходится часто перемещать данные между ОЗУ и диском. В худшем случае приложение может завершить работу с исключением "Недостаточно памяти".  
  
 The .NET *managed heap* is a region of virtual memory where reference objects created by an app are stored. Жизненный цикл объектов контролирует сборщик мусора (GC). Сборщик мусора использует ссылки для отслеживания объектов, занимающих блоки памяти. Ссылка создается, когда объект создается и назначается переменной. У одного объекта может быть несколько ссылок. Например, дополнительные ссылки на объект можно создать, добавив его в класс, коллекцию или другую структуру данных или назначив объект второй переменной. Менее очевидный способ создания ссылки — добавление обработчика в событие другого объекта. В этом случае второй объект содержит ссылку на первый объект, пока не будет явно удален обработчик или второй объект.  
  
 Для каждого приложения сборщик мусора хранит три ссылки, отслеживающие объекты, на которые ссылается приложение. The *reference tree* has a set of roots, which includes global and static objects, as well as associated thread stacks and dynamically instantiated objects. Объект становится корневым, если у него есть по крайней мере один родительский объект с ссылкой на него. Сборщик мусора может освободить память, занимаемую объектом, только если другие объекты или переменные в приложении не ссылаются на него.  
  
 ![Back to top](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
## <a name="BKMK_Identify_a_memory_issue_in_an_app"></a> Identify a memory issue in an app  
 Самым очевидным признаком проблем с памятью служит производительность приложения, особенно ее падение с течением времени. Ухудшение производительности других приложений во время работы вашего приложения также может указывать на проблему с памятью. If you suspect a memory issue, use a tool like Task Manager or [Windows Performance Monitor](https://technet.microsoft.com/library/cc749249.aspx) to investigate further. Например, посмотрите, существуют ли случаи увеличения общего объема памяти, которые вы не можете объяснить — возможно, это источник утечки памяти:  
  
 ![Consistent memory growth in Resource Monitor](../misc/media/mngdmem-resourcemanagerconsistentgrowth.png "MNGDMEM_ResourceManagerConsistentGrowth")  
  
 Вы также можете заметить пиковые объемы используемой памяти, которые превышают предполагаемый объем — это может указывать на неэффективное использование памяти в процедуре:  
  
 ![Memory spikes in Resource Manager](../misc/media/mngdmem-resourcemanagerspikes.png "MNGDMEM_ResourceManagerSpikes")  
  
## <a name="BKMK_Collect_memory_snapshots"></a> Collect memory snapshots  
 The memory analysis tool analyzes information in *dump files* that contain heap information. You can create dump files in Visual Studio, or you can use a tool like [ProcDump](https://technet.microsoft.com/sysinternals/dd996900.aspx) from [Windows Sysinternals](https://technet.microsoft.com/sysinternals). See [What is a dump, and how do I create one?](https://blogs.msdn.microsoft.com/debugger/2009/12/30/what-is-a-dump-and-how-do-i-create-one/) on the Visual Studio Debugger Team blog.  
  
> [!NOTE]
> Большинство средств могут собирать данные дампа с полными данными памяти кучи или без них. Анализатору памяти Visual Studio требуются полные сведения о куче.  
  
 **To collect a dump from Visual Studio**  
  
1. Вы можете создать файл дампа для процесса, запущенного из проекта Visual Studio, или можете присоединить отладчик к запущенному процессу. See [Attach to Running Processes](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
2. Остановите выполнение. The debugger stops when you choose **Break All** on the **Debug** menu, or at an exception or at a breakpoint  
  
3. On the **Debug** menu, choose **Save Dump As**. In the **Save Dump As** dialog box, specify a location and make sure that **Minidump with Heap** (the default) is selected in the **Save as type** list.  
  
   **To compare two memory snapshots**  
  
   Для анализа роста объема используемой приложением памяти получите два файла дампа из одного экземпляра приложения.  
  
   ![Back to top](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
## <a name="BKMK_Analyze_memory_use"></a> Analyze memory use  
 [Filter the list of objects](#BKMK_Filter_the_list_of_objects) **&#124;** [Analyze memory data in from a single snapshot](#BKMK_Analyze_memory_data_in_from_a_single_snapshot) **&#124;** [Compare two memory snapshots](#BKMK_Compare_two_memory_snapshots)  
  
 Чтобы проанализировать файл дампа на наличие проблем с памятью:  
  
1. In Visual Studio, choose **File**, **Open** and specify the dump file.  
  
2. On the **Minidump File Summary** page, choose **Debug Managed Memory**.  
  
    ![Dump file summary page](../misc/media/mngdmem-dumpfilesummary.png "MNGDMEM_DumpFileSummary")  
  
   Анализатор памяти начнет сеанс отладки для анализа файла, а результаты появятся на странице "Представление кучи":  
  
   ![Back to top](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
### <a name="BKMK_Filter_the_list_of_objects"></a> Filter the list of objects  
 По умолчанию анализатор памяти фильтрует список объектов в снимке памяти, отображая только типы и экземпляры, относящиеся к коду пользователя, и показывая только те типы, общий инклюзивный размер которых превышает процентный порог от общего размера кучи. You can change these options in the **View Settings** list:  
  
|||  
|-|-|  
|**Включение функции "Только мой код"**|В режиме "Только мой код" основные системные объекты скрыты, поэтому в списке отображаются только типы, созданные вами.<br /><br /> You can also set the Just My Code option in the Visual Studio **Options** dialog box. В меню **Отладка** выберите **Параметры и настройки**. In the **Debugging**/**General** tab, choose or clear **Just My Code**.|  
|**Collapse Small Objects**|**Collapse Small Objects** hides all types whose total inclusive size is less than 0.5 percent of the total heap size.|  
  
 You can also filter the type list by entering a string in the **Search** box. В списке будут показаны только типы, имена которых содержат введенную строку.  
  
 ![Back to top](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
### <a name="BKMK_Analyze_memory_data_in_from_a_single_snapshot"></a> Analyze memory data in from a single snapshot  
 Visual Studio начнет новый сеанс отладки для анализа файла, а результаты появятся в окне "Представление кучи".  
  
 ![The Object Type list](../misc/media/dbg-mma-objecttypelist.png "DBG_MMA_ObjectTypeList")  
  
 ![Back to top](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
#### <a name="object-type-table"></a>Таблица "Тип объекта"  
 В верхней таблице перечислены типы объектов, которые хранятся в памяти.  
  
- **Count** shows the number of instances of the type in the snapshot.  
  
- **Size (Bytes)** is the size of the all instances of the type, excluding the size of objects it holds references to. Классу  
  
- **Inclusive Size (Bytes)** includes the sizes of referenced objects.  
  
  You can choose the instances icon (![The instance icon in the Object Type column](../misc/media/dbg-mma-instancesicon.png "DBG_MMA_InstancesIcon")) in the **Object Type** column to view a list of the instances of the type.  
  
#### <a name="instance-table"></a>Таблица экземпляров  
 ![Instances table](../misc/media/dbg-mma-instancestable.png "DBG_MMA_InstancesTable")  
  
- **Instance** is the memory location of the object that serves as the object identifier of the object  
  
- **Value** shows the actual value of value types. Можно навести указатель мыши на имя ссылочного типа, чтобы просмотреть его значения в подсказке.  
  
   ![Instance values in a data tip](../misc/media/dbg-mma-instancevaluesindatatip.png "DBG_MMA_InstanceValuesInDataTip")  
  
- **Size (Bytes)** is the size of the object, excluding the size of objects it holds references to. Классу  
  
- **Inclusive Size (Bytes)** includes the sizes of referenced objects.  
  
  By default, types and instances are sorted by **Inclusive Size (Bytes)** . Выберите заголовок столбца в списке, чтобы изменить порядок сортировки.  
  
#### <a name="paths-to-root"></a>Пути к корню  
  
- For a type selected from the **Object Type** table, the **Paths to Root** table shows the unique type hierarchies that lead to root objects for all objects of the type, along with the number of references to the type that is above it in the hierarchy.  
  
- For an object selected from the instance of a type, **Paths to Root** shows a graph of the actual objects that hold a reference to the instance. Можно навести указатель мыши на имя объекта, чтобы просмотреть его значения в подсказке.  
  
#### <a name="referenced-types--referenced-objects"></a>Ссылочные типы и объекты  
  
- For a type selected from the **Object Type** table, the **Referenced Types** tab shows the size and number of referenced types held by all objects of the selected type.  
  
- For a selected instance of a type, **Referenced Objects** shows the objects that are held by the selected instance. Можно навести указатель мыши на имя, чтобы просмотреть значения в подсказке.  
  
  **Circular references**  
  
  Объект может ссылаться на второй объект, который напрямую или косвенно содержит ссылку на первый объект. When the memory analyzer encounters this situation, it stops expanding the reference path and adds a **[Cycle Detected]** annotation to the listing of the first object and stops.  
  
  **Root types**  
  
  Анализатор памяти добавляет к корневым объектам комментарии с описанием ссылки, которые содержатся в объектах:  
  
|Комментарий|Описание|  
|----------------|-----------------|  
|**Static variable** `VariableName`|Статическая переменная. `VariableName` — имя переменной.|  
|**Finalization Handle**|Ссылка из очереди метода завершения|  
|**Local Variable**|Локальная переменная.|  
|**Strong Handle**|Дескриптор строгой ссылки из таблицы дескрипторов объектов.|  
|**Async. Pinned Handle**|Асинхронный закрепленный объект из таблицы дескрипторов объектов.|  
|**Dependent Handle**|Зависимый объект из таблицы дескрипторов объектов.|  
|**Pinned Handle**|Закрепленная строгая ссылка из таблицы дескрипторов объектов.|  
|**RefCount Handle**|Объект с подсчетом ссылок из таблицы дескрипторов объектов.|  
|**SizedRef Handle**|Строгая ссылка, хранящая приблизительный размер общего закрытия всех объектов и корневых объектов во время сборки мусора.|  
|**Pinned local variable**|Закрепленная локальная переменная.|  
  
### <a name="BKMK_Compare_two_memory_snapshots"></a> Compare two memory snapshots  
 Вы можете сравнить два файла дампа процесса, чтобы найти объекты, которые могут вызывать утечку памяти. Интервал между сбором первого (более раннего) и второго (более позднего) файла должен быть достаточно большим, чтобы увеличение числа потерянных объектов было очевидным. Сравнение двух файлов  
  
1. Open the second dump file, and then choose **Debug Managed Memory** on the **Minidump File Summary** page.  
  
2. On the memory analysis report page, open the **Select baseline** list, and then choose **Browse** to specify the first dump file.  
  
   The analyzer adds columns to the top pane of the report that display the difference between the **Count**, **Size**, and **Inclusive Size** of the types to those values in the earlier snapshot.  
  
   ![Diff columns in the type list](../misc/media/mngdmem-diffcolumns.png "MNGDMEM_DiffColumns")  
  
   A **Reference Count Diff** column is also added to the **Paths to Root** table.  
  
   ![Back to top](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
## <a name="see-also"></a>См. также раздел  
 [VS ALM TFS Blog: Using Visual Studio 2013 to Diagnose .NET Memory Issues in Production](https://devblogs.microsoft.com/devops/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production/)   
 [Channel 9 &#124; Visual Studio TV &#124; Managed Memory Analysis](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Managed-Memory-Analysis)   
 [Channel 9 &#124; Visual Studio Toolbox &#124; Managed Memory Analysis in Visual Studio 2013](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Managed-Memory-Analysis-in-Visual-Studio-2013)