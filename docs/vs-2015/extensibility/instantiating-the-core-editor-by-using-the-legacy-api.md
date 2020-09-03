---
title: Создание экземпляра базового редактора с помощью API прежних версий | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 29306a16390039c8ee6e424b81a5ff617e533ab4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203910"
---
# <a name="instantiating-the-core-editor-by-using-the-legacy-api"></a>Создание экземпляра основного редактора с помощью API прежних версий
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Редактор отвечает за функции редактирования текста, такие как вставка, удаление, копирование и вставка. Он сочетает эти функции с функциями, предоставляемыми языковой службой, такими как выделение цветом текста, отступы и завершение операторов IntelliSense.  
  
 Экземпляр базового редактора можно создать одним из трех способов:  
  
- Явно создайте экземпляр базового редактора в окне.  
  
- Предоставление фабрики редактора, возвращающей экземпляр основного редактора  
  
- Откройте файл из иерархии проекта.  
  
  В следующих разделах описывается, как использовать старый API для создания экземпляра редактора.  
  
## <a name="explicitly-opening-a-core-editor-instance"></a>Явное открытие основного экземпляра редактора  
 При явном получении экземпляра базового редактора:  
  
- Получите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> для хранения редактируемого объекта данных документа.  
  
- Создайте линейное представление объекта данных документа, создав <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> интерфейс из <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> интерфейса.  
  
- Задайте в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> качестве объекта данных документа для экземпляра реализации по умолчанию <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> интерфейса с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A> метода.  
  
   Разместите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> экземпляр в <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> интерфейсе с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A> метода.  
  
  На этом этапе отображение <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> интерфейса предоставляет окно, содержащее экземпляр базового редактора.  
  
  Однако это не очень полезный экземпляр, так как у него нет сочетаний клавиш или доступ к дополнительным функциям. Чтобы получить доступ к сочетаниям клавиш и дополнительным функциям:  
  
- Используйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> метод, чтобы связать языковую службу и объект данных документа, используемый редактором.  
  
- Либо создайте собственные сочетания клавиш, либо используйте системные значения по умолчанию, задав для <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> них свойства. Для этого вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A> метод со <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> свойством.  
  
   Чтобы получить и использовать нестандартные сочетания клавиш, создайте их с помощью файла vsct. Дополнительные сведения см. в разделе [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>Использование фабрики редактора для получения базового редактора  
 При реализации базового редактора с фабрикой редактора с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метода выполните все шаги, описанные в предыдущем разделе, чтобы явным образом разместить объект <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> объекта данных документа в <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> объекте.  
  
 Чтобы отобразить текст, получите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> интерфейс из <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> объекта и вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метод.  
  
 Чтобы предоставить языковую службу редактору, вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> метод в <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> методе.  
  
 Для получения сочетаний клавиш по умолчанию, в отличие от предыдущего раздела, используется контекст команды, возвращаемый <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> методом при получении базового редактора из <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метода.  
  
 Если <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метод возвращает тот же идентификатор GUID команды, что и текстовый редактор, то экземпляр основного редактора автоматически получает сочетания клавиш по умолчанию.  
  
 Общие сведения см. [в разделе Пошаговое руководство. Создание основного редактора и регистрация типа файла редактора](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md).  
  
## <a name="see-also"></a>См. также:  
 [Внутри основного редактора](../extensibility/inside-the-core-editor.md)   
 [Открытие и сохранение элементов проекта](../extensibility/internals/opening-and-saving-project-items.md)   
 [Пошаговое руководство. Создание основного редактора и регистрация типов файлов в редакторе](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)
