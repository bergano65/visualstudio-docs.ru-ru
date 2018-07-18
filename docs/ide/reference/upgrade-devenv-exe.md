---
title: -Upgrade (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 25fe5a4e75ddf349210a936f47d99c94ec70c240
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704711"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)
Обновляет файл решения и все его файлы проектов либо указанный файл проекта до текущих форматов [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] для этих файлов.

## <a name="syntax"></a>Синтаксис

```cmd
devenv SolutionFile | ProjectFile /upgrade
```

## <a name="arguments"></a>Аргументы
 `SolutionFile`

 Требуется при обновлении всего решения и его проектов. Путь и имя для файла решения Можно ввести только имя файла решения или полный путь и имя файла решения. Если папка или файл еще не существуют, они будут созданы.

 `ProjectFile`

 Требуется при обновлении одного проекта. Путь и имя для файла проекта в решении. Можно ввести только имя файла проекта или полный путь и имя файла проекта. Если папка или файл еще не существуют, они будут созданы.

## <a name="remarks"></a>Примечания
 Резервные копии автоматически создаются и копируются в каталог с именем Backup, который создается в текущем каталоге.

 Решения или проекты в системе управления версиями необходимо получать для изменения, прежде чем их можно будет обновить.

 Использование параметра `/upgrade` не приводит к запуску [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Результаты обновления можно просмотреть в отчете об обновлении для языка разработки конкретного решения или проекта. Сведения об ошибках или использовании не возвращаются. Дополнительные сведения об обновлении проектов в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] см. в разделе [Перенос, миграция и обновление проектов Visual Studio](../../porting/port-migrate-and-upgrade-visual-studio-projects.md).

## <a name="example"></a>Пример
 В этом примере выполняется обновление файла решения с именем MyProject.sln в папке по умолчанию для решений [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

```cmd
devenv "MyProject.sln" /upgrade
```

## <a name="see-also"></a>См. также

- [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)