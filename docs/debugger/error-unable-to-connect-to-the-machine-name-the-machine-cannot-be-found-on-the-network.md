---
title: не удается подключиться к компьютеру &lt;имя&gt;. Не удается найти компьютер в сети. | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: error-reference
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
ms.openlocfilehash: d1ab43773b4aa9d2535eb6ac157ec39333907731
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852515"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Ошибка: не удается подключиться к компьютеру &lt;имя&gt;. Не удается найти компьютер в сети.
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