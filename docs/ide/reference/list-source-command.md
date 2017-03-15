---
title: "Команда List Source | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Debug.ListSource"
helpviewer_keywords: 
  - "Debug.ListSource - команда"
  - "Вывести исходный код - команда"
  - "ListSource - команда"
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# Команда List Source
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Отображение заданных строк исходного кода.  
  
## Синтаксис  
  
```  
Debug.ListSource [/Count:number] [/Current] [/File:filename]  
[/Line:number] [/ShowLineNumbers:yes|no]  
```  
  
## Переключатели  
 \/Count:`number`  
 Необязательный.  Указание числа строк для отображения.  
  
 \/Current  
 Необязательный.  Отображение текущей строки.  
  
 \/File:`filename`  
 Необязательный.  Путь к файлу для отображения.  Если имя файла не указано, при выполнении команды отображается исходный код строки текущего выражения.  
  
 \/Line:`number`  
 Необязательный.  Отображение определенного номера строки.  
  
 ShowLineNumbers `yes|no`  
 Необязательный.  Указание отображения номеров строк.  
  
## Заметки  
  
## Пример  
 В следующем примере показан исходный код со строки 4 файла Form1.vb с отображением номеров строк.  
  
```  
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes  
```  
  
## См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Окно "Команда"](../../ide/reference/command-window.md)