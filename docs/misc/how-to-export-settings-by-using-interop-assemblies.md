---
title: "Практическое руководство. Экспорт параметров с помощью сборок взаимодействия | Microsoft Docs"
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
  - "параметры интегрированной среды разработки, экспорт с помощью сборок взаимодействия"
  - "параметры пользователя [пакет SDK для Visual Studio], экспорт с помощью сборок взаимодействия"
  - "интегрированная среда разработки, экспорт параметров с помощью сборок взаимодействия"
ms.assetid: d470d4f9-3006-40c3-99db-21abcd5003b8
caps.latest.revision: 23
caps.handback.revision: 23
manager: "douge"
---
# Практическое руководство. Экспорт параметров с помощью сборок взаимодействия
Пакет VSPackage может экспортировать параметры из интегрированной среды разработки [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Интегрированная среда разработки использует реализацию VSPackage интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings>. Если пакет также предоставляет интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery>, то интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery> используется для определения способа сохранения конфигурации VSPackage.  
  
> [!NOTE]
>  Платформа Managed Package Framework \(MPF\) предоставляет набор управляемых классов, упрощающих создание расширений Visual Studio. Сведения о выполнении этой задачи с помощью MPF см. в разделе [Экспорт параметров](../misc/exporting-settings.md).  
  
### Реализация экспорта параметров в VSPackage  
  
1.  Реализуйте базовую поддержку механизма параметров [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    -   Зарегистрируйте пакет VSPackage как поддерживающий механизм параметров, определив одну или несколько точек настраиваемых параметров.  
  
         Для получения дополнительной информации см. [Поддержка параметров пользователя](../extensibility/internals/support-for-user-settings.md).  
  
    -   Объявите пакет VSPackage как реализующий интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings>. При необходимости пакет VSPackage также может реализовывать интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery>. Пример:  
  
        ```  
        public class MyPackage : IVsPackage, IVsUserSettings, IVsUserSettingsQuery  
        ```  
  
    -   Убедитесь в том, что реализация метода <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> в пакете VSPackage предоставляет интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> при вызове с `IID_IVsUserSettings`.  
  
         При необходимости `QueryInterface` может предоставлять интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery> при вызове с интерфейсом `IID_IVsUserSettingsQuery`.  
  
        ```  
        STDMETHODIMP MyPackage::QueryInterface(THIS_ REFIID riid, LPVOID FAR* ppvObj) { if (ppvObj == NULL) return E_POINTER; *ppvObj = NULL; if (riid == IID_IUnknown) *ppvObj = (LPVOID)(IUnknown *)(IClassFactory*)this; else if (riid == IID_IClassFactory) *ppvObj = (LPVOID)(IClassFactory *)this; else if (riid == IID_IVsPackage) *ppvObj = (LPVOID)(IVsPackage *)this; else if (riid == IID_IVsPersistSolutionOpts) *ppvObj = (LPVOID)(IVsPersistSolutionOpts *)this; else if (riid == IID_IVsPersistSolutionProps) *ppvObj = (LPVOID)(IVsPersistSolutionProps *)this; else if (riid == IID_IVsComponentSelectorProvider) *ppvObj = (LPVOID)(IVsComponentSelectorProvider *)this; else if (riid == IID_IVsUserSettings) *ppvObj = (LPVOID)(IVsUserSettings *)this; else if (riid == IID_IVsUserSettingsQuery) *ppvObj = (LPVOID)(IVsUserSettingsQuery *)this; if (*ppvObj) { AddRef(); return NOERROR; } return E_NOINTERFACE; }  
        ```  
  
2.  Кроме того, можно уведомить интегрированную среду разработки о необходимости экспортировать определенный параметр.  
  
     Пакет VSPackage может сохранить параметр, определяемый точкой настраиваемых параметров, при определенном условии. Например, параметр может сохраняться только в том случае, если пользователь указал, какой именно параметр нужно сохранить.  
  
     В этом случае необходимо реализовать интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery>.  
  
     Если пакет VSPackage не реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery>, вся информация о его состоянии сохраняется при экспорте параметров.  
  
     Пакет VSPackage может поддерживать несколько точек настраиваемых параметров \(категорий параметров\). Реализации метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery.NeedExport%2A> должны проверять предоставленный идентификатор GUID точки настраиваемых параметров или аргумент категории параметров для определения того, необходимо ли сохранить конкретную группу параметров.  
  
     В приведенном ниже примере пакет VSPackage всегда требует сохранения состояния своей панели команд, но состояние привязки ключей должно сохраняться только в том случае, если установлен флаг.  
  
3.  Запишите данные параметров в файл параметров.  
  
     Для поддержки экспорта параметров пакет VSPackage всегда должен реализовывать метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A>.  
  
     Реализация должна обрабатывать аргументы, переданные интегрированной средой разработки, идентификатор GUID категории точки настраиваемых параметров и интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter>.  
  
    1.  Пакет VSPackage может поддерживать несколько точек настраиваемых параметров \(категорий параметров\). В приведенном ниже примере метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> вызывает другую реализацию для сохранения состояния панели команд, а не состояния привязки ключей.  
  
    2.  Для сохранения данных в файл параметров пакет VSPackage должен использовать предоставленный интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter>.  
  
         `interface IVsSettingsWriter : IUnknown`  
  
         `{`  
  
         `HRESULT WriteSettingString( LPCOLESTR pszSettingName, LPCOLESTR pszSettingValue);`  
  
         `HRESULT WriteSettingLong( LPCOLESTR pszSettingName, long lSettingValue);`  
  
         `HRESULT WriteSettingBoolean( LPCOLESTR pszSettingName, BOOL fSettingValue);`  
  
         `HRESULT WriteSettingBytes( LPCOLESTR pszSettingName, BYTE *pSettingValue, long lDataLength);`  
  
         `HRESULT WriteSettingAttribute( LPCOLESTR pszSettingName, LPCOLESTR pszAttributeName, LPCOLESTR pszSettingValue);`  
  
         `HRESULT WriteSettingXml( IUnknown *pIXMLDOMNode);`  
  
         `HRESULT WriteSettingXmlFromString( LPCOLESTR szXML);`  
  
         `HRESULT ReportError( LPCOLESTR pszError, VSSETTINGSERRORTYPES dwErrorType);`  
  
         `};`  
  
         Значение аргумента `pszSettingName`, предоставленное в интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter>, должно уникальным образом определять каждый элемент данных, сохраненный в категории параметров.  
  
        > [!NOTE]
        >  Имена должны быть уникальными в пределах точки настраиваемых параметров, так как интегрированная среда разработки использует ее идентификатор GUID и значение `pszSettingName` для идентификации каждого сохраненного параметра. При вызове нескольких методов <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> с одинаковым значением `pszSettingName` исходное значение в файле параметров перезаписывается.  
  
         Файл параметров поддерживает произвольный доступ к данным. Поэтому очередность операций чтения и записи параметров не имеет значения.  
  
         Это проиллюстрировано в реализациях экспорта и импорта состояния панели команд \(`ExportSettings_CommandBa`r и `ImportSettings_CommandBar`\) в приведенном ниже примере.  
  
         Если реализация может сопоставить данные с одним из четырех поддерживаемых форматов, ограничений на объем записываемых данных и их тип нет.  
  
        > [!NOTE]
        >  Помимо явно записываемых данных, которые прозрачны для реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A>, интерфейс API параметров также сохраняет информацию о версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Сохраненные параметры можно сравнивать по признаку версии интегрированной среды разработки, которая создала их во время импорта параметров.  
  
## Пример  
 В приведенном ниже примере демонстрируется импорт и экспорт данных параметров.  
  
```  
// -------------------------------------------------------------------------- //    IVsUserSettings methods used for configuration export. //    Delegate to the right shell object based on the category GUID. // -------------------------------------------------------------------------- static const WCHAR c_szFirstSettingName[] = L"FirstSettingName"; static const WCHAR c_szRandomTrashBytes[] = L"RandomTrashBytes"; static const WCHAR c_szRandomTrashLength[] = L"RandomTrashLength"; static const WCHAR c_szBreakPointWindow[] = L"Breakpoints Window"; // Export Settings. STDMETHOD(NeedExport)(WCHAR* pszCategoryGUID, BOOL *pfNeedExport) { if (!pfNeedExport) return E_INVALIDARG; CLSID clsidCategory; HRESULT hr= S_OK; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); if (GUID_Profiles_CommandBars == clsidCategory) { *pfNeedExport = TRUE; //Always export Command Bar Configuration }else if (GUID_Profiles_KeyBindings == clsidCategory) { *pfNeedExport = FALSE; //By Default don't export key bindings if (m_fMake_Permanent) *pfNeedExport = TRUE; //Export if user wants current configuration saved. }else{ hr = E_UNEXPECTED; } Error: return hr; } STDMETHOD(ExportSettings)(WCHAR *pszCategoryGUID, IVsSettingsWriter *pSettings) { CLSID clsidCategory; HRESULT hr; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); // Delegate to the right internal implementation based on // the requested category. if (GUID_Profiles_CommandBars == clsidCategory) { hr = ExportSettings_CommandBars(pSettings); }else if (GUID_Profiles_KeyBindings == clsidCategory) { hr = ExportSettings_KeyBindings(pSettings); }else{ hr = E_UNEXPECTED; } Error: return hr; }; HRESULT ExportSettings_CommandBars(IVsSettingsWriter *pSettings) { if (!pSettings) return E_INVALIDARG; hr = pSettings->WriteSettingString(c_szFirstSettingName, L"Value1"); IfFailGo(hr); int cRandomTrash = 12345; BYTE *pRandomTrash = (BYTE *)VSAlloc(cRandomTrash); if (pRandomTrash){ hr = pSettings->WriteSettingBytes(c_szRandomTrashBytes, pRandomTrash, cRandomTrash); IfFailGo(hr); hr = pSettings->WriteSettingLong(c_szRandomTrashLength, cRandomTrash); IfFailGo(hr); } Error: return hr; }; HRESULT ExportSettings_KeyBindings(IVsSettingsWriter *pSettings) { if (!pSettings) return E_INVALIDARG; hr = pSettings->WriteSettingString(c_szBreakPointWindow, L"Ctrl + Alt + B"); IfFailGo(hr); Error: return hr; }; STDMETHOD(ImportSettings)(WCHAR *pszCategoryGUID, IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { CLSID clsidCategory; HRESULT hr; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); // Delegate to the right internal implementation based on // the requested category. if (GUID_Profiles_CommandBars == clsidCategory) { hr = ImportSettings_CommandBars(, pSettings, flags, pfRestartRequired); } else if (GUID_Profiles_KeyBindings == clsidCategory) { hr = ImportSettings_KeyBindings( pSettings, flags, pfRestartRequired); } else { hr = E_UNEXPECTED; } Error: return hr; }; // Import Settings. HRESULT ImportSettings_CommandBars(IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { if (!pSettings) return E_INVALIDARG; if (pfRestartRequired) { *pfRestartRequired = FALSE; //Nobody should require a restart!! } CComBSTR bstrFirstSettingName; long lTrashLength = 0; BYTE *pTrashBytes = NULL; // Determines whether to treat import as an additive operation, or a reset all settings operation. BOOL fResetCompletely = FALSE; if (flags & USF_ResetOnImport) fResetCompletely = TRUE; hr = pSettings->ReadSettingString(c_szFirstSettingName, &bstrFirstSettingName); IfFailGo(hr); hr = pSettings->ReadSettingLong(c_szRandomTrashLength, &lTrashLength); IfFailGo(hr); if (lTrashLength > 0) { pTrashBytes = (BYTE*)VSAlloc(lTrashLength); IfNullMemGo(pTrashBytes); long lDataRead = 0; hr = pSettings->ReadSettingBytes(c_szRandomTrashLength, pTrashBytes, &lDataRead, lTrashLength); IfFailGo(hr); if (lDataRead != lTrashLength) { hr = E_UNEXPECTED; goto Error; } } // Note: before returning, these settings should immediately //             be applied to your personal settings store, //             whether in the registry or the file system. // This write-through cache methodology is essential to to work //             in multi-instance IDE scenarios. hr = UpdateState_CommandBar(bstrFirstSettingName,lTrashLength,pTrashBytes,lDataRead); Error: return hr; }; HRESULT ImportSettings_KeyBindings(IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { if (!pSettings) return E_INVALIDARG; if (pfRestartRequired) { *pfRestartRequired = FALSE; //Nobody should require a restart!! } CComBSTR bstrBreakPointWindow; // Determines whether import can be treated as an additive // operation, or a reset all settings operation. BOOL fResetCompletely = FALSE; if (flags & USF_ResetOnImport) fResetCompletely = TRUE; hr = pSettings->ReadSettingString(c_szBreakPointWindow, &bstrBreakPointWindow); IfFailGo(hr); // Note: Before returning, these settings should immediately //             be applied to your personal settings //             store, whether in the registry or the file system. // This write-through cache methodology is essential to allow us //             to work in multi-instance IDE scenarios. hr = UpdateState_KeyBindings(bstrBreakPointWindow); Error: return hr; }  
```  
  
## См. также  
 [Поддержка параметров пользователя](../extensibility/internals/support-for-user-settings.md)   
 [Расширение настройки пользователя и параметры](../extensibility/extending-user-settings-and-options.md)   
 [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/ru-ru/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Практическое руководство. Использование сборок взаимодействия для импорта параметров](../misc/how-to-use-interop-assemblies-to-import-settings.md)