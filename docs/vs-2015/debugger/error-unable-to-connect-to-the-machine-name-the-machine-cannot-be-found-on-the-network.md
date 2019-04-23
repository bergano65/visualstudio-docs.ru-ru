---
title: 'Ошибка: Не удалось подключиться к машине &lt;имя&gt;. Не удается найти компьютер в сети. | Документы Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.remote.dcom_disabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- DCOM, unable to connect error
ms.assetid: b584b5db-ef52-45ed-8561-1314da3cc5b8
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 41b1cef49425540980938b4d84a1825c171b271b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60045698"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Ошибка: Не удалось подключиться к машине &lt;имя&gt;. Не удается найти компьютер в сети.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 [Настройка инструментов удаленной отладки на устройстве](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)   
 [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)
