---
title: Команда "Псевдоним" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- tools.alias
helpviewer_keywords:
- aliases, Visual Studio commands
- commands, aliases
- Tools.Alias command
- command aliases
- alias command
ms.assetid: bdf857df-b5d5-450f-8c10-a6fd4dccc130
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4260804760b4abe55f6a62efa4841ad08dead1b4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54753274"
---
# <a name="alias-command"></a>Команда Alias
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Создает псевдоним для полной команды, полной команды с аргументами или для другого псевдонима.  
  
> [!TIP]
>  Если ввести `>alias` без аргументов, отображается текущий список псевдонимов и их определений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]  
```  
  
## <a name="arguments"></a>Аргументы  
 `aliasname`  
 Необязательный параметр. Имя нового псевдонима. Если значение для `aliasname` не указано, отображается список текущих псевдонимов и их определений.  
  
 `aliasstring`  
 Необязательный параметр. Полное имя команды или существующий псевдоним и любые параметры, которые вы хотите создать в виде псевдонима. Если значение для `aliasstring` не указано, отображается имя и строка для заданного псевдонима.  
  
## <a name="switches"></a>Переключатели  
 /delete или /del или /d  
 Необязательный параметр. Удаляет указанный псевдоним, убирая его из функции автозавершения.  
  
 /reset  
 Необязательный параметр. Сбрасывает список предопределенных псевдонимов в исходные значения. То есть восстанавливает все предварительно определенные псевдонимы и удаляет все псевдонимы, определенные пользователем.  
  
## <a name="remarks"></a>Примечания  
 Так как псевдонимы представляют команды, они должны располагаться в начале командной строки.  
  
 При вводе данной команды нужно указать параметры сразу после нее, а не после псевдонимов. В противном случае параметр включается в состав строки псевдонима.  
  
 Параметр `/reset` запрашивает подтверждение перед восстановлением псевдонимов. У `/reset` нет краткой формы.  
  
## <a name="examples"></a>Примеры  
 Этот пример создает псевдоним `upper` для полной команды Edit.MakeUpperCase.  
  
```  
>Tools.Alias upper Edit.MakeUpperCase  
```  
  
 Этот пример удаляет псевдоним `upper`.  
  
```  
>Tools.alias /delete upper  
```  
  
 Этот пример отображает список всех текущих псевдонимов и их определений.  
  
```  
>Tools.Alias  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
