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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 465c90736f5470f48d47336bc916ca3cb2c09b6a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54779350"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Обновляет файл решения и все его файлы проектов либо указанный файл проекта до текущих форматов [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] для этих файлов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
  
 Использование параметра `/upgrade` не приводит к запуску [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Результаты обновления можно просмотреть в отчете об обновлении для языка разработки конкретного решения или проекта. Сведения об ошибках или использовании не возвращаются. Дополнительные сведения об обновлении проектов в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], см. в разделе [как: Устранение неполадок с неудачными обновлениями Visual Studio проект](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md).  
  
## <a name="example"></a>Пример  
 В этом примере выполняется обновление файла решения с именем MyProject.sln в папке по умолчанию для решений [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
```  
devenv "MyProject.sln" /upgrade  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Практическое руководство. Устранение неполадок с неудачными обновлениями Visual Studio проекта](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)   
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)
