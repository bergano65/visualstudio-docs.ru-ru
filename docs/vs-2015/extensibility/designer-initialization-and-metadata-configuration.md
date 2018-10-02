---
title: Инициализация конструктора и конфигурация метаданных | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 550f4c00d669d22b8c4a887c2917d9afdc462278
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562610"
---
# <a name="designer-initialization-and-metadata-configuration"></a>Инициализация конструктора и конфигурация метаданных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [инициализации конструктора и конфигурация метаданных](https://docs.microsoft.com/visualstudio/extensibility/designer-initialization-and-metadata-configuration).  
  
Манипуляции метаданных и фильтрация атрибутов, связанных с конструктором или конструктор компонентов предоставляет механизм для приложений определить, какие средства используются в определенный конструктором для обработки разных <xref:System.Type> объектов (таких как структуры данных классы или графический сущностей), когда доступен конструктор, и как интегрированной среде разработки Visual Studio настроена для поддержки конструктора (для экземпляра, который **элементов** вкладки или категории доступна).  
  
 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] Предоставляет несколько механизмов для упрощения управления инициализации конструктора или конструктор компонентов и манипуляции метаданных пакетом VSPackage.  
  
## <a name="initializing-metadata-and-configuration-information"></a>Инициализация метаданные и сведения о конфигурации  
 Так как они загружаются по запросу, пакеты VSPackage может не быть загружен [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] среды до создания экземпляра конструктора. Таким образом, пакеты VSPackage нельзя использовать стандартный механизм для настройки конструктором или конструктор компонентов при создании, который должен обрабатывать <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> событий. Вместо этого VSPackage реализует экземпляр <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> интерфейс и регистрируется для предоставления настроек, называется расширения поверхности проектирования.  
  
### <a name="customizing-initialization"></a>Настройка инициализации  
 Настройка конструктора, компонента или область конструктора, включает в себя:  
  
1.  Изменение метаданных конструктора и возможности настройки как определенного <xref:System.Type> доступ или преобразованы.  
  
     Обычно это делается через <xref:System.Drawing.Design.UITypeEditor> или <xref:System.ComponentModel.TypeConverter> механизмы.  
  
     Например, если <xref:System.Windows.Forms>-на основе конструкторы инициализируются, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] изменяет среду <xref:System.Drawing.Design.UITypeEditor> для <xref:System.Web.UI.WebControls.Image> объекты, используемые с конструктором, для использования resource manager для получения точечные рисунки, а не в файловой системе.  
  
2.  Интеграция со средой, например, подписка на события или получения информации о конфигурации проекта. Вы можете получить сведения о конфигурации проекта и подписаться на события путем получения <xref:System.ComponentModel.Design.ITypeResolutionService> интерфейс.  
  
3.  Изменения среды пользователем, активировав соответствующие **элементов** категорий или ограничивая применимость конструктора, применяя экземпляр <xref:System.ComponentModel.ToolboxItemFilterAttribute> класс в конструктор.  
  
### <a name="designer-initialization-by-a-vspackage"></a>Инициализация конструктора пакетом VSPackage  
 Пакет VSPackage должен обрабатывать инициализация конструктора с:  
  
1.  Создание объекта, реализующего <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> класса.  
  
    > [!NOTE]
    >  <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> Класс никогда не должны размещаться на один и тот же объект как <xref:Microsoft.VisualStudio.Shell.Package> класса.  
  
2.  Регистрация класса, реализующего <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> как предоставление поддержки для расширения конструктора в пакете VSPackage, применяя экземпляров <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>, <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute> и <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> в класс, предоставляющий реализацию VSPackage <xref:Microsoft.VisualStudio.Shell.Package> .  
  
 При создании любого конструктора или компонента конструктора [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] среды:  
  
1.  Обращается к расширение поверхности каждого зарегистрированного проектирования поставщика.  
  
2.  Создает и инициализирует экземпляр каждого поставщика расширение поверхности конструктора <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> объекта  
  
3.  Вызывает каждый поставщик расширение поверхности конструктора <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> метод или <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> метод (при необходимости).  
  
 При реализации <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> объект членом VSPackage, важно понимать, что:  
  
1.  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Среде нет контроля над метаданные или другие параметры конфигурации, определенный `DesignSurfaceExtension` изменяет поставщика. Это возможно для двух или более `DesignSurfaceExtension` изменение ту же функцию конструктора конфликтующие способами с помощью окончательного изменения, выполняется определенный поставщиков. Он не определен, какие изменения последнее применение.  
  
2.  Можно явным образом ограничить реализацию <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> объект для определенного конструкторы, применяя экземпляров <xref:System.ComponentModel.ToolboxItemFilterAttribute> для такой реализации. Дополнительные сведения о **элементов** товара фильтрации, см. в разделе <xref:System.ComponentModel.ToolboxItemFilterAttribute> и <xref:System.ComponentModel.ToolboxItemFilterType>.  
  
## <a name="additional-metadata-provisioning"></a>Дополнительные метаданные подготовки  
 Пакет VSPackage можно изменить конфигурацию конструктором или конструктор компонентов, отличных от во время разработки.  
  
 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> Класс можно использовать программно, или применить к VSPackage, предоставляющий конструктору.  
  
 Экземпляр <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> класс используется для изменения метаданных компонентов, созданных на поверхности разработки. Например, один может заменить обозревателя свойств по умолчанию, используемые <xref:System.Windows.Forms.CommonDialog> объектов с пользовательский обозреватель свойств.  
  
 Изменения, предоставляемые экземпляр <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> применяется к реализации VSPackage <xref:Microsoft.VisualStudio.Shell.Package> может иметь одно из двух областей:  
  
-   Global--для всех новых экземпляров данного компонента  
  
-   Локальный--относится только к экземпляру компонента, созданного на поверхности разработки, предоставленной текущим VSPackage.  
  
 `IsGlobal` Свойство <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> экземпляра применяется к реализации VSPackage <xref:Microsoft.VisualStudio.Shell.Package> определяет этой области.  
  
 Применение атрибута к реализации <xref:Microsoft.VisualStudio.Shell.Package> с <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> свойство <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> присвоено `true`, как показано ниже, изменяет браузера для всего [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] среды:  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
 Если задан глобальный флаг `false`, изменение метаданных является локальной для текущего конструктора поддерживается текущим VSPackage:  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
> [!NOTE]
>  В настоящее время в область конструктора поддерживает только создание компонентов, и таким образом только компоненты могут иметь локальные метаданные. В приведенном выше примере мы предпринималась попытка изменения свойства, такие как `Color` свойства объекта. Если `false` было передано в качестве глобального флага `CustomBrowser` никогда не будет отображаться, так как конструктор никогда не создает экземпляр `Color`. Установка для глобального флага `false` полезен для компонентов, таких как элементы управления, таймеры и диалоговые окна.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>   
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>   
 <xref:System.ComponentModel.ToolboxItemFilterType>   
 [Расширения поддержки времени разработки](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)

