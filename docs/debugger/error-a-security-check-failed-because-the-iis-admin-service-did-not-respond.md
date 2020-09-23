---
title: проверка безопасности не прошла, так как не был получен ответ от службы администрирования IIS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: error-reference
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
ms.openlocfilehash: 015a159f8d4910a2cc9bfbd97a50ebe01253d011
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852814"
---
# <a name="error-a-security-check-failed-because-the-iis-admin-service-did-not-respond"></a>Ошибка: проверка безопасности не прошла, так как не был получен ответ от службы администрирования IIS
Эта ошибка возникает, если не отвечает служба IIS Admin. Обычно это означает, что при установке IIS произошла ошибка. Сначала проверьте, что служба выполняется с помощью инструмента **Службы** в окне **Администрирование**.

### <a name="to-correct-this-error"></a>Исправление ошибки

- Переустановите IIS с помощью элемента панели управления **Установка и удаление программ**.

- -или-

- Удалите IIS с компьютера с помощью элемента панели управления "Установка и удаление программ". Если служба IIS была удалена и ошибка все равно возникает, проверьте реестр и убедитесь в отсутствии следующего ключа:

    `HKEY_CLASSES_ROOT\CLSID\{A9E69610-B80D-11D0-B9B9-00A0C922E750}`

     -или-

- Отключите службу IIS Admin с помощью элемента панели управления "Администрирование". При этом служба IIS будет отключена на данном компьютере.

     После выполнения любого из этих шагов следует перезагрузить данный компьютер.

     Дополнительные сведения см. в документации по IIS.

## <a name="see-also"></a>См. также
- [Отладка веб-приложений: ошибки и устранение неполадок](../debugger/debugging-web-applications-errors-and-troubleshooting.md)