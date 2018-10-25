---
title: Создание папок родительского контейнера для решений | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 87fbda8cb55d0d2a6ef9f21a2a7878d4babd3fe6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830696"
---
# <a name="create-parent-container-folders-for-solutions"></a>Создание родительской папки контейнера для решений
В исходный элемент управления Plug-in API версии 1.2 пользователь может указать место назначения элемента управления источника один корневой для всех веб-проектов в решении. Это единственный корневой называется Super единой корневой (SUR).  
  
 В исходный элемент управления Plug-in API версии 1.1 если пользователь добавил многопроектное решение в систему управления версиями, пользователю было предложено указать один элемент управления источника, назначения для каждого веб-проекта.  
  
## <a name="new-capability-flags"></a>Новые флаги возможностей  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## <a name="new-functions"></a>Новые функции  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Интегрированной среды разработки, почти всегда создается папка SUR, при добавлении решения в систему управления версиями. В частности она делает это в следующих случаях:  
  
-   Проект является веб-проекта файл общего ресурса.  
  
-   Существуют разные диски для проекта и файл решения.  
  
-   Существуют другие общие папки для проекта и файл решения.  
  
-   Проекты были добавлены отдельно (в решения, контролируемого системой управления версиями).  
  

В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], предполагается, что имя папки SUR совпадать с именем решения без расширения. В следующей таблице перечислены поведение в обеих версиях.  
  
|Функция|Система управления версиями API подключаемого модуля версии 1.1|Система управления версиями API подключаемого модуля версии 1.2|  
|-------------| - | - |  
|Добавьте решение в SCC|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|  
|Добавление проекта к решению, контролируемого системой управления версиями|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject()<br /><br />  **Примечание:** Visual Studio предполагается, что решение сейчас является прямым потомком SUR.|  
  
## <a name="examples"></a>Примеры  
 В следующей таблице перечислены два примера. В обоих случаях [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] пользователю предлагается ввести расположение для решения в системе управления версиями до *user_choice* указан в качестве места назначения. При указании user_choice решения и двух проектов добавляются без подтверждения от пользователя для источников управления получателей.  
  
|Решение содержит|На расположения диска|Структура базы данных по умолчанию|  
|-----------------------|-----------------------|--------------------------------|  
|*sln1.sln*<br /><br /> Web1<br /><br /> "Web2"|*C:\Solutions\sln1*<br /><br /> *C:\Inetpub\wwwroot\Web1*<br /><br /> \\\server\wwwroot$\Web2|$/ < user_choice > / sln1<br /><br /> $/ < user_choice >/C/Web1<br /><br /> $/ < user_choice > / "web2"|  
|*sln1.sln*<br /><br /> Web1<br /><br /> Win1|*C:\Solutions\sln1*<br /><br /> *D:\Inetpub\wwwroot\Web1*<br /><br /> *C:\solutions\sln1\Win1*|$/ < user_choice > / sln1<br /><br /> $/ < user_choice >/D/web1<br /><br /> $/ < user_choice >/sln1/win1|  
  
 SUR папки и вложенные папки создаются независимо от того, является ли операции отмены или сбоя из-за ошибки. Они не удаляются автоматически в Отмена или сообщений об ошибке.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] по умолчанию к поведению версии 1.1, если подключаемый модуль системы управления версиями не возвращает `SCC_CAP_CREATESUBPROJECT` и `SCC_CAP_GETPARENTPROJECT` флаги возможностей. Кроме того, пользователи [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] можно вернуться к поведению версии 1.1, задав значение следующего раздела *DWORD: 00000001*:  
  
 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] DoNotCreateSolutionRootFolderInSourceControl** = *DWORD: 00000001*
  
## <a name="see-also"></a>См. также  
 [Новые возможности в исходный элемент управления Plug-in API версии 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)