---
title: Создание родительских контейнерных контейнеров для решений Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e5481e20a12fc05ccba97eef55173e5ce9b30d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709101"
---
# <a name="create-parent-container-folders-for-solutions"></a>Создание папок родительского контейнера для решений
В версии API 1.2 управления исходного элемента может указать один пункт управления корнем для всех веб-проектов в решении. Этот единственный корень называется Супер единым корнем (SUR).

 В подключаемый API-версии 1.1, если пользователь добавил многопроектное решение для управления исходным кодом, пользователю было предложено указать один пункт управления исходом для каждого веб-проекта.

## <a name="new-capability-flags"></a>Новые флаги возможностей
 `SCC_CAP_CREATESUBPROJECT`

 `SCC_CAP_GETPARENTPROJECT`

## <a name="new-functions"></a>Новые функции
- [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)

- [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE почти всегда создает папку SUR при добавлении решения в элемент управления исходным управлением. В частности, он делает это в следующих случаях:

- Проект представляет собой веб-проект обмена файлами.

- Существуют различные диски для проекта и файла решения.

- Для проекта и файла решения существуют различные доли.

- Проекты были добавлены отдельно (в решении, контролируемом исходным ресурсом).

В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], предлагается, чтобы имя для папки SUR быть таким же, как имя решения без расширения. В следующей таблице кратко излагается поведение в двух версиях.

|Компонент|Подключаемый API-версия 1.1|Подключаемый API-версия 1.2|
|-------------| - | - |
|Добавление решения в SCC|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|
|Добавление проекта в решение, контролируемое исходным документом|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject()<br /><br />  **Примечание:**  Visual Studio предполагает, что решение является прямым ребенком SUR.|

## <a name="examples"></a>Примеры
 В следующей таблице приведены два примера. В обоих [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] случаях пользователю предлагается определить местоположение назначения для решения под контролем источника до тех пор, пока *user_choice* не указан как пункт назначения. Когда user_choice указан, решение и два проекта добавляются без запроса пользователя для назначения управления исходным кодом.

|Решение содержит|На дисках|Структура по умолчанию базы данных|
|-----------------------|-----------------------|--------------------------------|
|*sln1.sln*<br /><br /> Web1<br /><br /> Web2|*C:«Решения»*<br /><br /> *C:-Инетпуб-wwwroot-Web1*<br /><br /> \\«сервер»wwwroot$»Web2|$/<user_choice>/sln1<br /><br /> $$<user_choice>/C/Web1<br /><br /> $<user_choice>/Web2|
|*sln1.sln*<br /><br /> Web1<br /><br /> Win1|*C:«Решения»*<br /><br /> *D: «Инетпуб» wwwroot-Web1*<br /><br /> *C:«Решения»sln1»Win1*|$/<user_choice>/sln1<br /><br /> $/<user_choice>/D/web1<br /><br /> $/<user_choice>/sln1/win1|

 Папка SUR и субфолители создаются независимо от того, отменена операция или сбой из-за ошибки. Они не удаляются автоматически в условиях отмены или ошибки.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]по умолчанию к поведению версии 1.1, `SCC_CAP_CREATESUBPROJECT` если `SCC_CAP_GETPARENTPROJECT` плагин управления исходным элементом не возвращается и флаги возможностей. Кроме того, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] пользователи могут вернуться к поведению версии 1.1, установив значение следующего ключа *dword:00000001:*

 **«HKEY_CURRENT_USER»Программное обеспечение»Microsoft,VisualStudio»8.0 (SourceControl) DoNotCreateSolutionRootFolderInSourceControl** = *dword:000000001*

## <a name="see-also"></a>См. также
- [Что нового в версии API-элемента управления исходным элементом](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
