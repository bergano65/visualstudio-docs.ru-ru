---
title: Команда "Вывести память" | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- debug.listmemory
helpviewer_keywords:
- Debug.ListMemory command
- ListMemory command
- list memory command
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 25be71041f0ab127037a25a03cff1d6ffe42ac97
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49224501"
---
# <a name="list-memory-command"></a>Команда List Memory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Отображает содержимое указанного диапазона памяти.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]  
[/Hex|Signed|Unsigned] [expression]  
```  
  
## <a name="arguments"></a>Аргументы  
 `expression`  
 Необязательный. Адрес памяти, с которого начинается отображение памяти.  
  
## <a name="switches"></a>Переключатели  
 /ANSI&#124;Unicode  
 Необязательный. Отображает память в виде символов, соответствующих байтам памяти, в формате ANSI или Юникод.  
  
 /Count:`number`  
 Необязательный. Определяет, сколько байт памяти нужно отобразить, начиная с `expression`.  
  
 /Format:`formattype`  
 Необязательный. Тип формата для просмотра данных памяти в окне **Память**, может иметь значение OneByte, TwoBytes, FourBytes, EightBytes, Float (32-разрядный) или Double (64-разрядный). При использовании OneByte параметр `/Unicode` недоступен.  
  
 /Hex&#124;Signed&#124;Unsigned  
 Необязательный. Указывает формат для просмотра чисел: со знаком, без знака или в шестнадцатеричном формате.  
  
## <a name="remarks"></a>Примечания  
 Вместо записи полной команды **Debug.ListMemory** со всеми параметрами можно вызвать ее, используя стандартные псевдонимы, в которых отдельные параметры уже имеют определенные значения. Например, вместо ввода:  
  
```  
>Debug.ListMemory /Format:float /Count:30 /Unicode  
```  
  
 можно ввести:  
  
```  
>df /Count:30 /Unicode  
```  
  
 Ниже приведен список доступных псевдонимов для команды **Debug.ListMemory**:  
  
|Alias|Команда и параметры|  
|-----------|--------------------------|  
|**d**|Debug.ListMemory|  
|**da**|Debug.ListMemory /Ansi|  
|**db**|Debug.ListMemory /Format:OneByte|  
|**dc**|Debug.ListMemory /Format:FourBytes /Ansi|  
|**dd**|Debug.ListMemory /Format:FourBytes|  
|**df**|Debug.ListMemory /Format:Float|  
|**dq**|Debug.ListMemory /Format:EightBytes|  
|**du**|Debug.ListMemory /Unicode|  
  
## <a name="example"></a>Пример  
  
```  
>Debug.ListMemory /Format:float /Count:30 /Unicode  
```  
  
## <a name="see-also"></a>См. также  
 [Команда "Вывести стек вызовов"](../../ide/reference/list-call-stack-command.md)   
 [Команда List Thread](../../ide/reference/list-threads-command.md)   
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)




