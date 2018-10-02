---
title: Команда "Создать файл" | Документы Майкрософт
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
- file.newfile
helpviewer_keywords:
- File.NewFile command
- New File command
ms.assetid: 767868d6-a525-425b-a43b-2198f636ab6b
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0e925cee55f0e2c79a02a208a5d792339e6fd86e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570707"
---
# <a name="new-file-command"></a>Команда New File
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [команду создания файла](https://docs.microsoft.com/visualstudio/ide/reference/new-file-command).  
  
  
Создает файл и открывает его. Файл отображается в папке "Прочие файлы".  
  
## <a name="syntax"></a>Синтаксис  
  
```  
File.NewFile [filename] [/t:templatename] [/editor:editorname]  
```  
  
## <a name="arguments"></a>Аргументы  
 `filename`  
 Необязательный. Имя файла. Если имя не указано, задается имя по умолчанию. Если не указано имя шаблона, создается текстовый файл.  
  
## <a name="switches"></a>Переключатели  
 /t:`templatename`  
 Необязательный. Указывает тип создаваемого файла.  
  
 В синтаксической структуре аргумента /t:`templatename` используются данные из диалогового окна "Создание файла". Введите имя категории, обратную косую черту (`\`) и имя шаблона, а затем заключите всю строку в кавычки.  
  
 Например, чтобы создать исходный файл [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)], для аргумента /t:`templatename` нужно ввести следующее:  
  
```  
/t:"Visual C++\C++ File (.cpp)"  
```  
  
 В приведенном выше примере указано, что шаблон файла C++ находится внутри категории Visual C++ в диалоговом окне **Новый файл**.  
  
 /e:`editorname`  
 Необязательный. Имя редактора, в котором будет открыт файл. Если аргумент указан, но имя редактора не предоставляется, отображается диалоговое окно **Открыть с помощью**.  
  
 В синтаксической структуре аргумента /e:`editorname` имена редакторов используются в том виде, в каком они отображаются в диалоговом окне "Открыть с помощью", с заключением в кавычки.  
  
 Например, чтобы открыть файл в редакторе исходного кода, нужно ввести для аргумента /e:`editorname` следующую строку:  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## <a name="example"></a>Пример  
 Этот пример создает веб-страницу "test1.htm" и открывает ее в редакторе исходного кода.  
  
```  
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"  
```  
  
## <a name="see-also"></a>См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Окно интерпретации](../../ide/reference/immediate-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



