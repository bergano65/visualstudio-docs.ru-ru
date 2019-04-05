---
title: Практическое руководство. Регистрация типов файлов в редакторе | Документация Майкрософт
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
ms.openlocfilehash: 697565600ef37024abde3acd8f2092c690f31e32
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58994293"
---
# <a name="how-to-register-editor-file-types"></a>Практическое руководство. Регистрация типов файлов в редакторе
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Самый простой способ зарегистрировать редактор типов файлов — с помощью регистрации атрибутов, предоставляемых в составе [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] классы managed package framework (MPF). При реализации пакета в машинный код [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], можно также написать скрипт реестра, который регистрирует редактора и связанные расширения.  
  
## <a name="registration-using-mpf-classes"></a>Регистрацию с помощью классы MPF  
  
#### <a name="to-register-editor-file-types-using-mpf-classes"></a>Чтобы зарегистрировать редактор типов файлов, используя классы MPF  
  
1.  Укажите <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> класс с необходимыми параметрами для редактора в классе вашего VSPackage.  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     Где «. Пример» является модуль, зарегистрированный для этого редактора, которая «32» ее уровень приоритета.  
  
     `projectGuid` — Это GUID для произвольного файла типов, определенных в <xref:Microsoft.VisualStudio.VSConstants.CLSID.MiscellaneousFilesProject_guid>. Тип произвольного файла, который предоставляется, чтобы полученный файл не будет входить в состав процесса построения.  
  
     `TemplateDir` Представляет папку, содержащую файлы шаблонов, которые входят в состав образца управляемых простой редактор.  
  
     `NameResourceID` определяется в файле Resources.h BasicEditorUI проекта и определяющее редактор редактором «My».  
  
2.  Переопределите метод <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> .  
  
     В реализации <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> мы вызываем метод <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> метод и передайте экземпляр фабрикой редактора, как показано ниже.  
  
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
  
     Этот шаг регистрирует фабрику редактора и файл расширения редактора.  
  
3.  Отмена регистрации фабрики редакторов.  
  
     Фабрики редакторов отменяется автоматически, при удалении пакета VSPackage. Если объект фабрики редактора реализует <xref:System.IDisposable> интерфейс, его `Dispose` метод вызывается после фабрики были его регистрацию с помощью [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="registration-using-a-registry-script"></a>Регистрация с помощью скрипта реестра  
 Регистрация фабрик редактора и типы файлов в машинный код [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] осуществляется с помощью скрипта реестра для записи в реестре windows, как показано ниже.  
  
#### <a name="to-register-editor-file-types-using-a-registry-script"></a>Чтобы зарегистрировать редактор типов файлов, с помощью скрипта реестра  
  
1.  В скрипте реестра определить фабрику редактора и строка идентификатора GUID фабрики редактора как показано в `GUID_BscEditorFactory` части следующий скрипт реестра. Кроме того определите, расширение и приоритет расширения редактора.  
  
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
  
     Расширение редактора в этом примере определяется как «.rtf» и его приоритет равен «50». Строки GUID определяются в файле Resource.h BscEdit примера проекта.  
  
2.  Регистрация пакета VSPackage.  
  
3.  Регистрация фабрики редактора.  
  
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
  
     Строки GUID определяются в файле Resource.h BscEdit проекта.
