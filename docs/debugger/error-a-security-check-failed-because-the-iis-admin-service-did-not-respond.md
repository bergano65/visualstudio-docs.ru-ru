---
title: 'Ошибка: Сбоя проверки безопасности, поскольку не отвечает служба IIS Admin | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- vs.debug.error.iis_not_responding
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 85b96d9e1396933519da71e93bac075ee51af001
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="error-a-security-check-failed-because-the-iis-admin-service-did-not-respond"></a>Ошибка: не удается выполнить проверку безопасности — служба IIS Admin не отвечает
Эта ошибка возникает, если не отвечает служба IIS Admin. Обычно это означает, что при установке IIS произошла ошибка. Во-первых, убедитесь, что служба выполняется с помощью **службы** средства из **Администрирование**.  
  
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