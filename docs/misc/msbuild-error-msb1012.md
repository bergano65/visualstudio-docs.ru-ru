---
title: "Ошибка MSBuild MSB1012 | Microsoft Docs"
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
  - "MSBuild.MissingResponseFileError"
helpviewer_keywords: 
  - "MSB1012"
ms.assetid: 6e09e21d-9f64-4a8c-adec-f8efb28b7ac2
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB1012
**Укажите файл ответов.**  
  
 Для ключа @ необходимо указать файл ответов.  
  
### Чтобы исправить эту ошибку  
  
-   Укажите файл ответов.  Используйте следующий синтаксис: @\<имя файла\>, например `@BuildHW.txt`  
  
-   Не включайте ключ @ в командную строку.  
  
## См. также  
 [Справочник по командной строке](../msbuild/msbuild-command-line-reference.md)