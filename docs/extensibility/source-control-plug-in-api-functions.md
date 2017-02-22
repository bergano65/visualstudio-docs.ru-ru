---
title: "Функции API подключаемого модуля источника элемента управления | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "управление подключаемыми модулями источников, функции"
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# Функции API подключаемого модуля источника элемента управления
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

API подключаемых модулей исходный элемент управления предоставляет следующие функции, которые должны быть реализованы в соответствии с этой API модуль управления версиями. Подписи каждой функции и семантики, связанной с битовые флаги и другие параметры подробно описаны в данном справочном руководстве.  
  
## Инициализация и вспомогательные функции  
  
|Функция|Описание|  
|-------------|--------------|  
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Закрытие проекта.|  
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Пользователю предлагается для установки дополнительных параметров для данной команды.|  
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Возвращает версию системы управления версиями подключаемого модуля.|  
|[SccInitialize](../extensibility/sccinitialize-function.md)|Инициализирует модуль управления версиями. Он вызывается один раз для каждого экземпляра подключаемого модуля.|  
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Открывает проект.|  
|[SccSetOption](../extensibility/sccsetoption-function.md)|Универсальная функция используется для задания разнообразные параметры. Каждый параметр начинается с `SCC_OPT_xxx` и имеет свой собственный набор определенных значений.|  
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Вызывается, когда когда подключаемый модуль системы управления версиями должен быть подключен.|  
  
## Основные функции управления источника  
  
|Функция|Описание|  
|-------------|--------------|  
|[SccAdd](../extensibility/sccadd-function.md)|Добавляет массив файлов, указанных по именам полный путь к системе управления версиями.|  
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Позволяет пользователю выполнять поиск файлов, находящихся в системе управления версиями, а затем сделать частью текущего проекта, эти файлы.|  
|[SccCheckin](../extensibility/scccheckin-function.md)|Возвращает массив файлов.|  
|[SccCheckout](../extensibility/scccheckout-function.md)|Извлекает массив файлов.|  
|[SccDiff](../extensibility/sccdiff-function.md)|Отображает различия между локального пользователя файл, указанный параметром полное имя и версия системы управления версиями.|  
|[SccGet](../extensibility/sccget-function.md)|Извлекает копию набора файлов только для чтения.|  
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Проверяет состояние файлов, задаваемые в вызывающей стороны о \(через `SccQueryInfo`\).|  
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Вызывает модуль приглашение ввести путь проекта, который имеет смысл для подключаемого модуля управления версиями.|  
|[SccHistory](../extensibility/scchistory-function.md)|Показывает историю для массива имен полное имя локального файла.|  
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Проверяет список файлов для их текущее состояние. Кроме того, использует `pfnPopulate` функцию для уведомления вызывающей стороны, если файл не соответствует критериям для `nCommand`.|  
|[SccProperties](../extensibility/sccproperties-function.md)|Отображает свойства полного имени файла.|  
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Проверяет список полные имена файлов для их текущее состояние.|  
|[SccRemove](../extensibility/sccremove-function.md)|Удаляет массив полные имена файлов из системы управления версиями.|  
|[SccRename](../extensibility/sccrename-function.md)|Переименовывает указанный файл в новое имя в системе управления версиями.|  
|[SccRunScc](../extensibility/sccrunscc-function.md)|Обращается к полный спектр возможностей системы управления версиями.|  
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Отменяет извлечение массив файлов.|  
  
## Функции, которые поддерживают дополнительные возможности \(версия 1.2 API подключаемого модуля управления источника\)  
 Эта группа функций определяет дополнительные функциональные возможности, включенные в версии 1.2 API подключаемого модуля управления источника. Они предоставляют доступ к более сложных функций управления исходным кодом и возможности.  
  
|Функция|Описание|  
|-------------|--------------|  
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Запускает пакетную операцию.|  
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Создает подпроект с заданным именем в существующий проект родительского.|  
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Отображает различия между указанным полное имя и расположение базы данных системы управления версиями каталога локального пользователя.|  
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Проверяет список полное каталогов для их текущее состояние.|  
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Завершает пакетную операцию.|  
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Возвращает родительский путь \(проект должен существовать\) данного проекта.|  
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Проверяет, разрешено ли несколько одновременных извлечений в файле.|  
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Проверяет, является ли подключаемый модуль будет создавать MSSCCPRJ. Файлы SCC.|  
  
## Функции, поддерживающие расширенные возможности \(версия 1.3 API подключаемого модуля управления источника\)  
 Эта группа функций определяет дополнительные функциональные возможности, включенные в версии 1.3 API подключаемого модуля управления источника. Они предоставляют доступ к более сложных функций управления исходным кодом и возможности.  
  
|Функция|Описание|  
|-------------|--------------|  
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Добавляет список файлов из системы управления версиями в текущий проект.|  
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Получает список файлов из системы управления версиями без интерфейса пользователя.|  
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Получает список файлов в системе управления версиями, которые отличаются от локальных файлов.|  
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Получает флаги, определяющие расширенных возможностей, поддерживаемых подключаемым модулем системы управления версиями.|  
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Получает параметры для конкретного пользователя.|  
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Проверяет список каталогов и файлов в проект или проекты, которые находятся в системе управления версиями. Каждый каталог и имя файла найти передается функции обратного вызова.|  
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Проверяет имя изменений, внесенных в список файлов. Имя каждого файла передается функции обратного вызова с его изменить статус.|  
  
## Требования  
 Заголовок: scc.h  
  
 \(Указанный в пакет SDK для среды общие папки, по умолчанию включает *\[диск\]*\\Program Files\\VSIP 8.0\\EnvSDK\\common\\inc; также указан в папке VSIP с образцом MSSCCI *\[диск\]*\\Program Files\\VSIP 8.0\\MSSCCI\).  
  
## См. также  
 [Подключаемые модули управления версиями](../extensibility/source-control-plug-ins.md)   
 [Создание подключаемого модуля системы управления версиями](../extensibility/internals/creating-a-source-control-plug-in.md)