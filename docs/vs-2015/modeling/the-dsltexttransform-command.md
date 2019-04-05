---
title: Команда DslTextTransform | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
ms.assetid: 7d025d0b-6543-4a49-9f6b-8b8cfcad77ee
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 220ceab29cb2b9bc1b117a98326d22c3c546a162
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58993987"
---
# <a name="the-dsltexttransform-command"></a>Команда DslTextTransform
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DslTextTransform.cmd — это сценарий, который вызывает TextTransform.exe и запускает его с помощью общих параметров. DslTextTransformation.cmd можно использовать для автоматизации Ночные построения вашей [!INCLUDE[dsl](../includes/dsl-md.md)] проектов. Дополнительные сведения см. в разделе [Создание файлов с помощью служебной программы TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).  
  
 DslTextTransform.cmd находится в следующем каталоге:  
  
 **\<Visual Studio SDK Installation Path>\VisualStudioIntegration\Tools\Bin**  
  
 Можно указать следующие аргументы в качестве входных данных для DslTextTransform.cmd:  
  
- Выходной каталог проекта модели домена.  
  
- Выходной каталог проекта, определение конструктора.  
  
- Расположение текстового файла шаблона.  
  
  DslTextTransform.cmd обрабатывает указанный текстовый файл шаблона, используя процессоры директив по умолчанию и сборки. Если вы создаете пользовательские процессоры директив, можно создать собственный пакетный файл, который вызывает TextTransform.exe. В этом пакетном файле можно указать сборки и связанные пользовательские процессоры директив.
