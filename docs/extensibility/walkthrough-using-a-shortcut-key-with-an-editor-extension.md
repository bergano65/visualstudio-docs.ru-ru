---
title: "Пошаговое руководство: Использование сочетаний клавиш в редакторе расширений | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] new - ссылки нажатия клавиш для команды"
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
caps.latest.revision: 32
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 32
---
# Пошаговое руководство: Использование сочетаний клавиш в редакторе расширений
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Сочетания клавиш можно ответить в расширение редактора. Следующего пошагового руководства демонстрируется добавление обрамления представление в представление текста с помощью сочетания клавиш. В этом пошаговом руководстве основан на шаблоне редактор оформления окна просмотра и позволяет добавить оформление с помощью знаком \+.  
  
## Обязательные компоненты  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в установку Visual Studio. VS SDK также можно установить позже. Для получения дополнительной информации см. [Установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Создание проекта Managed Extensibility Framework \(MEF\)  
  
1.  Создайте проект VSIX C\#. \(В **Новый проект** диалогового окна выберите **Visual C\# и расширяемость**, затем **проект VSIX**.\) Присвойте решению имя `KeyBindingTest`.  
  
2.  Шаблон элемента оформления текстового редактора добавьте в проект и назовите его `KeyBindingTest`. Для получения дополнительной информации см. [Создание расширения с помощью редактора шаблона элемента](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Добавьте следующие ссылки и задать **CopyLocal** для `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
 В файле класса KeyBindingTest измените имя класса для PurpleCornerBox. Используйте лампочка, которая отображается в левом поле для внесите соответствующие изменения. В конструкторе измените имя слоя обрамления из **KeyBindingTest** для **PurpleCornerBox**:  
  
```c#  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  
  
## Определение фильтра команды  
 Команда фильтр является реализацией <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, создавая оформления, который обрабатывает команды.  
  
1.  Добавьте файл класса с именем `KeyBindingCommandFilter`.  
  
2.  Добавьте следующие инструкции using.  
  
    ```c#  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Text.Editor;  
  
    ```  
  
3.  Следует наследовать класс с именем KeyBindingCommandFilter <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
    ```c#  
    internal class KeyBindingCommandFilter : IOleCommandTarget  
    ```  
  
4.  Добавьте закрытые поля для представления текста, следующая команда в цепочке команды и флаг, представляют ли команда\-фильтр уже добавлен.  
  
    ```c#  
    private IWpfTextView m_textView;  
    internal IOleCommandTarget m_nextTarget;  
    internal bool m_added;  
    internal bool m_adorned;  
    ```  
  
5.  Добавьте конструктор, который задает текстовое представление.  
  
    ```c#  
    public KeyBindingCommandFilter(IWpfTextView textView)  
    {  
        m_textView = textView;  
        m_adorned = false;  
    }  
    ```  
  
6.  Реализация `QueryStatus()` метода, как показано ниже.  
  
    ```vb  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7.  Реализация `Exec()` метода, так что он добавляет фиолетовый поле к представлению, если \+ символа.  
  
    ```c#  
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
  
## Добавление фильтра команды  
 Поставщик обрамления фильтр команды необходимо добавить текстовое представление. В этом примере поставщик реализует <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> для прослушивания события создания представления текста. Этот поставщик обрамления также экспортирует слое оформления, который определяет Z\-порядка элемента оформления.  
  
1.  В файле KeyBindingTestTextViewCreationListener добавьте следующие операторы using:  
  
    ```c#  
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
  
2.  В определении обрамления слой, изменить имя AdornmentLayer из **KeyBindingTest** для **PurpleCornerBox**.  
  
    ```c#  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  
  
3.  Чтобы получить адаптер представления текста, необходимо импортировать <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>.  
  
    ```c#  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
4.  Изменение <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> метода, так что он добавляет `KeyBindingCommandFilter`.  
  
    ```c#  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
5.  `AddCommandFilter` Обработчик возвращает адаптер представления текста и добавляет фильтр команды.  
  
    ```c#  
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
  
## Создание оформления отображаются в каждой строке  
 Исходное оформление появлялись на каждый символ «» в текстовом файле. Теперь, когда мы изменили код для добавления обрамления в ответ на знак «\+», он добавляет оформления только в строке где '\+' типизирован. Мы можем изменить код оформления, чтобы отображалось обрамления еще раз на каждые «».  
  
 В файле KeyBindingTest.cs измените метод CreateVisuals\(\) для перебора всех строк в представлении для оформления символ «».  
  
```c#  
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
  
## Сборка и тестирование кода  
  
1.  Постройте решение KeyBindingTest и запустите его в экспериментальном экземпляре.  
  
2.  Создайте или откройте текстовый файл. Введите несколько слов, содержащих символ «» и введите \+ в любом месте текстового представления.  
  
     Фиолетовый квадрат должно отображаться на каждый символ «» в файле.