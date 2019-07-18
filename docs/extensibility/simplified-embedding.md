---
title: Упрощенное внедрение | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c77c7f19ff677ddbe8339c88ef3ea46953e23b7d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332076"
---
# <a name="simplified-embedding"></a>Упрощенное внедрение
Упрощенное внедрение включена в редакторе, его объекта представления документа является потомком (т. е стал является потомком) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]и <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> интерфейс реализуется для обработки его окно команд. Упрощенное внедрение редакторах, не могут содержать активных элементов управления. На следующем рисунке показаны объекты, используемые для создания редактора с упрощенной внедрения.

 ![График упрощенного вложенного редактора](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor") редактор с упрощенное внедрение

> [!NOTE]
> Объектов на этом рисунке, только `CYourEditorFactory` объект обязательно должен создать стандартный редактор на основе файлов. Если вы создаете настраиваемый редактор, вы не требуется реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>, так как редактора, скорее всего, будет иметь свой собственный закрытый механизм сохраняемости. Ненастраиваемых редакторов тем не менее, это необходимо сделать.

 Все интерфейсы, реализованные создания редактора с упрощенное внедрение содержатся в `CYourEditorDocument` объекта. Однако для поддержки нескольких представлений данных документа, разделите интерфейсы на отдельные объекты данных и представления, как указано в следующей таблице.

|Интерфейс|Расположение интерфейса|Использовать|
|---------------|---------------------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Просмотр|Обеспечивает подключение родительского окна.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Просмотр|Обрабатывает команды.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Просмотр|Обеспечивает обновление строки состояния.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Просмотр|Позволяет **элементов** элементов.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Данные|Отправляет уведомления при изменении файла.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Данные|Включает функцию сохранение для типа файла.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Данные|Обеспечивает сохраняемость документа.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Данные|Позволяет подавление событий изменения файла, такие как запуск перезагрузить.|