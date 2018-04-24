---
title: Команда "Задать текущий поток" | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- debug.setcurrentthread
helpviewer_keywords:
- Set Current Thread command
- Debug.SetCurrentThread command
ms.assetid: 9917ed1d-6c30-4d94-b2f0-69acce74f1b2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d3a3ccd860088c38b84b805a54ee17d50240b2e4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="set-current-thread-command"></a>Команда Set Current Thread
Задает указанный поток в качестве текущего.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.SetCurrentThread index  
```  
  
## <a name="arguments"></a>Аргументы  
 `index`  
 Обязательно. Выбирает поток по индексу.  
  
## <a name="example"></a>Пример  
  
```  
>Debug.SetCurrentThread 1  
```  
  
## <a name="see-also"></a>См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)