---
title: "Cannot copy multifile assembly &#39;assembly&#39; to directory &#39;directory&#39;. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannotcopyscatterassembly"
ms.assetid: 939519c7-741d-4e05-8b63-71e39fb426ad
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Cannot copy multifile assembly &#39;assembly&#39; to directory &#39;directory&#39;. &lt;reason&gt;
Многофайловые сборки копируются в ту вложенную папку папки проекта, из которого они будут запускаться.  К примеру, если путь выходных данных имеет вид c:\\project1\\bin, и существует содержащая файлы a.dll и b.dll сборка с именем Test, у которой свойство `CopyLocal` имеет значение `true`, то после завершения копирования файловая структура будет следующая:  
  
```  
c:\project1\bin\Test  
   c:\project1\bin\Test\Test.dll   (main assembly)  
   c:\project1\bin\Test\a.dll       (file a.dll)  
   c:\project1\bin\Test\b.dll       (file b.dll)  
```  
  
 Система работы с проектами выдаст это сообщение об ошибке, если на диске не удастся создать папку c:\\project1\\bin\\Test.  
  
 Эта ошибка означает, что отсутствует свободное пространство на диске или превышен предел MAX\_PATH для длины пути.  
  
 **Чтобы исправить эту ошибку**  
  
-   Убедитесь в наличии свободного пространства на диске.  
  
-   Переместите проект в другую папку с меньшей длиной пути.  
  
-   Замените выходную папку папкой с меньшей длиной абсолютного пути \(для веб\-проектов этого делать нельзя\).  
  
## См. также  
 [Диагностика неработающих ссылок](../ide/troubleshooting-broken-references.md)   
 [Практическое руководство. Добавление и удаление ссылок с помощью диалогового окна "Добавление ссылок"](http://msdn.microsoft.com/ru-ru/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Assemblies in the Common Language Runtime](http://msdn.microsoft.com/ru-ru/33a0bc6a-6bb3-44c7-ada7-4a046e8c0945)