---
title: Инициализация конструктора и конфигурация метаданных (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e876dd9e6fa95bbe180d1737bc8c4911f16e1e9a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712215"
---
# <a name="designer-initialization-and-metadata-configuration"></a>Инициализация конструктора и конфигурация метаданных

Манипуляция атрибутами метаданных и фильтров, связанных с компонентом конструктора или конструктора, обеспечивает <xref:System.Type> механизм для приложений для определения того, какие инструменты используются конкретным дизайнером для обработки различных объектов (таких как структуры данных, классы или графические объекты), когда дизайнер доступен, и как настраивается IDE Visual Studio для поддержки дизайнера (например, какая категория **Toolbox** или вкладка доступна).

Предоставляет [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] несколько механизмов для облегчения контроля инициализации компонента дизайнера или дизайнера и манипулирования его метаданными VSPackage.

## <a name="initialize-metadata-and-configuration-information"></a>Инициализация метаданных и информации о конфигурации
 Поскольку они загружаются по требованию, VSPackages, возможно, не были загружены средой Visual Studio до момента мгновенного дизайнера. Таким образом, VSPackages не может использовать стандартный механизм настройки компонента конструктора или конструктора на создание, которое заключается в обработке <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> события. Вместо этого VSPackage реализует экземпляр <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> интерфейса и регистрирует сяочку, чтобы обеспечить настройки, называемые расширениями поверхности дизайна.

### <a name="customize-initialization"></a>Настройка инициализации

Настройка дизайнера, компонента или поверхности конструктора включает в себя:

1. Изменение метаданных конструктора и эффективное <xref:System.Type> изменение того, как определенный доступ или преобразован.

    Это обычно делается <xref:System.Drawing.Design.UITypeEditor> <xref:System.ComponentModel.TypeConverter> через или механизмы.

    Например, <xref:System.Windows.Forms>когда дизайнеры на основе визуальных средств <xref:System.Drawing.Design.UITypeEditor> инициализируются, среда Visual Studio изменяет <xref:System.Web.UI.WebControls.Image> объекты, используемые с конструктором, для использования менеджера ресурсов для получения бит-карт, а не файловой системы.

2. Интеграция с окружающей средой, например, путем подписки на события или получения информации о конфигурации проекта. Вы можете получить информацию о конфигурации <xref:System.ComponentModel.Design.ITypeResolutionService> проекта и подписаться на события, получив интерфейс.

3. Изменение среды пользователя путем активации соответствующих категорий **Toolbox** или ограничения применимости дизайнера, применяя экземпляр <xref:System.ComponentModel.ToolboxItemFilterAttribute> класса к дизайнеру.

### <a name="designer-initialization-by-a-vspackage"></a>Дизайнерская инициализация VSPackage

VSPackage должен обрабатывать дизайнерскую инициализацию:

1. Создание объекта, реализующего <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> класс.

   > [!NOTE]
   > Класс <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> никогда не должен реализовываться на том же объекте, что и <xref:Microsoft.VisualStudio.Shell.Package> класс.

2. Регистрация класса, который <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> реализуется как обеспечивающий поддержку расширения конструктора VSPackage. <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>Зарегистрируйте класс, применяя <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute>экземпляры, и <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> в класс, который <xref:Microsoft.VisualStudio.Shell.Package>обеспечивает реализацию VSPackage.

Всякий раз, когда создается компонент дизайнера или дизайнера, среда Visual Studio:

- Доступ к каждому зарегистрированной поставщику расширения поверхности дизайна.

- Мгновеннои и инициализирует экземпляр <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> объекта каждого объекта расширения поверхности каждого проекта.

- Вызывает <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> метод или <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> метод каждого поставщика расширения поверхности конструкции (по мере необходимости).

При реализации <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> объекта в качестве участника VSPackage важно понимать, что:

- Среда Visual Studio не обеспечивает никакого контроля над тем, какие `DesignSurfaceExtension` метаданные или другие настройки конфигурации изменяется конкретным поставщиком. Это возможно для двух `DesignSurfaceExtension` или более провайдеров изменения той же функции дизайнера в противоречивых способов, с окончательной модификации является окончательным. Это неопределенный, какая модификация в последнюю инстанцию применяется.

- Можно прямо ограничить реализацию <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> объекта конкретными конструкторами, применяя экземпляры <xref:System.ComponentModel.ToolboxItemFilterAttribute> этой реализации. Для получения дополнительной информации о <xref:System.ComponentModel.ToolboxItemFilterAttribute> фильтрации <xref:System.ComponentModel.ToolboxItemFilterType>элементов **Toolbox** см.

## <a name="additional-metadata-provisioning"></a>Дополнительное предоставление метаданных

VSPackage может изменить конфигурацию компонента конструктора или конструктора, кроме времени проектирования.

Класс <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> может быть использован программно или применен к VSPackage, который предоставляет дизайнера.

Экземпляр <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> класса используется для изменения метаданных компонентов, созданных на поверхности конструкции. Например, можно заменить браузер свойств <xref:System.Windows.Forms.CommonDialog> по умолчанию, используемый объектами, с помощью пользовательского браузера свойств.

Изменения, предоставляемые <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> экземпляром, применяемым <xref:Microsoft.VisualStudio.Shell.Package> к реализации VSPackage, могут иметь одну из двух областей:

- Глобальный - для всех новых экземпляров данного компонента

- Локально - относящийся только к экземпляру компонента, созданного на поверхности конструкции, предоставленной текущим VSPackage.

Свойство `IsGlobal` <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> экземпляра, применяемого к <xref:Microsoft.VisualStudio.Shell.Package> реализации VSPackage определяет эту область.

<xref:Microsoft.VisualStudio.Shell.Package> Применение атрибута к реализации <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> с свойством <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> объекта, установленного, `true`как показано ниже, изменяет браузер для всей среды Visual Studio:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`

`internal class MyPackage : Package {}`

Если глобальный флаг `false`был установлен на , то изменение метаданных является локальным для текущего дизайнера, поддерживаемого текущим VSPackage:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`

`internal class MyPackage : Package {}`

> [!NOTE]
> Поверхность конструкции поддерживает только создание компонентов, и поэтому только компоненты могут иметь локальные метаданные. В приведенном выше примере мы пытались изменить `Color` свойство, например свойство объекта. Если `false` был принят в для `CustomBrowser` глобального флага, `Color`никогда не появится, потому что дизайнер никогда не создает экземпляр . Установка глобального `false` флага для компонентов, таких как элементы управления, таймеры и диалоговые коробки.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>
- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>
- <xref:System.ComponentModel.ToolboxItemFilterType>
- [Расширить поддержку времени проектирования](https://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
