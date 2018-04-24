---
title: Команда Quick Watch | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 75ac6c430d34dabdba3a6bebcce78c7c5b9817b7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="quick-watch-command"></a>Команда Quick Watch
Отображает выбранный или указанный текст в поле "Выражение" окна [Быстрая проверка](../../debugger/watch-and-quickwatch-windows.md). Это диалоговое окно предназначено для вычисления текущего значения переменной или выражения, распознанного отладчиком, либо содержимого регистра. Кроме того, можно изменить значение любой неконстантной переменной или содержимое регистров.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.QuickWatchq [text]  
```  
  
## <a name="arguments"></a>Аргументы  
 `text`  
 Необязательный. Текст для добавления в диалоговое окно **Быстрая проверка**  
  
## <a name="remarks"></a>Примечания  
 Если параметр `text` опущен, выделенный текст или слово в позиции курсора добавляется в окно контрольных значений.  
  
## <a name="example"></a>Пример  
  
```  
>Debug.QuickWatch  
```  
  
## <a name="see-also"></a>См. также  
 [Set a Watch on Variables using the Watch and QuickWatch Windows in Visual Studio](../../debugger/watch-and-quickwatch-windows.md)  (Установка контрольных значений для переменных с помощью окон "Контрольное значение" и "Быстрая проверка")  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)