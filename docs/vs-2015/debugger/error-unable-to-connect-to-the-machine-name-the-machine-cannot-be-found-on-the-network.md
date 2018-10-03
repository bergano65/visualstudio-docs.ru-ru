---
title: 'Ошибка: Не удалось подключиться к машине &lt;имя&gt;. Не удается найти компьютер в сети. | Документы Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fbd5299c8bd14581a9228b7aa0491af6455b1fda
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562608"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Ошибка: Не удалось подключиться к машине &lt;имя&gt;. Не удается найти компьютер в сети.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [ошибка: не удалось подключиться к машине &lt;имя&gt;. Не удается найти компьютер в сети. ](https://docs.microsoft.com/visualstudio/debugger/error-unable-to-connect-to-the-machine-name-the-machine-cannot-be-found-on-the-network).  
  
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



