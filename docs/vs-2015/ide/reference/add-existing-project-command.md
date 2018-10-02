---
title: Команда Add Existing Project | Документы Майкрософт
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
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 048ba8e43b66ac5ad4bbc1d0c09adb75a2d61e1d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558617"
---
# <a name="add-existing-project-command"></a>Команда Add Existing Project
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Добавление существующего проекта команды](https://docs.microsoft.com/visualstudio/ide/reference/add-existing-project-command).  
  
  
Добавляет существующий проект в текущее решение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
File.AddExistingProject filename  
```  
  
## <a name="arguments"></a>Аргументы  
 `filename`  
 Необязательный. Полный путь и имя проекта с расширением для проекта, который необходимо добавить в решение.  
  
 Если аргумент `filename` содержит пробелы, его необходимо заключить в кавычки.  
  
 Если имя файла не указано, при выполнении команды откроется диалоговое окно файла, в котором пользователь может выбрать проект.  
  
## <a name="remarks"></a>Примечания  
 Функция автозавершения пытается определить правильный путь и правильное имя файла во время их ввода.  
  
## <a name="example"></a>Пример  
 В этом примере в текущее решение добавляется проект [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] с именем TestProject1.  
  
```  
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"  
```  
  
## <a name="see-also"></a>См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



