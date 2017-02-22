---
title: "Практическое руководство. Отображение списка элементов, разделенных запятыми | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, форматирование коллекций элементов"
  - "MSBuild, разделение элементов точками с запятой"
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Практическое руководство. Отображение списка элементов, разделенных запятыми
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Во время работы со списками элементов в [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] \([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\) иногда бывает полезно представить содержимое этих списков в виде, наиболее удобном для чтения.  Возможно также, что задача заключается в получении списка элементов, отделенных друг от друга специальной строкой разделителей.  В обоих этих случаях можно указать строку разделителей для списка элементов.  
  
## Отделение элементов в списке с помощью запятых  
 По умолчанию в [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] в качестве разделителей элементов в списке используются точки с запятой.  Например, рассмотрим элемент `Message` со следующим значением:  
  
 `<Message Text="This is my list of TXT files: @(TXTFile)"/>`  
  
 Если в списке `@(TXTFile)` содержатся элементы App1.txt, App2.txt и App3.txt, сообщение выглядит следующим образом:  
  
 `This is my list of TXT files: App1.txt;App2.txt;App3.txt`  
  
 Используемый по умолчанию разделитель можно изменить, указав свой разделитель.  Чтобы указать разделитель списка элементов, используйте следующий синтаксис:  
  
 `@(ItemListName, '<separator>')`  
  
 Разделитель может представлять собой либо отдельный символ, либо строку, и его необходимо заключить в одинарные кавычки.  
  
#### Вставка запятой и пробела между элементами  
  
-   Используйте представление элемента следующего вида:  
  
     `@(TXTFile, ', ')`  
  
## Пример  
 В данном примере задача [Exec](../msbuild/exec-task.md) запускает средство findstr для поиска указанных текстовых строк в файле Phrases.txt.  В команде findstr текстовые строки поиска обозначены ключом **\/c:**, поэтому между элементами в списке `@(Phrase)` вставляется разделитель элементов `/c:`.  
  
 В данном примере соответствующая команда командной строки будет выглядеть следующим образом:  
  
 `findstr /i /c:hello /c:world /c:msbuild phrases.txt`  
  
```  
<Project DefaultTargets = "Find"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <ItemGroup>  
        <Phrase Include="hello"/>  
        <Phrase Include="world"/>  
        <Phrase Include="msbuild"/>  
    </ItemGroup>  
  
    <Target Name = "Find">  
        <!-- Find some strings in a file -->  
        <Exec Command="findstr /i /c:@(Phrase, ' /c:') phrases.txt"/>  
    </Target>  
</Project>  
```  
  
## См. также  
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)   
 [Элементы](../msbuild/msbuild-items.md)