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
ms.openlocfilehash: b8eebd082df031161604bd04afe61d1aca652f6a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850060"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Ошибка: Не удалось подключиться к машине &lt;имя&gt;. Не удается найти компьютер в сети.
Такая ошибка возникает, если выполняется одно из следующих условий:

- Подключение к удаленному компьютеру разорвано.

- Учетная запись пользователя на удаленном компьютере отключена.

- Истек срок действия пароля на удаленном компьютере.

### <a name="to-resolve-this-behavior"></a>Устранение ошибки

- Убедитесь, что удаленный и локальный компьютеры находятся в одной сети. Для этого попытайтесь обратиться к удаленному компьютеру с помощью Проводника Microsoft Windows.

     — и —

- Убедитесь в том, что учетная запись пользователя, используемая для подключения к удаленному компьютеру, активна.

     — и —

- Убедитесь в том, что пароль для подключения к удаленному компьютеру правильный, и срок его действия не истек.

## <a name="see-also"></a>См. также
- [Remote Debugging](../debugger/remote-debugging.md)
- [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)