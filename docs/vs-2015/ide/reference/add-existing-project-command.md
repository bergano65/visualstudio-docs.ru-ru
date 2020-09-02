---
title: Команда Add Existing Project | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 73d8e54938659920227b3614046b8a8f933023ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670212"
---
# <a name="add-existing-project-command"></a>Команда Add Existing Project
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Добавляет существующий проект в текущее решение.

## <a name="syntax"></a>Синтаксис

```
File.AddExistingProject filename
```

## <a name="arguments"></a>Аргументы
 `filename` Необязательный. Полный путь и имя проекта с расширением для проекта, который необходимо добавить в решение.

 Если аргумент `filename` содержит пробелы, его необходимо заключить в кавычки.

 Если имя файла не указано, при выполнении команды откроется диалоговое окно файла, в котором пользователь может выбрать проект.

## <a name="remarks"></a>Remarks
 Функция автозавершения пытается определить правильный путь и правильное имя файла во время их ввода.

## <a name="example"></a>Пример
 В этом примере в текущее решение добавляется проект [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] с именем TestProject1.

```
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"
```

## <a name="see-also"></a>См. также:
 Команды [Visual Studio командное](../../ide/reference/visual-studio-commands.md) [окно](../../ide/reference/command-window.md) [Найти/Команда](../../ide/find-command-box.md) командные [псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
