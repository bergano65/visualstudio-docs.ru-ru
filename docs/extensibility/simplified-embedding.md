---
title: "Упрощенное внедрения | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "пользовательские редакторы [Visual Studio SDK] - простой просмотр внедрения"
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Упрощенное внедрения
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Упрощенного внедрения включен в редакторе при его объект представления документа parented \(то есть является дочерним элементом\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]и  <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> интерфейс реализован для обработки его команды окна.  Редакторы не может внедрить упрощено Активные элементы управления основного приложения.  Объекты, используемые для создания редактор упрощенного внедрения с на следующем рисунке показаны.  
  
 ![График упрощенного вложенного редактора](~/extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor")  
Редактор упрощенного внедрения с  
  
> [!NOTE]
>  На этом рисунке только объектов `CYourEditorFactory` требуются создает объект стандартный на основе файлов редактор.  Если создать специализированный редактор, то не требуется реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>поскольку редактор, скорее всего, будет иметь свой собственный закрытый механизм сохраняемости.  Для редакторов non\-таможни, однако необходимо сделать.  
  
 Все интерфейсы, реализованные для создания редактор упрощенного внедрения с содержащимися в `CYourEditorDocument` объект.  Однако чтобы поддерживать несколько представлений данных документа, разбиение интерфейсы объектам данных и представления, как показано в следующей таблице.  
  
|Интерфейс|Расположение интерфейса|Применение|  
|---------------|-----------------------------|----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Просмотр|Предоставляет подключение к родительскому окну.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Просмотр|Обрабатывает команды.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Просмотр|Включает обновления строки состояния.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Просмотр|Разрешает **Панель элементов** элементы.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Данные|Отправляет уведомления при изменении файла.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Данные|Включает функцию " сохранить как " для типа файла.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Данные|Включить сохраняемость для документа.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Данные|Обеспечивает подавление событий изменения файла, как активировать перезагрузить.|