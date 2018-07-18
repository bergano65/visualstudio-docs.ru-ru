---
title: Упрощенное внедрение | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 01b06a0a63059c39035d15221feb201d3674d4a7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142936"
---
# <a name="simplified-embedding"></a>Упрощенное внедрения
Упрощенная внедрение включена в редакторе, его объекту представления документа имеет родителя (то есть сделаны дочерний) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]и <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> интерфейс реализуется для обработки его окно команд. Упрощенная внедрения редакторы, не могут содержать активные элементы управления. На следующем рисунке показаны объекты, используемые для создания редактора с упрощенной внедрения.  
  
 ![График упрощенного вложенного редактора](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor")  
Редактор с упрощенной внедрения  
  
> [!NOTE]
>  Объекты на этом рисунке, только `CYourEditorFactory` объекта, необходимые для создания стандартного редактора файла. При создании пользовательского редактора необходимые для реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>, так как ваш редактор, скорее всего будет свой собственный закрытый механизм сохраняемости. Для определенных пользователем редакторов тем не менее, это необходимо сделать.  
  
 Все интерфейсы, реализованные создания редактора с упрощенной внедрения находятся в `CYourEditorDocument` объекта. Однако для поддержки нескольких представлений данных документа, разделите интерфейсы на отдельные объекты данных и представления, как указано в следующей таблице.  
  
|Интерфейс|Расположение интерфейса|Использовать|  
|---------------|---------------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Просмотр|Обеспечивает подключение родительского окна.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Просмотр|Обработка команд.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Просмотр|Обеспечивает обновление строки состояния.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Просмотр|Включает **элементов** элементов.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Данные|Отправлять уведомления при изменении файла.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Данные|Включает функцию Сохранить как для типа файлов.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Данные|Обеспечивает сохраняемость документа.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Данные|Позволяет подавления событий изменения файла, например перезагрузить активации.|