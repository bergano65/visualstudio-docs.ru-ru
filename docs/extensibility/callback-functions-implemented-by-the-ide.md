---
title: Функции обратного вызова, реализованные интегрированной среды разработки | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dff6ee0a81472ea556aaca478a2ff33db93fe871
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321176"
---
# <a name="callback-functions-implemented-by-the-ide"></a>Функции обратного вызова, реализованные интегрированной среды разработки
Чтобы интеграция с по интегрированной среде разработки (IDE) как простой, как можно и для обеспечения единой конечных пользователей, подключаемый модуль системы управления версиями можно использовать функции обратного вызова, реализуемые интегрированной среды разработки с. Подключаемый модуль может вызывать эти функции в соответствующее время во время операции управления версиями для передачи информации в интегрированную среду разработки; Эти сведения затем можно отобразить интегрированной среды разработки как внедренные элементы в его собственном пользовательском Интерфейсе. Пользователь имеет возможность менее фрагментированных в этом сценарии, чем если подключаемый модуль используются свой UI.

 Обязательный заголовок файл *scc.h*. Расположение по умолчанию — *\Program Files\VSIP 8.0\EnvSDK\common\inc\\* . Это также в папку VSIP, образец подключаемого модуля управления источника в *\Program Files\VSIP 8.0\MSSCCI\\* .

## <a name="in-this-section"></a>Содержание раздела
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) описывает функцию обратного вызова, используемый [SccOpenProject](../extensibility/sccopenproject-function.md) для отображения сообщений из системы управления версиями, подключаемый модуль через среду IDE.

- [POPLISTFUNC](../extensibility/poplistfunc.md) описывает функцию обратного вызова, используемый [SccPopulateList](../extensibility/sccpopulatelist-function.md) при интегрированной среды разработки не имеет полный доступ к информации, которая доступна только для системы управления версиями, подключаемый модуль, например полный список файлы в системе управления версиями.

- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) описывает функцию обратного вызова, используемый [SccQueryChanges](../extensibility/sccquerychanges-function.md) операции.

- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) описывает функцию обратного вызова, используемый [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) операции.

- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) описывает функцию обратного вызова, установленный вызовом метода для [SccSetOption](../extensibility/sccsetoption-function.md) , позволяющий системы управления версиями, подключаемый модуль для связи имя изменения обратно в интегрированную среду разработки.

## <a name="related-sections"></a>Связанные разделы
- [SccOpenProject](../extensibility/sccopenproject-function.md) открывает проект.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) проверяет список файлов для их текущее состояние. Кроме того, использует `pfnPopulate` функция уведомляет вызывающего объекта, если файл не соответствует критериям для `nCommand`.

- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) проверяет список каталогов и файлов в проект или проекты, которые находятся в системе управления версиями. Каждый каталог и имя файла найден передается функции обратного вызова.

- [SccQueryChanges](../extensibility/sccquerychanges-function.md) проверяет изменения имен, которые были внесены в список файлов. Имя каждого файла передается функции обратного вызова, вместе с его состоянием изменения.

- [SccSetOption](../extensibility/sccsetoption-function.md) задает разнообразные параметры. Каждый параметр начинается с `SCC_OPT_xxx` и имеет свой собственный определенный набор значений.

- [Подключаемые модули управления источника](../extensibility/source-control-plug-ins.md) описывает содержимое в справочном разделе пакета SDK подключаемого модуля управления источника.