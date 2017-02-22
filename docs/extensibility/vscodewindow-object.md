---
title: "Объект VSCodeWindow | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VSCodeWindow"
helpviewer_keywords: 
  - "представления [Visual Studio SDK] VSCodeWindow объекта"
  - "Объект VsCodeWindow"
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Объект VSCodeWindow
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Окно кода является специальных документов, обычно включают один или несколько текстовых представлений <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> объекта.  
  
 С точки зрения архитектуры окно кода — окно документа, в котором находится внутри рамки окна. Функционально окно кода — просто окно документа с дополнительными возможностями. В режиме многодокументного интерфейса \(MDI\) окно кода имеет дочерние окна MDI. Для получения дополнительной информации см. [Настройка кода Windows с помощью API прежних версий](../extensibility/customizing-code-windows-by-using-the-legacy-api.md).  
  
 В следующей таблице перечислены интерфейсы в <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> объекта.  
  
|Метод|Описание|  
|-----------|--------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Предоставляет универсальный доступ механизм для поиска службы, определяющий глобальный уникальный идентификатор \(GUID\).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Представляет несколько дочерний интерфейс \(MDI\) документа, содержащий одно или несколько представлений кода.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Заполняет рамки окна.|  
  
## См. также  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Figures Edit](http://msdn.microsoft.com/ru-ru/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)