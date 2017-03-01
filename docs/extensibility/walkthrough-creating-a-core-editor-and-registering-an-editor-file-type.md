---
title: "Создание базового редактора и регистрация файла тип редактора | Документы Microsoft»"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - walkthrough
ms.assetid: 24d2bffd-a35c-46db-8515-fd60b884b7fb
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
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: 7bde276b0d53793f57266c13c5ccf63583f7aacf
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-creating-a-core-editor-and-registering-an-editor-file-type"></a>Пошаговое руководство: Создание базового редактора и регистрация файла тип редактора
В этом пошаговом руководстве демонстрируется создание VSPackage, который запускает [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] базового редактора при создании файла с расширением имени файла .myext загружается.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Расположения для шаблона проекта пакета Visual Studio  
 Шаблон проекта пакета Visual Studio можно найти в трех разных местах диалогового окна **Создание проекта** .  
  
1.  В разделе Visual Basic, "Расширяемость". Язык проекта по умолчанию — Visual Basic.  
  
2.  В разделе Visual C#, "Расширяемость". Язык проекта по умолчанию — C#.  
  
3.  В разделе "Другие типы проектов", "Расширяемость". Язык проекта по умолчанию — C++.  
  
### <a name="to-create-the-vspackage"></a>Чтобы создать VSPackage  
  
