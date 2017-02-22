---
title: "Практическое руководство: использование текстовых меток | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] прежних версий - с помощью текстовых меток"
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Практическое руководство: использование текстовых меток
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Текст метки можно применять для редактирования a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> объект.  
  
## Процедуры  
  
#### Применение метки текста  
  
1.  Получение экземпляра <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> класс.  
  
    > [!NOTE]
    >  Редактор автоматически применяет основные стандартные текстовой метки к любому документу, он изменяется и не должен быть должны быть применены стандартные текстовой метки явно.  
  
2.  Получите идентификатор типа маркера метки необходимо внутри путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> метод с  `GUID` текстовой метки необходимо работать с.  
  
    > [!NOTE]
    >  Не использовать `GUID` VSPackage или службы, предоставляющего метку текста.  
  
3.  Используйте идентификатор типа маркера, полученные путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> метод, вызываемый как параметр  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> метод или  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> метод, чтобы применить метку текста в данной области текста.  
  
#### Добавить функции к маркерам текста  
  
1.  Может быть требуется добавить дополнительные функции на метку текст, такие как всплывающие подсказки, специальное контекстное меню или обработчик для особых обстоятельствах.  Сделать:  
  
2.  Создание реализации объекта <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейс.  
  
3.  Если дополнительные возможности пожелана реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>и  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced> интерфейсы для одного и того же объекта, реализующего  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейс.  
  
4.  Передайте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> интерфейс, который будет создан, к вызову  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> метод или  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> метод, используемый, чтобы применить метку текста в данной области текста.  
  
5.  При добавлении поддержки контекстного меню в области текстовой метки должны быть созданы меню.  
  
     Дополнительные сведения см. в разделе создание контекстного меню [Контекстные меню](../extensibility/context-menus.md).  
  
6.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> среда вызывает методы предоставленных интерфейсов, таких как  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A> метод или  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] метод как требуется.  
  
## См. также  
 [С помощью текстовых маркеров с API прежних версий](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Практическое руководство: Добавление маркеров стандартный текст](../extensibility/how-to-add-standard-text-markers.md)   
 [Практическое руководство: Создание пользовательского текста маркеры](../extensibility/how-to-create-custom-text-markers.md)   
 [Практическое руководство: реализации маркеры ошибки](../extensibility/how-to-implement-error-markers.md)