---
title: "Команда \"Печать\" | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6eaf5d77da1dbc6e005764087dad338458e7ce8c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="print-command"></a>Команда Print
Вычисляет выражение или отображает указанный текст.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.Print text  
```  
  
## <a name="arguments"></a>Аргументы  
 `text`  
 Обязательный. Вычисляемое выражение или отображаемый текст.  
  
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