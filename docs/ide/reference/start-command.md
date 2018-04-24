---
title: Команда "Запустить" | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2a4c372d3f384eeaa0ac137188e325ccde777cd4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="start-command"></a>Команда Start
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
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)