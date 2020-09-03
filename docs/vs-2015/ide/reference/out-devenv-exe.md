---
title: -Out (devenv.exe) | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio], builds
- Devenv, /out switch
- builds [Visual Studio], logs
- error logs [Visual Studio], command-line build errors
- error logs [Visual Studio]
- /out Devenv switch
- out Devenv switch
- builds [Visual Studio], errors
- output files, build errors
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 075746353440462a66133cd83ed9158470d8de5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662202"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Задает файл для хранения и отображения ошибок при запуске, создании, перестроении или развертывании решения.

## <a name="syntax"></a>Синтаксис

```
devenv /out FileName
```

## <a name="arguments"></a>Аргументы
 `FileName` Обязательный. Путь и имя файла для приема ошибок при сборке исполняемого файла.

## <a name="remarks"></a>Remarks
 Если указано несуществующее имя файла, такой файл создается автоматически. Если файл уже существует, то результаты добавляются к имеющемуся в нем содержимому.

 Ошибки сборки в командной строке отображаются в окне **Команда** и представлении "Построитель решений" окна **Вывод**. Этот параметр полезен, если вы выполняете автоматические сборки и хотите видеть результаты.

## <a name="example"></a>Пример
 Этот пример запускает `MySolution` и записывает ошибки в файл `MyErrorLog.txt`.

```
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"
```

## <a name="see-also"></a>См. также:
 [Параметры командной строки devenv](../../ide/reference/devenv-command-line-switches.md) [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md) [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md) [/REBUILD (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md) [/deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
