---
title: "Команда \"Открыть проект\" | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: file.openproject
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a3b0916874fbd4c16dfe2232a6a5865743d0c388
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="open-project-command"></a>Команда Open Project
Открывает существующий проект.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
File.OpenProject filename  
```  
  
## <a name="arguments"></a>Аргументы  
 `filename`  
 Обязательный. Полный путь и имя файла для открываемого проекта.  
  
 В соответствии с требованиями синтаксиса для аргумента `filename` путь, содержащий пробелы, должен заключаться в кавычки.  
  
## <a name="remarks"></a>Примечания  
 Функция автозавершения пытается определить правильный путь и правильное имя файла во время их ввода.  
  
 Эта команда недоступна при отладке.  
  
## <a name="example"></a>Пример  
 Этот пример открывает проект [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] — Test1.  
  
```  
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"  
```  
  
## <a name="see-also"></a>См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)