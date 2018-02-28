---
title: "Как: регистрация типов файлов редактор | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register file types
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 679223f21bd839a8d94b299319ad22c6701bc407
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-register-editor-file-types"></a>Как: регистрация редактор типов файлов
Самый простой способ регистрации редактора типы файлов — с помощью регистрации атрибутов, предоставляемых в составе [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] классы managed package framework (MPF). При реализации пакета в собственном формате [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], также можно написать скрипт реестра, который регистрирует редактора и связанные с ним расширения.  
  
## <a name="registration-using-mpf-classes"></a>Регистрация с помощью MPF классов  
  
#### <a name="to-register-editor-file-types-using-mpf-classes"></a>Для регистрации редактора типов файлов, используя классы MPF  
  
1.  Укажите <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> класса с соответствующими параметрами для редактора в классе вашего VSPackage.  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     Где «. Образец» расширения, зарегистрированные для этого редактора, который «32» ее уровень приоритета.  
  
     `projectGuid` — Это GUID для произвольного файла, типы, определенные в <xref:Microsoft.VisualStudio.VSConstants.CLSID_MiscellaneousFilesProject>. Тип произвольного файла, который предоставляется, чтобы получившийся файл не будет входить в состав процесса построения.  
  
     `TemplateDir`Представляет папку, содержащую файлы шаблонов, включенные в образец управляемого базового редактора.  
  
     `NameResourceID`определяется в файле Resources.h BasicEditorUI проекта и выявляет редактора как «Мой редактор».  
  
2.  Переопределите метод <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.  
  
     В реализации <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> метод, вызовите <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> метод и передайте экземпляр фабрики редактора, как показано ниже.  
  
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
  
     Этот шаг регистрирует фабрики редакторов и расширения файлов для редактора.  
  
3.  Отмена регистрации фабрики редактора.  
  
     Редактор фабрики отменяется автоматически, при удалении пакета VSPackage. Если объект фабрики редактора реализует <xref:System.IDisposable> интерфейса, его `Dispose` метод вызывается после фабрику отменена с [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="registration-using-a-registry-script"></a>Регистрация с помощью скрипта реестра  
 Регистрация фабрики редакторов и типов файлов в основном [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] осуществляется с помощью скрипта реестра для записи в реестре windows, как показано ниже.  
  
#### <a name="to-register-editor-file-types-using-a-registry-script"></a>Чтобы зарегистрировать типы файлов редактор, с помощью скрипта реестра  
  
1.  В скрипте реестра определить фабрику редактора и строка GUID фабрики редакторов `GUID_BscEditorFactory` раздел следующий скрипт реестра. Кроме того можно определите расширение и приоритет расширения редактора:  
  
    ```  
  
          NoRemove Editors     {         %GUID_BscEditorFactory% = s 'RTF Editor'         {             val Package = s '%CLSID_Package%'             val DisplayName = s 'An RTF Editor'             val ExcludeDefTextEditor = d 1             val AcceptBinaryFiles = d 0  
  
            LogicalViews  
            {  
                val %LOGVIEWID_TextView% = s ''  
            }  
  
            OpenWithEntries  
            {  
            }  
  
            Extensions            {                val rtf = d 50            }  
        }  
    }  
    ```  
  
     Расширение редактора в этом примере определяется как «.rtf» и ее приоритет — «50». Строки GUID определены в файле Resource.h BscEdit образца проекта.  
  
2.  Регистрация VSPackage.  
  
3.  Регистрация фабрики редакторов.  
  
     Фабрика редакторов регистрируется в <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> реализации.  
  
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
  
     В файле Resource.h BscEdit проекта определяются строки GUID.