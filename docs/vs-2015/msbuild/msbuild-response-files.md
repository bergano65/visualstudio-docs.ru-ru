---
title: Файлы ответов MSBuild | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 71fdc29db3e2af66c85637648bb0703e7f7d80c1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558828"
---
# <a name="msbuild-response-files"></a>Файлы ответов MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [файлы ответов MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-response-files).  
  
  
Файлы ответов (RSP) — это текстовые файлы, содержащие параметры командной строки MSBuild.exe. Каждый параметр может находиться в отдельной строке, либо все они могут быть в одной строке. Перед строками примечаний указывается символ **#**. Параметр **@** используется для передачи другого файла ответов в MSBuild.exe.  
  
 Файл автоматического ответа — это специальный файл RSP, который автоматически используется программой MSBuild.exe при сборке проекта. Этот файл MSBuild.rsp должен находится в одном каталоге с программой MSBuild.exe, иначе он не будет обнаружен. Этот файл можно изменять для того, чтобы задать для MSBuild.exe параметры командной строки по умолчанию. Например, если при сборке проекта всегда используется одно и то же средство ведения журнала, можно добавить в файл MSBuild.rsp параметр **/logger**. В этом случае MSBuild.exe будет всегда использовать это средство ведения журнала при сборке проекта.  
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)   
 [Справочник по командной строке](../msbuild/msbuild-command-line-reference.md)



