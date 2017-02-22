---
title: "Отображение файлов с помощью команды Open | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "типы проектов, поддерживающих открыть с помощью команды"
  - "Открыть с помощью команды"
  - "Сохраняемость, поддерживающий открыть с помощью команды"
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Отображение файлов с помощью команды Open
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Проект может запросить интегрированную среду разработки для отображения **Открыть с помощью** диалоговое окно.  Этот запрос пользователю предлагается открыть файл, имеющий выделение стандартных редакторов.  Следующие шаги описывают процесс.  
  
1.  Вызовы проекта <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, указав значение для OSE\_UseOpenWithDialog  `OSEOpenDocEditor` параметр.  
  
2.  В зависимости от расширения имени файла документа, интегрированная среда разработки определяет, редакторам, перечисленных в реестре удалось открыть указанный документ и отображает эти сведения в **Открыть с помощью** диалоговое окно.  
  
    > [!NOTE]
    >  Проекты, которые содержат встроенный редактор, который необходимо включить в **Открыть с помощью** диалоговое окно должно зарегистрировать фабрику редактора для каждого такого редактора.  Встроенные редакторы работают только с указанным типом проекта, который задается принудительно для реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метод.  Интегрированная среда разработки имеет встроенное фабрика редактора для текстового редактора core и binary редактора.  Интегрированная среда разработки также создает экземпляр фабрики редактора именем каждой зарегистрированной ассоциации файлов windows.  Примером такого файла Microsoft Word.  
  
3.  Когда пользователь выбирает элемент <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> диалоговое окно " интегрированная среда разработки затем открывает документ, вызвав  **Открыть с помощью** метод.  Дополнительные сведения см. в разделе [Практическое руководство: Откройте стандартные редакторы](../../extensibility/how-to-open-standard-editors.md).  
  
## См. также  
 [Открытие и сохранение элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Отображение файлов с помощью команды Открыть файл](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)   
 [Практическое руководство: Откройте стандартные редакторы](../../extensibility/how-to-open-standard-editors.md)