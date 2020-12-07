---
title: -UseEnv (devenv.exe)
description: Узнайте, как использовать параметр командной строки UseEnv devenv для запуска Visual Studio и загрузки определенных переменных среды для компиляции.
ms.custom: SEO-VS-2020
ms.date: 01/10/2019
ms.topic: reference
f1_keywords:
- VC.Project.UseEnvVars.ExcludePath
- VC.Project.UseEnvVars.LibraryPath
- VC.Project.UseEnvVars.SourcePath
- VC.Project.UseEnvVars.Include
- VC.Project.UseEnvVars.Path
- VC.Project.UseEnvVars.ReferencePath
helpviewer_keywords:
- UseEnv switch
- /UseEnv Devenv switch
- Devenv, /UseEnv
ms.assetid: 2dd14603-a61b-42d2-ba31-427a0ee8a799
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 51b47156b73d81f427c08e62006dc6e457e5780b
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040944"
---
# <a name="useenv-devenvexe"></a>/UseEnv (devenv.exe)

Запускает Visual Studio и загружает переменные среды для компиляции.

> [!NOTE]
> Параметр устанавливается с рабочей нагрузкой **Разработка классических приложений на C++** .

## <a name="syntax"></a>Синтаксис

```shell
devenv /UseEnv {SolutionName|ProjectName}
```

## <a name="arguments"></a>Аргументы

- *SolutionName*

  Полный путь и имя для файла решения.

- *Имя проекта*

  Полный путь и имя для файла проекта.

## <a name="remarks"></a>Комментарии

Этот параметр изменяет интегрированную среду разработки Visual Studio в свойствах проекта для **каталогов VC++**. Если указать параметр `/UseEnv`, в узле **Каталоги VC++** отображаются значения переменных среды PATH, INCLUDE, LIBPATH и LIB. (Здесь также показаны значения для узлов **Каталоги исходного кода** и **Исключаемые каталоги**.) В противном случае узел заменяет переменные среды пятью значениями каталога: **каталоги исполняемых файлов**, **каталоги включаемых файлов**, **каталоги ссылок**, **каталоги библиотек** и **каталоги библиотек WinRT**.

> [!TIP]
> Откройте свойства проекта, щелкнув правой кнопкой мыши проект C++ и выбрав **Свойства**. В диалоговом окне **Страницы свойств** выберите **Свойства конфигурации**, а затем **Каталоги VC++**.

Если имя проекта указано с помощью этого параметра, переменные среды отображаются для всех проектов в родительском проекте.

## <a name="example"></a>Пример

Приведенный ниже пример запускает Visual Studio и загружает переменные среды на страницы свойств решения `MySolution`.

```shell
devenv.exe /useenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>См. также раздел

- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)
- [Страница свойств каталогов VC++ (Windows)](/cpp/build/reference/vcpp-directories-property-page)
