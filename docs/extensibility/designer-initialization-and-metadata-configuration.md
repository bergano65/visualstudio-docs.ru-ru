---
title: "Конструктор инициализации и настройки метаданных | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
caps.latest.revision: 16
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: c0865b62cc2683a8197b5eb6cbc0599d6c063534
ms.lasthandoff: 02/22/2017

---
# <a name="designer-initialization-and-metadata-configuration"></a>Конструктор инициализации и настройки метаданных
Обработка метаданных и фильтрации атрибутов, связанных с конструктором или конструктор компонентов предоставляет механизм для приложений определить, какие средства используются определенный конструктором для обработки различных <xref:System.Type>объектов (например, структуры данных, классы или графические объекты), при наличии конструктора и о том, как интегрированная среда разработки Visual Studio настроена для поддержки конструктора (для экземпляра, который **элементов** категория или вкладка доступна).</xref:System.Type>  
  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Предоставляет несколько механизмов для упрощения управления конструктора или конструктор компонентов инициализации и обработки метаданных, VSPackage.  
  
## <a name="initializing-metadata-and-configuration-information"></a>Инициализация метаданных и сведений о конфигурации  
 Так как они загружаются по запросу, VSPackages может не были загружены [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] среды до создания экземпляра конструктора. Таким образом, VSPackages нельзя использовать стандартный механизм для настройки конструктора или конструктор компонентов при его создании, который обрабатывает <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated>событий.</xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> Вместо этого VSPackage реализует экземпляр <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>интерфейса и регистрирует себя для обеспечения настройки, называют расширения поверхности разработки.</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
### <a name="customizing-initialization"></a>Настройка инициализации  
 Настройка конструктора, компонента или конструктора, включает в себя:  
  
1.  Изменение метаданных конструктора и возможности настройки как определенный <xref:System.Type>доступ или преобразованы.</xref:System.Type>  
  
     Обычно это делается через <xref:System.Drawing.Design.UITypeEditor>или <xref:System.ComponentModel.TypeConverter>механизмы.</xref:System.ComponentModel.TypeConverter> </xref:System.Drawing.Design.UITypeEditor>  
  
     Например, если <xref:System.Windows.Forms>-инициализации конструкторов на основе [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] изменяет среды <xref:System.Drawing.Design.UITypeEditor>для <xref:System.Web.UI.WebControls.Image>объектов с помощью конструктора для получения точечные рисунки, а не в файловой системе с помощью диспетчера ресурсов.</xref:System.Web.UI.WebControls.Image> </xref:System.Drawing.Design.UITypeEditor> </xref:System.Windows.Forms>  
  
2.  Интеграция со средой, например, подписка на события или получения информации о конфигурации проекта. Вы можете получить сведения о конфигурации проекта и подписаться на события, получая <xref:System.ComponentModel.Design.ITypeResolutionService>интерфейса.</xref:System.ComponentModel.Design.ITypeResolutionService>  
  
3.  Изменения среды пользователем, активировав соответствующие **элементов** категорий или ограничьте применимости конструктора путем применения экземпляр <xref:System.ComponentModel.ToolboxItemFilterAttribute>класс в конструктор.</xref:System.ComponentModel.ToolboxItemFilterAttribute>  
  
### <a name="designer-initialization-by-a-vspackage"></a>Инициализация конструктора по VSPackage  
 VSPackage должен обрабатывать инициализацию конструктора:  
  
1.  Создание объекта, реализующего <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>класса.</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
    > [!NOTE]
    >  <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>Класс никогда не должен быть реализован на тот же объект <xref:Microsoft.VisualStudio.Shell.Package>класса.</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
2.  Зарегистрировать класс, реализующий <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>как предоставление поддержки для расширения конструктора VSPackage, применяя экземпляров <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute>и <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>класс предоставляет реализацию <xref:Microsoft.VisualStudio.Shell.Package>.</xref:Microsoft.VisualStudio.Shell.Package> VSPackage</xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> </xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
 При создании любой конструктор или конструктор компонентов [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] среды:  
  
