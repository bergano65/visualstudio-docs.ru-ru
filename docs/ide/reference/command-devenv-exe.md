---
title: -Command (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /command switch
- /command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c21402c3b2b71372aaf170c68c65777eba4e95bf
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)
Выполняет заданную команду после запуска интегрированной среды разработки (IDE) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="syntax"></a>Синтаксис

```cmd
devenv /command CommandName
```

## <a name="arguments"></a>Аргументы
 `CommandName` Обязательный. Полное имя команды [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] или ее псевдоним, заключенные в двойные кавычки. Дополнительные сведения о синтаксисе команд и псевдонимов см. в разделе [Команды Visual Studio](../../ide/reference/visual-studio-commands.md).

## <a name="remarks"></a>Примечания
 После завершения запуска интегрированная среда разработки выполняет именованную команду. При использовании этого параметра среда IDE не отображает начальную страницу [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] при запуске.

 Если надстройка предоставляет команду, этот параметр можно использовать для запуска надстройки из командной строки. Дополнительные сведения см. в разделе [Практическое руководство. Управление надстройками с помощью диспетчера надстроек](http://msdn.microsoft.com/Library/4f60444a-cb48-4cdb-8df4-941f6419aeeb).

## <a name="example"></a>Пример
 В данном примере запускается [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и автоматически выполняется макрос Open Favorite Files.

```cmd
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"
```

## <a name="see-also"></a>См. также

- [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)
- [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)