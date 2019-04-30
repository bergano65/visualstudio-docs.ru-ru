---
title: 'Ошибка: Не удается автоматически выполнить шаг на сервере | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2d979b53f4bd5962a01fa5eb1b77cc7c81c68a4a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62538464"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Ошибка: не удалось автоматически перейти в режим пошагового выполнения
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Текст сообщения об ошибке.  
  
 "Не удается автоматически выполнить шаг на сервере. Отладчик не получил уведомления перед выполнением удаленной процедуры."  
  
 Эта ошибка может возникнуть, когда предпринята попытка в пошаговом режиме зайти в веб-службу (см. раздел [Вход в пошаговом режиме в веб-службу XML](http://msdn.microsoft.com/8e67de38-bf5f-41cc-a457-1b88ce63d764)). Ошибка может произойти всякий раз при неправильно настроенном [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] .  
  
 Возможные причины:  
  
- Параметр отладки не установлен в "true" в файле web.config приложения [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] (см. раздел [Режим отладки в приложениях ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).  
  
- Версия [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] была установлена после установки Visual Studio. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] следует устанавливать до Visual Studio. Чтобы устранить эту неполадку, откройте **Панель управления**Windows и воспользуйтесь компонентом **Программы и компоненты** для исправления установки Visual Studio.  
  
## <a name="see-also"></a>См. также  
 [Ошибки удаленной отладки и их устранение](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)
