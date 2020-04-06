---
title: Функции обратного вызова, реализованные IDE Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 666486f5b800707a4467a129abeed7a13306f10a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739891"
---
# <a name="callback-functions-implemented-by-the-ide"></a>Функции обратного вызова, реализованные IDE
Чтобы сделать интеграцию с интегрированной средой разработки (IDE) максимально бесшовной и обеспечить единый интерфейс управления исходным управлением, плагин управления исходным управлением может использовать функции обратного вызова, которые реализуются IDE. Плагин может вызывать эти функции в соответствующее время во время операции управления исходным источником, чтобы передать информацию в IDE; IDE может отображать эту информацию в качестве встроенных элементов в своем родном uI. Пользователь имеет менее фрагментированный опыт в этом сценарии, чем если бы плагин использовал свой собственный пользовательский интерфейс.

 Требуемый файл *заголовка scc.h*. Местоположение по умолчанию *является «Файлы программы»VSIP 8.0»EnvSDK.common.inc\\*. Кроме того, в папке VSIP, которая имеет образец плагина управления исходным элементом на *«Программные файлы» VSIP 8.0»MSSCCI.\\*

## <a name="in-this-section"></a>В этом разделе
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) Описывает функцию обратного вызова, которая используется [SccOpenProject](../extensibility/sccopenproject-function.md) для отображения сообщений от плагина управления исходным кодом через IDE.

- [ПОПЛИСФУНК](../extensibility/poplistfunc.md) Описывает функцию обратного вызова, которая используется [SccPopulateList,](../extensibility/sccpopulatelist-function.md) когда IDE не имеет полного доступа к информации, которая доступна только плагину управления исходным кодом, например, полный список файлов под управлением версии.

- [КЕРИРАЗЕВЕФУНК](../extensibility/querychangesfunc.md) Описывает функцию обратного вызова, которая используется в операции [Scc'ruryChanges.](../extensibility/sccquerychanges-function.md)

- [ПОПДИРЛИСТФУНК](../extensibility/popdirlistfunc.md) Описывает функцию обратного вызова, используемую в операции [SccPopulateDirList.](../extensibility/sccpopulatedirlist-function.md)

- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) Описывает функцию обратного вызова в [SccSetOption,](../extensibility/sccsetoption-function.md) которая позволяет плагину управления исходным источником передавать изменения имен обратно в IDE.

## <a name="related-sections"></a>См. также
- [SccOpenProject](../extensibility/sccopenproject-function.md) Открывает проект.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) Изучит список файлов для их текущего состояния. Кроме того, `pfnPopulate` использует функцию для уведомления вызываемого, когда `nCommand`файл не соответствует критериям для .

- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) Изучит список каталогов и файлов в проекте или проектах, накоторыехаемых под контролем источников. Каждый найденный каталог и найденное имя файла передаются функции обратного вызова.

- [СккериИзменения](../extensibility/sccquerychanges-function.md) Рассматривает изменения имен, внесенные в список файлов. Каждое имя файла передается функции обратного вызова вместе со статусом изменения.

- [SccSetOption](../extensibility/sccsetoption-function.md) Устанавливает широкий спектр опций. Каждый вариант `SCC_OPT_xxx` начинается с определенного набора значений и имеет свой собственный определенный набор.

- [Подключаемые модули управления исходным элементом](../extensibility/source-control-plug-ins.md) Описывает содержание справочного раздела SDK управления исходным управлением.
