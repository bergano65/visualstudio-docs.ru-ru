---
title: Команда DslTextTransform | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, commands
ms.assetid: 7d025d0b-6543-4a49-9f6b-8b8cfcad77ee
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 8a565fa6226348a1fe1b6dcfcbb67f704e74abc8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568486"
---
# <a name="the-dsltexttransform-command"></a>Команда DslTextTransform
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [команда DslTextTransform](https://docs.microsoft.com/visualstudio/modeling/the-dsltexttransform-command).  
  
DslTextTransform.cmd — это сценарий, который вызывает TextTransform.exe и запускает его с помощью общих параметров. DslTextTransformation.cmd можно использовать для автоматизации Ночные построения вашей [!INCLUDE[dsl](../includes/dsl-md.md)] проектов. Дополнительные сведения см. в разделе [Создание файлов с помощью служебной программы TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).  
  
 DslTextTransform.cmd находится в следующем каталоге:  
  
 **\<Путь установки пакета SDK для Visual Studio > \VisualStudioIntegration\Tools\Bin**  
  
 Можно указать следующие аргументы в качестве входных данных для DslTextTransform.cmd:  
  
-   Выходной каталог проекта модели домена.  
  
-   Выходной каталог проекта, определение конструктора.  
  
-   Расположение текстового файла шаблона.  
  
 DslTextTransform.cmd обрабатывает указанный текстовый файл шаблона, используя процессоры директив по умолчанию и сборки. Если вы создаете пользовательские процессоры директив, можно создать собственный пакетный файл, который вызывает TextTransform.exe. В этом пакетном файле можно указать сборки и связанные пользовательские процессоры директив.



