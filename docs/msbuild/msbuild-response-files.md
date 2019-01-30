---
title: Файлы ответов MSBuild | Документы Майкрософт
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3777be5701e9876352db41a5454d5e12668f6f1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54932121"
---
# <a name="msbuild-response-files"></a>Файлы ответов MSBuild
Файлы ответов (*RSP*) — это текстовые файлы, содержащие параметры командной строки *MSBuild.exe*. Каждый параметр может находиться в отдельной строке, либо все они могут быть в одной строке. Перед строками примечаний указывается символ **#**. Параметр **@** используется для передачи другого файла ответов в *MSBuild.exe*.  
  
## <a name="msbuildrsp"></a>MSBuild.rsp
Файл автоматического ответа — это специальный файл *RSP*, который автоматически используется программой *MSBuild.exe* при сборке проекта. Этот файл *MSBuild.rsp* должен находиться в одном каталоге с программой *MSBuild.exe*, иначе он не будет обнаружен. Этот файл можно изменять для того, чтобы задать для *MSBuild.exe* параметры командной строки по умолчанию. Например, если при сборке проекта всегда используется одно и то же средство ведения журнала, можно добавить в файл *MSBuild.rsp* параметр **-logger**. В этом случае *MSBuild.exe* будет всегда использовать это средство ведения журнала при сборке проекта. 

## <a name="directorybuildrsp"></a>Directory.Build.rsp
В версиях 15.6 и более поздних MSBuild будет выполнять поиск файла *Directory.Build.rsp* в родительских каталогах проекта.  Этот файл может использоваться в репозитории исходного кода для указания аргументов по умолчанию в процессе построения из командной строки.  Кроме того, он может применяться для указаний аргументов командной строки размещенных сборок. 

## <a name="see-also"></a>См. также  
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)   
 [Справочник по командной строке](../msbuild/msbuild-command-line-reference.md)