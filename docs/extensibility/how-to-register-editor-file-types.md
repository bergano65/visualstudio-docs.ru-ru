---
title: "Практическое руководство: регистрация редактор типов файлов | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] прежних версий - Регистрация типов файлов"
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Практическое руководство: регистрация редактор типов файлов
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Самый простой способ регистрации редактора типов файлов с помощью атрибутов регистрации, предоставляемых как часть [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] управляемые классы платформы пакета \(MPF\).  Если реализуется пакет в собственном [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)]можно также написать скрипт реестра, регистрирующий редактор и соответствующие расширения.  
  
## Регистрация с помощью классов MPF  
  
#### Регистрация редактора типов файлов с помощью классов MPF  
  
1.  Обеспечьте <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> класс с соответствующими параметрами для редактора в классе в VSPackage.  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     Где ". Образец" расширение, зарегистрированного для данного редактора и "32" свой уровень приоритета.  
  
     `projectGuid` идентификатор GUID типов произвольного файла, указанное в пределах  <xref:Microsoft.VisualStudio.VSConstants.CLSID_MiscellaneousFilesProject>.  Тип произвольного файла указан, поэтому результирующий файл не будет перейти быть частью процесса построения.  
  
     `TemplateDir` представляет папку, содержащую файлы шаблона, включенных в управляемый простой пример редактора.  
  
     `NameResourceID` определяет Resources.h в файле проекта BasicEditorUI и задает редактор, например "my" редактор.  
  
2.  Переопределите метод <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.  
  
     В реализации <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> вызывает метод  <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> метод и передает экземпляр фабрики редактора, как показано ниже.  
  
    ```  
    protected override void Initialize()  
    {  
        Trace.WriteLine (string.Format(CultureInfo.CurrentCulture,   
        "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
           //Create Editor Factory  
        editorFactory = new EditorFactory(this);  
        base.RegisterEditorFactory(editorFactory);  
    }  
    ```  
  
     Этот шаг и регистрирует фабрику редактора и расширения файлов редактора.  
  
3.  Отмены регистрации фабрики редактора.  
  
     Фабрики редактора автоматически удалены, когда VSPackage удалено.  Если объект фабрики редактора реализует <xref:System.IDisposable>, интерфейс  `Dispose` метод вызывается после того, как производство с незарегистрированно  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Регистрация использование скрипт реестра  
 Регистрация фабрики редактора в собственном и типы файлов [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)] делает использование скрипт реестра для записи к окнам реестр, как показано в следующим.  
  
#### Зарегистрировать типы файлов скриптов с помощью редактора реестра  
  
1.  В скрипте реестра, укажите фабрику редактора и строка GUID фабрики редактора, как показано в `GUID_BscEditorFactory` раздел следующего сценария реестра.  Также укажите расширение и приоритет расширения редактора.  
  
    ```  
  
                NoRemove Editors     {         %GUID_BscEditorFactory% = s 'RTF Editor'         {             val Package = s '%CLSID_Package%'             val DisplayName = s 'An RTF Editor'             val ExcludeDefTextEditor = d 1             val AcceptBinaryFiles = d 0  
  
            LogicalViews  
            {  
                val %LOGVIEWID_TextView% = s ''  
            }  
  
            OpenWithEntries  
            {  
            }  
  
            Extensions             {                 val rtf = d 50             }  
        }  
    }  
    ```  
  
     Расширение файла редактора в этом примере определяется как ".rtf" и ее приоритет "50".  Строки GUID определяются в файле Resource.h проекта образца BscEdit.  
  
2.  Зарегистрируйте VSPackage.  
  
3.  Зарегистрируйте фабрику редактора.  
  
     Фабрика редактора зарегистрировано в <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> реализация.  
  
    ```  
    // create editor factory.  
    if (m_srpEdFact == NULL)   
    {  
        CComObject<CBscEditorFactory> *pEdFact = new CComObject<CBscEditorFactory>;  
        if (NULL == pEdFact)  
          return E_OUTOFMEMORY;  
  
        if (!pEdFact->FInit(this))  
          return E_UNEXPECTED;  
  
        m_srpEdFact = (IVsEditorFactory *) pEdFact;    // Note: assignment to a smart pointer does an AddRef()  
    }  
    // Query service for IVsRegisterEditors, register the editor factory  
    CComPtr<IVsRegisterEditors> srpRegEd;  
    if ((SUCCEEDED(m_srpPkgSiteSP->QueryService(SID_SVsRegisterEditors, IID_IVsRegisterEditors,(void **)&srpRegEd ))) && (srpRegEd != NULL))  
      {  
        ATLTRACE(TEXT(">> CVsPackage, registering editor factory.\n"));  
          if (FAILED(srpRegEd->RegisterEditor(GUID_BscEditorFactory,  
                      m_srpEdFact, &m_dwEditorCookie)))   
          {  
             ATLTRACE(TEXT(">> CVsPackage, RegisterEditor() failed.\n"));  
            return E_FAIL;  
          }  
      }  
        return S_OK;  
    }  
    ```  
  
     Строки GUID определяются в файле Resource.h проекта BscEdit.