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
ms.openlocfilehash: dd1402a476ce2dceaaaf78580b36db20c3eed24f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65682557"
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
 [Настройка инструментов удаленной отладки на устройстве](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)   
 [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)
