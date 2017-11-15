---
title: "Команда \"Задать текущий поток\" | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.setcurrentthread
helpviewer_keywords:
- Set Current Thread command
- Debug.SetCurrentThread command
ms.assetid: 9917ed1d-6c30-4d94-b2f0-69acce74f1b2
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 18c417016071cc25bdccde1c85e97431f20195d9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="set-current-thread-command"></a>Команда Set Current Thread
Задает указанный поток в качестве текущего.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.SetCurrentThread index  
```  
  
## <a name="arguments"></a>Аргументы  
 `index`  
 Обязательный. Выбирает поток по индексу.  
  
## <a name="example"></a>Пример  
  
```  
>Debug.SetCurrentThread 1  
```  
  
## <a name="see-also"></a>См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)