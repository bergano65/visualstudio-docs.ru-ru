---
title: Команда "Добавить новый элемент" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- project.addnewitem
helpviewer_keywords:
- Add New Item command
- File.AddNewItem command
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0ba7820bfa6df7273f170b2222d6a55e685e445e
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59668136"
---
# <a name="add-new-item-command"></a>Команда Add New Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Добавляет новый элемент решения, такой как HTM, CSS, TXT или набор фреймов, в текущее решение и открывает его.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
File.AddNewItem [filename] [/t:templatename] [/e:editorname]  
```  
  
## <a name="arguments"></a>Аргументы  
 `filename`  
 Необязательный параметр. Путь и имя файла элемента, который необходимо добавить в решение.  
  
## <a name="switches"></a>Переключатели  
 /t: `templatename`  
 Необязательный параметр. Указывает тип создаваемого файла. Если имя шаблона не задано, по умолчанию создается текстовый файл.  
  
 В синтаксической структуре аргумента /t:`templatename` используются данные, находящиеся в диалоговом окне **Добавление нового элемента решения**. Вам необходимо ввести полную категорию, затем тип файла, отделив имя категории от типа файла обратной косой чертой (`\`) и заключив всю строку в кавычки.  
  
 Например, чтобы создать текстовый файл, для аргумента /t:`templatename` необходимо ввести следующую строку:  
  
```  
/t:"General\Style Sheet"  
```  
  
 /e: `editorname`  
 Необязательный параметр. Имя редактора, в котором будет открыт файл. Если аргумент указан, но имя редактора не предоставляется, отображается диалоговое окно **Открыть с помощью**.  
  
 В синтаксической структуре аргумента /e:`editorname` имена редакторов используются в том виде, в каком они отображаются в диалоговом окне **Открыть с помощью**, с заключением в кавычки.  
  
 Например, чтобы открыть таблицу стилей в редакторе исходного кода, необходимо ввести для аргумента /e:`editorname` следующую строку:  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## <a name="example"></a>Пример  
 В приведенном примере в текущее решение добавляется новый элемент решения MyHTMLpg.  
  
```  
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
