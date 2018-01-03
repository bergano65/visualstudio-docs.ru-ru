---
title: "Команда Watch | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ad450688e8399ef247333685f95423e5fab7bec8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="watch-command"></a>Команда Watch
Создает и открывает указанный экземпляр окна **Контрольное значение** . Окно **Контрольные значения** можно использовать для вычисления значений переменных, выражений и регистров, чтобы изменять эти значения и сохранять результаты.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.Watch[index]  
```  
  
## <a name="arguments"></a>Аргументы  
 `index`  
 Обязательно. Номер экземпляра окна контрольных значений  
  
## <a name="remarks"></a>Примечания  
 Значение `index` должно быть целым числом. Допустимые значения: 1, 2, 3 и 4.  
  
## <a name="example"></a>Пример  
  
```  
>Debug.Watch1  
```  
  
## <a name="see-also"></a>См. также  
 [Окна "Видимые" и "Локальные"](../../debugger/autos-and-locals-windows.md)   
 [Set a Watch on Variables using the Watch and QuickWatch Windows in Visual Studio](../../debugger/watch-and-quickwatch-windows.md)  (Установка контрольных значений для переменных с помощью окон "Контрольное значение" и "Быстрая проверка")  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)