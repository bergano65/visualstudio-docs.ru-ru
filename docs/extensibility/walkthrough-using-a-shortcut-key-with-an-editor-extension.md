---
title: 'Пошаговое руководство: Использование сочетания клавиш с расширением редактор | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f3d0a9f8f730808cd8179599669342b530f921a9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-using-a-shortcut-key-with-an-editor-extension"></a>Пошаговое руководство: Использование сочетания клавиш с расширением редактора
Можно ответить на сочетания клавиш для расширения редактора. Следующее пошаговое руководство демонстрирует добавление оформления представления в представление текста с помощью сочетания клавиш. В этом пошаговом руководстве основан на шаблоне просмотра оформления редактора и его можно добавить с помощью оформления + символ.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки Майкрософт. Он включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Создание проекта Managed Extensibility Framework (MEF)  
  
1.  Создайте проект VSIX C#. (В **новый проект** диалогового окна выберите **Visual C# / Extensibility**, затем **проект VSIX**.) Присвойте решению имя `KeyBindingTest`.  
  
2.  Добавление шаблона элементов оформления текстового редактора в проект и назовите его `KeyBindingTest`. Дополнительные сведения см. в разделе [создания расширения с помощью шаблона элемента редактор](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Добавьте следующие ссылки и задать **CopyLocal** для `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
 В файле класса KeyBindingTest измените имя класса на PurpleCornerBox. Лампочка, который отображается в левом поле можно используете для внесите соответствующие изменения. Внутри конструктора, измените имя уровня оформления от **KeyBindingTest** для **PurpleCornerBox**:  
  
```csharp  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  
  
## <a name="defining-the-command-filter"></a>Определение фильтра команды  
 Команда фильтр является реализацией <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, которая обрабатывает команды, создав оформления.  
  
1.  Добавьте файл класса и назовите его `KeyBindingCommandFilter`.  
  
2.  Добавьте следующие инструкции using.  
  
    ```csharp  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Text.Editor;  
  
    ```  
  
3.  Следует наследовать класс с именем KeyBindingCommandFilter <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
    ```csharp  
    internal class KeyBindingCommandFilter : IOleCommandTarget  
    ```  
  
4.  Добавление закрытых полей для представления текста, следующей команды в цепочке команды и флаг, представляют ли команда фильтр уже добавлен.  
  
    ```csharp  
    private IWpfTextView m_textView;  
    internal IOleCommandTarget m_nextTarget;  
    internal bool m_added;  
    internal bool m_adorned;  
    ```  
  
5.  Добавьте конструктор, который задает представления текста.  
  
    ```csharp  
    public KeyBindingCommandFilter(IWpfTextView textView)  
    {  
        m_textView = textView;  
        m_adorned = false;  
    }  
    ```  
  
6.  Реализуйте `QueryStatus()` метод следующим образом.  
  
    ```vb  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7.  Реализация `Exec()` метода, так что он добавляет фиолетовой поле в представление, если + символа.  
  
    ```csharp  
    int IOleCommandTarget.Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)  
    {  
        if (m_adorned == false)  
        {  
            char typedChar = char.MinValue;  
  
            if (pguidCmdGroup == VSConstants.VSStd2K && nCmdID == (uint)VSConstants.VSStd2KCmdID.TYPECHAR)  
            {  
                typedChar = (char)(ushort)Marshal.GetObjectForNativeVariant(pvaIn);  
                if (typedChar.Equals('+'))  
                {  
                    new PurpleCornerBox(m_textView);  
                    m_adorned = true;  
                }  
            }  
        }  
        return m_nextTarget.Exec(ref pguidCmdGroup, nCmdID, nCmdexecopt, pvaIn, pvaOut);  
    }  
  
    ```  
  
## <a name="adding-the-command-filter"></a>Добавление фильтра команд  
 Поставщик оформления необходимо добавить фильтр команды для представления текста. В этом примере поставщик реализует <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> для прослушивания событий создания представления текста. Этот поставщик оформления также экспортирует уровня оформления, который определяет Z-порядок для оформления.  
  
1.  В файле KeyBindingTestTextViewCreationListener добавьте следующие операторы using:  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio.Utilities;  
    using Microsoft.VisualStudio.Editor;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.TextManager.Interop;  
  
    ```  
  
