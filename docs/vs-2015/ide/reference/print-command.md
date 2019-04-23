---
title: Команда "Печать" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 65d78387c6d60d0b432db9aab175fbfe8dc2869b
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59666550"
---
# <a name="print-command"></a>Команда Print
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
  
## <a name="see-also"></a>См. также раздел  
 [Команда "Вычислить оператор"](../../ide/reference/evaluate-statement-command.md)   
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
