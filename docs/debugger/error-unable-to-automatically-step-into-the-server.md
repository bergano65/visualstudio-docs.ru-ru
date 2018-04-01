---
title: 'Ошибка: Не удается автоматически выполнить шаг на сервере | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- vs.debug.error.causality_no_server_response
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, notification error
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 890c3e650b656d3c69a574ba477b797ba120c0a6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Ошибка: не удалось автоматически перейти в режим пошагового выполнения
Текст сообщения об ошибке.  
  
 "Не удается автоматически выполнить шаг на сервере. Отладчик не получил уведомления перед выполнением удаленной процедуры."  
  
 Эта ошибка может возникнуть, когда предпринята попытка в пошаговом режиме зайти в веб-службу (см. раздел [Вход в пошаговом режиме в веб-службу XML](http://msdn.microsoft.com/en-us/8e67de38-bf5f-41cc-a457-1b88ce63d764)). Ошибка может произойти всякий раз при неправильно настроенном [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] .  
  
 Возможные причины:  
  
-   Параметр отладки не установлен в "true" в файле web.config приложения [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] (см. раздел [Режим отладки в приложениях ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).  
  
-   Версия [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] была установлена после установки Visual Studio. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] следует устанавливать до Visual Studio. Чтобы устранить эту проблему, воспользуйтесь окном **панель управления > программы и компоненты** для исправления установки Visual Studio.  
  
## <a name="see-also"></a>См. также  
 [Ошибки удаленной отладки и устранения неполадок](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Удаленная отладка](../debugger/remote-debugging.md)