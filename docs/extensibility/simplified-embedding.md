---
title: Упрощенное внедрение | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b9252db6202754e534b1af8a284d768fcd70eb47
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434558"
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