---
title: "Создание папки родительского контейнера для решения | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "решения, создание родительские контейнеры"
  - "Источник подключаемые модули управления, создании родительских контейнеров"
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Создание папки родительского контейнера для решения
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

В версии 1.2 API системы управления версиями вставляемой пользователь может задать единое назначение системы управления версиями корня для всех веб\-проекта в решении.  Этот единственный корень вызывается super унифицированным корнем \(SUR\).  
  
 В версии 1.1 API системы управления версиями вставляемой, если пользователь добавил multiproject решение к системе управления версиями, то пользователю было предложено указать одну цель системы управления версиями для каждого веб\-проекта.  
  
## Новые возможности флаги  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## Новые функции  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Интегрированная среда разработки почти всегда создает папку SUR при добавлении решения в систему управления версиями.  В частности, он выполняется в следующих случаях:  
  
-   Проект является веб\-проектом общую папку.  
  
-   Разные диски для файла проекта и решения.  
  
-   Различные общей папки для файла проекта и решения.  
  
-   Проекты были добавлены отдельно \(в источник\-контролируемом решении\).  
  
 IN [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] предложено, что имя для папки SUR такой же, как и имя решения без расширения.  В следующей таблице приведены расширения функциональности в 2 выпусках.  
  
|Функция|версия 1.1 API управления tSource подключаемых модулей|Версия 1,2 API системы управления версиями подключаемых модулей|  
|-------------|------------------------------------------------------------|---------------------------------------------------------------------|  
|Добавьте в решение SCC|SccInitialize \(\)<br /><br /> SccGetProjPath \(\)<br /><br /> SccGetProjPath \(\)<br /><br /> SccOpenProject \(\)|SccInitialize \(\)<br /><br /> SccGetProjPath \(\)<br /><br /> SccCreateSubProject \(\)<br /><br /> SccCreateSubProject \(\)<br /><br /> SccOpenProject \(\)|  
|Добавление проекта к решению источник\-контролируемому|SccGetProjPath \(\)<br /><br /> OpenProject \(\)|SccGetParentProjectPath \(\)<br /><br /> SccOpenProject \(\) **Note:**  Visual Studio предполагается, что решение непосредственно дочерний элемент SUR.|  
  
## Примеры  
 В следующей таблице перечислены 2 примера.  В обоих случаях [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] пользователь не запрашивается места назначения для решения в системе управления версиями, пока  *user\_choice* указывает, как назначение. При user\_choice указано, решение и проект добавляются 2 без вывода пользователю сообщения о необходимости для целей системы управления версиями.  
  
|Решение содержит|В расположениях диска|Структура базы данных по умолчанию|  
|----------------------|---------------------------|----------------------------------------|  
|sln1.sln<br /><br /> Web1<br /><br /> Web2|C:\\Solutions\\sln1<br /><br /> C:\\Inetpub\\wwwroot\\Web1<br /><br /> \\ \\ сервер \\ \\ web2 wwwroot$|$\/*user\_choice*\/sln1<br /><br /> $\/*user\_choice*\/C\/Web1<br /><br /> $\/*user\_choice*\/Web2|  
|sln1.sln<br /><br /> Web1<br /><br /> Win1|C:\\Solutions\\sln1<br /><br /> D:\\Inetpub\\wwwroot\\Web1<br /><br /> C:\\solutions\\sln1\\Win1|$\/*user\_choice*\/sln1<br /><br /> $\/*user\_choice*\/D\/web1<br /><br /> $\/*user\_choice*\/sln1\/win1|  
  
 Папка и вложенные папки SUR созданы независимо от того, является ли операция отменена или завершилась ошибкой из\-за ошибке.  Они не удаляются автоматически в отменять или условия ошибки.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] по умолчанию имеет значение расширения функциональности версии 1.1, если подключаемый модуль системы управления версиями не возвращает  `SCC_CAP_CREATESUBPROJECT` и  `SCC_CAP_GETPARENTPROJECT` флаги возможности.  Кроме того, пользователи [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] позволяет выбрать, чтобы отменить изменения для расширения функциональности версии 1.1, устанавливая значение следующего ключа к двойному слова: 00000001:  
  
 \[HKEY\_CURRENT\_USER \\ software \\ microsoft \\ VisualStudio \\ 8,0 \\ SourceControl\] "DoNotCreateSolutionRootFolderInSourceControl" \=dword: 00000001  
  
## См. также  
 [Новые возможности в подключаемый модуль API версия системы управления версиями 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)