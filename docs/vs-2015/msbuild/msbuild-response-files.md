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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189379"
---
# <a name="msbuild-response-files"></a>Файлы ответов MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Файлы ответов (RSP) — это текстовые файлы, содержащие параметры командной строки MSBuild.exe. Каждый параметр может находиться в отдельной строке, либо все они могут быть в одной строке. Перед строками примечаний указывается символ **#** . **@** Параметр используется для передачи другого файла ответа в MSBuild.exe.  
  
 Файл автоматического ответа — это специальный файл RSP, который автоматически используется программой MSBuild.exe при сборке проекта. Этот файл MSBuild.rsp должен находится в одном каталоге с программой MSBuild.exe, иначе он не будет обнаружен. Этот файл можно изменять для того, чтобы задать для MSBuild.exe параметры командной строки по умолчанию. Например, если одно и то же средство ведения журнала используется при каждом построении проекта, можно добавить параметр **/Logger** в MSBuild. rsp, а MSBuild.exe будет использовать средство ведения журнала при каждом построении проекта.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по MSBuild](../msbuild/msbuild-reference.md)   
 [Справочник по командной строке](../msbuild/msbuild-command-line-reference.md)
