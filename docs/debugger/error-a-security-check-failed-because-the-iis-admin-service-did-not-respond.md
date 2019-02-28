---
title: 'Ошибка: Не отвечает служба IIS Admin сбоя проверки безопасности | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.iis_not_responding
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe294bd375f4896286b32d0d2c638fa8b467061b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56688034"
---
# <a name="error-a-security-check-failed-because-the-iis-admin-service-did-not-respond"></a>Ошибка: не удается выполнить проверку безопасности — служба IIS Admin не отвечает
Эта ошибка возникает, если не отвечает служба IIS Admin. Обычно это означает, что при установке IIS произошла ошибка. Сначала проверьте, что служба выполняется с помощью инструмента **Службы** в окне **Администрирование**.

### <a name="to-correct-this-error"></a>Исправление ошибки

-   Переустановите IIS с помощью элемента панели управления **Установка и удаление программ**.

-   - или -

-   Удалите IIS с компьютера с помощью элемента панели управления "Установка и удаление программ". Если служба IIS была удалена и ошибка все равно возникает, проверьте реестр и убедитесь в отсутствии следующего ключа:

    `HKEY_CLASSES_ROOT\CLSID\{A9E69610-B80D-11D0-B9B9-00A0C922E750}`

     - или -

-   Отключите службу IIS Admin с помощью элемента панели управления "Администрирование". При этом служба IIS будет отключена на данном компьютере.

     После выполнения любого из этих шагов следует перезагрузить данный компьютер.

     Дополнительные сведения см. в документации по IIS.

## <a name="see-also"></a>См. также раздел
- [Отладка веб-приложений: ошибки и устранение неполадок](../debugger/debugging-web-applications-errors-and-troubleshooting.md)