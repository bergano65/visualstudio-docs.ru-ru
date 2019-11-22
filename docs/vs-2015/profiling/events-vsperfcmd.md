---
title: Параметр Events (VSPerfCmd) | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 265dc7f84fbd1ec19b520e2e30d3554e2c66683b
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302138"
---
# <a name="events-vsperfcmd"></a>Параметр Events (VSPerfCmd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Параметр **Events** программы VSPerfCmd.exe позволяет управлять ведением журнала трассировки событий Windows. Данные трассировки событий Windows сохраняются в ETL-файле, который отличается от файла данных профилировщика. Эти данные можно просмотреть в отчете с помощью команды [VSPerfReport](../profiling/vsperfreport.md) /summary:etw.  
  
 Параметр **Events** можно использовать в любой момент перед вызовом команды **Shutdown** программы VSPerfCmd для остановки профилирования.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]  
```  
  
#### <a name="parameters"></a>Параметры  
 **On**&#124;**Off**  
 Запускает или останавливает сбор данных события.  
  
 `Guid`  
 Идентификатор GUID элемента управления поставщика.  
  
 `ProviderName`  
 Имя поставщика, созданного с помощью инструментария управления Windows (WMI).  
  
 `Flags`  
 Значение флагов с префиксом "0x", заданное поставщиком событий.  
  
 `Level`  
 Задает объем собираемых данных. `Level` определяется поставщиком событий.  
  
 Параметр **Events** распознает в качестве имен поставщиков перечисленные ниже ключевые слова ядра.  
  
 **Process**  
 События процесса  
  
 **Поток**  
 События потока  
  
 **Изображение**  
 События загрузки и выгрузки образов  
  
 **Disk**  
 События ввода-вывода на диске  
  
 **Файл**  
 События ввода-вывода в файле  
  
 **Hardfault**  
 Ошибки страниц физической памяти  
  
 **Pagefault**  
 Ошибки страниц ОЗУ  
  
 **Network**  
 Сетевые события  
  
 **Registry**  
 События доступа к реестру  
  
 Необходимо заметить, что Kernel Provider можно только включить. До завершения работы монитора невозможно отключить этот поставщик или изменить его флаги.  
  
## <a name="remarks"></a>Заметки  
  
> [!NOTE]
> При возникновении событий трассировки событий Windows среды CLR для отчета представления трассировки собираются также дополнительные сведения о запуске. Чтобы исключить события запуска из отчета, используйте следующую команду:  
  
```  
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5  
```  
  
> [!IMPORTANT]
> Так как события запуска не перечислены в MOF-файле, то если их не исключить, они отображаются в отчете в виде идентификаторов GUID. Дополнительные сведения см. на странице [Образец файла формата управляемого объекта (MOF)](https://go.microsoft.com/fwlink/?linkid=37118) веб-сайта корпорации Майкрософт.  
  
## <a name="see-also"></a>См. также раздел  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Профилирование служб](../profiling/command-line-profiling-of-services.md)
