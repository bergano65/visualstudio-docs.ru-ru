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
ms.openlocfilehash: 9531151402b5070aaa3a680e09e0082b4e1237f0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54972044"
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
 [Удаленная отладка](../debugger/remote-debugging.md)   
 [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)