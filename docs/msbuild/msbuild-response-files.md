---
title: Файлы ответов MSBuild | Документы Майкрософт
description: Сведения о файлах ответов (.rsp), которые представляют собой текстовые файлы, содержащие параметры командной строки MSBuild.exe.
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b18ad00c3be8c3684551f28bc170dbd4a8428533
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049139"
---
# <a name="msbuild-response-files"></a>Файлы ответов MSBuild

Файлы ответов ( *RSP* ) — это текстовые файлы, содержащие параметры командной строки *MSBuild.exe*. Каждый параметр может находиться в отдельной строке, либо все они могут быть в одной строке. Перед строками примечаний указывается символ **#** . Параметр **@** используется для передачи другого файла ответов в *MSBuild.exe*.

## <a name="msbuildrsp"></a>MSBuild.rsp

Файл автоматического ответа — это специальный файл *RSP* , который автоматически используется программой *MSBuild.exe* при сборке проекта. Этот файл *MSBuild.rsp* должен находиться в одном каталоге с программой *MSBuild.exe* , иначе он не будет обнаружен. Этот файл можно изменять для того, чтобы задать для *MSBuild.exe* параметры командной строки по умолчанию. Например, если при сборке проекта всегда используется одно и то же средство ведения журнала, можно добавить в файл *MSBuild.rsp* параметр **-logger**. В этом случае *MSBuild.exe* будет всегда использовать это средство ведения журнала при сборке проекта.

## <a name="directorybuildrsp"></a>Directory.Build.rsp

В версиях 15.6 и более поздних MSBuild будет выполнять поиск файла *Directory.Build.rsp* в родительских каталогах проекта.  Этот файл может использоваться в репозитории исходного кода для указания аргументов по умолчанию в процессе построения из командной строки.  Кроме того, он может применяться для указаний аргументов командной строки размещенных сборок.

## <a name="see-also"></a>См. также

- [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)
- [Справочник по командной строке](../msbuild/msbuild-command-line-reference.md)
