---
title: "Команда DslTextTransform | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Доменный язык, команды"
ms.assetid: 7d025d0b-6543-4a49-9f6b-8b8cfcad77ee
caps.latest.revision: 30
caps.handback.revision: 30
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Команда DslTextTransform
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

DslTextTransform.cmd — это сценарий, который вызывает TextTransform.exe и запускает его с помощью общих параметров. DslTextTransformation.cmd можно использовать для автоматизации Ночные построения вашей [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] проектов. Дополнительные сведения см. в разделе [Создание файлов с помощью служебной программы TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).  
  
 DslTextTransform.cmd находится в следующем каталоге:  
  
 **\< путь установки пакета SDK ДЛЯ visual Studio>\VisualStudioIntegration\Tools\Bin**  
  
 Можно указать следующие аргументы в качестве входных данных для DslTextTransform.cmd:  
  
-   Выходной каталог проекта модели домена.  
  
-   Выходной каталог проекта определение конструктора.  
  
-   Расположение файла текстового шаблона.  
  
 DslTextTransform.cmd обрабатывает шаблон в указанный текстовый файл, используя процессоры директив по умолчанию и сборки. Если создать пользовательские процессоры директив, можно создать собственный пакетный файл, вызывающий TextTransform.exe. В этом пакетном файле можно указать сборки и связанные пользовательские процессоры директив.