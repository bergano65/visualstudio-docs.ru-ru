---
title: Инициализация конструктора и Настройка метаданных | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2dec3937616c712c56b7012949e044702e6b11f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703069"
---
# <a name="designer-initialization-and-metadata-configuration"></a>Инициализация конструктора и конфигурация метаданных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Управление метаданными и атрибутами фильтра, связанными с конструктором или компонентом конструктора, предоставляет приложениям механизм для определения того, какие средства используются определенным конструктором для обработки различных <xref:System.Type> объектов (например, структур данных, классов или графических сущностей), когда конструктор доступен, и как настроена интегрированная среда разработки Visual Studio для поддержки конструктора (например, доступна вкладка или категория **панели элементов** ).  
  
 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]Предоставляет несколько механизмов для упрощения управления инициализацией компонента конструктора или конструктора и манипуляцией с его метаданными с помощью VSPackage.  
  
## <a name="initializing-metadata-and-configuration-information"></a>Инициализация метаданных и сведений о конфигурации  
 Так как они загружаются по запросу, пакеты VSPackage могут быть не загружены [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] средой до создания экземпляра конструктора. Поэтому пакеты VSPackage не могут использовать стандартный механизм настройки конструктора или компонента конструктора при создании, который обрабатывает <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> событие. Вместо этого VSPackage реализует экземпляр <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> интерфейса и регистрирует себя для предоставления настроек, называемых расширениями поверхности разработки.  
  
### <a name="customizing-initialization"></a>Настройка инициализации  
 Настройка конструктора, компонента или области конструктора включает в себя:  
  
1. Изменение метаданных конструктора и эффективное изменение того, как <xref:System.Type> осуществляется доступ к определенному или преобразованию.  
  
     Обычно это осуществляется с помощью <xref:System.Drawing.Design.UITypeEditor> механизмов или <xref:System.ComponentModel.TypeConverter> .  
  
     Например, при <xref:System.Windows.Forms> инициализации конструкторов на основе [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Среда изменяет объект <xref:System.Drawing.Design.UITypeEditor> для <xref:System.Web.UI.WebControls.Image> объектов, используемых с конструктором, чтобы использовать диспетчер ресурсов для получения точечных рисунков, а не файловой системы.  
  
2. Интеграция с средой, например, подписка на события или получение сведений о конфигурации проекта. Вы можете получить сведения о конфигурации проекта и подписываться на события, получая <xref:System.ComponentModel.Design.ITypeResolutionService> интерфейс.  
  
3. Изменение пользовательской среды путем активации соответствующих категорий **панели элементов** или путем изменения применимости конструктора путем применения экземпляра <xref:System.ComponentModel.ToolboxItemFilterAttribute> класса к конструктору.  
  
### <a name="designer-initialization-by-a-vspackage"></a>Инициализация конструктора VSPackage  
 Пакет VSPackage должен выполнять инициализацию конструктора следующим образом:  
  
1. Создание объекта, реализующего <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> класс.  
  
   > [!NOTE]
   > <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>Класс никогда не должен реализовываться на том же объекте, что и <xref:Microsoft.VisualStudio.Shell.Package> класс.  
  
2. Зарегистрируйте класс, реализующий реализацию <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> , для расширения конструктора VSPackage, применив экземпляры  <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute> и <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> к классу, предоставляющему реализацию VSPackage <xref:Microsoft.VisualStudio.Shell.Package> .  
  
   При создании любого компонента конструктора или конструктора [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Среда:  
  
3. Обращается к каждому зарегистрированному поставщику расширения рабочей области конструирования.  
  
4. Создает и инициализирует экземпляр каждого объекта поставщика расширения области разработки. <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
5. Вызывает метод или метод поставщика расширения области разработки <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> (при необходимости).  
  
   При реализации <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> объекта в качестве члена VSPackage важно понимать, что:  
  
6. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Среда не предоставляет никакого контроля над тем, какие метаданные или другие параметры конфигурации `DesignSurfaceExtension` изменяются определенным поставщиком. Возможно, что два или более `DesignSurfaceExtension` поставщика изменяют одну и ту же функцию конструктора в конфликтующих способах, и окончательное изменение является окончательным. Это неопределенное применение последнего применения изменений.  
  
7. Можно явно ограничить реализацию <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> объекта определенными конструкторами, применяя экземпляры <xref:System.ComponentModel.ToolboxItemFilterAttribute> к этой реализации. Дополнительные сведения о фильтрации элементов **панели элементов** см. в разделе <xref:System.ComponentModel.ToolboxItemFilterAttribute> и <xref:System.ComponentModel.ToolboxItemFilterType> .  
  
## <a name="additional-metadata-provisioning"></a>Дополнительная подготовка метаданных  
 Пакет VSPackage может изменять конфигурацию конструктора или компонента конструктора, а не во время разработки.  
  
 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>Класс можно использовать программно или применить к пакету VSPackage, предоставляющему конструктор.  
  
 Экземпляр <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> класса используется для изменения метаданных компонентов, созданных в области конструктора. Например, можно заменить обозреватель свойств по умолчанию <xref:System.Windows.Forms.CommonDialog> , используемый объектами, с помощью браузера настраиваемых свойств.  
  
 Изменения, предоставляемые экземпляром, <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> примененным к реализации VSPackage, <xref:Microsoft.VisualStudio.Shell.Package> могут иметь одну из двух областей:  
  
- Global--для всех новых экземпляров данного компонента  
  
- Local — относится только к экземпляру компонента, созданному в области конструктора, предоставляемой текущим VSPackage.  
  
  `IsGlobal`Свойство <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> экземпляра, применяемое к реализации VSPackage, <xref:Microsoft.VisualStudio.Shell.Package> определяет эту область.  
  
  Применение атрибута к реализации <xref:Microsoft.VisualStudio.Shell.Package> со <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> свойством <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> объекта, установленным в `true` , как показано ниже, приводит к изменению браузера для всей [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] среды:  
  
  `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`  
  
  `internal class MyPackage : Package {}`  
  
  Если для глобального флага задано значение `false` , то изменение метаданных является локальным для текущего конструктора, поддерживаемого текущим пакетом VSPackage:  
  
  `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`  
  
  `internal class MyPackage : Package {}`  
  
> [!NOTE]
> В настоящее время область конструктора поддерживает только создание компонентов и, следовательно, только компоненты могут иметь локальные метаданные. В приведенном выше примере мы попытались изменить свойство, например `Color` свойство объекта. Если параметр `false` был передан для глобального флага, `CustomBrowser` он никогда не будет отображаться, поскольку конструктор никогда не создает экземпляр `Color` . Установка глобального флага `false` будет полезна для таких компонентов, как элементы управления, таймеры и диалоговые окна.  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>   
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>   
 <xref:System.ComponentModel.ToolboxItemFilterType>   
 [Расширения поддержки времени разработки](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
