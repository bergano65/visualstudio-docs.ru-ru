---
title: Пошаговое руководство. Использование сочетания клавиш с расширением редактора | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5c9cb20bafa552c47a2f599d12e6b66fdb2bde59
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201948"
---
# <a name="walkthrough-using-a-shortcut-key-with-an-editor-extension"></a>Пошаговое руководство. Использование сочетания клавиш в расширении редактора
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете реагировать на сочетания клавиш в расширении редактора. В следующем пошаговом руководстве показано, как добавить Оформление представления в текстовое представление с помощью сочетания клавиш. Это пошаговое руководство основано на шаблоне "редактор оформлений" окна просмотра и позволяет добавлять Оформление с помощью символа +.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Кроме того, пакет SDK для VS можно установить позже. Дополнительные сведения см. [в разделе Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Создание проекта Managed Extensibility Framework (MEF)  
  
1. Создание проекта VSIX C#. (В диалоговом окне **Новый проект** выберите **Visual C#/Extensibility**, а затем **проект VSIX**.) Присвойте решению имя `KeyBindingTest` .  
  
2. Добавьте шаблон элемента оформления текста редактора в проект и присвойте ему имя `KeyBindingTest` . Дополнительные сведения см. в разделе [Создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Добавьте следующие ссылки и задайте для свойства **CopyLocal** значение `false` :  
  
    Microsoft. VisualStudio. Editor  
  
    Microsoft. VisualStudio. OLE. Interop  
  
    Microsoft. VisualStudio. Shell.,  
  
    Microsoft. VisualStudio. TextManager. Interop  
  
   В файле класса Кэйбиндингтест измените имя класса на Пурплекорнербокс. Используйте лампочку, которая отображается в левом поле, чтобы внести другие необходимые изменения. В конструкторе измените имя слоя оформления с **кэйбиндингтест** на **пурплекорнербокс**:  
  
```csharp  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  
  
## <a name="defining-the-command-filter"></a>Определение фильтра команд  
 Фильтр команд является реализацией <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , которая обрабатывает команду, создавая Оформление.  
  
1. Добавьте файл класса с именем `KeyBindingCommandFilter`.  
  
2. Добавьте следующие инструкции using.  
  
    ```csharp  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Text.Editor;  
  
    ```  
  
3. Класс с именем Кэйбиндингкоммандфилтер должен наследовать от <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
    ```csharp  
    internal class KeyBindingCommandFilter : IOleCommandTarget  
    ```  
  
4. Добавьте закрытые поля для текстового представления, следующую команду в цепочке команд и флаг для представления того, был ли уже добавлен фильтр команд.  
  
    ```csharp  
    private IWpfTextView m_textView;  
    internal IOleCommandTarget m_nextTarget;  
    internal bool m_added;  
    internal bool m_adorned;  
    ```  
  
5. Добавьте конструктор, который задает текстовое представление.  
  
    ```csharp  
    public KeyBindingCommandFilter(IWpfTextView textView)  
    {  
        m_textView = textView;  
        m_adorned = false;  
    }  
    ```  
  
6. Реализуйте `QueryStatus()` метод следующим образом.  
  
    ```vb  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7. Реализуйте `Exec()` метод таким образом, чтобы он добавил фиолетовый прямоугольник к представлению при вводе символа +.  
  
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
 Поставщик декоративных элементов должен добавить фильтр команд в текстовое представление. В этом примере поставщик реализует <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> для прослушивания событий создания текстового представления. Этот поставщик декоративных элементов также экспортирует слой оформления, который определяет Z-порядок оформления.  
  
1. В файл Кэйбиндингтесттекствиевкреатионлистенер добавьте следующие операторы using:  
  
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
  
2. В определении слоя декоративных элементов измените имя Адорнментлайер с **кэйбиндингтест** на **пурплекорнербокс**.  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  
  
3. Чтобы получить адаптер представления текста, необходимо импортировать <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> .  
  
    ```csharp  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
4. Измените <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> метод так, чтобы он добавил `KeyBindingCommandFilter` .  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
5. `AddCommandFilter`Обработчик получает адаптер текстового представления и добавляет фильтр команд.  
  
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
  
## <a name="making-the-adornment-appear-on-every-line"></a>Отображение оформления в каждой строке  
 Исходный элемент оформления появлялся на каждом символе "a" в текстовом файле. Теперь, когда мы изменили код для добавления оформления в ответ на символ "+", он добавляется только в строку, где введен знак "+". Мы можем изменить код оформления, чтобы в каждом элементе "a" появился крайний элемент.  
  
 В файле KeyBindingTest.cs измените метод Креатевисуалс (), чтобы выполнить итерацию по всем строкам в представлении для украшения символа "a".  
  
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
  
1. Создайте решение Кэйбиндингтест и запустите его в экспериментальном экземпляре.  
  
2. Создайте или откройте текстовый файл. Введите несколько слов, содержащих символ "a", а затем введите + в любом месте в текстовом представлении.  
  
     Сиреневый квадрат должен отображаться на каждом символе "a" в файле.
