---
title: Команда "Запустить" | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a3b2f482fb33664796a4e6fe451a6a2917e9592f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49247721"
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
 Необязательный. Адрес, по которому программа приостанавливает выполнение, сходен с точкой останова в исходном коде. Этот аргумент применяется только в режиме отладки.  
  
## <a name="remarks"></a>Примечания  
 При запуске команды **Запустить** она выполняет операцию RunToCursor по указанному адресу.  
  
## <a name="example"></a>Пример  
 Этот пример запускает отладчик и игнорирует все возникающие исключения.  
  
```  
>Debug.Start  
```  
  
## <a name="see-also"></a>См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



