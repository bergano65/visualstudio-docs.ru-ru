---
title: Пошаговое руководство. Использование сочетаний клавиш в расширении редактора | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e669b86a84f21dd6187558fc0a853c875d5d2e71
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53953015"
---
# <a name="walkthrough-use-a-shortcut-key-with-an-editor-extension"></a>Пошаговое руководство. Сочетания клавиш в расширении редактора
Можно ответить на сочетания клавиш в расширении редактора. Следующее пошаговое руководство демонстрирует добавление оформления представления для текстового представления с помощью сочетания клавиш. В этом пошаговом руководстве основан на шаблоне редактор оформление окна просмотра, а также вы можете добавить оформления с помощью + символ.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не устанавливайте Visual Studio SDK в центре загрузки. Этот пакет включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установить пакет SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-managed-extensibility-framework-mef-project"></a>Создание проекта Managed Extensibility Framework (MEF)  
  
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

В файле класса KeyBindingTestTextViewCreationListener.cs измените имя AdornmentLayer из **KeyBindingTest** для **PurpleCornerBox**:
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  

## <a name="handle-typechar-command"></a>Команда typechar дескриптор
До Visual Studio 2017 версии 15.6, единственным способом для обработки команд в расширении редактора было внедрение <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> основе фильтр команд. Visual Studio 2017 версии 15.6 появился современный упрощенный подход зависимости от обработчиков команд редактора. Следующих двух разделах показано, как обрабатывать команду, используя как старые и современные подход.

## <a name="define-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Определить фильтр команды (до версии Visual Studio 2017 версии 15.6)

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
  
    ```csharp  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7.  Реализуйте `Exec()` метод, поэтому он добавляет сиреневый поле в представление, если знак плюс (**+**) символа.  
  
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
  
## <a name="add-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Добавить фильтр команды (до версии Visual Studio 2017 версии 15.6)
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
  
2.  Чтобы получить соответствующий адаптер представления текста, необходимо импортировать <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>.  
  
    ```csharp  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
3.  Изменение <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> метода, так что он добавляет `KeyBindingCommandFilter`.  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
4.  `AddCommandFilter` Обработчик получает соответствующий адаптер представления текста и добавляет фильтр команд.  
  
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

## <a name="implement-a-command-handler-starting-in-visual-studio-2017-version-156"></a>Реализуйте обработчик команды (начиная с Visual Studio 2017 версии 15.6)

Во-первых обновление ссылок проекта Nuget для ссылки на последнюю редактор API:

1. Щелкните правой кнопкой мыши проект и выберите **управление пакетами Nuget**.

2. В **диспетчер пакетов Nuget**выберите **обновления** выберите **выбрать все пакеты** флажок, а затем выберите **обновления**.

Обработчик команд — это реализация <xref:Microsoft.VisualStudio.Commanding.ICommandHandler%601>, который обрабатывает команду путем создания экземпляра оформления.  
  
1. Добавьте файл класса с именем `KeyBindingCommandHandler`.  
  
2. Добавьте следующие инструкции using.  
  
   ```csharp  
   using Microsoft.VisualStudio.Commanding;
   using Microsoft.VisualStudio.Text.Editor;
   using Microsoft.VisualStudio.Text.Editor.Commanding.Commands;
   using Microsoft.VisualStudio.Utilities;
   using System.ComponentModel.Composition;   
   ```  
  
3. Следует наследовать класс с именем KeyBindingCommandHandler `ICommandHandler<TypeCharCommandArgs>`и экспортировать его как <xref:Microsoft.VisualStudio.Commanding.ICommandHandler>:
  
   ```csharp  
   [Export(typeof(ICommandHandler))]
   [ContentType("text")]
   [Name("KeyBindingTest")]
   internal class KeyBindingCommandHandler : ICommandHandler<TypeCharCommandArgs>  
   ```  
  
4. Добавьте отображаемое имя обработчика:  
  
   ```csharp  
   public string DisplayName => "KeyBindingTest";
   ```  
    
5. Реализуйте `GetCommandState()` метод следующим образом. Поскольку обработчику этой команды обрабатывает core редактор команда typechar, его можно делегировать, включение команду, чтобы базовым редактором.
  
   ```csharp  
   public CommandState GetCommandState(TypeCharCommandArgs args)
   {
       return CommandState.Unspecified;
   } 
   ```  
  
6. Реализуйте `ExecuteCommand()` метод, поэтому он добавляет сиреневый поле в представление, если знак плюс (**+**) символа. 
  
   ```csharp  
   public bool ExecuteCommand(TypeCharCommandArgs args, CommandExecutionContext executionContext)
   {
       if (args.TypedChar == '+')
       {
           bool alreadyAdorned = args.TextView.Properties.TryGetProperty(
               "KeyBindingTextAdorned", out bool adorned) && adorned;
           if (!alreadyAdorned)
           {
               new PurpleCornerBox((IWpfTextView)args.TextView);
               args.TextView.Properties.AddProperty("KeyBindingTextAdorned", true);
           }
       }

       return false;
   }
   ```  
   7. Скопируйте определение элемента оформления уровня из *KeyBindingTestTextViewCreationListener.cs* файл *KeyBindingCommandHandler.cs* , а затем удалите  *KeyBindingTestTextViewCreationListener.cs* файла:
 
   ```csharp  
   /// <summary>
   /// Defines the adornment layer for the adornment. This layer is ordered
   /// after the selection layer in the Z-order.
   /// </summary>
   [Export(typeof(AdornmentLayerDefinition))]
   [Name("PurpleCornerBox")]
   [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
   private AdornmentLayerDefinition editorAdornmentLayer;    
   ```  

## <a name="make-the-adornment-appear-on-every-line"></a>Сделать оформление появляются в каждой строке  

Исходное оформление появлялись на каждый символ «» в текстовом файле. Теперь, когда мы изменили код для добавления оформления в ответ на **+** символ, он добавляет оформления только в строке где **+** символа. Мы можем изменить код оформления для отображения оформления еще раз на каждые «».  
  
В *KeyBindingTest.cs* измените `CreateVisuals()` метод для перебора всех строк в представлении, чтобы снабдить символ «».  
  
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
  
## <a name="build-and-test-the-code"></a>Построение и тестирование кода  
  
1.  Выполните сборку решения KeyBindingTest и запустите его в экспериментальном экземпляре.  
  
2.  Создайте или откройте текстовый файл. Введите некоторые слова, содержащие символ «», а затем введите **+** в любом месте в представлении текста.  
  
     На каждый символ «» в файле появится фиолетовой квадрата.
