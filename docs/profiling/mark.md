---
title: Параметр Mark | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e610644713d630ce4f54befa8535c3b00c7aaf92
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
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