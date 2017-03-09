---
title: "Ошибка MSBuild MSB1027 | Microsoft Docs"
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
  - "MSBuild.CannotAutoDisableAutoResponseFile"
helpviewer_keywords: 
  - "MSB1027"
ms.assetid: 2ef8d643-616c-4608-be76-5c2c8e18a9e7
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB1027
**Ключ \/noautoresponse нельзя указывать в файле автоответов MSBuild.rsp или каком\-либо другом файле, на который ссылается файл автоответов.**  
  
 Ключ **\/noautoresponse** обнаружен в файле MSBuild.rsp или другом файле ответов, включенном в файл MSBuild.rsp.  Файл автоответов нельзя использовать для отключения самого себя.  
  
### Чтобы исправить эту ошибку  
  
-   Укажите другой файл ответов.  
  
-   Удалите ключ **\/noautoresponse** из файла ответов MSBuild.rsp.  
  
## См. также  
 [Справочник по командной строке](../msbuild/msbuild-command-line-reference.md)