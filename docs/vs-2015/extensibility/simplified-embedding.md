---
title: Упрощенное внедрение | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b8e1ac2fa17409ac3228f87eb71c99ce9e725521
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842380"
---
# <a name="simplified-embedding"></a>Упрощенное внедрение
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Упрощенное внедрение в редакторе включается, если его объект представления документа является родительским для (то есть дочерним элементом) [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , а <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> интерфейс реализуется для обработки его команд окна. Упрощенные редакторы внедрений не могут размещать активные элементы управления. На следующем рисунке показаны объекты, используемые для создания редактора с упрощенным внедрением.  
  
 ![График упрощенного вложенного редактора](../extensibility/media/vssimplifiedembeddingeditor.gif "вссимплифиедембеддинжедитор")  
Редактор с упрощенным внедрением  
  
> [!NOTE]
> Из объектов на этом рисунке `CYourEditorFactory` для создания стандартного редактора на основе файлов требуется только объект. При создании пользовательского редактора не требуется реализовывать <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> , так как в редакторе, скорее всего, будет собственный частный механизм сохранения. Однако для непользовательских редакторов это необходимо.  
  
 Все интерфейсы, реализованные для создания редактора с упрощенным внедрением, содержатся в `CYourEditorDocument` объекте. Однако для поддержки нескольких представлений данных документа разделите интерфейсы на отдельные данные и объекты представления, как показано в следующей таблице.  
  
|Интерфейс|Расположение интерфейса|Использовать|  
|---------------|---------------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Просмотр|Обеспечивает подключение к родительскому окну.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Просмотр|Обрабатывает команды.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Просмотр|Обеспечивает обновление строки состояния.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Просмотр|Включает элементы **панели элементов** .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Данные|Отправляет уведомления при изменении файла.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Данные|Включает функцию "Сохранить как" для типа файлов.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Данные|Обеспечивает сохраняемость документа.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Данные|Позволяет подавлять события изменения файлов, такие как запуск повторной загрузки.|
