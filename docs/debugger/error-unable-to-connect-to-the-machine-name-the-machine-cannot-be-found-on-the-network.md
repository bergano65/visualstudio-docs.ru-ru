---
title: 'Ошибка: Не удалось подключиться к машине &lt;имя&gt;. Не удается найти компьютер в сети. | Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.remote.dcom_disabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DCOM, unable to connect error
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6dc7a9b5e066304e27e784312707400d9571a60
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56686578"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Ошибка: Не удалось подключиться к машине &lt;имя&gt;. Не удается найти компьютер в сети.
Такая ошибка возникает, если выполняется одно из следующих условий:

-   Подключение к удаленному компьютеру разорвано.

-   Учетная запись пользователя на удаленном компьютере отключена.

-   Истек срок действия пароля на удаленном компьютере.

### <a name="to-resolve-this-behavior"></a>Устранение ошибки

-   Убедитесь, что удаленный и локальный компьютеры находятся в одной сети. Для этого попытайтесь обратиться к удаленному компьютеру с помощью Проводника Microsoft Windows.

     — и —

-   Убедитесь в том, что учетная запись пользователя, используемая для подключения к удаленному компьютеру, активна.

     — и —

-   Убедитесь в том, что пароль для подключения к удаленному компьютеру правильный, и срок его действия не истек.

## <a name="see-also"></a>См. также раздел
- [Remote Debugging](../debugger/remote-debugging.md)
- [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)