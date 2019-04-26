---
title: Команда "Запустить" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c334f52ba080329ef5cbd6dfde1e3e3beed1dc70
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62551277"
---
# <a name="start-command"></a>Команда Start
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Начинает отладку запускаемого проекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.Start [address]  
```  
  
## <a name="arguments"></a>Аргументы  
 `address`  
 Необязательный параметр. Адрес, по которому программа приостанавливает выполнение, сходен с точкой останова в исходном коде. Этот аргумент применяется только в режиме отладки.  
  
## <a name="remarks"></a>Примечания  
 При запуске команды **Запустить** она выполняет операцию RunToCursor по указанному адресу.  
  
## <a name="example"></a>Пример  
 Этот пример запускает отладчик и игнорирует все возникающие исключения.  
  
```  
>Debug.Start  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
