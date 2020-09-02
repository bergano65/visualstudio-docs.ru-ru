---
title: Пошаговое руководство. Создание основного редактора и регистрация типа файла редактора | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - walkthrough
ms.assetid: 24d2bffd-a35c-46db-8515-fd60b884b7fb
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 14296aa335ba6710d4d9eac8e5338af7463c0aac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687637"
---
# <a name="walkthrough-creating-a-core-editor-and-registering-an-editor-file-type"></a>Пошаговое руководство. Создание основного редактора и регистрация типов файлов в редакторе
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве показано, как создать пакет VSPackage, который запускает [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] основной редактор при загрузке файла с расширением имени файла myext.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Расположения для шаблона проекта пакета Visual Studio  
 Шаблон проекта пакета Visual Studio можно найти в трех разных местах диалогового окна **Создание проекта** .  
  
1. В разделе Visual Basic, "Расширяемость". Язык проекта по умолчанию — Visual Basic.  
  
2. В разделе Visual C#, "Расширяемость". Язык проекта по умолчанию — C#.  
  
3. В разделе "Другие типы проектов", "Расширяемость". Язык проекта по умолчанию — C++.  
  
### <a name="to-create-the-vspackage"></a>Создание пакета VSPackage  
  
- Запустите [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и создайте пакет [!INCLUDE[csprcs](../includes/csprcs-md.md)] VSPackage с именем `MyPackage` , как описано в [разделе Пошаговое руководство. Создание команды меню VSPackage](https://msdn.microsoft.com/d699c149-5d1e-47ff-94c7-e1222af02c32).  
  
### <a name="to-add-the-editor-factory"></a>Добавление фабрики редактора  
  
1. Щелкните правой кнопкой мыши проект **myPackage** , наведите указатель на пункт **Добавить** и выберите **класс**.  
  
2. В диалоговом окне **Добавление нового элемента** убедитесь, что выбран шаблон **класса** , введите `EditorFactory.cs` имя и нажмите кнопку **Добавить** , чтобы добавить класс в проект.  
  
     Файл EditorFactory.cs должен быть автоматически открыт.  
  
3. Сослаться на следующие сборки из кода.  
  
    ```vb  
    Imports System.Runtime.InteropServices  
    Imports Microsoft.VisualStudio  
    Imports Microsoft.VisualStudio.Shell  
    Imports Microsoft.VisualStudio.Shell.Interop  
    Imports Microsoft.VisualStudio.OLE.Interop  
    Imports Microsoft.VisualStudio.TextManager.Interop  
    Imports IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider  
    ```  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio.TextManager.Interop;  
    using IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
  
    ```  
  
4. Добавьте идентификатор GUID в `EditorFactory` класс, добавив `Guid` атрибут непосредственно перед объявлением класса.  
  
     Новый идентификатор GUID можно создать с помощью программы guidgen.exe в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] командной строке или выбрав команду **Создать GUID** в меню **Сервис** . Используемый здесь идентификатор GUID является только примером; не используйте его в проекте.  
  
    ```vb  
    <Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")> _  
    ```  
  
    ```csharp  
    [Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")]   
    ```  
  
5. В определении класса добавьте две частные переменные, которые содержат родительский пакет и поставщик услуг.  
  
    ```vb  
    Class EditorFactory  
        Private parentPackage As Package  
        Private serviceProvider As IOleServiceProvider  
    ```  
  
    ```csharp  
    class EditorFactory  
    {  
        private Package parentPackage;  
        private IOleServiceProvider serviceProvider;  
    }  
  
    ```  
  
6. Добавьте конструктор открытого класса, который принимает один параметр типа <xref:Microsoft.VisualStudio.Shell.Package> :  
  
    ```vb  
    Public Sub New(ByVal parentPackage As Package)  
        Me.parentPackage = parentPackage  
    End Sub  
    ```  
  
    ```csharp  
    public EditorFactory(Package parentPackage)  
    {  
        this.parentPackage = parentPackage;  
    }  
    ```  
  
7. Измените `EditorFactory` объявление класса, чтобы он был производным от <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> интерфейса.  
  
    ```vb  
    Class EditorFactory Implements IVsEditorFacto  
    ```  
  
    ```csharp  
    class EditorFactory : IVsEditorFactory  
  
    ```  
  
8. Щелкните правой кнопкой мыши <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> , выберите команду **реализовать интерфейс**, а затем выберите **реализовать интерфейс явным образом**.  
  
     При этом добавляются четыре метода, которые должны быть реализованы в <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> интерфейсе.  
  
9. Замените содержимое метода `IVsEditorFactory.Close` указанным ниже кодом.  
  
    ```vb  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
10. Замените содержимое объекта `IVsEditorFactory.SetSite` следующим кодом.  
  
    ```vb  
    Me.serviceProvider = psp  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    this.serviceProvider = psp;  
    return VSConstants.S_OK;  
    ```  
  
11. Замените содержимое метода `IVsEditorFactory.MapLogicalView` указанным ниже кодом.  
  
    ```vb  
    Dim retval As Integer = VSConstants.E_NOTIMPL  
    pbstrPhysicalView = Nothing ' We support only one view.  
    If rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer)OrElse _  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary) Then  
        retval = VSConstants.S_OK  
    End If  
    Return retval  
    ```  
  
    ```csharp  
    int retval = VSConstants.E_NOTIMPL;  
    pbstrPhysicalView = null;   // We support only one view.  
    if (rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer) ||  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary))  
    {  
        retval = VSConstants.S_OK;  
    }  
    return retval;  
    ```  
  
12. Замените содержимое метода `IVsEditorFactory.CreateEditorInstance` указанным ниже кодом.  
  
    ```vb  
    Dim retval As Integer = VSConstants.E_FAIL          
  
    ' Initialize these to empty to start with   
    ppunkDocView = IntPtr.Zero  
    ppunkDocData = IntPtr.Zero  
    pbstrEditorCaption = ""  
    pguidCmdUI = Guid.Empty  
    pgrfCDW = 0  
  
    If (grfCreateDoc And (VSConstants.CEF_OPENFILE Or _  
    VSConstants.CEF_SILENT)) = 0 Then  
        Throw New ArgumentException("Only Open or Silent is valid")  
    End If  
    If punkDocDataExisting <> IntPtr.Zero Then  
        Return VSConstants.VS_E_INCOMPATIBLEDOCDATA  
    End If  
  
    ' Instantiate a text buffer of type VsTextBuffer.   
    ' Note: we only need an IUnknown (object) interface for   
    ' this invocation.   
    Dim clsidTextBuffer As Guid = GetType(VsTextBufferClass).GUID  
    Dim iidTextBuffer As Guid = VSConstants.IID_IUnknown  
    Dim pTextBuffer As Object = pTextBuffer = _  
    parentPackage.CreateInstance(clsidTextBuffer, iidTextBuffer, _  
    GetType(Object))  
  
    If Not pTextBuffer Is Nothing Then  
        ' "Site" the text buffer with the service provider we were   
        ' provided.   
        Dim textBufferSite As IObjectWithSite = TryCast(pTextBuffer, _  
        IObjectWithSite)  
        If Not textBufferSite Is Nothing Then  
            textBufferSite.SetSite(Me.serviceProvider)  
        End If  
  
        ' Instantiate a code window of type IVsCodeWindow.   
        Dim clsidCodeWindow As Guid = GetType(VsCodeWindowClass).GUID  
        Dim iidCodeWindow As Guid = GetType(IVsCodeWindow).GUID  
        Dim pCodeWindow As IVsCodeWindow = _  
        CType(Me.parentPackage.CreateInstance(clsidCodeWindow, _  
        iidCodeWindow, GetType(IVsCodeWindow)), IVsCodeWindow)  
        If Not pCodeWindow Is Nothing Then  
            ' Give the text buffer to the code window.   
            ' We are giving up ownership of the text buffer!   
            pCodeWindow.SetBuffer(CType(pTextBuffer, IVsTextLines))  
  
            ' Now tell the caller about all this new stuff   
            ' that has been created.   
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow)  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer)  
  
            ' Specify the command UI to use so keypresses are   
            ' automatically dealt with.   
            pguidCmdUI = VSConstants.GUID_TextEditorFactory  
  
            ' This caption is appended to the filename and   
            ' lets us know our invocation of the core editor   
            ' is up and running.   
            pbstrEditorCaption = " [MyPackage]"  
  
            retval = VSConstants.S_OK  
        End If  
    End If  
    Return retval  
    ```  
  
    ```csharp  
    int retval = VSConstants.E_FAIL;  
  
    // Initialize these to empty to start with  
    ppunkDocView       = IntPtr.Zero;  
    ppunkDocData       = IntPtr.Zero;  
    pbstrEditorCaption = "";  
    pguidCmdUI         = Guid.Empty;   
    pgrfCDW            = 0;  
  
    if ((grfCreateDoc & (VSConstants.CEF_OPENFILE |   
          VSConstants.CEF_SILENT)) == 0)  
    {   
        throw new ArgumentException("Only Open or Silent is valid");  
    }  
    if (punkDocDataExisting != IntPtr.Zero)  
    {  
        return VSConstants.VS_E_INCOMPATIBLEDOCDATA;  
    }  
  
    // Instantiate a text buffer of type VsTextBuffer.  
    // Note: we only need an IUnknown (object) interface for   
    // this invocation.  
    Guid clsidTextBuffer = typeof(VsTextBufferClass).GUID;  
    Guid iidTextBuffer   = VSConstants.IID_IUnknown;  
    object pTextBuffer   = pTextBuffer = parentPackage.CreateInstance(  
          ref clsidTextBuffer,  
          ref iidTextBuffer,  
          typeof(object));  
  
    if (pTextBuffer != null)  
    {  
        // "Site" the text buffer with the service provider we were  
        // provided.  
        IObjectWithSite textBufferSite = pTextBuffer as IObjectWithSite;  
        if (textBufferSite != null)  
        {  
            textBufferSite.SetSite(this.serviceProvider);  
        }  
  
        // Instantiate a code window of type IVsCodeWindow.  
        Guid clsidCodeWindow = typeof(VsCodeWindowClass).GUID;  
        Guid iidCodeWindow   = typeof(IVsCodeWindow).GUID;  
        IVsCodeWindow pCodeWindow =  
        (IVsCodeWindow)this.parentPackage.CreateInstance(   
              ref clsidCodeWindow,  
              ref iidCodeWindow,  
              typeof(IVsCodeWindow));  
        if (pCodeWindow != null)  
        {  
            // Give the text buffer to the code window.  
            // We are giving up ownership of the text buffer!  
            pCodeWindow.SetBuffer((IVsTextLines)pTextBuffer);  
  
            // Now tell the caller about all this new stuff   
            // that has been created.  
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow);  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer);  
  
            // Specify the command UI to use so keypresses are   
            // automatically dealt with.  
            pguidCmdUI = VSConstants.GUID_TextEditorFactory;  
  
            // This caption is appended to the filename and  
            // lets us know our invocation of the core editor   
            // is up and running.  
            pbstrEditorCaption = " [MyPackage]";  
  
            retval = VSConstants.S_OK;  
        }   
    }   
    return retval;   
    ```  
  
13. Скомпилируйте проект и убедитесь в отсутствии ошибок.  
  
### <a name="to-register-the-editor-factory"></a>Регистрация фабрики редактора  
  
1. В **Обозреватель решений**дважды щелкните файл Resources. resx, чтобы открыть его в таблице строк, в которой выбрана запись **строка1** .  
  
2. Измените имя идентификатора на `IDS_EDITORNAME` , а текст — на **myPackage Editor (редактор** текста). Эта строка будет отображаться в качестве имени редактора.  
  
3. Откройте файл VSPackage. resx и добавьте новую строку, присвойте ей имя **101** и значение `IDS_EDITORNAME` . Это предоставляет пакету идентификатор ресурса для доступа к только что созданной строке.  
  
    > [!NOTE]
    > Если файл VSPackage. resx содержит другую строку, для которой `name` атрибуту присвоено значение **101**, замените еще одно уникальное числовое значение, приведенное здесь, и выполните следующие действия.  
  
4. В **Обозреватель решений**откройте файл MyPackagePackage.cs.  
  
     Это основной файл пакета.  
  
5. Добавьте следующие атрибуты пользователя непосредственно перед `Guid` атрибутом.  
  
    ```vb  
    <ProvideEditorFactoryAttribute(GetType(EditorFactory), 101)> _  
    <ProvideEditorExtensionAttribute(GetType(EditorFactory), _  
          ".myext", 32, NameResourceID:=101 )> _  
    ```  
  
    ```csharp  
    [ProvideEditorFactory(typeof(EditorFactory), 101)]  
    [ProvideEditorExtension(typeof(EditorFactory),   
          ".myext", 32, NameResourceID = 101)]   
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute>Атрибут связывает расширение файла myext с фабрикой редактора, чтобы каждый раз при загрузке файла с этим расширением была вызвана Фабрика редактора.  
  
6. Добавьте в класс закрытую переменную `MyPackage` непосредственно перед конструктором и присвойте ей тип `EditorFactory` .  
  
    ```vb  
    Private editorFactory As EditorFactory  
    ```  
  
    ```csharp  
    private EditorFactory editorFactory;  
    ```  
  
7. Найдите `Initialize` метод (может потребоваться открыть `Package Members` скрытую область) и добавьте следующий код после вызова `base.Initialize()` .  
  
    ```vb  
    'Create our editor factory and register it.   
    Me.editorFactory = New EditorFactory(Me)  
    MyBase.RegisterEditorFactory(Me.editorFactory)  
    ```  
  
    ```csharp  
    // Create our editor factory and register it.  
    this.editorFactory = new EditorFactory(this);  
    base.RegisterEditorFactory(this.editorFactory);  
  
    ```  
  
8. Скомпилируйте программу и убедитесь в отсутствии ошибок.  
  
     Этот шаг регистрирует фабрику редактора в экспериментальном кусте реестра для [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . При появлении запроса на переопределение файла resource. h нажмите кнопку **ОК**.  
  
9. Создайте пример файла с именем TextFile1. myext.  
  
10. Нажмите клавишу **F5** , чтобы открыть экземпляр экспериментального [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
11. В экспериментальном режиме [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] в меню **файл** наведите указатель мыши на пункт **Открыть** и выберите **файл**.  
  
12. Найдите TextFile1. myext и нажмите кнопку **Открыть**.  
  
     Теперь файл должен быть загружен.  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Основной редактор обрабатывает широкий спектр текстовых типов файлов и тесно взаимодействует с языковыми службами для предоставления обширного набора таких функций, как выделение синтаксиса, сопоставление фигурных скобок и списки завершения слов и элементов IntelliSense. При работе с текстовыми файлами можно использовать базовый редактор вместе с пользовательской языковой службой, которая поддерживает файлы определенного типа.  
  
 Пакет VSPackage может вызывать [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] редактор ядра, предоставляя фабрику редактора. Эта фабрика редактора используется в любой момент загрузки связанного с ним файла. Если файл является частью проекта, основной редактор вызывается автоматически, если он не переопределен пакетом VSPackage. Однако если файл загружен вне проекта, базовый редактор должен быть явно вызван пакетом VSPackage.  
  
 Дополнительные сведения о основном редакторе см. в разделе, посвященном основному [редактору](../extensibility/inside-the-core-editor.md).  
  
## <a name="see-also"></a>См. также:  
 [Внутри основного редактора](../extensibility/inside-the-core-editor.md)   
 [Создание экземпляра основного редактора с помощью API прежних версий](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)
