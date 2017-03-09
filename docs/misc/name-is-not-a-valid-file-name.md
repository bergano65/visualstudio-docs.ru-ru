---
title: "&lt;name&gt; is not a valid file name. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS_E_INVALIDFILENAME"
  - "VS.Message.0x00006A72"
ms.assetid: c5969671-3b64-4854-acb6-328e8a30863f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# &lt;name&gt; is not a valid file name.
Эта ошибка обычно возникает при попытке создать новый файл в окне "Команда", когда в его имя вводятся неподдерживаемые знаки.  
  
 Имя файла не может содержать следующие знаки:  
  
-   решетка \(\#\)  
  
-   процент \(%\)  
  
-   амперсанд \(&\)  
  
-   звездочка \(\*\)  
  
-   вертикальная черта \(&#124;\)  
  
-   обратная косая черта \(\\\)  
  
-   двоеточие \(:\)  
  
-   двойные кавычки \("\)  
  
-   меньше \(\<\)  
  
-   больше \(\>\)  
  
-   точка \(.\)  
  
-   вопросительный знак \(?\)  
  
-   косая черта \(\/\)  
  
-   начальные и конечные пробелы \(' '\)  
  
-   имена, зарезервированные в операционной системе Windows или DOS \(например "nul", "aux", "con", "com1", "lpt1" и т. д.\).  
  
### Чтобы исправить эту ошибку  
  
-   Ведите команду с новым именем файла, в котором отсутствуют перечисленные выше знаки.  
  
## См. также  
 [Команда New File](../ide/reference/new-file-command.md)   
 [Команды Visual Studio](../ide/reference/visual-studio-commands.md)