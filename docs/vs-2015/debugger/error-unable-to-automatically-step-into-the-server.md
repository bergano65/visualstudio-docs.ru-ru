---
title: 'Ошибка: Не удается автоматически выполнить шаг на сервере | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.causality_no_server_response
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- remote debugging, notification error
ms.assetid: 9a370ccc-d358-429c-b285-9b6c0649bc68
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d75ed4ddb42705b95a5ddd834596bc828e0f3ec2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558267"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Ошибка: не удалось автоматически перейти в режим пошагового выполнения
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [ошибка: не удалось автоматически шаг в сервер](https://docs.microsoft.com/visualstudio/debugger/error-unable-to-automatically-step-into-the-server).  
  
Текст сообщения об ошибке.  
  
 "Не удается автоматически выполнить шаг на сервере. Отладчик не получил уведомления перед выполнением удаленной процедуры."  
  
 Эта ошибка может возникнуть, когда предпринята попытка в пошаговом режиме зайти в веб-службу (см. раздел [Вход в пошаговом режиме в веб-службу XML](http://msdn.microsoft.com/en-us/8e67de38-bf5f-41cc-a457-1b88ce63d764)). Ошибка может произойти всякий раз при неправильно настроенном [!INCLUDE[vstecasp](../includes/vstecasp-md.md)].  
  
 Возможные причины:  
  
-   Файл web.config для вашего [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] приложения отладки не установлен в «true» (см. в разделе [режим отладки в приложениях ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).  
  
-   Это версия [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] была установлена после установки Visual Studio. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] следует устанавливать до Visual Studio. Чтобы устранить эту неполадку, откройте **Панель управления**Windows и воспользуйтесь компонентом **Программы и компоненты** для исправления установки Visual Studio.  
  
## <a name="see-also"></a>См. также  
 [Ошибки удаленной отладки и устранения неполадок](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Удаленная отладка](../debugger/remote-debugging.md)



