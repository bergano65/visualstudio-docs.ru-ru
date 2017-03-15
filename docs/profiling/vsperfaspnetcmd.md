---
title: "VSPerfASPNetCmd | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
ms.assetid: f9e9f895-57bb-41e8-8bd1-cdaa738ec220
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 970593f1141c2fc067ce181f6f756889180a231b
ms.lasthandoff: 02/22/2017

---
# <a name="vsperfaspnetcmd"></a>Средство VSPerfASPNetCmd
Средство командной строки **VSPerfASPNetCmd.exe** позволяет профилировать веб-сайты ASP.Net без необходимости определять переменные среды или перезагружать компьютер. **VSPerfASPNetCmd.exe** можно использовать вместо [VSPerfCmd](../profiling/vsperfcmd.md) при профилировании веб-сайтов ASP.NET, если вам не требуется дополнительные функции, предоставляемые **VSPerCmd**. Дополнительные сведения о команде **VSPerfASPNetCmd** см. в статье [Rapid Web Site Profiling with VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md) (Быстрое профилирование веб-сайтов с помощью средства VSPerfASPNETCmd). **VSPerfASPNETCmd** будет оптимальным вариантом, если необходим автономный профилировщик для профилирования веб-сайта ASP.NET.  
  
## <a name="syntax"></a>Синтаксис  
 **vsperfaspnetcmd** [/*параметры*] *веб-сайт*  
  
## <a name="options"></a>Параметры  
  
|Параметр|Описание|  
|------------|-----------------|  
|**/Sample** или **/s**|Профилирует веб-сайт с использованием метода выборки. Метод **/Sample** используется по умолчанию. /Sample не может использоваться в сочетании с **/Trace**.|  
|**/Trace** или **/t**|Профилирует веб-сайт с использованием метода инструментирования. /Trace не может использоваться в сочетании с **/Sample**.|  
|**/Memory**[**:**`Type`] или **/m**[**:**{**a**&#124;**l**}]|Профилирует выделение памяти и может дополнительно профилировать время существования объектов (сборку мусора). **/Memory** можно использовать совместно с методами выборки или инструментирования.<br /><br /> Параметр *Type* может иметь одно из следующих значений:<br /><br /> -   **allocation** (или **a**) — сбор данных только о выделении памяти.<br />-   **lifetime** (или **l**) — сбор данных о выделении памяти и времени существования объектов.<br /><br /> По умолчанию для `Type` используется значение **allocation**.|  
|**/Tip** или **/i**|Добавляет в данные профилирования подробные данные о запросе ASP.NET и вызове ADO.NET. **/Tip** можно использовать совместно с методами выборки или инструментирования, а также в сочетании с параметром **/Memory**.|  
|**/Output:** `File` или **/o:**`File`|Указывает имя и расположение для файла данных профилирования (VSP-файла).|  
|**/NoWait** или **/n**|Немедленно возвращает управление в командную строку, что позволяет выполнять дополнительные команды. В этом случае, чтобы отключить профилирование, выполните команду **VSPerfASPNETCmd/Shutdown** в отдельной строке.|  
|**/PackSymbols**[:{**on**&#124;**off**} или **/p**[:{**on**&#124;**off**}|Встраивает в файл данных профилирования (VSP-файл) символы (имена функций, параметров и т. д.).|  
|**/Shutdown:** `Website`или **/d:**`Website`|Отключает профилирование. Этот параметр должен быть единственным в командной строке. Он используется, если профилирование запущено с параметром **/nowait** или профилировщик неожиданно завершил работу. Укажите тот же URL-адрес, который использовался в исходной команде **VSPerfASPNETCmd**.|  
|`Website`|URL-адрес веб-сайта для профилирования.|  
  
## <a name="see-also"></a>См. также  
 [Rapid Web Site Profiling with VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)  (Быстрое профилирование веб-сайтов с помощью средства VSPerfASPNETCmd)  
 [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
