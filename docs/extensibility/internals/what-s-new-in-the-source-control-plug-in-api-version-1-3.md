---
title: Что&#39;нового в подключаемый API версии 1.3 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9654f1f3ae6d4a3d73ddc3afca2977a57a98297d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703364"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>Что&#39;нового в подключаемый API версии 1.3
Версия API API управления исходным элементом вводит следующие новые функции для обеспечения более продвинутого управления.

## <a name="changes"></a>Изменения
 Следующие функции являются новыми для подключаемого API версии 1.3:

|Функция|Обзор|
|--------------|--------------|
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Позволяет сообщать о дополнительных битах возможностей|
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Позволяет изучить файлы, которые имеют новые версии в базе данных управления версиями, чем на локальном диске|
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Позволяет изучить состояние изменений имен (переимены, дополнения и удаления) для указанных файлов|
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Позволяет изучить каталоги и файлы в базе данных управления версиями|
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Добавлен определенный список файлов из базы данных управления версиями в текущий проект|
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Выполняет бесшумное "Получить" указанных файлов (пользовательский интерфейс не отображается)|
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Позволяет получить доступ к определенным опциям|

## <a name="see-also"></a>См. также
- [Начало работы](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
- [Новые возможности в API версии 1.2 подключаемого модуля системы управления версиями](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
