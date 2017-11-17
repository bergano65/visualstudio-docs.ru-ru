---
title: "Команда DslTextTransform | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, commands
ms.assetid: 7d025d0b-6543-4a49-9f6b-8b8cfcad77ee
caps.latest.revision: "30"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: fd45a33b421e889b05fd78eceddc0b05126e4a21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="the-dsltexttransform-command"></a>Команда DslTextTransform
DslTextTransform.cmd — это сценарий, который вызывает TextTransform.exe и запускает его с помощью общих параметров. DslTextTransformation.cmd можно использовать для автоматизации Ночные построения из вашего [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] проектов. Дополнительные сведения см. в разделе [создания файлов с помощью служебной программы TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).  
  
 DslTextTransform.cmd находится в следующем каталоге:  
  
 **\<Путь установки пакета SDK для Visual Studio > \VisualStudioIntegration\Tools\Bin**  
  
 В качестве входного для DslTextTransform.cmd можно указать следующие аргументы:  
  
-   Выходной каталог проекта модели домена.  
  
-   Выходной каталог проекта, определение конструктора.  
  
-   Расположение текстового файла шаблона.  
  
 DslTextTransform.cmd обрабатывает указанный текстовый файл шаблона, с помощью процессоров директив по умолчанию и сборки. При создании пользовательского процессора директив, можно создать собственные пакетный файл, который вызывает TextTransform.exe. В этом пакетном файле можно указать сборки и связанные пользовательские процессоры директив.