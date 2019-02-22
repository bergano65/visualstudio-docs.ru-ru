---
title: Сравнить папки проекта для управления Store источника | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5ac710fd3994dca24d8e15e3d15c18d9f456a744
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56614198"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Необязательное сравнение папки локального проекта с системой управления версиями
В источнике управления 1.2 API подключаемых модулей, сравнение между локальной папке проекта и система управления версиями осуществляется с помощью функции [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) и [SccDirDiff](../../extensibility/sccdirdiff-function.md).

 В рамках **обозревателе решений**, если папка выбрана вместо отдельного файла, **сравнить версии** контекстное меню вызывает новый [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) и [ SccDirDiff](../../extensibility/sccdirdiff-function.md) подключаемый модуль системы управления версиями.

## <a name="new-capability-flags"></a>Новые флаги возможностей
 `SCC_CAP_DIRECTORYDIFF`

 `SCC_CAP_DIRECTORYCHECKOUT`

## <a name="new-functions"></a>Новые функции
- [SccDirDiff](../../extensibility/sccdirdiff-function.md)

- [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)

 `SccDirQueryInfo` Функция вызывается перед `SccDirDiff` чтобы определить рабочий каталог, контролируемого системой управления версиями. `SccDirDiff` Функция отображает различия между текущий локальный каталог и соответствующие папки системы управления версиями. Эта команда запрашивает у системы управления версиями, подключаемый модуль, чтобы отобразить список изменений в каталог. Подключаемый модуль системы управления версиями предоставляет свой собственный пользовательский Интерфейс для отображения различий.

> [!NOTE]
>  Эта функция использует те же флаги команды, как [SccDiff](../../extensibility/sccdiff-function.md). Как подключаемый модуль поставщика управления версиями вы можете не поддерживают «быстрые операции инструмента сравнения» для каталогов.

## <a name="see-also"></a>См. также
- [Новые возможности в API версии 1.2 подключаемого модуля системы управления версиями](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)