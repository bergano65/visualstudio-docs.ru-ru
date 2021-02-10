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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dcf52a258a46f44afaf6e890531496f57b11fc24
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871069"
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