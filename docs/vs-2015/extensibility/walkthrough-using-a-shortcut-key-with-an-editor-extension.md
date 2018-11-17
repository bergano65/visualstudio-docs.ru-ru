---
title: 'Пошаговое руководство: Использование сочетаний клавиш в расширении редактора | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
caps.latest.revision: 33
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1e68cf9d3e33ad07ab092de680078972dfaf2d70
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51797459"
---
# <a name="walkthrough-using-a-shortcut-key-with-an-editor-extension"></a>Пошаговое руководство. Использование сочетания клавиш в расширении редактора
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно ответить на сочетания клавиш в расширении редактора. Следующее пошаговое руководство демонстрирует добавление оформления представления для текстового представления с помощью сочетания клавиш. В этом пошаговом руководстве основан на шаблоне редактор оформление окна просмотра, а также вы можете добавить оформления с помощью + символ.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Создание проекта Managed Extensibility Framework (MEF)  
  
1. Создайте проект VSIX C#. (В **новый проект** диалоговом окне выберите **Visual C# / Extensibility**, затем **проект VSIX**.) Назовите решение `KeyBindingTest`.  
  
2. Добавьте в проект шаблон элемента оформления текстового редактора и назовите его `KeyBindingTest`. Дополнительные сведения см. в разделе [создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Добавьте следующие ссылки и задать **CopyLocal** для `false`:  
  
    Microsoft.VisualStudio.Editor  
  
    Microsoft.VisualStudio.OLE.Interop  
  
    Microsoft.VisualStudio.Shell.14.0  
  
    Microsoft.VisualStudio.TextManager.Interop  
  
   В файле класса KeyBindingTest измените имя класса на PurpleCornerBox. Используйте лампочки, который отображается в левом поле на внесение соответствующих изменений. Внутри конструктора, измените имя элемента оформления уровня от **KeyBindingTest** для **PurpleCornerBox**:  
  
```csharp  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  
  
## <a name="defining-the-command-filter"></a>Определение фильтра команды  
 Фильтр команд представляет собой реализацию <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, который обрабатывает команду путем создания экземпляра оформления.  
  
1.  Добавьте файл класса с именем `KeyBindingCommandFilter`.  
  
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
    internal class KeyBindingCommandFilter : IOleCommandTarget  
    ```  
  
4.  Добавьте закрытые поля для представления текста, следующая команда в цепочке команды, а флаг, представляют ли фильтр команды уже был добавлен.  
  
    ```csharp  
    private IWpfTextView m_textView;  
    internal IOleCommandTarget m_nextTarget;  
    internal bool m_added;  
    internal bool m_adorned;  
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
  
7.  Реализуйте `Exec()` он добавляет сиреневый поле в представление, если метод + символа.  
  
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
  
## <a name="adding-the-command-filter"></a>Добавление фильтра команды  
 Поставщик элемента оформления необходимо добавить фильтр команд к текстовому представлению. В этом примере реализован поставщик <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> для прослушивания события создания представления текста. Этот поставщик элемента оформления также экспортирует слое оформлений, который определяет Z-порядок элемента оформления.  
  
1.  В файле KeyBindingTestTextViewCreationListener, добавьте следующие операторы using:  
  
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
  
2.  В определении слой оформлений, измените имя AdornmentLayer из **KeyBindingTest** для **PurpleCornerBox**.  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  
  
3.  Чтобы получить соответствующий адаптер представления текста, необходимо импортировать <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>.  
  
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
  
5.  `AddCommandFilter` Обработчик получает соответствующий адаптер представления текста и добавляет фильтр команд.  
  
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
  
## <a name="making-the-adornment-appear-on-every-line"></a>Создание оформления появляются в каждой строке  
 Исходное оформление появлялись на каждый символ «» в текстовом файле. Теперь, когда мы изменили код для добавления оформления в ответ на знак «+», он добавляет оформления только в строке где «+» типизирован. Мы можем изменить код оформления для отображения оформления еще раз на каждые «».  
  
 В файле KeyBindingTest.cs измените метод CreateVisuals() для перебора всех строк в представлении, чтобы снабдить символ «».  
  
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
  
1.  Выполните сборку решения KeyBindingTest и запустите его в экспериментальном экземпляре.  
  
2.  Создайте или откройте текстовый файл. Введите некоторые слова, содержащие символ «», а затем введите + в любом месте в представлении текста.  
  
     На каждый символ «» в файле появится фиолетовой квадрата.

