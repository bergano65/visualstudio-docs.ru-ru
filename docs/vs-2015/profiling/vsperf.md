---
title: VSPerf | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a8042b228a481dc3d720d8b422963db41abbddcd
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85533839"
---
# <a name="vsperf"></a>VSPerf
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

С помощью программы командной строки **VsPerf** можно выполнять следующие задачи:  
  
1. профилирование приложений для Магазина Windows из командной строки, когда среда Visual Studio не установлена на устройстве;  
  
2. профилирование классических приложений Windows 8 и приложений Windows Server 2012 с помощью метода профилирования с выборкой.  
  
   Дополнительные сведения о вариантах профилирования см. в разделе [Средства производительности в приложениях Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> Содержание раздела  
 В этом разделе описываются параметры, которые можно использовать с программой командной строки `vsperf.exe`. В нем содержатся следующие подразделы:  
  
 [Только приложения для Магазина Windows](#BKMK_windows_store_apps_only)  
  
 [Только классические приложения Windows 8 и Windows Server 2012](#BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only)  
  
 [Все приложения](#BKMK_All_applications)  
  
## <a name="windows-store-apps-only"></a><a name="BKMK_windows_store_apps_only"></a> Только приложения для Магазина Windows  
 Эти параметры применяются только к приложениям Магазина Windows.  
  
|Параметр|Описание|  
|-|-|  
|**/app:{имя_приложения}**|Запускает профилировщик и ожидает запуска указанного приложения из меню "Пуск".<br /><br /> Чтобы просмотреть имена и полные имена пакетов для установленных приложений, выполните команду `vsperf /listapps`.|  
|**/package:{полное_имя_пакета}**|Запускает профилировщик и ожидает запуска указанного приложения из меню "Пуск".<br /><br /> Чтобы просмотреть имена и полные имена пакетов для установленных приложений, выполните команду `vsperf /listapps`.|  
|**переключателем/JS**|Требуется для профилирования приложений, написанных на JavaScript.<br /><br /> Соберите данные производительности из приложений, написанных на JavaScript.<br /><br /> Используется только с параметром /package или /attach.|  
|**/noclr**|Необязательный параметр. Не собирать данные среды CLR.<br /><br /> Используется только с параметром /package или /attach.<br /><br /> Оптимизация, управляемые символы разрешаться не будут.|  
|**/listapps**|Вывод списка имен и полных имен пакетов для установленных приложений.|  
  
## <a name="windows-8-desktop-applications-and-windows-server-2012-applications-only"></a><a name="BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only"></a> Только классические приложения Windows 8 и приложения Windows Server 2012  
 Эти параметры не работают в приложениях для Магазина Windows.  
  
|Параметр|Описание|  
|-|-|  
|**/launch:{исполняемый_файл}**|Запускает профилирование заданного исполняемого файла.|  
|**/args:{аргументы_исполняемого_файла}**|Задает аргументы командной строки для передачи целевому объекту **/launch**.|  
|**/Console**|Запускает целевой объект **/launch** в новом командном окне.|  
  
## <a name="all-applications"></a><a name="BKMK_All_applications"></a>Все приложения  
 Этот параметр применяется к любому приложению Windows 8 или Windows Server 2012.  
  
|Параметр|Описание|  
|-|-|  
|**/attach:{идентификатор_процесса&#124;имя_процесса}[,идентификатор_процесса&#124;имя_процесса]...**|Сбор данных из указанных процессов.<br /><br /> Используйте диспетчер задач Windows для просмотра идентификатора процесса (PID) и обработайте имена запущенных приложений.|  
|**/file:{имя_отчета}**|Необязательный параметр. Указывает выходной файл (перезаписывает существующий файл).<br /><br /> Используется только с параметром /package или /attach.|  
|**/Pause**|Приостановить сбор данных.|  
|**/Resume**|Возобновить сбор данных.|  
|**/Stop**|Остановить сбор данных и завершить работу целевых процессов.|  
|**/Detach**|Остановить сбор данных без прекращения работы целевых процессов.|  
|**/STA**|Показать состояние профилировщика.|  
  
## <a name="see-also"></a>См. также  
 [Средства производительности в приложениях Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)   
 [Профилирование из командной строки](../profiling/using-the-profiling-tools-from-the-command-line.md)
