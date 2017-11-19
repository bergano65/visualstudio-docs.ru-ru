---
title: "Источник функции API подключаемого модуля управления | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1085312849ce33518654e044a795d6aa4b735e07
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="source-control-plug-in-api-functions"></a>Функции API подключаемого модуля управления источника
API подключаемых модулей исходный элемент управления предоставляет следующие функции, которые должны реализовывать системы управления версиями в соответствии с этот API. Подписи каждой функции и семантику, связанные с битовые флаги и другие параметры описаны в этой справке.  
  
## <a name="initialization-and-housekeeping-functions"></a>Инициализация и вспомогательные функции  
  
|Функция|Описание|  
|--------------|-----------------|  
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Закрывает проект.|  
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Запрашивает пользователя для настройки дополнительных параметров для данной команды.|  
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Возвращает версию системы управления версиями подключаемого модуля.|  
|[SccInitialize](../extensibility/sccinitialize-function.md)|Инициализирует подключаемый модуль системы управления версиями. Он вызывается один раз для каждого экземпляра подключаемого модуля.|  
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Открывает проект.|  
|[SccSetOption](../extensibility/sccsetoption-function.md)|Универсальная функция используется для задания разнообразные параметры. Каждый параметр начинается с `SCC_OPT_xxx` и имеет собственный набор определенных значений.|  
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Вызывается, когда когда подключаемый модуль системы управления версиями должен быть подключен.|  
  
## <a name="core-source-control-functions"></a>Основные функции управления источника  
  
|Функция|Описание|  
|--------------|-----------------|  
|[SccAdd](../extensibility/sccadd-function.md)|Добавляет массив имен полный путь для системы управления версиями, заданные файлы.|  
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Позволяет пользователю для поиска файлов, которые уже находятся в системе управления версиями, а затем сделайте эти файлы частью текущего проекта.|  
|[SccCheckin](../extensibility/scccheckin-function.md)|Возвращает массив файлов.|  
|[SccCheckout](../extensibility/scccheckout-function.md)|Извлекает массив файлов.|  
|[SccDiff](../extensibility/sccdiff-function.md)|Показаны различия между файлом локального пользователя, заданного полным путем к файлу и версии в системе управления версиями.|  
|[SccGet](../extensibility/sccget-function.md)|Извлекает копию набора файлов только для чтения.|  
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Проверяет состояние файлов, которые вызывающий объект задаваемые о (через `SccQueryInfo`).|  
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Вызывает подключаемый модуль на приглашение ввести путь проекта, имеющее смысл подключаемый модуль системы управления версиями.|  
|[SccHistory](../extensibility/scchistory-function.md)|Показывает историю для массива имен полное имя локального файла.|  
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Проверяет список файлов для их текущего состояния. Кроме того, использует `pfnPopulate` функции для уведомления вызывающего объекта, если файл не соответствует критериям для `nCommand`.|  
|[SccProperties](../extensibility/sccproperties-function.md)|Показывает свойства полное имя файла.|  
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Проверяет список полные имена файлов для их текущего состояния.|  
|[SccRemove](../extensibility/sccremove-function.md)|Удаляет массив полные имена файлов из системы управления версиями.|  
|[SccRename](../extensibility/sccrename-function.md)|Переименовывает данный файл в новое имя в системе управления версиями.|  
|[SccRunScc](../extensibility/sccrunscc-function.md)|Обращается к полный спектр функций системы управления версиями.|  
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Отменяет извлечение массив файлов.|  
  
## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Функции, которые поддерживают дополнительные возможности (версия 1.2 API-интерфейса подключаемого модуля управления источника)  
 Эта группа функций определяет дополнительные функциональные возможности, включенные в версии 1.2 API подключаемых модулей управления источника. Они предоставляют доступ к более сложных функций управления исходным кодом и возможности.  
  
|Функция|Описание|  
|--------------|-----------------|  
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Запускает пакетную операцию.|  
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Создает подпроект с заданным именем в существующий проект родительского.|  
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Отображает различия между каталог локального пользователя, указанный с полным путем к файлу и расположение базы данных системы управления версиями.|  
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Проверяет список полное каталогов для их текущего состояния.|  
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Завершает пакетную операцию.|  
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Возвращает родительский путь данный проект (проект должна существовать).|  
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Проверяет, разрешено ли несколько одновременных извлечений на файл.|  
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Проверяет, является ли подключаемый модуль создаст MSSCCPRJ. Файлы SCC.|  
  
## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Функции, поддерживающие расширенные возможности (версия 1.3 API-интерфейса подключаемого модуля управления источника)  
 Эта группа функций определяет дополнительные функциональные возможности, включенные в версии 1.3 API подключаемых модулей управления источника. Они предоставляют доступ к более сложных функций управления исходным кодом и возможности.  
  
|Функция|Описание|  
|--------------|-----------------|  
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Добавляет список файлов из системы управления версиями в текущий проект.|  
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Возвращает список файлов из системы управления версиями без пользовательского интерфейса.|  
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Возвращает список файлов в системе управления версиями, которые отличаются от локальных файлов.|  
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Получает флаги, определяющие расширенные возможности, поддерживаемые подключаемый модуль системы управления версиями.|  
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Извлекает параметры конкретного пользователя.|  
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Проверяет список каталогов и файлов в проект или проекты, которые находятся в системе управления версиями. Каждый каталог и имя файла найден передается функции обратного вызова.|  
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Проверяет имя изменения, внесенные в список файлов. Имя каждого файла передается в функцию обратного вызова с его изменить статус.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: scc.h  
  
 (В пакет SDK для среды общие папки, по умолчанию включает *[диск]*\Program Files\VSIP 8.0\EnvSDK\common\inc; также показан в папку с образцом MSSCCI VSIP *[диск]*\Program Files\VSIP 8.0\MSSCCI).  
  
## <a name="see-also"></a>См. также  
 [Подключаемые модули управления версиями](../extensibility/source-control-plug-ins.md)   
 [Создание подключаемого модуля системы управления версиями](../extensibility/internals/creating-a-source-control-plug-in.md)