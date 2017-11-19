---
title: "Создание папок родительского контейнера для решений | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6ea901fe4e380fd867db1c63e44bc1cb6e144feb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="creating-parent-container-folders-for-solutions"></a>Создание папок родительского контейнера для решений
В API подключаемых модулей исходный элемент управления версии 1.2 пользователь может указать один корневой источник управления назначения для всех веб-проектов в решении. Это единственный корневой называется Super единой корневой (SUR).  
  
 В API подключаемых модулей исходный элемент управления версии 1.1 если пользователь добавлен многопроектное решение в систему управления версиями пользователя было предложено указать один целевой элемент управления источника для каждого веб-проекта.  
  
## <a name="new-capability-flags"></a>Флаги новых возможностей  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## <a name="new-functions"></a>Новые функции  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Интегрированной среды разработки, почти всегда создает папку SUR, при добавлении решения в систему управления версиями. В частности это происходит в следующих случаях:  
  
-   Проект является общей папкой, веб-проекта.  
  
-   Существуют разные диски для проекта и файл решения.  
  
-   Существуют другие общие папки для проекта и файл решения.  
  
-   Проекты были добавлены отдельно (в решения, контролируемого системой управления версиями).  
  
 В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] предполагается, что имя папки SUR совпадать имя решения без расширения. В следующей таблице перечислены двух версий.  
  
|Функция|tSource управления Plug-in API версии 1.1|Система управления версиями API подключаемого модуля версии 1.2|  
|-------------|----------------------------------------------|---------------------------------------------|  
|Добавить решение в систему управления версиями|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|  
|Добавьте проект в решение с управлением версиями|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject() **Примечание:** Visual Studio предполагает, что это решение является прямым потомком SUR.|  
  
## <a name="examples"></a>Примеры  
 В следующей таблице перечислены два примера. В обоих случаях [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] пользователю предлагается ввести в место назначения для решения в системе управления версиями до *user_choice* указан в качестве места назначения. При указании user_choice, решения и двух проектов добавляются без подтверждения от пользователя для назначения элемента управления источника.  
  
|Решение содержит|На дисках|Структура базы данных по умолчанию|  
|-----------------------|-----------------------|--------------------------------|  
|sln1.sln<br /><br /> Web1<br /><br /> Web2|C:\Solutions\sln1<br /><br /> C:\Inetpub\wwwroot\Web1<br /><br /> \\\server\wwwroot$\web2|$/*user_choice*/sln1<br /><br /> $/*user_choice*  /C/Web1<br /><br /> $/*user_choice*/Web2|  
|sln1.sln<br /><br /> Web1<br /><br /> Win1|C:\Solutions\sln1<br /><br /> D:\Inetpub\wwwroot\Web1<br /><br /> C:\solutions\sln1\Win1|$/*user_choice*/sln1<br /><br /> $/*user_choice*  /D/web1<br /><br /> $/*user_choice*  /sln1/win1|  
  
 SUR папка и вложенные папки создаются независимо от того, является ли операция была отменена, или происходит сбой из-за ошибки. Они не удаляются автоматически в условиях cancel или ошибки.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]по умолчанию поведение версии 1.1, если подключаемый модуль системы управления версиями не возвращает `SCC_CAP_CREATESUBPROJECT` и `SCC_CAP_GETPARENTPROJECT` флаги возможностей. Кроме того, пользователи [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] можно вернуться к поведению версии 1.1, задав значение DWORD: 00000001 значение следующего раздела:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] «DoNotCreateSolutionRootFolderInSourceControl» = DWORD: 00000001  
  
## <a name="see-also"></a>См. также  
 [Новые возможности в API версии 1.2 подключаемого модуля системы управления версиями](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)