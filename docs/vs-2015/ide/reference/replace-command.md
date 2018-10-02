---
title: Команда "Заменить" | Документы Майкрософт
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
- edit.replace
helpviewer_keywords:
- Edit.Replace command
- Replace command
ms.assetid: a15767f1-5a3d-44f5-8c77-7b0f1157f340
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d4de79f804637f13b0fd487b1db62ad4bf7490ce
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561907"
---
# <a name="replace-command"></a>Команда Replace
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [команда Replace](https://docs.microsoft.com/visualstudio/ide/reference/replace-command).  
  
  
Заменяет текст в файлах с использованием подмножества параметров, доступных на вкладке **Заменить в файлах** окна **Поиск и замена**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Edit.Replace findwhat replacewith [/all] [/case]  
[/doc|/proc|/open|/sel] [/hidden] [/options] [/reset] [/up]  
[/wild|/regex] [/word]  
```  
  
## <a name="arguments"></a>Аргументы  
 `findwhat`  
 Обязательно. Текст для поиска совпадения.  
  
 `replacewith`  
 Обязательно. Текст для замены совпавшего текста.  
  
## <a name="switches"></a>Переключатели  
 /all или /a  
 Необязательный. Заменяет все вхождения искомого текста на замещающий текст.  
  
 /case или /c  
 Необязательный. Совпадение происходит только в том случае, если прописные и строчные знаки точно соответствуют тем, что указаны в аргументе `findwhat`.  
  
 /doc или /d  
 Необязательный. Выполняет поиск только в текущем документе. Укажите только одну из доступных областей поиска — `/doc`, `/proc`, `/open` или `/sel`.  
  
 /hidden или /h  
 Необязательный. Выполняет поиск скрытого или свернутого текста, например метаданных элемента управления времени разработки, скрытой области структурированного документа либо свернутого класса или метода.  
  
 /open или /o  
 Необязательный. Выполняет поиск по всем открытым документам, как если бы они были одним документом. Укажите только одну из доступных областей поиска — `/doc`, `/proc`, `/open` или `/sel`.  
  
 /options или /t  
 Необязательный. Отображает список текущих параметров поиска, но не выполняет сам поиск.  
  
 /proc или /p  
 Необязательный. Выполняет поиск только в текущей процедуре. Укажите только одну из доступных областей поиска — `/doc`, `/proc`, `/open` или `/sel`.  
  
 /regex или /r  
 Необязательный. Использует стандартные специальные символы в аргументе `findwhat` для представления текстовых шаблонов вместо самих букв. Полный список знаков регулярных выражений см. в разделе [Регулярные выражения](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 /reset или /e  
 Необязательный. Для параметров поиска возвращает их значения по умолчанию, но не выполняет сам поиск.  
  
 /sel или /s  
 Необязательный. Выполняет поиск только в текущем выделенном фрагменте. Укажите только одну из доступных областей поиска — `/doc`, `/proc`, `/open` или `/sel`.  
  
 /up или /u  
 Необязательный. Выполняет поиск от текущего расположения в файле до его начала. По умолчанию поиск начинается в текущем расположении в файле и ведется по направлению к его концу.  
  
 /wild или /l  
 Необязательный. Использует стандартные специальные символы в аргументе `findwhat` для представления символа или последовательности символов.  
  
 /word или /w  
 Необязательный. Выполняет поиск только целых слов.  
  
## <a name="example"></a>Пример  
 Этот пример заменяет `btnSend` на `btnSubmit` во всех открытых документах.  
  
```  
>Edit.Replace btnSend btnSubmit /open  
```  
  
## <a name="see-also"></a>См. также  
 [Поиск и замена текста](../../ide/finding-and-replacing-text.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



