---
title: Источник функции API подключаемого модуля управления | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eadf9c76fcebe79eb8e8f599aecdf934485a34ca
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562623"
---
# <a name="source-control-plug-in-api-functions"></a>Функции API подключаемого модуля системы управления версиями
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [функции API подключаемого модуля управления источника](https://docs.microsoft.com/visualstudio/extensibility/source-control-plug-in-api-functions).  
  
API подключаемых модулей исходный элемент управления предоставляет следующие функции, которые должны быть реализованы системы управления версиями, подключаемый модуль, в соответствии с этого API. Подписи каждой функции и семантики, связанные с битовых флагов, и другие параметры, описаны в этой справке.  
  
## <a name="initialization-and-housekeeping-functions"></a>Инициализация и функций по обслуживанию  
  
|Функция|Описание|  
|--------------|-----------------|  
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Закрывает проект.|  
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Запрашивает у пользователя Дополнительные параметры для данной команды.|  
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Возвращает версию системы управления версиями подключаемого модуля.|  
|[SccInitialize](../extensibility/sccinitialize-function.md)|Инициализирует модуль управления версиями. Он вызывается один раз для каждого экземпляра подключаемого модуля.|  
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Открывает проект.|  
|[SccSetOption](../extensibility/sccsetoption-function.md)|Универсальная функция, используемый для задания разнообразные параметры. Каждый параметр начинается с `SCC_OPT_xxx` и имеет свой собственный определенный набор значений.|  
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Вызывается, когда когда подключаемый модуль системы управления версиями необходимо отсоединения.|  
  
## <a name="core-source-control-functions"></a>Основные функции элемента управления источника  
  
|Функция|Описание|  
|--------------|-----------------|  
|[SccAdd](../extensibility/sccadd-function.md)|Добавляет массив файлов, указанных по именам полный путь к системе управления версиями.|  
|[SccAddFilesFromSCC](../extensibility/sccaddfromscc-function.md)|Позволяет пользователю для поиска файлов, которые уже находятся в системе управления версиями, а затем сделайте этих файлов, входящих в текущий проект.|  
|[SccCheckin](../extensibility/scccheckin-function.md)|Возвращает массив файлов.|  
|[SccCheckout](../extensibility/scccheckout-function.md)|Извлекает массив файлов.|  
|[SccDiff](../extensibility/sccdiff-function.md)|Показаны различия между файл локального пользователя, указанный параметром полный путь к файлу и версии в системе управления версиями.|  
|[SccGet](../extensibility/sccget-function.md)|Получает доступную только для чтения копию набора файлов.|  
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Проверяет состояние файлов, которые вызывающий объект попросил об (через `SccQueryInfo`).|  
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Вызывает подключаемые модули, приглашение ввести путь к проекту, подключаемый модуль системы управления версиями.|  
|[SccHistory](../extensibility/scchistory-function.md)|Отображается журнал для массива имен полное локальный файл.|  
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Проверяет список файлов для их текущее состояние. Кроме того, использует `pfnPopulate` функция уведомляет вызывающего объекта, если файл не соответствует критериям для `nCommand`.|  
|[SccProperties](../extensibility/sccproperties-function.md)|Показывает свойства полное имя файла.|  
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Проверяет список полные имена файлов для их текущее состояние.|  
|[SccRemove](../extensibility/sccremove-function.md)|Удаляет массив полные имена файлов из системы управления версиями.|  
|[SccRename](../extensibility/sccrename-function.md)|Переименовывает данный файл в новое имя в системе управления версиями.|  
|[SccRunScc](../extensibility/sccrunscc-function.md)|Осуществляет доступ к полному набору функций системы управления версиями.|  
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Отменяет извлечение массив файлов.|  
  
## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Функции, которые поддерживают дополнительные возможности (версия 1.2 API подключаемого модуля управления источника)  
 Эта группа функций определяет дополнительные функциональные возможности, включенные в версии 1.2 API подключаемых модулей управления источника. Они предоставляют доступ к более сложных функций системы управления версиями и возможностям.  
  
|Функция|Описание|  
|--------------|-----------------|  
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Начинает пакетную операцию.|  
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Создает подпроект с заданным именем в существующий родительский проект.|  
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Показаны различия между локального пользователя каталоге, заданном параметром полное имя и расположение базы данных системы управления версиями.|  
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Проверяет список полных каталогов для их текущее состояние.|  
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Завершает пакетную операцию.|  
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Возвращает родительский путь данного проекта (проект должна существовать).|  
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Проверяет, разрешено ли несколько одновременных извлечений с файлом.|  
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Проверяет, является ли подключаемый модуль создаст MSSCCPRJ. Файлы SCC.|  
  
## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Функции, поддерживающие расширенные возможности (версии 1.3 подключаемого модуля API управления источника)  
 Эта группа функций определяет дополнительные функциональные возможности, включенные в версии 1.3 API подключаемых модулей управления источника. Они предоставляют доступ к более сложных функций системы управления версиями и возможностям.  
  
|Функция|Описание|  
|--------------|-----------------|  
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Добавляет список файлов из системы управления версиями в текущий проект.|  
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Извлекает список файлов из системы управления версиями без пользовательского интерфейса.|  
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Извлекает список файлов в системе управления версиями, которые отличаются от локальных файлов.|  
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Получает флаги, определяющие расширенные возможности, поддерживаемые подключаемый модуль системы управления версиями.|  
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Возвращает пользовательские параметры.|  
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Проверяет список каталогов и файлов в проект или проекты, которые находятся в системе управления версиями. Каждый каталог и имя файла найден передается функции обратного вызова.|  
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Проверяет имя изменения, внесенные в список файлов. Имя каждого файла передается функции обратного вызова с его изменить статус.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: scc.h  
  
 (В пакет SDK для среды общие папки, по умолчанию включает *[диск]* \Program Files\VSIP 8.0\EnvSDK\common\inc; также указан в папке с примером MSSCCI VSIP *[диск]* \Program Files\VSIP 8.0\MSSCCI).  
  
## <a name="see-also"></a>См. также  
 [Подключаемых модулей системы управления версиями](../extensibility/source-control-plug-ins.md)   
 [Создание подключаемого модуля системы управления версиями](../extensibility/internals/creating-a-source-control-plug-in.md)

