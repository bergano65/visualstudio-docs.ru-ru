---
title: Команда "Печать" | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 66175f8aa1d371386793b892c0ead5b4dd1885b0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="print-command"></a>Команда Print
Вычисляет выражение или отображает указанный текст.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.Print text  
```  
  
## <a name="arguments"></a>Аргументы  
 `text`  
 Обязательно. Вычисляемое выражение или отображаемый текст.  
  
## <a name="remarks"></a>Примечания  
 Вы можете использовать вопросительный знак (?) в качестве псевдонима для этой команды. Таким образом, команда  
  
```  
>Debug.Print expA  
```  
  
 может быть записана в виде  
  
```  
>? expA  
```  
  
 Обе версии этой команды возвращают текущее значение выражения `expA`.  
  
## <a name="example"></a>Пример  
  
```  
>Debug.Print varA  
```  
  
## <a name="see-also"></a>См. также  
 [Команда "Вычислить оператор"](../../ide/reference/evaluate-statement-command.md)   
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)