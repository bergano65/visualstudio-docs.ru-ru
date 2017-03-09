---
title: "Практическое руководство. Использование сборок взаимодействия для импорта параметров | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "параметры IDE, экспорт с помощью сборок взаимодействия"
  - "IDE, импорт параметров с помощью сборок взаимодействия"
  - "параметры пользователя [Visual Studio SDK], экспорт с помощью сборок взаимодействия"
ms.assetid: 8a43dbe2-fdc0-471b-8235-3f489b77db0f
caps.latest.revision: 26
caps.handback.revision: 26
manager: "douge"
---
# Практическое руководство. Использование сборок взаимодействия для импорта параметров
Пакет VSPackage может импортировать параметры из интегрированной среды разработки \(IDE\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. IDE использует реализацию VSPackage интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> для определения, как извлечь конфигурацию VSPackage.  
  
> [!NOTE]
>  Managed Package Framework \(MPF\) предоставляет набор управляемых классов, упрощающих создание расширений Visual Studio. О том, как выполнить эту задачу с помощью MPF, см. в разделе [Импорт параметров](/visual-cpp/misc/importing-settings).  
  
### Реализация импорта параметров в VSPackage  
  
1.  Реализуйте базовую поддержку механизма параметров [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    -   Зарегистрируйте пакет VSPackage как поддерживающий механизм параметров, определив одну или несколько точек настраиваемых параметров.  
  
         Для получения дополнительной информации см. [Поддержка параметров пользователя](../extensibility/internals/support-for-user-settings.md).  
  
    -   Объявите, что VSPackage реализует интерфейс, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings>, например:  
  
        ```  
        public class MyPackage : IVsPackage, IVsUserSettings, IVsUserSettingsQuery  
        ```  
  
    -   Убедитесь, что реализация метода <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> в пакете VSPackage предоставляет интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> при вызове с `IID_IVsUserSettings`. Пример:  
  
        ```  
        STDMETHODIMP MyPackage::QueryInterface(THIS_ REFIID riid, LPVOID FAR* ppvObj) { if (ppvObj == NULL) return E_POINTER; *ppvObj = NULL; if (riid == IID_IUnknown) *ppvObj = (LPVOID)(IUnknown *)(IClassFactory*)this; else if (riid == IID_IClassFactory) *ppvObj = (LPVOID)(IClassFactory *)this; else if (riid == IID_IVsPackage) *ppvObj = (LPVOID)(IVsPackage *)this; else if (riid == IID_IVsPersistSolutionOpts) *ppvObj = (LPVOID)(IVsPersistSolutionOpts *)this; else if (riid == IID_IVsPersistSolutionProps) *ppvObj = (LPVOID)(IVsPersistSolutionProps *)this; else if (riid == IID_IVsComponentSelectorProvider) *ppvObj = (LPVOID)(IVsComponentSelectorProvider *)this; else if (riid == IID_IVsUserSettings) *ppvObj = (LPVOID)(IVsUserSettings *)this; else if (riid == IID_IVsUserSettingsQuery) *ppvObj = (LPVOID)(IVsUserSettingsQuery *)this; if (*ppvObj) { AddRef(); return NOERROR; } return E_NOINTERFACE; }  
        ```  
  
2.  Получите сведения о параметрах.  
  
     Для поддержки получения сведений о параметрах VSPackage должен реализовывать метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A>.  
  
     Для чтения данных реализация интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> в пакете VSPackage должна использовать первые два аргумента, передаваемые с помощью IDE: GUID категории точки настраиваемых параметров и интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader>.  
  
    1.  Реализация метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> в VSPackage должна проверять переданный GUID категории и выбирать правильный механизм для извлечения состояния.  
  
         В приведенном ниже примере метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> вызывает другую реализацию для получения состояния панели команд вместо получения состояния привязки ключей.  
  
    2.  Для извлечения данных в файл параметров пакет VSPackage должен использовать предоставленный интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader>.  
  
        > [!NOTE]
        >  Если сведения о параметрах изменяются в зависимости от версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], реализация метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> в пакете VSPackage перед чтением данных должна использовать метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader.ReadFileVersion%2A> для проверки версии IDE.  
  
         Этот интерфейс предоставляет методы для чтения различных типов данных из файла параметров.  
  
         `interface IVsSettingsReader : IUnknown`  
  
         `{`  
  
         `HRESULT ReadSettingString(WCHAR *pszSettingName, BSTR *pbstrSettingValue);`  
  
         `HRESULT ReadSettingLong(WCHAR *pszSettingName, long *plSettingValue);`  
  
         `HRESULT ReadSettingBoolean(WCHAR *pszSettingName, BOOL *pfSettingValue);`  
  
         `HRESULT ReadSettingAttribute(LPCOLESTR pszSettingName,LPCOLESTR pszAttributeName, BSTR *pbstrSettingValue);  //Internal use only`  
  
         `HRESULT ReadSettingBytes(WCHAR *pszSettingName, BYTE *pSettingValue, long *plDataLength, long lDataMax);`  
  
         `HRESULT ReadVersion(int *pnMajor, int *pnMinor, int *pnBuild);`  
  
         `HRESULT ReportError(WCHAR *pszError);`  
  
         `};`  
  
     Файл параметров поддерживает произвольный доступ к данным, поэтому порядок операций чтения и записи параметров не имеет значения.  
  
     Это иллюстрируется экспортом и импортом состояния панели команд \(`ExportSettings_CommandBa`r и `ImportSettings_CommandBar`\) реализации в приведенном ниже примере.  
  
3.  Проверьте полученные данные.  
  
     Сведения о параметрах содержатся в XML\-файлах, которые можно изменять вручную.  
  
> [!IMPORTANT]
>  Сведения о параметрах могут быть повреждены на диске, могут содержать параметры, зависящие от версии, а также могут использоваться в качестве способа вредоносной атаки. Необходимо проверять допустимость каждого элемента данных, возвращаемого методом <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader>.  
  
-   Чтобы проверить поддержку версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], использовавшейся для создания полученных параметров, вызовите метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader.ReadFileVersion%2A> для получения этой версии.  
  
