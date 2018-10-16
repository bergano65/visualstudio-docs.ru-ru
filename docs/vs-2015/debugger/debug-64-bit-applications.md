---
title: Отладка 64-разрядных приложений | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], 64-bit
- 64-bit debugging
ms.assetid: db648e5f-6375-4e2d-aa98-eb7261958927
caps.latest.revision: 38
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc64900016322c1d2c96c70d9daca8bb902e67de
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49246263"
---
# <a name="debug-64-bit-applications"></a>Отладка 64-разрядных приложений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Отладка 64-разрядных приложений](https://docs.microsoft.com/visualstudio/debugger/debug-64-bit-applications) .  
  
Существует возможность отладки 64-разрядного приложения, которое выполняется на локальном или удаленном компьютере.  
  
 Сведения об отладке 64-разрядного приложения, которое выполняется на удаленном компьютере, см. в статье [Remote Debugging](../debugger/remote-debugging.md).  
  
 Для отладки 64-разрядных приложений локально в Visual Studio используется 64-разрядная версия рабочего процесса (msvsmon.exe) для выполнения низкоуровневых операций, которые невозможно выполнить в 32-разрядном процессе Visual Studio.  
  
 Отладка в смешанном режиме не поддерживается для 64-разрядных процессов, использующих платформу .NET Framework 3.5 или более раннюю версию.  
  
## <a name="debug-a-64-bit-application"></a>Отладка 64-разрядных приложений  
 Чтобы отладить 64-разрядное приложение, выполните следующее.  
  
1.  Создайте решение Visual Studio, например консольное приложение C#.  
  
2.  С помощью Configuration Manager задайте для конфигурации 64-разрядный режим. Для получения дополнительной информации см. [How to: Configure Projects to Target Platforms](../ide/how-to-configure-projects-to-target-platforms.md).  
  
3.  На этом этапе запускается 64-разрядная версия удаленного отладчика (msvsmon.exe). Он работает до тех пор, пока открыто решение с 64-разрядной конфигурацией.  
  
4.  Приступите к отладке. Результат должен быть таким же, как и в случае с 32-разрядной конфигурацией. Если возникли ошибки, обратитесь к разделу "Устранение проблем", расположенному ниже.  
  
## <a name="troubleshooting-64-bit-debugging"></a>Устранение проблем при 64-разрядной отладке  
 Может появиться ошибка: "Операции 64-разрядной отладки занимают больше времени, чем ожидалось". В этом случае из Visual Studio отправлен запрос к 64-разрядной версии msvsmon.exe, и потребовалось много времени на возвращение результата этого запроса.  
  
 Есть две основных причины этой ошибки.  
  
-   На компьютере установлено программное обеспечение для защиты сети, из-за чего сетевой стек стал ненадежным и стал терять пакеты, идущие через localhost. Попробуйте отключить все программное обеспечение для защиты сети. Если проблема устранена, сообщите поставщику программного обеспечения для защиты сети о том, что его программа мешает трафику localhost.  
  
-   Программа не отвечает на запросы, или возникла проблема с производительностью Visual Studio. Если проблема возникает регулярно, можно собрать дампы Visual Studio (devenv.exe) и рабочего процесса (msvsmon.exe) и отправить их в корпорацию Майкрософт. 
  
## <a name="see-also"></a>См. также  
 [64-разрядные приложения](http://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)   
 [Настройка программ для 64-разрядных систем](http://msdn.microsoft.com/library/cb99f72b-8c74-48f4-846a-8921b37b97e9)   
 [Поддержка 64-разрядных сред IDE Visual Studio](../ide/visual-studio-ide-64-bit-support.md)   
 [Использование файлов дампа](../debugger/using-dump-files.md)   
 [Remote Debugging](../debugger/remote-debugging.md)






