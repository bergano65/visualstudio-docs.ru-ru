---
title: Как зарегистрировать типы файлов редактора | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register file types
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8d22e61d88b5f6e3959a369f6957efbc824384b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204116"
---
# <a name="how-to-register-editor-file-types"></a>Практическое руководство. Регистрация типов файлов в редакторе
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Самый простой способ зарегистрировать типы файлов редактора — использовать атрибуты регистрации, предоставленные в составе [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] классов MPF Framework. При реализации пакета в машинном коде [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] можно также написать сценарий реестра, регистрирующий редактор и связанные с ним расширения.  
  
## <a name="registration-using-mpf-classes"></a>Регистрация с помощью классов MPF  
  
#### <a name="to-register-editor-file-types-using-mpf-classes"></a>Регистрация типов файлов редактора с помощью классов MPF  
  
1. Предоставьте <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> класс с соответствующими параметрами для редактора в классе VSPackage.  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     Где ". Пример "— это расширение, зарегистрированное для этого редактора, а" 32 "— уровень приоритета.  
  
     `projectGuid`— Это GUID для прочих типов файлов, определенных в <xref:Microsoft.VisualStudio.VSConstants.CLSID.MiscellaneousFilesProject_guid> . Предоставляется тип "Прочие файлы", чтобы полученный файл не был частью процесса сборки.  
  
     `TemplateDir` представляет папку, содержащую файлы шаблонов, которые включены в пример управляемого базового редактора.  
  
     `NameResourceID` определяется в файле resources. h проекта Басицедиторуи и идентифицирует редактор как "Мой редактор".  
  
2. Переопределите метод <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.  
  
     В реализации <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> метода вызовите <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> метод и передайте экземпляр фабрики редактора, как показано ниже.  
  
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
  
     Этот шаг регистрирует как фабрику редактора, так и расширения файлов редактора.  
  
3. Отмените регистрацию фабрик редактора.  
  
     При удалении VSPackage фабрики редактора автоматически отменяют регистрацию. Если объект фабрики редактора реализует <xref:System.IDisposable> интерфейс, его `Dispose` метод вызывается после отмены регистрации фабрики в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="registration-using-a-registry-script"></a>Регистрация с помощью скрипта реестра  
 Регистрация фабрик редактора и типов файлов в собственном [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] режиме выполняется с помощью скрипта реестра для записи в реестр Windows, как показано ниже.  
  
#### <a name="to-register-editor-file-types-using-a-registry-script"></a>Регистрация типов файлов редактора с помощью скрипта реестра  
  
1. В скрипте реестра определите фабрику редактора и строку GUID фабрики редактора, как показано в `GUID_BscEditorFactory` разделе следующего скрипта реестра. Кроме того, определите расширение и приоритет расширения редактора:  
  
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
  
     Расширение файла редактора в этом примере определяется как ". RTF", а его приоритет — "50". Строки GUID определяются в файле Resource. h образца проекта Бсцедит.  
  
2. Зарегистрируйте пакет VSPackage.  
  
3. Зарегистрируйте фабрику редактора.  
  
     Фабрика редактора зарегистрирована в <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> реализации.  
  
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
  
     Строки GUID определяются в файле Resource. h проекта Бсцедит.
