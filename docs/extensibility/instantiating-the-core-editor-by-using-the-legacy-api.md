---
title: "Создание базового редактора с помощью API прежних версий | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e18118d73d46aeee7612eb7dff64f778726778f0
ms.lasthandoff: 02/22/2017

---
# <a name="instantiating-the-core-editor-by-using-the-legacy-api"></a>Создание базового редактора с помощью API прежних версий
Редактор несет ответственность за редактирование функций, таких как вставки, удаления, копирования и вставки текста. Он объединяет эти функции с предоставляемыми языковой службы, такие как выделение текста цветом, отступы и завершения операторов IntelliSense.  
  
 Можно создать экземпляр базового редактора одним из трех способов:  
  
-   Явно создайте экземпляр основной редактор в окне.  
  
-   Укажите фабрики редактора, который возвращает экземпляр базового редактора  
  
-   Откройте файл из иерархии проекта.  
  
 В следующих разделах рассматриваются способы использования старый API для создания экземпляра редактора.  
  
## <a name="explicitly-opening-a-core-editor-instance"></a>Явно открывать экземпляр базового редактора  
 Получив явно экземпляр базового редактора:  
  
-   Получить <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>для хранения редактируемого объекта данных документа.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>  
  
-   Создать представление ориентированного строки данных объекта документа путем создания <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>интерфейс из <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>интерфейса.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>  
  
-   Задать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>как объект документа данных для экземпляра по умолчанию реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>интерфейс, с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A>метод.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>  
  
     Узел <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>экземпляра в <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>интерфейса с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A>метод.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>  
  
 На этом этапе отображение <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>интерфейс предоставляет окно, которое содержит экземпляр базового редактора.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>  
  
 Однако это не очень полезный экземпляр, так как он не имеет сочетания клавиш, или доступ к расширенным функциям. Чтобы получить доступ к сочетания клавиш, а также дополнительные возможности:  
  
-   Использование <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>метода, чтобы установить языковую службу и объект данных документа, который используется в редакторе.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>  
  
-   Создавать собственные сочетания клавиш, или с помощью системы по умолчанию, задав <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>объектов отображения свойств.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> Для этого вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A>метод <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>свойство.</xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> </xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A>  
  
     Чтобы получить и использовать нестандартные сочетания клавиш, создайте их с помощью файла .vsct. Дополнительные сведения см. в разделе [таблицы команд Visual Studio (. Файлы Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>Как использовать фабрику редактора для получения базового редактора  
 При реализации базового редактора с помощью редактора фабрики с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>метод, выполните все шаги, описанные в предыдущем разделе, чтобы явным образом разместить <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>в документ данных объекта <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>объекта.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> </xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>  
  
 Для отображения текста, получить <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>интерфейс из <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>и вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>метод.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>  
  
 Для предоставления редактор языковую службу, вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>метода в <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>метод.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>  
  
 Для получения по умолчанию сочетания клавиш, в отличие от предыдущего раздела, используйте команду контекста, возвращенный <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>метод при получении из базового редактора <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>метод.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>  
  
 Если <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>метод возвращает ту же команду GUID как текстовый редактор, экземпляр базового редактора автоматически получает значение по умолчанию сочетания клавиш.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>  
  
 Общие сведения см. в разделе [Пошаговое руководство: создание базового редактора и регистрация файла тип редактора](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md).  
  
## <a name="see-also"></a>См. также  
 [В редакторе ядра](../extensibility/inside-the-core-editor.md)   
 [Открытие и сохранение элементов проекта](../extensibility/internals/opening-and-saving-project-items.md)   
 [Пошаговое руководство: Создание базового редактора и регистрация файла тип редактора](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)
