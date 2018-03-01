---
title: "Команда \"Задать текущий кадр стека\" | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- debug.setcurrentstackframe
helpviewer_keywords:
- Set Current Stack Frame command
- Debug.SetCurrentStackFrame command
ms.assetid: 3dcf52c0-6781-4598-bac2-0094dce67c20
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 3011b37cd7794745ce1700c412ccf227147728f0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="set-current-stack-frame-command"></a>Команда Set Current Stack Frame
Позволяет задать определенный кадр стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.SetCurrentStackFrame index  
```  
  
## <a name="arguments"></a>Аргументы  
 `index`  
 Обязательно. Выбирает кадр стека по индексу.  
  
## <a name="example"></a>Пример  
  
```  
>Debug.SetCurrentStackFrame 1  
```  
  
## <a name="see-also"></a>См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)