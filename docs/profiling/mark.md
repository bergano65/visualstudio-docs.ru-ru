---
title: "Параметр Mark | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6992254d9c62c3f8e35d20a56bd7edd32315f10a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="mark"></a>Метка
Параметр **Mark** программы VSPerfCmd.exe вставляет указанные сведения в файл данных профилирования. Метка может быть указана в отдельном отчете VSPerfReport или в представлении отчета "Метки" пользовательского интерфейса профилировщика. Параметр **Mark** можно использовать для указания начальных и конечных точек в фильтрах отчетов и представлений.  
  
 Параметр **Mark** должен быть единственным параметром, указанным в командной строке.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
VSPerfCmd.exe /Mark:MarkID,[MarkName]  
```  
  
#### <a name="parameters"></a>Параметры  
 `MarkID`  
 Определенное пользователем целое число, указанное в качестве идентификатора метки в представлениях и отчетах профилировщика. Идентификатор `MarkID` необязательно должен быть уникальным.  
  
 `MarkName`  
 Определенная пользователем строка, указанная в качестве имени метки в представлениях и отчетах профилировщика (необязательно). Если параметр `MarkName` не задан, поле "Имя метки" в списке остается пустым. Строки, содержащие пробелы или косую черту ("/"), заключаются в кавычки.  
  
## <a name="example"></a>Пример  
 В этом примере вставляется метка с идентификатором 123 и именем TestMark.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
VSPerfCmd.exe /Mark:123,TestMark  
```  
  
## <a name="see-also"></a>См. также  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Профилирование служб](../profiling/command-line-profiling-of-services.md)