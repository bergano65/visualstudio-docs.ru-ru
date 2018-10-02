---
title: Упрощенное внедрение | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: de1ef1b6538c010a1428dfa54ea4296a870d7ad5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570722"
---
# <a name="simplified-embedding"></a>Упрощенное внедрение
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [упрощенное внедрение](https://docs.microsoft.com/visualstudio/extensibility/simplified-embedding).  
  
Упрощенное внедрение включена в редакторе, его объекта представления документа является потомком (т. е стал является потомком) [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]и <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> интерфейс реализуется для обработки его окно команд. Упрощенное внедрение редакторах, не могут содержать активных элементов управления. На следующем рисунке показаны объекты, используемые для создания редактора с упрощенной внедрения.  
  
 ![График упрощенного вложенного редактора](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor")  
Редактор с упрощенное внедрение  
  
> [!NOTE]
>  Объектов на этом рисунке, только `CYourEditorFactory` объект обязательно должен создать стандартный редактор на основе файлов. Если вы создаете настраиваемый редактор, вы не требуется реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>, так как редактора, скорее всего, будет иметь свой собственный закрытый механизм сохраняемости. Ненастраиваемых редакторов тем не менее, это необходимо сделать.  
  
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

