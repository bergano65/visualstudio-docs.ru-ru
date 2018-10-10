---
title: VSPerf | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f57318867ac758be0652d30154a30aa1d285b7c2
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2018
ms.locfileid: "48879157"
---
# <a name="vsperf"></a>VSPerf
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [VSPerf](https://docs.microsoft.com/visualstudio/profiling/vsperf).  
  
С помощью программы командной строки **VsPerf** можно выполнять следующие задачи:  
  
1.  профилирование приложений для Магазина Windows из командной строки, когда среда Visual Studio не установлена на устройстве;  
  
2.  профилирование классических приложений Windows 8 и приложений Windows Server 2012 с помощью метода профилирования с выборкой.  
  
 Дополнительные сведения о вариантах профилирования см. в разделе [Средства производительности в приложениях Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
##  <a name="BKMK_In_this_topic"></a> Содержание раздела  
 В этом разделе описываются параметры, которые можно использовать с программой командной строки `vsperf.exe`. В нем содержатся следующие подразделы:  
  
 [Только приложения для Магазина Windows](#BKMK_windows_store_apps_only)  
  
 [Только классические приложения Windows 8 и приложения Windows Server 2012](#BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only)  
  
 [Все приложения](#BKMK_All_applications)  
  
##  <a name="BKMK_windows_store_apps_only"></a> Только приложения для Магазина Windows  
 Эти параметры применяются только к приложениям Магазина Windows.  
  
|||  
|-|-|  
|**/app:{имя_приложения}**|Запускает профилировщик и ожидает запуска указанного приложения из меню "Пуск".<br /><br /> Чтобы просмотреть имена и полные имена пакетов для установленных приложений, выполните команду `vsperf /listapps`.|  
|**/package:{полное_имя_пакета}**|Запускает профилировщик и ожидает запуска указанного приложения из меню "Пуск".<br /><br /> Чтобы просмотреть имена и полные имена пакетов для установленных приложений, выполните команду `vsperf /listapps`.|  
|**/js**|Требуется для профилирования приложений, написанных на JavaScript.<br /><br /> Соберите данные производительности из приложений, написанных на JavaScript.<br /><br /> Используется только с параметром /package или /attach.|  
|**/noclr**|Необязательный. Не собирать данные среды CLR.<br /><br /> Используется только с параметром /package или /attach.<br /><br /> Оптимизация, управляемые символы разрешаться не будут.|  
|**/listapps**|Вывод списка имен и полных имен пакетов для установленных приложений.|  
  
##  <a name="BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only"></a> Только классические приложения Windows 8 и приложения Windows Server 2012  
 Эти параметры не работают в приложениях для Магазина Windows.  
  
|||  
|-|-|  
|**/launch:{исполняемый_файл}**|Запускает профилирование заданного исполняемого файла.|  
|**/args:{аргументы_исполняемого_файла}**|Задает аргументы командной строки для передачи целевому объекту **/launch**.|  
|**/console**|Запускает целевой объект **/launch** в новом командном окне.|  
  
##  <a name="BKMK_All_applications"></a> Все приложения  
 Этот параметр применяется к любому приложению Windows 8 или Windows Server 2012.  
  
|||  
|-|-|  
|**/attach:{идентификатор_процесса&#124;имя_процесса}[,идентификатор_процесса&#124;имя_процесса]...**|Сбор данных из указанных процессов.<br /><br /> Используйте диспетчер задач Windows для просмотра идентификатора процесса (PID) и обработайте имена запущенных приложений.|  
|**/file:{имя_отчета}**|Необязательный. Указывает выходной файл (перезаписывает существующий файл).<br /><br /> Используется только с параметром /package или /attach.|  
|**/pause**|Приостановить сбор данных.|  
|**/resume**|Возобновить сбор данных.|  
|**/stop**|Остановить сбор данных и завершить работу целевых процессов.|  
|**/detach**|Остановить сбор данных без прекращения работы целевых процессов.|  
|**/status**|Показать состояние профилировщика.|  
  
## <a name="see-also"></a>См. также  
 [Средства производительности в приложениях Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)   
 [Профилирование из командной строки](../profiling/using-the-profiling-tools-from-the-command-line.md)



