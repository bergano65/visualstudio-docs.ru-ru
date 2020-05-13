---
title: Упрощенное встраивание Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b9bc9619ae1ed75aed3656ff014296f7c7d88fa0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700072"
---
# <a name="simplified-embedding"></a>Упрощенное внедрение
Упрощенное встраивание включено в редактор, когда объект представления документа является родительским (т.е. сделан ребенком) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]и <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> интерфейс реализован для обработки команд окна. Упрощенные встраиваемые редакторы не могут размещать активные элементы управления. Объекты, используемые для создания редактора с упрощенным встраиванием, показаны на следующей иллюстрации.

 ![Упрощенное встраивание редактор графический](../extensibility/media/vssimplifiedembeddingeditor.gif "vs УпрощенныйEmbeddingEditor") Редактор с упрощенным встраиванием

> [!NOTE]
> Из объектов на этой `CYourEditorFactory` иллюстрации требуется только объект для создания стандартного редактора на основе файлов. Если вы создаете пользовательский редактор, вы <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>не обязаны реализовывать, потому что ваш редактор, скорее всего, будет иметь свой собственный частный механизм настойчивости. Для непользовательских редакторов, однако, вы должны сделать это.

 Все интерфейсы, реализованные для создания редактора с `CYourEditorDocument` упрощенным встраиванием, содержатся в объекте. Однако для поддержки нескольких представлений данных документов разделите интерфейсы на отдельные данные и просмотрите объекты, указанные в следующей таблице.

|Интерфейс|Расположение интерфейса|Использовать|
|---------------|---------------------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Просмотр|Обеспечивает подключение к родительскому окну.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Просмотр|Ручки команд.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Просмотр|Обеспечивает обновление строки состояния.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Просмотр|Включает элементы **Toolbox.**|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Данные|Отправляет уведомления при изменении файла.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Данные|Позволяет сохранить как функцию для типа файла.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Данные|Обеспечивает сохраняемость документа.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Данные|Позволяет подавление событий изменения файла, таких как перезагрузить срабатывание.|
