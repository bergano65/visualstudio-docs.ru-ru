---
title: "Файлы ответов MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "RSP-файлы"
  - "MSBuild, RSP-файлы"
  - "MSBuild, файлы ответа"
  - "файлы ответа, MSBuild"
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
caps.latest.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 3
---
# Файлы ответов MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Файлы ответов \(.rsp\) — это текстовые файлы, содержащие переключатель командной строки MSBuild.exe.  Каждый переключатель может находится на отдельной строке или на одной строке с остальными переключателями.  Перед строками примечаний расположен символ **\#**.  Переключатель **@** используется для передачи другого файла ответов в MSBuild.exe.  
  
 Файл автоматического ответа — это специальный файл .rsp, который автоматически используется MSBuild.exe при построении проекта.  Этот файл MSBuild.rsp должен находится в одном каталоге с MSBuild.exe, иначе он не будет обнаружен.  Этот файл можно изменять для того, чтобы задать для MSBuild.exe переключатели командной строки по умолчанию.  Например, если при построении проекта всегда используется одно и то же средство ведения журнала, можно добавить в файл MSBuild.rsp переключатель **\/logger**, тогда MSBuild.exe будет всегда использовать это средство ведения журнала при построении проекта.  
  
## См. также  
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)   
 [Справочник по командной строке](../msbuild/msbuild-command-line-reference.md)