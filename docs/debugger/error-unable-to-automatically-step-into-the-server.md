---
title: 'Ошибка: Не удается автоматически выполнить шаг на сервере | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b9e7b3c45e49425c07c545f2a04673887fc8cac7
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2018
ms.locfileid: "44278677"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Ошибка: не удалось автоматически перейти в режим пошагового выполнения
Текст сообщения об ошибке.  
  
 "Не удается автоматически выполнить шаг на сервере. Отладчик не получил уведомления перед выполнением удаленной процедуры."  
  
 Эта ошибка может возникать при попытке зайти в веб-службы (см. в разделе [шаг с заходом в веб-службы XML](https://msdn.microsoft.com/library/8e67de38-bf5f-41cc-a457-1b88ce63d764)). Ошибка может произойти всякий раз при неправильно настроенном [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] .  
  
 Возможные причины:  
  
-   Параметр отладки не установлен в "true" в файле web.config приложения [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] (см. раздел [Режим отладки в приложениях ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).  
  
-   Версия [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] была установлена после установки Visual Studio. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] следует устанавливать до Visual Studio. Чтобы устранить эту проблему, используйте Windows **панель управления > программы и компоненты** восстановить установку Visual Studio.  
  
## <a name="see-also"></a>См. также  
 [Ошибки удаленной отладки и устранения неполадок](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Удаленная отладка](../debugger/remote-debugging.md)