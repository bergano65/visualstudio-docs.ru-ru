---
title: "Практическое руководство: открытие редакторов конкретного проекта | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "типы проектов, откройте редактор конкретного проекта"
  - "открытие редакторов конкретного проекта редакторы [Visual Studio SDK]"
  - "Открытие папки проектов [Visual Studio SDK]"
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Практическое руководство: открытие редакторов конкретного проекта
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Если файл элемента проекта открываемый подсистемы, привязанный к определенному редактор для этого проекта, он должен открыть файл с помощью редактора проектов.  Файл нельзя делегировать вниз к механизму интегрированной среды разработки для выбора редактор.  Например, вместо использования стандартных редактора растрового изображения с помощью этого параметра можно указать определенный редактора проектов редактор растрового изображения, который распознает данные в файле, который является уникальным в проект.  
  
 Интегрированная среда разработки вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> метод, если он указывает, что файл должен быть открыт определенный проект.  Дополнительные сведения см. в разделе [Отображение файлов с помощью команды Открыть файл](../extensibility/internals/displaying-files-by-using-the-open-file-command.md).  Используйте следующие рекомендации для реализации `OpenItem` метод иметь свой открытый проект файл с помощью редактора проектов.  
  
### Реализация метода OpenItem с редактором проектов  
  
1.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> метод \(RDT\_EditLock\), чтобы указать, относится ли файл данных \(объект документа\) уже открыт.  
  
    > [!NOTE]
    >  Дополнительные сведения об объектах представления данных документа и документ см. в разделе [Данные документа и представления документа в редакторах](../extensibility/document-data-and-document-view-in-custom-editors.md).  
  
2.  Если файл уже открыт, то resurface файл, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> метод и указать значение для IDO\_ActivateIfOpen  `grfIDO` параметр.  
  
     Если файл открыт и документ принадлежит проектом, отличный от вызывающего проекта, предупреждение будет отображаться пользователю, открываемый в редакторе из другого проекта.  Окно файла затем отображается.  
  
3.  Если текстовый буфер \(объект данных документа\) уже открыт и их нужно вложить другое представление, то ответственность за подключение по этому представлению.  Рекомендуемый способ создания представления \(объект представления документа\) в проекте следующим образом:  
  
    1.  Вызов `QueryService` на  <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> служба для получения указателя на  <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> интерфейс.  
  
    2.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> метод, чтобы создать экземпляр класса представления документа.  
  
4.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> метод, указывая объект представления документа.  
  
     Сайты этого метода объект представления документа в окне документа.  
  
5.  Выполните соответствующие вызовы к этому <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> или  <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> методы.  
  
     На этом этапе представление должно быть полностью инициализирован и готово его открытия.  
  
6.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> метод указания и открыть представление.  
  
## См. также  
 [Открытие и сохранение элементов проекта](../extensibility/internals/opening-and-saving-project-items.md)   
 [Практическое руководство: Откройте стандартные редакторы](../extensibility/how-to-open-standard-editors.md)   
 [Практическое руководство: открытие редакторов для открытых документов](../extensibility/how-to-open-editors-for-open-documents.md)