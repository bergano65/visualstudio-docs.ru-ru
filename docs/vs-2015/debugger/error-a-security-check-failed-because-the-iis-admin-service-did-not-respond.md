---
title: 'Ошибка: Не удалось выполнить проверку безопасности, поскольку служба IIS Admin не отвечает | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.iis_not_responding
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 6060e94e-71dc-49f2-bb59-2584216eadbf
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 65eb724d14123292a0694623bf46859f8a3966f9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197087"
---
# <a name="error-a-security-check-failed-because-the-iis-admin-service-did-not-respond"></a>Ошибка: проверка безопасности не прошла, так как не был получен ответ от службы администрирования IIS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эта ошибка возникает, если не отвечает служба IIS Admin. Обычно это означает, что при установке IIS произошла ошибка. Сначала проверьте, что служба выполняется с помощью инструмента **Службы** в окне **Администрирование**.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Переустановите IIS с помощью элемента панели управления **Установка и удаление программ**.  
  
- -или-  
  
- Удалите IIS с компьютера с помощью элемента панели управления "Установка и удаление программ". Если служба IIS была удалена и ошибка все равно возникает, проверьте реестр и убедитесь в отсутствии следующего ключа:  
  
    ```  
    HKEY_CLASSES_ROOT\CLSID\{A9E69610-B80D-11D0-B9B9-00A0C922E750}  
    ```  
  
     -или-  
  
- Отключите службу IIS Admin с помощью элемента панели управления "Администрирование". При этом служба IIS будет отключена на данном компьютере.  
  
     После выполнения любого из этих шагов следует перезагрузить данный компьютер.  
  
     Дополнительные сведения см. в документации по IIS.  
  
## <a name="see-also"></a>См. также  
 [Отладка веб-приложений: ошибки и устранение неполадок](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
