---
title: Файлы ответов MSBuild | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- response files, MSBuild
- MSBuild, response files
- MSBuild, .rsp files
- .rsp files
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a1ce11edac37368b9c4993a87a8c2b3e734b7862
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59649619"
---
# <a name="msbuild-response-files"></a>Файлы ответов MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Файлы ответов (RSP) — это текстовые файлы, содержащие параметры командной строки MSBuild.exe. Каждый параметр может находиться в отдельной строке, либо все они могут быть в одной строке. Перед строками примечаний указывается символ **#**. Параметр **@** используется для передачи другого файла ответов в MSBuild.exe.  
  
 Файл автоматического ответа — это специальный файл RSP, который автоматически используется программой MSBuild.exe при сборке проекта. Этот файл MSBuild.rsp должен находится в одном каталоге с программой MSBuild.exe, иначе он не будет обнаружен. Этот файл можно изменять для того, чтобы задать для MSBuild.exe параметры командной строки по умолчанию. Например, если при сборке проекта всегда используется одно и то же средство ведения журнала, можно добавить в файл MSBuild.rsp параметр **/logger**. В этом случае MSBuild.exe будет всегда использовать это средство ведения журнала при сборке проекта.  
  
## <a name="see-also"></a>См. также раздел  
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)   
 [Справочник по командной строке](../msbuild/msbuild-command-line-reference.md)
