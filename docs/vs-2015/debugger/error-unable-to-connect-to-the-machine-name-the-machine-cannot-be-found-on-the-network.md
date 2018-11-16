---
title: 'Ошибка: Не удалось подключиться к машине &lt;имя&gt;. Не удается найти компьютер в сети. | Документы Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: e8660b08adb0d925eb0f1b084673877734a47207
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733762"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Ошибка: Не удалось подключиться к машине &lt;имя&gt;. Не удается найти компьютер в сети.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
## <a name="see-also"></a>См. также  
 [Настройка инструментов удаленной отладки на устройстве](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)   
 [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)