-   Чтобы среда IDE уведомляла пользователя, что импортированный элемент данных не проверен, VSPackage вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader.ReportError%2A>.  
  
1.  Примените сведения о параметрах.  
  
    1.  Реализация метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> должна учитывать значение третьего аргумента, переданного в метод интегрированной средой разработки. Поддерживаемые значения являются членами перечисления <xref:Microsoft.VisualStudio.Shell.Interop.__UserSettingsFlags>. Для получения дополнительной информации см. <xref:Microsoft.VisualStudio.Shell.Interop.__UserSettingsFlags>.  
  
         В примере ниже реализация для импорта параметров командной строки \(`ImportSettings_Commandbar`\) использует значение этого аргумента для определения, следует ли применять параметры, чтобы перезаписать существующие значения или аддитивно обновить их.  
  
    2.  При применении импортированных параметров необходимо реализовать методологию кэша сквозной записи.  
  
         Одновременно с применением параметров в IDE должны обновляться сведения о состоянии в реестре или в файловой системе. Это гарантирует согласованность конфигурации и поддерживает сценарии с несколькими экземплярами IDE.  
  
2.  Предупредите IDE, как обрабатывать импорт параметров.  
  
     Используйте возвращенный аргумент `pfRestartRequired` метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> для уведомления IDE, если требуется перезапуск, чтобы импортированные параметры вступили в силу.  
  
     Если реализация метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> в пакете VSPackage возвращает значение `true`, пользователю будет предложено перезапустить IDE.  
  
## Пример  
 В приведенном ниже примере демонстрируется импорт и экспорт данных параметров.  
  