-   Запустите [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и создать [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] VSPackage с именем `MyPackage`, как описано в [Пошаговое руководство: создание VSPackage команды меню](http://msdn.microsoft.com/en-us/d699c149-5d1e-47ff-94c7-e1222af02c32).  
  
### <a name="to-add-the-editor-factory"></a>Чтобы добавить фабрики редактора  
  
1.  Щелкните правой кнопкой мыши **MyPackage** проект, выберите пункт **добавить** и нажмите кнопку **класса**.  
  
2.  В **Добавление нового элемента** диалогового окна убедитесь, что **класса** выбран шаблон, тип `EditorFactory.cs` имя, а затем нажмите кнопку **добавить** для добавления класса в проект.  
  
     Файл EditorFactory.cs должен открываться автоматически.  
  
3.  Ссылки на следующие сборки в коде.  
  
    ```vb#  
    Imports System.Runtime.InteropServices  
    Imports Microsoft.VisualStudio  
    Imports Microsoft.VisualStudio.Shell  
    Imports Microsoft.VisualStudio.Shell.Interop  
    Imports Microsoft.VisualStudio.OLE.Interop  
    Imports Microsoft.VisualStudio.TextManager.Interop  
    Imports IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider  
    ```  
  
    ```c#  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio.TextManager.Interop;  
    using IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
  
    ```  
  
4.  Добавьте идентификатор GUID, `EditorFactory` класс, добавив `Guid` атрибут непосредственно перед объявлением класса.  
  
     Можно создать новый идентификатор GUID с помощью программы guidgen.exe в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] или в командной строке, щелкнув **создать GUID** на **средства** меню. Идентификатор GUID, используемый здесь указано только для примера; не используйте его в проект.  
  
    ```vb#  
    <Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")> _  
    ```  
  
    ```c#  
    [Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")]   
    ```  
  
5.  В определении класса добавьте две закрытых переменных родительского пакета и поставщика услуг.  
  
    ```vb#  
    Class EditorFactory  
        Private parentPackage As Package  
        Private serviceProvider As IOleServiceProvider  
    ```  
  
    ```c#  
    class EditorFactory  
    {  
        private Package parentPackage;  
        private IOleServiceProvider serviceProvider;  
    }  
  
    ```  
  
6.  Добавьте открытый класс конструктор, который принимает один параметр типа <xref:Microsoft.VisualStudio.Shell.Package>:</xref:Microsoft.VisualStudio.Shell.Package>  
  
    ```vb#  
    Public Sub New(ByVal parentPackage As Package)  
        Me.parentPackage = parentPackage  
    End Sub  
    ```  
  
    ```c#  
    public EditorFactory(Package parentPackage)  
    {  
        this.parentPackage = parentPackage;  
    }  
    ```  
  
7.  Изменить `EditorFactory` объявление для наследования от класса <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>интерфейса.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>  
  
    ```vb#  
    Class EditorFactory Implements IVsEditorFacto  
    ```  
  
    ```c#  
    class EditorFactory : IVsEditorFactory  
  
    ```  
  
8.  Щелкните правой кнопкой мыши <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>, нажмите кнопку **реализовать интерфейс**, а затем нажмите кнопку **реализовать интерфейс явно**.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>  
  
     Это добавляет четыре метода, которые должны быть реализованы в <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>интерфейса.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>  
  
9. Замените содержимое метода `IVsEditorFactory.Close` следующим кодом.  
  
    ```vb#  
    Return VSConstants.S_OK  
    ```  
  
    ```c#  
    return VSConstants.S_OK;  
    ```  
  
10. Замените содержимое файла `IVsEditorFactory.SetSite` с помощью следующего кода.  
  
    ```vb#  
    Me.serviceProvider = psp  
    Return VSConstants.S_OK  
    ```  
  
    ```c#  
    this.serviceProvider = psp;  
    return VSConstants.S_OK;  
    ```  
  
11. Замените содержимое метода `IVsEditorFactory.MapLogicalView` следующим кодом.  
  
    ```vb#  
    Dim retval As Integer = VSConstants.E_NOTIMPL  
    pbstrPhysicalView = Nothing ' We support only one view.  
    If rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer)OrElse _  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary) Then  
        retval = VSConstants.S_OK  
    End If  
    Return retval  
    ```  
  
    ```c#  
    int retval = VSConstants.E_NOTIMPL;  
    pbstrPhysicalView = null;   // We support only one view.  
    if (rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer) ||  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary))  
    {  
        retval = VSConstants.S_OK;  
    }  
    return retval;  
    ```  
  
12. Замените содержимое метода `IVsEditorFactory.CreateEditorInstance` следующим кодом.  
  
    ```vb#  
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
  
    ```c#  
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
  
13. Скомпилируйте проект и убедитесь, что ошибок нет.  
  
### <a name="to-register-the-editor-factory"></a>Чтобы зарегистрировать фабрику редактора  
  
1.  В **обозревателе решений**, дважды щелкните файл Resources.resx, чтобы открыть его в таблицу строки, в котором операция **строка1** выбранных.  
  
2.  Измените имя идентификатора, `IDS_EDITORNAME` и текст, **MyPackage редактора.** Эта строка будет отображаться как имя редактора.  
  
3.  Откройте файл VSPackage.resx и добавьте новую строку, задайте имя **101** и значение для `IDS_EDITORNAME`. Это обеспечивает пакет с Идентификатором ресурса для доступа к строке, которую вы только что создали.  
  
    > [!NOTE]
    >  Если файл VSPackage.resx содержит другой строкой, которую `name` атрибута **101**, подставьте другое уникальное числовое значение, здесь и далее.  
  
4.  В **обозревателе**, откройте файл MyPackagePackage.cs.  
  
     Это файл основного пакета.  
  
5.  Добавьте следующие атрибуты пользователя непосредственно перед `Guid` атрибута.  
  
    ```vb#  
    <ProvideEditorFactoryAttribute(GetType(EditorFactory), 101)> _  
    <ProvideEditorExtensionAttribute(GetType(EditorFactory), _  
          ".myext", 32, NameResourceID:=101 )> _  
    ```  
  
    ```c#  
    [ProvideEditorFactory(typeof(EditorFactory), 101)]  
    [ProvideEditorExtension(typeof(EditorFactory),   
          ".myext", 32, NameResourceID = 101)]   
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute>Атрибут связывает расширение файла .myext с фабрики редактора, чтобы файл, содержащий вызывается фабрики редактора, модуль загружается в любое время.</xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute>  
  
6.  Добавьте частную переменную для `MyPackage` класса непосредственно перед конструктором и присвойте ему тип `EditorFactory`.  
  
    ```vb#  
    Private editorFactory As EditorFactory  
    ```  
  
    ```c#  
    private EditorFactory editorFactory;  
    ```  
  
7.  Найти `Initialize` метод (может потребоваться открыть `Package Members` скрытой области) и добавьте следующий код после вызова `base.Initialize()`.  
  
    ```vb#  
    'Create our editor factory and register it.   
    Me.editorFactory = New EditorFactory(Me)  
    MyBase.RegisterEditorFactory(Me.editorFactory)  
    ```  
  
    ```c#  
    // Create our editor factory and register it.  
    this.editorFactory = new EditorFactory(this);  
    base.RegisterEditorFactory(this.editorFactory);  
  
    ```  
  
8.  Скомпилируйте программу и убедитесь в отсутствии ошибок.  
  
     Этот шаг регистрирует фабрику редактора в экспериментальном реестра для [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. При появлении переопределения в файле resource.h, щелкните **ОК**.  
  
9. Создание образца файла с именем TextFile1.myext.  
  
10. Нажмите клавишу **F5** в экспериментальном экземпляре откройте [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
11. В экспериментальном экземпляре [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]на **файл** наведите указатель мыши на **откройте** и нажмите кнопку **файл**.  
  
12. Найти TextFile1.myext и нажмите кнопку **откройте**.  
  
     Теперь удается загрузить файл.  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Базового редактора обрабатывает широкий спектр типов текстовых файлов и тесно сотрудничает с языковые службы, которые предоставляют широкий набор функций, например, выделение синтаксиса, парные фигурные скобки и списки завершение слов и член завершения IntelliSense. При работе с файлами на основе текста, можно использовать редактор core совместно со службой пользовательский язык, поддерживающий на определенные типы файлов.  
  
 Можно вызвать VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] базового редактора, указав фабрику редактора. Фабрика этот редактор используется каждый раз, когда загружается файл, связанный с ним. Если файл является частью проекта, затем базового редактора вызывается автоматически при отсутствии иных VSPackage. Тем не менее если файл загружается за пределами проекта, затем базового редактора должен явно вызываться VSPackage.  
  
 Дополнительные сведения о редакторе core см [внутри базового редактора](../extensibility/inside-the-core-editor.md).  
  
## <a name="see-also"></a>См. также  
 [В редакторе ядра](../extensibility/inside-the-core-editor.md)   
 [Создание базового редактора с помощью API прежних версий](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)
