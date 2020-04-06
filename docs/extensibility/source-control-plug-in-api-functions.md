---
title: Функции API управления исходным элементом (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ce685729dda8750d772e244398b736cff4951b72
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699921"
---
# <a name="source-control-plug-in-api-functions"></a>Функции API подключаемого модуля системы управления версиями
API управления исходным элементом предоставляет следующие функции, которые должны быть реализованы плагином управления исходным элементом в соответствии с этим API. В этой ссылке подробно описаны подписи каждой функции и семантика, связанная с битовыми флагами и другими параметрами.

## <a name="initialization-and-housekeeping-functions"></a>Инициализация и функции домашнего хозяйства

|Функция|Описание|
|--------------|-----------------|
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Закрывает проект.|
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Подталкивает пользователя к расширенным опциям для данной команды.|
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Возвращает версию плагина управления исходным элементом.|
|[SccInitialize](../extensibility/sccinitialize-function.md)|Инициализирует плагин управления исходным элементом. Он называется один раз для каждого экземпляра плагина.|
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Открывает проект.|
|[SccSetOption](../extensibility/sccsetoption-function.md)|Общая функция, используемая для набора широкого спектра опций. Каждый вариант `SCC_OPT_xxx` начинается с определенного набора значений и имеет свой собственный определенный набор.|
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Вызывается один раз, когда плагин управления исходным элементом должен быть отключен.|

## <a name="core-source-control-functions"></a>Основные функции управления источником

|Функция|Описание|
|--------------|-----------------|
|[SccAdd](../extensibility/sccadd-function.md)|Добавляет массив файлов, указанных полностью квалифицированными именами путей, в систему управления исходным источником.|
|[SccAddFilesFromSCC](../extensibility/sccaddfromscc-function.md)|Позволяет пользователю просматривать файлы, которые уже находятся в системе управления исходным источником, а затем сделать эти файлы частью текущего проекта.|
|[SccCheckin](../extensibility/scccheckin-function.md)|Проверка массива файлов.|
|[SccCheckout](../extensibility/scccheckout-function.md)|Проверяет массив файлов.|
|[SccDiff](../extensibility/sccdiff-function.md)|Отображаетразличия различия между файлом локального пользователя, указанным полностью квалифицированным именем пути, и версией, наймеуправления исходным элементом.|
|[SccGet](../extensibility/sccget-function.md)|Извлекает только для чтения копию набора файлов.|
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Проверяет состояние файлов, о которыми задал `SccQueryInfo`абонент (через).|
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Вызывает плагин управления исходным элементом, чтобы побудить пользователя к траектории проекта, которая имеет смысл для плагина.|
|[SccHistory](../extensibility/scchistory-function.md)|Отображает историю для массива полностью квалифицированных локальных имен файлов.|
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Изучит список файлов для их текущего состояния. Кроме того, `pfnPopulate` использует функцию для уведомления вызываемого, когда `nCommand`файл не соответствует критериям для .|
|[SccProperties](../extensibility/sccproperties-function.md)|Отображает свойства полностью квалифицированного файла.|
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Изучит список полностью квалифицированных файлов для их текущего состояния.|
|[SccRemove](../extensibility/sccremove-function.md)|Удаляет массив полностью квалифицированных файлов из системы управления исходным источником.|
|[SccRename](../extensibility/sccrename-function.md)|Переименуйте данный файл на новое имя в системе управления исходным источником.|
|[SccRunScc](../extensibility/sccrunscc-function.md)|Доступ к полному спектру функций системы управления исходным кодом.|
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Отменяет проверку массива файлов.|

## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Функции, поддерживающие дополнительные возможности (версия 1.2 API подключаемого к источнику управления)
 Эта группа функций определяет дополнительную функциональность, включенную в версию 1.2 API подключаемого элемента управления исходным управлением. Они обеспечивают доступ к более продвинутым функциям управления исходом и возможностям.

|Функция|Описание|
|--------------|-----------------|
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Запускает пакетную операцию.|
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Создает подпроект с заданное имя в рамках существующего родительского проекта.|
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Отображается различия между каталогом локального пользователя, указанным полностью квалифицированным именем пути, и местоположением базы данных управления исходным управлением.|
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Изучит список полностью квалифицированных каталогов для их текущего статуса.|
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Завершает пакетную операцию.|
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Возвращает родительский путь данного проекта (проект должен существовать).|
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Проверяет, разрешены ли несколько выездов в файле.|
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Проверяет, будет ли плагин создавать MSSCCPRJ. Файлы SCC.|

## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Функции, поддерживающие расширенные возможности (версия 1.3 API подключаемого к источнику управления)
 Эта группа функций определяет дополнительную функциональность, включенную в версию 1.3 API подключаемого элемента управления исходным управлением. Они обеспечивают доступ к более продвинутым функциям управления исходом и возможностям.

|Функция|Описание|
|--------------|-----------------|
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Добавляет список файлов от управления исходным ресурсом к текущему проекту.|
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Извлекает список файлов из исходного элемента управления без пользовательского интерфейса.|
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Извлекает список файлов в исходном управлении, которые отличаются от локальных файлов.|
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Извлекает флаги, указывающие расширенные возможности, поддерживаемые плагином управления исходным управлением.|
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Извлекает пользовательские параметры.|
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Изучит список каталогов и файлов в проекте или проектах, накоторыехаемых под контролем источников. Каждый найденный каталог и найденное имя файла передаются функции обратного вызова.|
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Рассматривает изменения имен, внесенные в список файлов. Каждое имя файла передается функции обратного вызова с ее изменением статуса.|

## <a name="requirements"></a>Требования
 Заголовок: scc.h

 (Поставляется в среде SDK общего включает в себя папку, по умолчанию *«драйв»*«Программные файлы» VSIP 8.0 »EnvSDK»Common-inc; также поставляется в папке VSIP с образцом MSSCCI, *«драйв»*«Программные файлы»VSIP 8.0»MSSCCI).

## <a name="see-also"></a>См. также
- [Подключаемые модули системы управления версиями](../extensibility/source-control-plug-ins.md)
- [Создание подключаемого модуля системы управления версиями](../extensibility/internals/creating-a-source-control-plug-in.md)
