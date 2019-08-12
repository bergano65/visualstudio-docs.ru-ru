---
title: Команда "Перейти" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 010d2c395d77be590b3d8d3bc26fc83aaa63adfa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199264"
---
# <a name="go-to-command"></a>Команда Go To
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Перемещение курсор на указанную строку.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Edit.GoTo [linenumber]  
```  
  
## <a name="arguments"></a>Аргументы  
 `linenumber`  
 Необязательный параметр. Целое число, задающее номер строки, к которой нужно перейти.  
  
## <a name="remarks"></a>Примечания  
 Нумерация строк начинается с единицы. Если значение `linenumber` меньше единицы, отображается первая строка. Если значение `linenumber` больше номера последней строки, отображается последняя строка.  
  
 Если значение `linenumber` не указано, отображается диалоговое окно **Переход на строку**.  
  
 Эта команда имеет псевдоним GoToLn.  
  
## <a name="example"></a>Пример  
  
```  
>Edit.GoTo 125  
```  
  
## <a name="see-also"></a>См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
