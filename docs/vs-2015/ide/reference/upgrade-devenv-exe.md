---
title: -Upgrade (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 24bb6160f9895f129c4d7d36c2b0aa8a56ca282a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657902"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Обновляет файл решения и все его файлы проектов либо указанный файл проекта до текущих форматов [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] для этих файлов.

## <a name="syntax"></a>Синтаксис

```
devenv SolutionFile | ProjectFile /upgrade
```

## <a name="arguments"></a>Аргументы
 `SolutionFile` Требуется при обновлении всего решения и его проектов. Путь и имя для файла решения Можно ввести только имя файла решения или полный путь и имя файла решения. Если папка или файл еще не существуют, они будут созданы.

 `ProjectFile` Требуется при обновлении одного проекта. Путь и имя для файла проекта в решении. Можно ввести только имя файла проекта или полный путь и имя файла проекта. Если папка или файл еще не существуют, они будут созданы.

## <a name="remarks"></a>Remarks
 Резервные копии автоматически создаются и копируются в каталог с именем Backup, который создается в текущем каталоге.

 Решения или проекты в системе управления версиями необходимо получать для изменения, прежде чем их можно будет обновить.

 Использование параметра `/upgrade` не приводит к запуску [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Результаты обновления можно просмотреть в отчете об обновлении для языка разработки конкретного решения или проекта. Сведения об ошибках или использовании не возвращаются. Дополнительные сведения об обновлении проектов в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] см. в статье [Практическое руководство. Устранение неполадок, связанных с неудачными обновлениями проектов Visual Studio](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md).

## <a name="example"></a>Пример
 В этом примере выполняется обновление файла решения с именем MyProject.sln в папке по умолчанию для решений [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

```
devenv "MyProject.sln" /upgrade
```

## <a name="see-also"></a>См. также:
 [Как устранить неудачные попытки обновления проекта Visual Studio](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md) [devenv параметры командной строки](../../ide/reference/devenv-command-line-switches.md)
