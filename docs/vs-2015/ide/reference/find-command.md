---
title: Команда "Найти" | Документы Майкрософт
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
- edit.find
helpviewer_keywords:
- Find command
- Edit.Find command
ms.assetid: f0c705dc-2b97-423d-abbf-5584d4827208
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6deea29955bac41fb9714f094456775862259b40
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571082"
---
# <a name="find-command"></a>Команда Find
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [найти команду](https://docs.microsoft.com/visualstudio/ide/reference/find-command).  
  
  
Выполняет поиск в файлах с использованием набора параметров, доступных на вкладке **Найти в файлах** диалогового окна **Поиск и замена**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]   
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]  
```  
  
## <a name="arguments"></a>Аргументы  
 `findwhat`  
 Обязательно. Текст для поиска совпадения.  
  
## <a name="switches"></a>Переключатели  
 /case или /c  
 Необязательный. Совпадение происходит только в том случае, если прописные и строчные знаки точно соответствуют тем, что указаны в аргументе `findwhat`.  
  
 /doc или /d  
 Необязательный. Выполняет поиск только в текущем документе. Укажите только одну из доступных областей поиска — `/doc`, `/proc`, `/open` или `/sel`.  
  
 /markall или/m  
 Необязательный. Помещает изображение в каждой строке, содержащей совпадение в текущем документе.  
  
 /open или /o  
 Необязательный. Выполняет поиск по всем открытым документам, как если бы они были одним документом. Укажите только одну из доступных областей поиска — `/doc`, `/proc`, `/open` или `/sel`.  
  
 /options или /t  
 Необязательный. Отображает список текущих параметров поиска, но не выполняет сам поиск.  
  
 /proc или /p  
 Необязательный. Выполняет поиск только в текущей процедуре. Укажите только одну из доступных областей поиска — `/doc`, `/proc`, `/open` или `/sel`.  
  
 /reset или /e  
 Необязательный. Для параметров поиска возвращает их значения по умолчанию, но не выполняет сам поиск.  
  
 /sel или /s  
 Необязательный. Выполняет поиск только в текущем выделенном фрагменте. Укажите только одну из доступных областей поиска — `/doc`, `/proc`, `/open` или `/sel`.  
  
 /up или /u  
 Необязательный. Выполняет поиск от текущего расположения в файле до его начала. По умолчанию поиск начинается в текущем расположении в файле и ведется по направлению к его концу.  
  
 /regex или /r  
 Необязательный. Использует стандартные специальные символы в аргументе `findwhat` для представления текстовых шаблонов вместо самих букв. Полный список знаков регулярных выражений см. в разделе [Регулярные выражения](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 /wild или /l  
 Необязательный. Использует стандартные специальные символы в аргументе `findwhat` для представления символа или последовательности символов.  
  
 /word или /w  
 Необязательный. Выполняет поиск только целых слов.  
  
## <a name="example"></a>Пример  
 Этот пример выполняет учитывающий регистр поиск слова "somestring" в выбранном разделе кода.  
  
```  
>Edit.Find somestring /sel /case  
```  
  
## <a name="see-also"></a>См. также  
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



