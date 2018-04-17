---
title: Команда DslTextTransform | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 11fb12f3716fe9f8b5fee13a7eecd88ee107ff45
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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