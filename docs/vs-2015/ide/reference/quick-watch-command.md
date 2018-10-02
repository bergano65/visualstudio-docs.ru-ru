---
title: Команда Quick Watch | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9d340f88b83e5dce3054a264a2815fa96707a19f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568770"
---
# <a name="quick-watch-command"></a>Команда Quick Watch
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Контрольное значение-команда](https://docs.microsoft.com/visualstudio/ide/reference/quick-watch-command).  
  
  
Отображает выбранный или указанный текст в поле выражения [диалоговое окно "Быстрая проверка"](http://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867). Это диалоговое окно предназначено для вычисления текущего значения переменной или выражения, распознанного отладчиком, либо содержимого регистра. Кроме того, можно изменить значение любой неконстантной переменной или содержимое регистров.  
  
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
 [Практическое: используйте диалоговое окно "Быстрая проверка"](http://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



