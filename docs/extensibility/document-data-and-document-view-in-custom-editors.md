---
title: "Данные документа и документа представление в редакторах | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 7c7e24ed2db4538ab0fd38dbb85930452611f0ee
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="document-data-and-document-view-in-custom-editors"></a>Данные документа и представление документа в редакторах
Пользовательский редактор состоит из двух частей: объект данных документа и объект представления документа. Как бы имена, объект данных документа представляет текстовые данные для отображения, а объект представления документа (или «view») — один или несколько периодов, в котором отображается объект данных документа.  
  
## <a name="document-data-object"></a>Объект данных документа  
 Объект данных документа является представлением данных текста в буфер текста. Это объект COM, сохраняет текст документа и другие сведения, обработки документа сохраняемости и включает несколько представлений данных. Дополнительные сведения см. в разделе .  
  
 <xref:EnvDTE80.Window2.DocumentData%2A>и [окна документов](../extensibility/internals/document-windows.md).  
  
 Пользовательские редакторы и конструкторы можно использовать <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> объекта или собственные настраиваемые буфера. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>ниже упрощенная модель внедрения стандартного редактора, поддерживает несколько представлений и предоставляет интерфейсы событий, которые используются для управления несколькими представлениями.  
  
## <a name="document-view-object"></a>Объект представления документа  
 Окно, отображающее код и текст называется документа представления или представления. При создании редактора, можно выбрать одно представление, в котором текст отображается в одном окне, или несколько представление, в котором отображается текст в несколько окон. Выбор зависит от приложения. Например при необходимости изменения side-by-side выбирается несколько представления. Каждое представление связан с элементом в интегрированной среды разработки (IDE) под управлением таблицы document (RDT). Представление windows принадлежит проекту или <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> объекта.  
  
 Если ваш редактор поддерживает несколько представлений объект данных документа, то данные документа и объекты представления документа необходимо отдельных. В противном случае они могут быть сгруппированы вместе. Дополнительные сведения см. в разделе [поддержки нескольких представлений документа](../extensibility/supporting-multiple-document-views.md).  
  
 IDE оповещает представления о событиях (например, при закрытии решений, содержащих документ), соответствующий идентификатор элемента (ItemID) для каждой записи в запущенной таблице документов. Дополнительные сведения см. в разделе [под управлением таблицы Document](../extensibility/internals/running-document-table.md).  
  
 Существует два варианта для создания представления для настраиваемого редактора. Такая модель активации по месту размещения представлении в окне с помощью элемента управления ActiveX или объект данных документа. Второй — упрощенная модель внедрения, где размещается представление [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> реализуется для обработки команд окна. Сведения о модели встроенной активации см. в разделе [встроенной активации](../extensibility/in-place-activation.md). Сведения о упрощенная модель внедрения разделе [упрощенный внедрение](../extensibility/simplified-embedding.md).  
  
## <a name="see-also"></a>См. также  
 [Поддержка нескольких представлений документов](../extensibility/supporting-multiple-document-views.md)   
 [Упрощенное внедрения](../extensibility/simplified-embedding.md)   
 [Как: присоединение представления для документирования данных](../extensibility/how-to-attach-views-to-document-data.md)   
 [Управление владельца блокировки документа](../extensibility/document-lock-holder-management.md)   
 [Одной или несколькими вкладку представления](../extensibility/single-and-multi-tab-views.md)   
 [Сохранение стандартного документа](../extensibility/internals/saving-a-standard-document.md)   
 [Сохранение состояния и выполнения таблицы Document](../extensibility/internals/persistence-and-the-running-document-table.md)   
 [Определение редактора откроется файл в проекте](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)   
 [Редактор фабрики](../extensibility/editor-factories.md)