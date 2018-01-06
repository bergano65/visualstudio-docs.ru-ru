---
title: "При создании экземпляра базового редактора с помощью прежних версий API | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e508bda0b22c798246b0f6abf4dfb03c41a92d6d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="instantiating-the-core-editor-by-using-the-legacy-api"></a>При создании экземпляра базового редактора с помощью API прежних версий
Редактор несет ответственность за редактирование функции, такие как вставки, удаления, копирования и вставки текста. Он объединяет эти функции с помощью предоставленных языковой службы, такие как цвет текста, отступы и завершения операторов IntelliSense.  
  
 Можно создать экземпляр базового редактора в одном из трех способов:  
  
-   Явно создайте экземпляр ядро редактора в окне.  
  
-   Предоставить фабрику редактора, который возвращает экземпляр базового редактора  
  
-   Откройте файл из иерархии проекта.  
  
 В следующих разделах рассматриваются способы использования устаревшего API для создания экземпляра редактора.  
  
## <a name="explicitly-opening-a-core-editor-instance"></a>Явно открывать экземпляр базового редактора  
 Получив явно экземпляр базового редактора:  
  
-   Получить <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> для хранения редактируемого объекта данных документа.  
  
-   Создайте представление строки ориентированного объект данных документа путем создания <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> интерфейс из <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> интерфейса.  
  
-   Задать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> как объект данных документа для экземпляра по умолчанию реализация <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> интерфейс, с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A> метод.  
  
     Узел <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> экземпляра в <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> интерфейса с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A> метод.  
  
 На этом этапе отображение <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> интерфейс предоставляет окно, которое содержит экземпляр базового редактора.  
  
 Однако это не очень полезный экземпляр, так как он не имеет сочетания клавиш, или доступ к расширенным функциям. Для получения доступа к сочетания клавиш, а также дополнительные возможности:  
  
-   Используйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> способ сопоставления языковой службы и объект данных документа, который используется в редакторе.  
  
-   Создайте собственные сочетания клавиш или использовать системные значения по умолчанию, задав <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> объекты отображаются свойства. Чтобы сделать это, вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A> метод с <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> свойство.  
  
     Чтобы получить и использовать нестандартные сочетания клавиш, создайте их с помощью vsct-файле. Дополнительные сведения см. в разделе [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>Как использовать фабрику редактора для получения базового редактора  
 При реализации базового редактора с фабрики редактора с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метод, выполните все шаги, описанные в предыдущем разделе, чтобы явным образом разместить <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> объект данных документа, в <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> объекта.  
  
 Для отображения текста, получить <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> интерфейс из <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> и вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метод.  
  
 Чтобы обеспечить редакторе языковую службу, вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> метода в <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метод.  
  
 Для получения по умолчанию сочетания клавиш, в отличие от предыдущего раздела, используйте контекст командной строки, возвращенные <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метод при получении базового редактора из <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метод.  
  
 Если <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метод возвращает ту же команду GUID как текстовый редактор, экземпляр базового редактора автоматически получает значение по умолчанию сочетания клавиш.  
  
 Общие сведения см. в разделе [Пошаговое руководство: создание базового редактора и регистрация файла тип редактора](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md).  
  
## <a name="see-also"></a>См. также  
 [В редакторе Core](../extensibility/inside-the-core-editor.md)   
 [Открытие и сохранение элементов проекта](../extensibility/internals/opening-and-saving-project-items.md)   
 [Пошаговое руководство: Создание базового редактора и регистрация файла тип редактора](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)