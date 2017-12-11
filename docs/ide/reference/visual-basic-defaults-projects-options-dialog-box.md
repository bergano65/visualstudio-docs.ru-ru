---
title: "Страница \"Параметры Visual Basic по умолчанию\", папка \"Проекты\", диалоговое окно \"Параметры\" | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.ToolsOptionsPages.Projects.VBDefaults
helpviewer_keywords:
- Option Explicit statement, setting in the IDE
- Option Compare statement, setting in the IDE
- Option Strict statement, setting in the IDE
ms.assetid: 2465cd9d-18b6-4c4a-b1ea-86dbab23fc79
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7765323944508eb0d739703bcb78dcf2cdfe08c2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="visual-basic-defaults-projects-options-dialog-box"></a>Страница "Параметры Visual Basic по умолчанию", папка "Проекты", диалоговое окно "Параметры"
Задает значения по умолчанию для параметров проекта Visual Basic. При создании проекта указанные операторы option добавляются в заголовок проекта в редакторе кода. Эти параметры применяются ко всем проектам Visual Basic.  
  
 Чтобы открыть это диалоговое окно, в меню **Сервис** выберите **Параметры**, разверните папку **Проекты и решения** и выберите **Параметры Visual Basic по умолчанию**.  
  
 **Option Explicit**  
 Задает значение компилятора по умолчанию, чтобы требовались явные объявления переменных. По умолчанию **Option Explicit** имеет значение **On**. Дополнительные сведения см. в описании [/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit).  
  
 **Option Strict**  
 Задает значение компилятора по умолчанию, чтобы требовались явные сужающие преобразования, а позднее связывание было запрещено. По умолчанию **Option Strict** имеет значение **Off**. Дополнительные сведения см. в описании [/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict).  
  
 **Option Compare**  
 Задает значение компилятора по умолчанию для сравнения строк: двоичный файл (с учетом регистра) или текст (без учета регистра). По умолчанию **Option Compare** имеет значение **Binary**. Дополнительные сведения см. в описании [/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare).  
  
 **Option Infer**  
 Задает значение компилятора по умолчанию для вывода локального типа. По умолчанию **Option Infer** имеет значение **On** для вновь созданных проектов и **Off** для проектов, перенесенных из более ранних версий Visual Basic. Дополнительные сведения см. в описании [/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer).  
  
## <a name="see-also"></a>См. также  
 [Решения и проекты](../../ide/solutions-and-projects-in-visual-studio.md)