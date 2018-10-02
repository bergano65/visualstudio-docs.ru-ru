---
title: 'Ошибка: Не отвечает служба IIS Admin сбоя проверки безопасности | Документация Майкрософт'
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f91c872b2012ad677e13450dcb9301b4c8a762fe
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568796"
---
# <a name="error-a-security-check-failed-because-the-iis-admin-service-did-not-respond"></a>Ошибка: не удается выполнить проверку безопасности — служба IIS Admin не отвечает
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [ошибка: безопасность проверить не удалось служба IIS Admin не отвечает](https://docs.microsoft.com/visualstudio/debugger/error-a-security-check-failed-because-the-iis-admin-service-did-not-respond).  
  
Эта ошибка возникает, если не отвечает служба IIS Admin. Обычно это означает, что при установке IIS произошла ошибка. Во-первых, убедитесь, что служба выполняется с помощью **служб** средство из **Администрирование**.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Переустановите IIS с помощью **Установка и удаление программ** панели управления.  
  
-   - или -  
  
-   Удалите IIS с компьютера с помощью элемента панели управления "Установка и удаление программ". Если служба IIS была удалена и ошибка все равно возникает, проверьте реестр и убедитесь в отсутствии следующего ключа:  
  
    ```  
    HKEY_CLASSES_ROOT\CLSID\{A9E69610-B80D-11D0-B9B9-00A0C922E750}  
    ```  
  
     - или -  
  
-   Отключите службу IIS Admin с помощью элемента панели управления "Администрирование". При этом служба IIS будет отключена на данном компьютере.  
  
     После выполнения любого из этих шагов следует перезагрузить данный компьютер.  
  
     Дополнительные сведения см. в документации по IIS.  
  
## <a name="see-also"></a>См. также  
 [Отладка веб-приложений: ошибки и устранение неполадок](../debugger/debugging-web-applications-errors-and-troubleshooting.md)