```  
static const WCHAR c_szFirstSettingName[] = L"FirstSettingName"; static const WCHAR c_szRandomTrashBytes[] = L"RandomTrashBytes"; static const WCHAR c_szRandomTrashLength[] = L"RandomTrashLength"; static const WCHAR c_szBreakPointWindow[] = L"Breakpoints Window"; // -------------------------------------------------------------------------- //    IVsUserSettings methods used for configuration export and import //    Delegate to the right shell object based on the category GUID // -------------------------------------------------------------------------- static const WCHAR c_szFirstSettingName[] = L"FirstSettingName"; static const WCHAR c_szRandomTrashBytes[] = L"RandomTrashBytes"; static const WCHAR c_szRandomTrashLength[] = L"RandomTrashLength"; static const WCHAR c_szBreakPointWindow[] = L"Breakpoints Window"; // Export Settings. STDMETHOD(NeedExport)(WCHAR* pszCategoryGUID, BOOL *pfNeedExport) { if (!pfNeedExport) return E_INVALIDARG; CLSID clsidCategory; HRESULT hr= S_OK; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); if (GUID_Profiles_CommandBars == clsidCategory) { *pfNeedExport = TRUE; //Always export Command Bar Configuration }else if (GUID_Profiles_KeyBindings == clsidCategory) { *pfNeedExport = FALSE; //By Default don't export key bindings if (m_fMake_Permanent) *pfNeedExport = TRUE; //Export if user wants current configuration saved. }else{ hr = E_UNEXPECTED; } Error: return hr; } STDMETHOD(ExportSettings)(WCHAR *pszCategoryGUID, IVsSettingsWriter *pSettings) { CLSID clsidCategory; HRESULT hr; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); // Delegate to the right internal implementation based on the requested category. if (GUID_Profiles_CommandBars == clsidCategory) { hr = ExportSettings_CommandBars(pSettings); }else if (GUID_Profiles_KeyBindings == clsidCategory) { hr = ExportSettings_KeyBindings(pSettings); }else{ hr = E_UNEXPECTED; } Error: return hr; }; HRESULT ExportSettings_CommandBars(IVsSettingsWriter *pSettings) { if (!pSettings) return E_INVALIDARG; hr = pSettings->WriteSettingString(c_szFirstSettingName, L"Value1"); IfFailGo(hr); int cRandomTrash = 12345; BYTE *pRandomTrash = (BYTE *)VSAlloc(cRandomTrash); if (pRandomTrash){ hr = pSettings->WriteSettingBytes(c_szRandomTrashBytes, pRandomTrash, cRandomTrash); IfFailGo(hr); hr = pSettings->WriteSettingLong(c_szRandomTrashLength, cRandomTrash); IfFailGo(hr); } Error: return hr; }; HRESULT ExportSettings_KeyBindings(IVsSettingsWriter *pSettings) { if (!pSettings) return E_INVALIDARG; hr = pSettings->WriteSettingString(c_szBreakPointWindow, L"Ctrl + Alt + B"); IfFailGo(hr); Error: return hr; }; STDMETHOD(ImportSettings)(WCHAR *pszCategoryGUID, IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { CLSID clsidCategory; HRESULT hr; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); // Delegate to the right internal implementation based on the requested category. if (GUID_Profiles_CommandBars == clsidCategory) { hr = ImportSettings_CommandBars(, pSettings, flags, pfRestartRequired); } else if (GUID_Profiles_KeyBindings == clsidCategory) { hr = ImportSettings_KeyBindings( pSettings, flags, pfRestartRequired); } else { hr = E_UNEXPECTED; } Error: return hr; }; // Import Settings. HRESULT ImportSettings_CommandBars(IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { if (!pSettings) return E_INVALIDARG; if (pfRestartRequired) { *pfRestartRequired = FALSE; //Nobody should require a restart!! } CComBSTR bstrFirstSettingName; long lTrashLength = 0; BYTE *pTrashBytes = NULL; // Determines whether to import as an additive operation, or a reset all settings operation. BOOL fResetCompletely = FALSE; if (flags & USF_ResetOnImport) fResetCompletely = TRUE; hr = pSettings->ReadSettingString(c_szFirstSettingName, &bstrFirstSettingName); IfFailGo(hr); hr = pSettings->ReadSettingLong(c_szRandomTrashLength, &lTrashLength); IfFailGo(hr); if (lTrashLength > 0) { pTrashBytes = (BYTE*)VSAlloc(lTrashLength); IfNullMemGo(pTrashBytes); long lDataRead = 0; hr = pSettings->ReadSettingBytes(c_szRandomTrashLength, pTrashBytes, &lDataRead, lTrashLength); IfFailGo(hr); if (lDataRead != lTrashLength) { hr = E_UNEXPECTED; goto Error; } } // Note: before returning these settings should immediately be applied to your personal //            settings store, whether in the registry or the file system. // This write-thru cache methodology is essential to work in multi-instance IDE scenarios. hr = UpdateState_CommandBar(bstrFirstSettingName,lTrashLength,pTrashBytes,lDataRead); Error: return hr; }; HRESULT ImportSettings_KeyBindings(IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { if (!pSettings) return E_INVALIDARG; if (pfRestartRequired) { *pfRestartRequired = FALSE; //Nobody should require a restart!! } CComBSTR bstrBreakPointWindow; // Determines whether to import as an additive operation or a reset all settings operation. BOOL fResetCompletely = FALSE; if (flags & USF_ResetOnImport) fResetCompletely = TRUE; hr = pSettings->ReadSettingString(c_szBreakPointWindow, &bstrBreakPointWindow); IfFailGo(hr); // Note: before returning these settings should immediately be applied to your personal //            settings store, whether in the registry or the file system. // This write-thru cache methodology is essential to work in multi-instance IDE scenarios. hr = UpdateState_KeyBindings(bstrBreakPointWindow); Error: return hr; }  
```  
  
## См. также  
 [Практическое руководство. Экспорт параметров с помощью сборок взаимодействия](../misc/how-to-export-settings-by-using-interop-assemblies.md)   
 [Поддержка параметров пользователя](../extensibility/internals/support-for-user-settings.md)   
 [Расширение настройки пользователя и параметры](../extensibility/extending-user-settings-and-options.md)   
 [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/ru-ru/22c4debb-4e31-47a8-8f19-16f328d7dcd3)