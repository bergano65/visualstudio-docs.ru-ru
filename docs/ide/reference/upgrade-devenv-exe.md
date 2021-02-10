---
title: -Upgrade (devenv.exe)
description: Узнайте, как использовать параметр командной строки Upgrade devenv для обновления файла решения, всех его файлов проекта или указанного файла проекта до текущих форматов Visual Studio для этих файлов.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e7dc759cefae4ae262362265daf67ee5b1cb50f2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960563"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)

Обновляет файл решения и все его файлы проектов либо указанный файл проекта до текущих форматов Visual Studio для этих файлов.

## <a name="syntax"></a>Синтаксис

```shell
devenv {SolutionFile|ProjectFile} /Upgrade [/Out OutputFilename]
```

## <a name="arguments"></a>Аргументы

- *SolutionFile*

  Требуется при обновлении всего решения и его проектов. Путь и имя для файла решения Можно ввести только имя файла решения или полный путь и имя файла решения. Если папка или файл еще не существуют, они будут созданы.

- *ProjectFile*

  Требуется при обновлении одного проекта. Путь и имя для файла проекта в решении. Можно ввести только имя файла проекта или полный путь и имя файла проекта. Если папка или файл еще не существуют, они будут созданы.

- `/Out` *OutputFilename*

  Необязательный элемент. Имя файла, в который вы хотите отправить выходные данные средства. Если файл уже существует, средство добавляет в его конец выходные данные.

## <a name="remarks"></a>Комментарии

Резервные копии автоматически создаются и копируются в каталог с именем Backup, который создается в текущем каталоге.

Решения или проекты в системе управления версиями необходимо получать для изменения, прежде чем их можно будет обновить.

Использование параметра `/Upgrade` не приводит к запуску Visual Studio. Результаты обновления можно просмотреть в отчете об обновлении для языка разработки конкретного решения или проекта. Сведения об ошибках или использовании не возвращаются. См. дополнительные сведения о [переносе, миграции и обновлении проектов Visual Studio](../../porting/port-migrate-and-upgrade-visual-studio-projects.md).

## <a name="example"></a>Пример

В этом примере выполняется обновление файла решения с именем MyProject.sln.

```shell
devenv "%USERPROFILE%\source\repos\MyProject\MyProject.sln" /upgrade
```

## <a name="see-also"></a>См. также раздел

- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)
