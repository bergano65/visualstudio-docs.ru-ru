---
title: "VSPerf | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VSPerf
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Используйте средство командной строки **VsPerf**:  
  
1.  Профилируйте приложения для Магазина Windows из командной строки, когда Visual Studio не установлено на устройстве.  
  
2.  Профилируйте приложения Windows 8 для настольных систем и приложения Windows Server 2012, используя метод профилирования выборки.  
  
 Дополнительные сведения о параметрах профилирования см. в разделе [Профилирование приложений для Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
##  <a name="BKMK_In_this_topic"></a> В этом разделе  
 В этом подразделе описываются параметры, которые можно использовать со средством командной строки `vsperf.exe`.  В этом разделе содержатся следующие подразделы.  
  
 [Только приложения для Магазина Windows](#BKMK_windows_store_apps_only)  
  
 [Только приложения Windows 8 для настольных систем и приложения Windows Server 2012](#BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only)  
  
 [Все приложения](#BKMK_All_applications)  
  
##  <a name="BKMK_windows_store_apps_only"></a> Только приложения для Магазина Windows  
 Эти параметры применяются только к приложениям Магазина Windows.  
  
|||  
|-|-|  
|**\/app:{AppName}**|Запускает профилировщик и ожидает указанное приложение для запуска из меню «Пуск».<br /><br /> Запустите `vsperf /listapps` для просмотра имени и полного имени приложения из установленных приложений.|  
|**\/package:{PackageFullName}**|Запускает профилировщик и ожидает указанное приложение для запуска из меню «Пуск».<br /><br /> Запустите `vsperf /listapps` для просмотра имени и полного имени приложения из установленных приложений.|  
|**\/js**|Требуется для профилирования приложений, написанных на JavaScript.<br /><br /> Соберите данные о производительности от приложений, написанных на JavaScript.<br /><br /> Используется только с параметром \/package или \/attach.|  
|**\/noclr**|Необязательно.  Не собирайте данные CLR.<br /><br /> Используется только с параметром \/package или \/attach.<br /><br /> Оптимизация, управляемые символы разрешаться не будут.|  
|**\/listapps**|Перечисление установленных имен и полных имен приложений.|  
  
##  <a name="BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only"></a> Только приложения Windows 8 для настольных систем и приложения Windows Server 2012  
 Эти параметры не работают в приложениях для Магазина Windows.  
  
|||  
|-|-|  
|**\/launch:{Executable}**|Запускает профилирование заданного исполняемого файла.|  
|**\/args:{ExecutableArguments}**|Задает аргументы командной строки для передачи целевой объект **\/launch**.|  
|**\/console**|Запускает целевой объект **\/launch** в новом командном окне.|  
  
##  <a name="BKMK_All_applications"></a> Все приложения  
 Этот параметр применяется к любому приложению Windows 8 или Windows Server 2012.  
  
|||  
|-|-|  
|**\/attach:{PID&#124;ProcessName}\[,PID&#124;ProcessName\]...**|Cобирает данные из указанных процессов.<br /><br /> Используйте диспетчер задач Windows для просмотра идентификатора процесса \(PID\) и обработайте имена запущенных приложений.|  
|**\/file:{ReportName}**|Необязательно.  Указывает выходной файл \(перезаписывает существующий файл\).<br /><br /> Используется только с параметром \/package или \/attach.|  
|**\/pause**|Остановить сбор данных.|  
|**\/resume**|Возобновить сбор данных.|  
|**\/stop**|Остановить сбор данных и завершите работы целевых процессов.|  
|**\/detach**|Остановить сбор данных без прекращения работы целевых процессов.|  
|**\/status**|Показать состояние профилировщика.|  
  
## См. также  
 [Профилирование приложений для Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)   
 [Профилирование из командной строки](../profiling/using-the-profiling-tools-from-the-command-line.md)