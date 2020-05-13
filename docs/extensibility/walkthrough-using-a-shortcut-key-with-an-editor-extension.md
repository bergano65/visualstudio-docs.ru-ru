---
title: 'Прохождение: Использование клавиши shortcut с расширением редактора (ru) Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 651598c0dbe746a9a26a6d60ce72b02853f98d47
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697153"
---
# <a name="walkthrough-use-a-shortcut-key-with-an-editor-extension"></a>Прохождение: Используйте клавишу ярлыка с расширением редактора
Вы можете ответить на клавиши быстрого отсечения в расширении редактора. Следующее пошаговое представление показывает, как добавить украшение представления в текстовое представление с помощью ключа ярлыка. Это пошаговое пошаговое решение основано на шаблоне редактора редактора украшения viewport, и позволяет добавлять украшение с помощью символа.

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, вы не устанавливаете Visual Studio SDK из центра загрузки. Он включен в качестве дополнительной функции в Visual Studio установки. Вы также можете установить VS SDK позже. Для получения дополнительной информации, [см.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Создание проекта управляемой расширительности (MEF)

1. Создайте проект СЗ VSIX. (В **диалоге нового проекта** выберите **Visual C / Расширяемость,** затем **VSIX Project**.) Назовите решение. `KeyBindingTest`

2. Добавьте шаблон элемента «Украшение текста `KeyBindingTest`редактора» в проект и назовите его. Для получения дополнительной информации [см.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Добавьте следующие ссылки и `false`установите **CopyLocal:**

    Microsoft.VisualStudio.Редактор

    Microsoft.VisualStudio.OLE.Interop

    Microsoft.VisualStudio.Shell.14.0

    Microsoft.VisualStudio.TextManager.Interop

   В файле класса KeyBindingTest измените название класса на PurpleCornerBox. Используйте лампочку, которая появляется в левом краю, чтобы сделать другие соответствующие изменения. Внутри конструктора измените название слоя украшения с **KeyBindingTest** на **PurpleCornerBox:**

```csharp
this.layer = view.GetAdornmentLayer("PurpleCornerBox");
```

В файле класса KeyBindingTestTextViewCreationListener.cs измените название AdornmentLayer с **KeyBindingTest** на **PurpleCornerBox:**

```csharp
[Export(typeof(AdornmentLayerDefinition))]
[Name("PurpleCornerBox")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
public AdornmentLayerDefinition editorAdornmentLayer;
```

## <a name="handle-typechar-command"></a>Ручка команды TYPECHAR
До версии Visual Studio 2017 15.6 единственным способом обработки команд <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> в расширении редактора была реализация на основе командного фильтра. Версия Visual Studio 2017 15.6 представила современный упрощенный подход, основанный на обработчиках команд редакторов. Следующие два раздела демонстрируют, как обращаться с командой, используя как наследие, так и современный подход.

## <a name="define-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Определите командный фильтр (до версии Visual Studio 2017 15.6)

 Командный фильтр представляет <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>собой реализацию, которая обрабатывает команду, мгновенно украшая.

1. Добавьте файл класса с именем `KeyBindingCommandFilter`.

2. Добавьте следующие директивы.

    ```csharp
    using System;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.OLE.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Text.Editor;

    ```

3. Класс под названием KeyBindingCommandFilter должен наследовать от <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.

    ```csharp
    internal class KeyBindingCommandFilter : IOleCommandTarget
    ```

4. Добавьте частные поля для представления текста, следующую команду в цепочке команд и флаг, чтобы представить ли уже добавлен фильтр команды.

    ```csharp
    private IWpfTextView m_textView;
    internal IOleCommandTarget m_nextTarget;
    internal bool m_added;
    internal bool m_adorned;
    ```

5. Добавьте конструктор, который устанавливает текстовое представление.

    ```csharp
    public KeyBindingCommandFilter(IWpfTextView textView)
    {
        m_textView = textView;
        m_adorned = false;
    }
    ```

6. Реализовать `QueryStatus()` метод следующим образом.

    ```csharp
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)
    {
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);
    }
    ```

7. Реализация `Exec()` метода так, чтобы он добавил фиолетовый ящик**+** в представление, если знак плюс () символ набран.

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

## <a name="add-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Добавьте командный фильтр (до версии Visual Studio 2017 15.6)
 Поставщик украшений должен добавить в текстовое представление командный фильтр. В этом примере поставщик <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> реализует возможность прослушивания событий создания текстового представления. Этот поставщик украшений также экспортирует слой украшения, который определяет порядок украшения.

1. В файле KeyBindingTestTextViewCreationListener добавьте следующие директивы:

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

2. Чтобы получить адаптер представления текста, <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>необходимо импортировать .

    ```csharp
    [Import(typeof(IVsEditorAdaptersFactoryService))]
    internal IVsEditorAdaptersFactoryService editorFactory = null;

    ```

3. Измените <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> метод так, `KeyBindingCommandFilter`чтобы он добавил .

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));
    }
    ```

4. Обработчик `AddCommandFilter` получает адаптер представления текста и добавляет командный фильтр.

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

## <a name="implement-a-command-handler-starting-in-visual-studio-2017-version-156"></a>Реализация обработчика команд (начиная с Visual Studio 2017 версия 15.6)

Во-первых, обновите ссылки Nuget проекта, чтобы ссылка на последний API редактора:

1. Нажмите на проект и выберите **пакеты Управления Nuget.**

2. В **Nuget Package Manager**выберите вкладку **Обновления,** выберите флажок **всех пакетов,** а затем выберите **обновление.**

Обработчик команды — <xref:Microsoft.VisualStudio.Commanding.ICommandHandler%601>это реализация, которая обрабатывает команду, мгновенно разносив украшение.

1. Добавьте файл класса с именем `KeyBindingCommandHandler`.

2. Добавьте следующие директивы.

   ```csharp
   using Microsoft.VisualStudio.Commanding;
   using Microsoft.VisualStudio.Text.Editor;
   using Microsoft.VisualStudio.Text.Editor.Commanding.Commands;
   using Microsoft.VisualStudio.Utilities;
   using System.ComponentModel.Composition;
   ```

3. Класс под названием KeyBindingCommandHandler должен наследовать от, `ICommandHandler<TypeCharCommandArgs>`и экспортировать его как: <xref:Microsoft.VisualStudio.Commanding.ICommandHandler>

   ```csharp
   [Export(typeof(ICommandHandler))]
   [ContentType("text")]
   [Name("KeyBindingTest")]
   internal class KeyBindingCommandHandler : ICommandHandler<TypeCharCommandArgs>
   ```

4. Добавьте имя отображения обработчика команд:

   ```csharp
   public string DisplayName => "KeyBindingTest";
   ```

5. Реализовать `GetCommandState()` метод следующим образом. Поскольку обработчик команды обрабатывает команду основного редактора TYPECHAR, он может делегировать включенную команду основному редактору.

   ```csharp
   public CommandState GetCommandState(TypeCharCommandArgs args)
   {
       return CommandState.Unspecified;
   }
   ```

6. Реализация `ExecuteCommand()` метода так, чтобы он добавил фиолетовый ящик**+** в представление, если знак плюс () символ набран.

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

   7. Копирование определения слоя украшения из *KeyBindingTestTextViewCreationListener.cs* файла в *KeyBindingCommandHandler.cs,* а затем удалите *KeyBindingTestTextViewCreationListener.cs* файл:

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

## <a name="make-the-adornment-appear-on-every-line"></a>Сделать украшения появляются на каждой строке

Оригинальное украшение появилось на каждом символе 'a' в текстовом файле. Теперь, когда мы изменили код, чтобы **+** добавить украшение в ответ на **+** символ, он добавляет украшение только на линии, где символ набран. Мы можем изменить код украшения так, чтобы украшение еще раз появляется на каждом 'a'.

В *KeyBindingTest.cs* файле, `CreateVisuals()` измените метод итерировать через все линии в представлении, чтобы украсить символ 'a'.

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

## <a name="build-and-test-the-code"></a>Создание и тестирование кода

1. Создайте решение KeyBindingTest и запустите его в экспериментальном примере.

2. Создайте или откройте текстовый файл. Введите несколько слов, содержащих символ **+** 'a', а затем введите в любом месте в текстовом представлении.

     Фиолетовый квадрат должен отображаться на каждом символе 'a' в файле.