2.  В определении оформления слой, измените имя AdornmentLayer из **KeyBindingTest** для **PurpleCornerBox**.  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  
  
3.  Чтобы получить адаптер представления текста, необходимо импортировать <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>.  
  
    ```csharp  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
4.  Изменение <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> метода, так что он добавляет `KeyBindingCommandFilter`.  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
5.  `AddCommandFilter` Обработчик возвращает адаптер представления текста и добавляет фильтр команды.  
  
    ```csharp  
    void AddCommandFilter(IWpfTextView textView, KeyBindingCommandFilter commandFilter)  
    {  
        if (commandFilter.m_added == false)  
        {  
            //get the view adapter from the editor factory  
            IOleCommandTarget next;   
            IVsTextView view = editorFactory.GetViewAdapter(textView);  
  
            int hr = view.AddCommandFilter(commandFilter, out next);  
  
            if (hr == VSConstants.S_OK)  
            {      
                commandFilter.m_added = true;  
                 //you'll need the next target for Exec and QueryStatus   
                if (next != null)  
                commandFilter.m_nextTarget = next;  
            }  
        }  
    }  
    ```  
  
## <a name="making-the-adornment-appear-on-every-line"></a>Создание оформления отображаются в каждой строке  
 Исходное оформление появлялись на каждый символ «» в текстовом файле. Теперь, когда мы изменили код для добавления оформления в ответ на знак «+», он добавляет оформления только в строке где «+» типизирован. Мы можем изменить оформления кода для отображения оформления еще раз на каждые «».  
  
 В файле KeyBindingTest.cs измените метод CreateVisuals() для итерации по всем строкам в представлении для оформления символ «».  
  
```csharp  
private void CreateVisuals(ITextViewLine line)  
{  
    IWpfTextViewLineCollection textViewLines = this.view.TextViewLines;  
  
    foreach (ITextViewLine textViewLine in textViewLines)  
    {  
        if (textViewLine.ToString().Contains("a"))  
        {  
            // Loop through each character, and place a box around any 'a'   
            for (int charIndex = textViewLine.Start; charIndex < textViewLine.End; charIndex++)  
            {  
                if (this.view.TextSnapshot[charIndex] == 'a')  
                {  
                    SnapshotSpan span = new SnapshotSpan(this.view.TextSnapshot, Span.FromBounds(charIndex, charIndex + 1));  
                    Geometry geometry = textViewLines.GetMarkerGeometry(span);  
                    if (geometry != null)  
                    {  
                        var drawing = new GeometryDrawing(this.brush, this.pen, geometry);  
                        drawing.Freeze();  
  
                        var drawingImage = new DrawingImage(drawing);  
                        drawingImage.Freeze();  
  
                        var image = new Image  
                        {  
                            Source = drawingImage,  
                        };  
  
                        // Align the image with the top of the bounds of the text geometry  
                        Canvas.SetLeft(image, geometry.Bounds.Left);  
                        Canvas.SetTop(image, geometry.Bounds.Top);  
  
                        this.layer.AddAdornment(AdornmentPositioningBehavior.TextRelative, span, null, image, null);  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="building-and-testing-the-code"></a>Сборка и тестирование кода  
  
1.  Постройте решение KeyBindingTest и запустите его в экспериментальном экземпляре.  
  
2.  Создайте или откройте текстовый файл. Введите некоторые слова, содержащие символ «», а затем введите + в любом месте текстового представления.  
  
     Квадрат фиолетовой должно отображаться на каждый символ «» в файле.