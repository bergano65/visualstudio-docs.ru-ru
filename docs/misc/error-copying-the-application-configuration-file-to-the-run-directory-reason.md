---
title: "Error copying the application configuration file to the run directory. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cant_copy_appcfg_file"
ms.assetid: 15699a76-16ef-40a8-8ed4-5eef4d2c0e72
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error copying the application configuration file to the run directory. &lt;reason&gt;
Системе работы с проектами не удается скопировать файл app.config в папку, из которой запускается проект.  При возникновении этой ошибки процесс построения завершается неудачей.  
  
 Эта ошибка возникает только при построении EXE\-файла.  
  
 Система построения проектов предпринимает попытку найти файл с именем app.config в корневой папке проекта.  Этот файл затем копируется в выходную папку проекта; его имя в выходной папке будет *outputfile.*config.  
  
 Возможные причины ошибки:  
  
-   нехватка места на диске;  
  
-   превышен предел MAX\_PATH.  
  
 Следует также убедиться, что не существует другой копии работающего приложения.  
  
## См. также  
 [NIB How to: Modify Project Properties and Configuration Settings](http://msdn.microsoft.com/ru-ru/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)