---
title: Конструктор инициализации и настройки метаданных | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a6334f65b942b2eab3543d866ae1b98a186569ea
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132751"
---
# <a name="designer-initialization-and-metadata-configuration"></a>Конструктор инициализации и настройки метаданных
Обработка метаданных и фильтрация атрибутов, связанных с конструктором или конструктор компонентов предоставляет механизм для приложений, чтобы определить, какие средства используются определенного конструктором для обработки различных <xref:System.Type> объектов (таких как структуры данных классы или графический сущности), когда конструктор доступен, и как интегрированная среда разработки Visual Studio настроена для поддержки конструктора (для экземпляра, который **элементов** категорию или вкладку доступен).  
  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Предоставляет несколько механизмов для упрощения управления инициализации конструктора или конструктор компонентов и обработки его метаданных пакетом VSPackage.  
  
## <a name="initializing-metadata-and-configuration-information"></a>Инициализация метаданные и сведения о конфигурации  
 Так как они загружаются по запросу, пакеты VSPackage могут не быть загружены по [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] среды до создания экземпляра конструктора. Таким образом, пакеты VSPackage нельзя использовать стандартный механизм для настройки конструктора или конструктор компонентов при его создании, который обрабатывает <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> событий. Вместо этого пакет VSPackage реализует экземпляр <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> интерфейс, а также регистрируется для предоставления документа, называют расширения поверхности разработки.  
  
### <a name="customizing-initialization"></a>Настройка инициализации  
 Настройка конструктора, компонента или конструктора, включает в себя:  
  
1.  Изменение метаданных конструктора и возможности настройки как определенного <xref:System.Type> доступ или преобразованы.  
  
     Обычно это осуществляется посредством <xref:System.Drawing.Design.UITypeEditor> или <xref:System.ComponentModel.TypeConverter> механизмы.  
  
     Например, если <xref:System.Windows.Forms>-инициализированы на основе конструкторы, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] изменяет среды <xref:System.Drawing.Design.UITypeEditor> для <xref:System.Web.UI.WebControls.Image> объектов с помощью конструктора для получения растровые изображения, а не в файловой системе с помощью диспетчера ресурсов.  
  
2.  Интеграция со средой, например, подписка на события или получения информации о конфигурации проекта. Вы можете получить сведения о конфигурации проекта и подписаться на события, получая <xref:System.ComponentModel.Design.ITypeResolutionService> интерфейса.  
  
3.  Изменения среды пользователем, активировав соответствующие **элементов** категории или путем ограничения конструктора применимости, применяя экземпляр <xref:System.ComponentModel.ToolboxItemFilterAttribute> класс в конструктор.  
  
### <a name="designer-initialization-by-a-vspackage"></a>Инициализация конструктора путем VSPackage  
 Пакет VSPackage должен обрабатывать конструктора инициализация по:  
  
1.  Создание объекта, реализующего <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> класса.  
  
    > [!NOTE]
    >  <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> Класс никогда не должен быть реализован в один и тот же объект как <xref:Microsoft.VisualStudio.Shell.Package> класса.  
  
2.  Зарегистрируйте класс, реализующий <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> как обеспечения поддержки расширения конструктора VSPackage, применяя экземпляров <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>, <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute> и <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> в класс, предоставляющий реализацию VSPackage <xref:Microsoft.VisualStudio.Shell.Package> .  
  
 При создании любого конструктора или конструктор компонентов [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] среды:  
  
1.  Обращается к каждый поставщик контактной расширения зарегистрированных конструктора.  
  
2.  Создает и инициализирует новый экземпляр класса каждый поставщик расширений поверхности разработки <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> объекта  
  
3.  Вызывает каждый поставщик расширений поверхности разработки <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> метода или <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> метод (при необходимости).  
  
 При реализации <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> объекта как член VSPackage, важно понимать, что:  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Среды нет контроля над метаданные или другие параметры конфигурации определенное `DesignSurfaceExtension` изменяет поставщика. Это возможно для двух или более `DesignSurfaceExtension` изменение одной функции конструктора конфликтующие способами, с помощью окончательного изменения, выполняется определенный поставщиков. Он не определен, какие изменения последнего применения.  
  
2.  Можно явным образом ограничить реализация <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> объекта для конкретных конструкторов, применяя экземпляров <xref:System.ComponentModel.ToolboxItemFilterAttribute> для этой реализации. Дополнительные сведения о **элементов** фильтрации см. в разделе <xref:System.ComponentModel.ToolboxItemFilterAttribute> и <xref:System.ComponentModel.ToolboxItemFilterType>.  
  
## <a name="additional-metadata-provisioning"></a>Подготовка дополнительных метаданных  
 Пакет VSPackage можно изменить конфигурацию или конструктор компонентов, отличный от конструктора во время разработки.  
  
 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> Класса можно использовать программно, или применить пакет VSPackage, предоставляя конструктор.  
  
 Экземпляр <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> класс используется для изменения метаданных компонентов, созданных на поверхности разработки. Например, один замените браузера свойство по умолчанию, используемые <xref:System.Windows.Forms.CommonDialog> объектов с помощью пользовательского свойства браузера.  
  
 Изменения, предоставляемые экземпляр <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> применяется к реализации VSPackage <xref:Microsoft.VisualStudio.Shell.Package> может иметь одно из двух областей:  
  
-   Глобальная--для всех новых экземпляров данного компонента  
  
-   Локальный--относится только к экземпляру компонента, созданного на поверхности разработки, предоставляемых в текущий пакет VSPackage.  
  
 `IsGlobal` Свойство <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> экземпляр, применить к реализацию VSPackage <xref:Microsoft.VisualStudio.Shell.Package> определяет эту область.  
  
 Применение атрибута с реализацией <xref:Microsoft.VisualStudio.Shell.Package> с <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> свойство <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> объект равным `true`, как показано ниже, изменяет браузера для всего [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] среды:  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
 Если задан этот глобальный флаг `false`, то изменение метаданных является локальным для текущего конструктора поддерживается в текущем пакете VSPackage:  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
> [!NOTE]
>  В настоящий момент область конструктора поддерживает только создание компонентов и поэтому только компоненты могут иметь локальные метаданные. В приведенном выше примере мы предпринималась попытка изменения свойства, такие как `Color` свойство объекта. Если `false` было передано в качестве глобального флага `CustomBrowser` никогда не отображаются, так как конструктор фактически не создает экземпляр `Color`. Установите значение глобального флага `false` полезен для компонентов, таких как элементы управления, таймеры и диалоговым окнам.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>   
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>   
 <xref:System.ComponentModel.ToolboxItemFilterType>   
 [Расширения поддержки времени разработки](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)