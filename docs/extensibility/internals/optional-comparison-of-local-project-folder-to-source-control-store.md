---
title: Сравните проект Фолдер с магазином управления исходом (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: facb3b656e0ac50b50fdb0291307aa2fe98b1df4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706864"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Необязательное сравнение папки локального проекта с системой управления версиями
В элементе управления source Plug-in API 1.2 сравнение локальной папки проекта и управления исходным кодом осуществляется с помощью функций [SccDir-''иенфофо](../../extensibility/sccdirqueryinfo-function.md) и [SccDirDiff.](../../extensibility/sccdirdiff-function.md)

 В **solution Explorer**, если папка выбрана вместо отдельного файла, меню ярлыка **версий Сравнения** вызывает новые [SccDir'eryInfo](../../extensibility/sccdirqueryinfo-function.md) и [SccDirDiff](../../extensibility/sccdirdiff-function.md) в плагине управления исходным кодом.

## <a name="new-capability-flags"></a>Флаги новых возможностей
 `SCC_CAP_DIRECTORYDIFF`

 `SCC_CAP_DIRECTORYCHECKOUT`

## <a name="new-functions"></a>Новые функции
- [SccDirDiff](../../extensibility/sccdirdiff-function.md)

- [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)

 Функция `SccDirQueryInfo` вызывается `SccDirDiff` раньше, чтобы определить, контролируется ли рабочий каталог. Функция `SccDirDiff` отображает различия между текущим локальным каталогом и соответствующей папкой управления исходом. Эта команда просит плагин управления исходным источником для отображения списка изменений в каталоге. Плагин управления исходным элементом обеспечивает свой собственный uii для отображения различий.

> [!NOTE]
> Эта функция использует те же флаги команды, [что и SccDiff.](../../extensibility/sccdiff-function.md) Как поставщик плагинов управления исходным кодом, вы можете отказаться от поддержки операции «быстрый дифф» для каталогов.

## <a name="see-also"></a>См. также
- [Новые возможности в API версии 1.2 подключаемого модуля системы управления версиями](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
