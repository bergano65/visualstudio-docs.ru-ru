---
title: "Реализация пакетов VSPackage с помощью библиотеки Visual Studio | Microsoft Docs"
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
  - "Библиотека Visual Studio, реализация пакетов VSPackage"
ms.assetid: 4cbac13f-2a9d-4955-b411-dad79081fdeb
caps.latest.revision: 7
caps.handback.revision: 7
manager: "douge"
---
# Реализация пакетов VSPackage с помощью библиотеки Visual Studio
`IVsPackageImpl` класс в библиотеке Visual Studio предоставляет минимальную реализация  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> интерфейс.  `IVsPackageImpl` позаботит о большинство методов службы  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.  Другие методы можно переопределить, чтобы предоставить содержательной реализации:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.CreateTool%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Шаблон пакета приводит весь код обсуженный здесь.  Можно сэкономить время с помощью шаблона для создания VSPackage.  
  
 Пакеты, которые реализуются с помощью библиотеки Visual Studio ultimate наследующие класс VSPackage из библиотеки ATL [CComObjectRootEx Class](/visual-cpp/atl/reference/ccomobjectrootex-class) и  [CComCoClass Class](/visual-cpp/atl/reference/ccomcoclass-class) и IVsPackageImpl библиотеки Visual Studio.  Например, ниже объявление класса VSPackage из образца Reference.Package:  
  
```  
class ATL_NO_VTABLE BasicPackage :   
    public CComObjectRootEx<CComSingleThreadModel>,  
    public CComCoClass<BasicPackage, &CLSID_BasicPackage>,  
    public IVsPackageImpl<BasicPackage, &CLSID_BasicPackage>,  
    ...  
```  
  
 `IVsPackageImpl` отображаемые параметры шаблона класс является VSPackage и указатель на идентификатор GUID, определяющий VSPackage.  
  
## Поддержка QueryInterface с сопоставлениями модели COM  
 Получить поддержку для библиотеки ATL `QueryInterface`его сопоставление модели COM должен перечислить интерфейсы, реализуемые классом.  Например, при поиске сопоставление модели COM для класса VSPackage в образце Reference.Package:  
  
```  
BEGIN_COM_MAP(BasicPackage)  
    COM_INTERFACE_ENTRY(IVsPackage)  
    ...  
END_COM_MAP()  
```  
  
 Дополнительные сведения о сопоставлениях модели COM см. в разделе [Implementing CComObjectRootEx](/visual-cpp/atl/implementing-ccomobjectrootex) и  [COM\_INTERFACE\_ENTRY Macros](../Topic/COM_INTERFACE_ENTRY%20Macros.md).  
  
## Поддержка регистрацию с сопоставлениями реестра  
 Библиотека Visual Studio использует файлы библиотек ATL\-стиля .RGS, чтобы поддерживать регистрацию COM\-объект.  Чтобы обеспечить замену токена в файле .RGS библиотека Visual Studio использует сопоставления реестра.  Сопоставления реестра перечислены символы, которые нужно заменить, поддерживают использование идентификаторов ресурсов таблицы строки.  
  
 Например, при поиске сопоставление реестра для класса VSPackage в образце Reference.Package:  
  
```  
VSL_BEGIN_REGISTRY_MAP(IDR_BASICPACKAGE_RGS)  
    VSL_REGISTRY_MAP_GUID_ENTRY(CLSID_BasicPackage)  
    VSL_REGISTRY_RESOURCE_STRING_ENTRY(IDS_BASICPACKAGE_REGISTRY_NAME)  
    ...  
VSL_END_REGISTRY_MAP()  
```  
  
## См. также  
 [Примеры VSSDK](../misc/vssdk-samples.md)