1.  Обращается к каждый поставщик контактной расширения зарегистрированных конструктора.  
  
2.  Создает и инициализирует экземпляр каждого поставщика расширений поверхности конструктора <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>объектов</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
3.  Вызывает каждый поставщик расширений поверхности разработки <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A>метода или <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A>метод (при необходимости).</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A>  
  
 При реализации <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>объект как член VSPackage, важно понимать, что:</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Среды нет контроля над метаданные или другие параметры настройки, определенный `DesignSurfaceExtension` изменяет поставщика. Возможно, для двух или более `DesignSurfaceExtension` изменение такие же возможности конструктора конфликтующие способами с помощью последней модификации, выполняется полное поставщиков. Оно не определено, какие изменения последнего применения.  
  
2.  Можно явным образом ограничить реализация <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>объекта для конкретных конструкторов, применяя экземпляров <xref:System.ComponentModel.ToolboxItemFilterAttribute>для этой реализации.</xref:System.ComponentModel.ToolboxItemFilterAttribute> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> Дополнительные сведения о **элементов** элемент фильтрации см. в разделе <xref:System.ComponentModel.ToolboxItemFilterAttribute>и <xref:System.ComponentModel.ToolboxItemFilterType>.</xref:System.ComponentModel.ToolboxItemFilterType> </xref:System.ComponentModel.ToolboxItemFilterAttribute>  
  
## <a name="additional-metadata-provisioning"></a>Подготовка дополнительных метаданных  
 VSPackage можно изменить настройки конструктора или конструктор компонентов, отличный от во время разработки.  
  
 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>Класса можно использовать программно, или применяться к VSPackage, предоставляя конструктор.</xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>  
  
 Экземпляр <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>класс используется для изменения метаданных компонентов, созданных на поверхности разработки.</xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> Например, один заменить обозреватель свойств по умолчанию, используемые <xref:System.Windows.Forms.CommonDialog>объектов с помощью пользовательского свойства браузера.</xref:System.Windows.Forms.CommonDialog>  
  
 Изменения, предоставляемые экземпляр <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>применяется для реализации VSPackage <xref:Microsoft.VisualStudio.Shell.Package>может иметь одно из двух областей:</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>  
  
-   Global--для всех новых экземпляров данного компонента  
  
-   Локальный--относится только к экземпляру компонента, созданного на поверхности разработки, предоставляемых текущего VSPackage.  
  
 `IsGlobal` Свойство <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>экземпляра применяется для реализации VSPackage <xref:Microsoft.VisualStudio.Shell.Package>определяет эту область.</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>  
  
 Применение атрибута на реализацию <xref:Microsoft.VisualStudio.Shell.Package>с <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A>свойство <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>объекта установить `true`, как показано ниже, изменяет браузера для всего [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] среды:</xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> </xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> </xref:Microsoft.VisualStudio.Shell.Package>  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
 Если задан глобальный флаг `false`, то изменение метаданных является локальной в текущем конструкторе, поддерживаемых текущей VSPackage:  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
> [!NOTE]
>  В настоящий момент область конструктора поддерживает только создание компонентов, и поэтому только компоненты могут иметь локальные метаданные. В приведенном выше примере мы предпринималась попытка изменения свойства, такие как `Color` свойство объекта. Если `false` было передано в качестве глобального флага `CustomBrowser` никогда не отображаются, так как конструктор фактически не создает экземпляр `Color`. Значение глобального флага `false` полезен для компонентов, таких как элементы управления, таймеры и диалоговые окна.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension></xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>   
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute></xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>   
 <xref:System.ComponentModel.ToolboxItemFilterType></xref:System.ComponentModel.ToolboxItemFilterType>   
 [Расширение поддержки времени разработки](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
