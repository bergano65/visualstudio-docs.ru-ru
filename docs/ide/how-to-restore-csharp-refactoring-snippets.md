---
redirect_url: /visualstudio/csharp-ide/refactoring-csharp
title: "Практическое руководство. Восстановление фрагментов кода для оптимизации в C# | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unsafe expansion
- expansions, unsafe
ms.assetid: 12114273-7f2f-43d0-abcb-2d4711a3a68d
caps.latest.revision: 20
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a4721d8bbd5dd6ec29f555ee8d4848ef3660243f
ms.openlocfilehash: 87ecb3149443bc90c2398b67158df35b193bcfe1
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-restore-c-refactoring-snippets"></a>Практическое руководство. Восстановление фрагментов кода для оптимизации в C#
Операции рефакторинга в C# основываются на фрагментах кода, находящихся в следующем каталоге:  
  
 *Каталог установки*\Microsoft Visual Studio 14.0\VC#\Snippets\\*код языка*\Refactoring  
  
 Если этот каталог Refactoring или какие либо файлы в нем удалены или повреждены, то операции рефакторинга C# могут не работать в интегрированной среде разработки. Описанные ниже процедуры позволяют восстановить фрагменты кода для рефакторинга в C#.  
  
### <a name="to-verify-c-refactoring-snippets-are-available-through-the-code-snippet-manager"></a>Проверка наличия фрагментов кода для рефакторинга в C# с помощью диспетчера фрагментов кода  
  
1.  В меню **Сервис** выберите пункт **Диспетчер фрагментов кода**.  
  
2.  В диалоговом окне **Диспетчер фрагментов кода** выберите вариант **Visual C#** в раскрывающемся списке **Язык**.  
  
     В древовидном представлении списка папок должна появиться папка **Refactoring**.  
  
### <a name="to-restore-refactoring-see-comment-in-code-snippet-manager"></a>Восстановление функции рефакторинга с помощью примечания в диспетчере фрагментов кода  
  
1.  Если папка **Refactoring** в древовидном представлении списка папок в диспетчере фрагментов кода отсутствует, выполните описанную ниже процедуру, чтобы добавить фрагменты кода для рефакторинга в диспетчер фрагментов кода.  
  
2.  В меню **Сервис** выберите пункт **Диспетчер фрагментов кода**.  
  
3.  В диалоговом окне **Диспетчер фрагментов кода** выберите вариант **Visual C#** в раскрывающемся списке **Язык**.  
  
4.  Нажмите кнопку **Добавить**. Откроется диалоговое окно **Каталог фрагментов кода**, с помощью которого можно найти и указать каталог, который нужно добавить в диспетчер фрагментов кода.  
  
5.  Найдите папку **Refactoring**, путь к которой следующий:  
  
     *Каталог установки*\Microsoft Visual Studio 14.0\VC#\Snippets\\*код языка*\Refactoring  
  
     Фактический путь подобен представленному ниже для установки по умолчанию:  
  
     C:\Program Files\Microsoft Visual Studio 14.0\VC#\Snippets\1033\Refactoring.  
  
6.  Нажмите кнопку **Открыть** в диалоговом окне **Каталог фрагментов кода** и затем нажмите кнопку **ОК** в диспетчере фрагментов кода.  
  
## <a name="see-also"></a>См. также  
 [Фрагменты кода Visual C#](../ide/visual-csharp-code-snippets.md)   
 [Рефакторинг (C#)](../csharp-ide/refactoring-csharp.md)   
 [Фрагменты кода](../ide/code-snippets.md)
