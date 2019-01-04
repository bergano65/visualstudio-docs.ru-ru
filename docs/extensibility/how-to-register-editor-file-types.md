---
title: Как выполнить Регистрация типов файлов в редакторе | Документация Майкрософт
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register file types
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 23a3277a550b17371b4d8315da64eb7507c8c863
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53857806"
---
# <a name="how-to-register-editor-file-types"></a>Как выполнить Регистрация типов файлов в редакторе
Самый простой способ зарегистрировать редактор типов файлов — с помощью регистрации атрибутов, предоставляемых в составе [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] классы managed package framework (MPF). При реализации пакета в машинный код [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], можно также написать скрипт реестра, который регистрирует редактора и связанные расширения.

## <a name="registration-using-mpf-classes"></a>Регистрацию с помощью классы MPF

### <a name="to-register-editor-file-types-using-mpf-classes"></a>Чтобы зарегистрировать редактор типов файлов, используя классы MPF

1. Укажите <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> класс с необходимыми параметрами для редактора в классе вашего VSPackage.

   ```
   [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,
        ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",
        TemplateDir = "..\\..\\Templates",
        NameResourceID = 106)]
   ```

    Где *. Пример* — расширение, которое регистрируется для этого редактора, а «32» — уровень приоритета.

    `projectGuid` — Это GUID для произвольного файла типов, определенных в <xref:Microsoft.VisualStudio.VSConstants.CLSID.MiscellaneousFilesProject_guid>. Тип произвольного файла, который предоставляется, чтобы полученный файл не будет входить в состав процесса построения.

    *TemplateDir* представляет папку, содержащую файлы шаблонов, которые входят в состав образца управляемых простой редактор.

    `NameResourceID` определяется в *Resources.h* BasicEditorUI проекта и определяющее редактор редактором «My».

2. Переопределите метод <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> .

    В реализации <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> мы вызываем метод <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> метод и передайте экземпляр фабрикой редактора, как показано ниже.

   ```csharp
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

3. Отмена регистрации фабрики редакторов.

    Фабрики редакторов отменяется автоматически, при удалении пакета VSPackage. Если объект фабрики редактора реализует <xref:System.IDisposable> интерфейс, его `Dispose` метод вызывается после фабрики были его регистрацию с помощью [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="registration-using-a-registry-script"></a>Регистрация с помощью скрипта реестра
 Регистрация фабрик редактора и типы файлов в машинный код [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] осуществляется с помощью скрипта реестра для записи в реестре windows, как показано ниже.

### <a name="to-register-editor-file-types-using-a-registry-script"></a>Чтобы зарегистрировать редактор типов файлов, с помощью скрипта реестра

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

     Расширение редактора в этом примере определяется как *.rtf* и его приоритет равен «50». Определенные строки GUID в *Resource.h* файл BscEdit примера проекта.

2.  Регистрация пакета VSPackage.

3.  Регистрация фабрики редактора.

     Фабрика редакторов регистрируется в <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> реализации.

    ```cpp
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

     Определенные строки GUID в *Resource.h* BscEdit проекта.