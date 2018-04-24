---
title: Команда "Задать текущий кадр стека" | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- debug.setcurrentstackframe
helpviewer_keywords:
- Set Current Stack Frame command
- Debug.SetCurrentStackFrame command
ms.assetid: 3dcf52c0-6781-4598-bac2-0094dce67c20
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f8851530dec3e5e1a2c3e829c1508155a2dbda8a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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