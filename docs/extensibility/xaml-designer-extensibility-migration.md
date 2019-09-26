---
title: Миграция Конструктор XAML расширяемости
ms.date: 07/09/2019
ms.topic: conceptual
author: lutzroeder
ms.author: lutzr
manager: jillfra
dev_langs:
- csharp
- vb
monikerRange: vs-2019
ms.openlocfilehash: 9f5085c7a655f186c3c8a4a6eecada8b440650cd
ms.sourcegitcommit: 528178a304e66c0cb7ab98b493fe3c409f87493a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2019
ms.locfileid: "71273221"
---
# <a name="xaml-designer-extensibility-migration"></a>Миграция расширяемости конструктора XAML

В Visual Studio 2019 конструктор XAML поддерживает две различные архитектуры: архитектура изоляции конструктора и более свежую архитектуру изоляции поверхности. Этот переход архитектуры необходим для поддержки целевых сред выполнения, которые не могут быть размещены в .NET Framework процессе. Переход на архитектуру изоляции Surface вводит критические изменения в модель расширяемости стороннего разработчика. В этой статье описаны эти изменения, которые доступны в Visual Studio 2019 начиная с версии 16,3.

**Изоляция конструктора** используется конструктором WPF для проектов, предназначенных для .NET Framework и поддерживает расширения *Design. dll* . Пользовательский код, библиотеки элементов управления и сторонние расширения загружаются во внешний процесс (*ксдеспрок. exe*) вместе с реальными панелями кода и конструктора.

**Изоляция поверхности** используется конструктором UWP. Он также используется конструктором WPF для проектов, предназначенных для .NET Core. В режиме изоляции Surface только пользовательские код и библиотеки элементов управления загружаются в отдельный процесс, а конструктор и его панели загружаются в процесс Visual Studio (*devenv. exe*). Среда выполнения, используемая для выполнения пользовательского кода и библиотек элементов управления, отличается от среды, используемой .NET Framework для фактического конструктора и кода расширяемости стороннего разработчика.

![Расширяемость-миграция-архитектура](media/xaml-designer-extensibility-migration-architecture.png)

Из-за этого перехода архитектуры сторонние расширения больше не загружаются в тот же процесс, что и сторонние библиотеки элементов управления. Расширения больше не могут иметь прямые зависимости от библиотек элементов управления или напрямую обращаться к объектам времени выполнения. Расширения, написанные ранее для архитектуры изоляции конструктора с помощью API *Microsoft. Windows. Extensibility. dll* , должны быть перенесены на новый подход к работе с архитектурой изоляции Surface. На практике существующее расширение должно быть скомпилировано для новых сборок API расширения. Доступ к типам управления времени выполнения через [typeof](/dotnet/csharp/language-reference/keywords/typeof) или экземпляры времени выполнения необходимо заменить или удалить, так как теперь библиотеки элементов управления загружаются в другом процессе.

## <a name="new-extensibility-api-assemblies"></a>Новые сборки API расширения

Новые сборки API расширяемости похожи на существующие сборки API расширения, но следуют другой схеме именования, чтобы отличать их друг от друга. Аналогичным образом имена пространств имен изменились, чтобы отразить новые имена сборок.

| Сборка API изоляции конструктора            | Сборка API изоляции Surface                       |
|:------------------------------------------ |:---------------------------------------------------- |
| Microsoft. Windows. Design. Extensibility. dll | Microsoft. VisualStudio. Десигнтулс. Extensibility. dll |
| Microsoft. Windows. Design. взаимодействие. dll   | Microsoft. VisualStudio. Десигнтулс. взаимодействие. dll   |

## <a name="new-file-extension-and-discovery"></a>Новое расширение и обнаружение файлов

Вместо использования расширения файла *. Design. dll* новые расширения Surface будут обнаружены с помощью расширения файла *. десигнтулс. dll* . *. Design. dll* и *. десигнтулс. dll* могут существовать в одной подпапке *конструктора* .

Хотя сторонние библиотеки элементов управления компилируются для фактической целевой среды выполнения (.NET Core или UWP), расширение *. десигнтулс. dll* всегда должно быть скомпилировано как сборка .NET Framework.

## <a name="decouple-attribute-tables-from-run-time-types"></a>Отделение таблиц атрибутов от типов времени выполнения

Модель расширяемости изоляции Surface не допускает, чтобы расширения зависели от реальных библиотек элементов управления, поэтому расширения не могут ссылаться на типы из библиотеки элементов управления. Например, *файл MyLibrary. десигнтулс. dll* не должен иметь зависимость от *MyLibrary. dll*.

Такие зависимости наиболее распространены при регистрации метаданных для типов через таблицы атрибутов. Код расширения, который ссылается на типы библиотек элементов управления непосредственно через [typeof](/dotnet/csharp/language-reference/keywords/typeof) или [GetType](/dotnet/visual-basic/language-reference/operators/gettype-operator) , подставляется в новые интерфейсы API с использованием имен типов на основе строк:

```csharp
using Microsoft.VisualStudio.DesignTools.Extensibility.Metadata;
using Microsoft.VisualStudio.DesignTools.Extensibility.Features;
using Microsoft.VisualStudio.DesignTools.Extensibility.Model;

[assembly: ProvideMetadata(typeof(AttributeTableProvider))]

public class AttributeTableProvider : IProvideAttributeTable
{
  public AttributeTable AttributeTable
  {
    get
    {
      var builder = new AttributeTableBuilder();
      builder.AddCustomAttributes("MyLibrary.MyControl", new DescriptionAttribute(Strings.MyControlDescription);
      builder.AddCustomAttributes("MyLibrary.MyControl", new FeatureAttribute(typeof(MyControlDefaultInitializer));
      return builder.CreateTable();
    }
  }
}
```

```vb
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Metadata
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Features
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Model

<Assembly: ProvideMetadata(GetType(AttributeTableProvider))>

Public Class AttributeTableProvider
    Implements IProvideAttributeTable

    Public ReadOnly Property AttributeTable As AttributeTable Implements IProvideAttributeTable.AttributeTable
        Get
            Dim builder As New AttributeTableBuilder
            builder.AddCustomAttributes("MyLibrary.MyControl", New DescriptionAttribute(Strings.MyControlDescription))
            builder.AddCustomAttributes("MyLibrary.MyControl", New FeatureAttribute(GetType(MyControlDefaultInitializer)))
            Return builder.CreateTable()
        End Get
    End Property
End Class
```

## <a name="feature-providers-and-model-api"></a>Поставщики функций и API модели

Поставщики функций реализуются в сборках расширения и загружаются в процесс Visual Studio. `FeatureAttribute`службы продолжат ссылаться на типы поставщиков функций непосредственно с помощью [typeof](/dotnet/csharp/language-reference/keywords/typeof).

В настоящее время поддерживаются следующие поставщики функций:

* `DefaultInitializer`
* `AdornerProvider`
* `ContextMenuProvider`
* `ParentAdapter`
* `PlacementAdapter`
* `DesignModeValueProvider`поддерживается с ограничением, которое `TranslatePropertyValue` будет вызываться через `InvalidateProperty` или при изменении в конструкторе. Он не будет вызываться при изменении кода во время выполнения.

Поскольку поставщики компонентов теперь загружаются в процессе, отличном от фактического кода времени выполнения и библиотек элементов управления, они больше не могут напрямую обращаться к объектам времени выполнения. Вместо этого все такие взаимодействия должны быть преобразованы для использования соответствующих интерфейсов API на основе модели. API модели обновлен, доступ <xref:System.Type> к или <xref:System.Object> больше недоступен или был заменен на `TypeIdentifier` и `TypeDefinition`.

`TypeIdentifier`представляет строку без имени сборки, определяющей тип. Можно разрешить в, `TypeDefinition` чтобы запросить дополнительные сведения о типе. `TypeIdenfifier` `TypeDefinition`экземпляры не могут кэшироваться в коде расширения.

```csharp
TypeDefinition type = ModelFactory.ResolveType(
    item.Context, new TypeIdentifier("MyLibrary.MyControl"));
TypeDefinition buttonType = ModelFactory.ResolveType(
    item.Context, new TypeIdentifier("System.Windows.Controls.Button"));
if (type?.IsSubclassOf(buttonType) == true)
{
}
```

```vb
Dim type As TypeDefinition = ModelFactory.ResolveType(
    item.Context, New TypeIdentifier("MyLibrary.MyControl"))
Dim buttonType As TypeDefinition = ModelFactory.ResolveType(
    item.Context, New TypeIdentifier("System.Windows.Controls.Button"))
If type?.IsSubclassOf(buttonType) Then

End If
```

API, удаленные из набора API-интерфейсов расширения изоляции Surface:

* `ModelFactory.CreateItem(EditingContext context, object item)`
* `ViewItem.PlatformObject`
* `ModelProperty.DefaultValue`
* `AssemblyReferences.GetTypes(Type baseType)`

API-интерфейсы `TypeIdentifier` , использующие <xref:System.Type>вместо:

* `ModelFactory.CreateItem(EditingContext context, Type itemType, params object[] arguments)`
* `ModelFactory.CreateItem(EditingContext context, Type itemType, CreateOptions options, params object[] arguments)`
* `ModelFactory.CreateStaticMemberItem(EditingContext context, Type type, string memberName)`
* Замена `ModelFactory.ResolveType(EditingContext context, Type)` на `MetadataFactory.ResolveType(EditingContext context, TypeIdentifier typeIdentifier)`
* Замена `ModelService.ResolveType(TypeIdentifier typeIdentifier)` на `MetadataService.ResolveType(TypeIdentifier typeIdentifier)`
* `ViewItem.ItemType`
* `ModelEvent.EventType`
* `ModelEvent.IsEventOfType(Type type)`
* `ModeItem.IsItemOfType(Type type)`
* `ModelParent.CanParent(EditingContext context, ModelItem parent, Type childType)`
* `ModelParent.FindParent(EditingContext context, Type childType, ModelItem startingItem)`
* `ModelParent.FindParent(Type childType, GestureData gestureData)`
* `ModelProperty.IsPropertyOfType(Type type)`
* `ParentAdpater.CanParent(ModelItem parent, Type childType)`
* `ParentAdapter.RedirectParent(ModelItem parent, Type childType)`

API-интерфейсы `TypeIdentifier` , использующие <xref:System.Type> вместо и больше не поддерживают аргументы конструктора:

* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, params object[] arguments)`
* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, CreateOptions options, params object[] arguments)`

API-интерфейсы `TypeDefinition` , использующие <xref:System.Type>вместо:

* `ValueTranslationService.GetProperties(Type itemType)`
* `ValueTranslationService.HasValueTranslation(Type itemType, PropertyIdentifier identifier)`
* `ValueTranslationService.TranslatePropertyValue(Type itemType, ModelItem item, PropertyIdentifier identifier, object value)`
* `ModelService.Find(ModelItem startingItem, Type type)`
* `ModelService.Find(ModelItem startingItem, Predicate<Type> match)`
* `ModelItem.ItemType`
* `ModelProperty.AttachedOwnerType`
* `ModelProperty.PropertyType`
* `FeatureManager.CreateFeatureProviders(Type featureProviderType, Type type)`
* `FeatureManager.CreateFeatureProviders(Type featureProviderType, Type type, Predicate<Type> match)`
* `FeatureManager.InitializeFeatures(Type type)`
* `FeatureManager.GetCustomAttributes(Type type, Type attributeType)`
* `AdapterService.GetAdapter<TAdapterType>(Type itemType)`
* `AdapterService.GetAdapter(Type adapterType, Type itemType)`
* `PropertyEntry.PropertyType`

API-интерфейсы `AssemblyIdentifier` , использующие `<xref:System.Reflection.AssemblyName?displayProperty=fullName>`вместо:

* `AssemblyReferences.ReferencedAssemblies`
* Замена `AssemblyReferences.LocalAssemblyName` на `AssemblyReferences.LocalAssemblyIdentifier`

Кроме того `ModelItem` , интерфейсы `SetValue` API, такие как, поддерживают только экземпляры простых типов или встроенных типов .NET Framework, которые можно преобразовать в целевую среду выполнения. В настоящее время поддерживаются следующие типы:

* Примитивные типы .NET Framework `Boolean`: `Byte`, `Char`, `DateTime`, `Double`, ,`Enum`, ,`Int16`, ,`Nullable`,, `Int32` `Int64` `Guid` `SByte` , `Single`, `String`, `Type`, `UInt16`, `UInt32`, `UInt64`,`Uri`
* Известные типы .NET Framework WPF (и производные типы) `Brush`: `Color`, `CompositeTransform`, `CornerRadius`, `Duration`, `EasingFunctionBase`, `EasingMode`, `EllipseGeometry`, `FontFamily`, `GeneralTransform`, `Geometry` , , `GradientStopCollection`, `GradientStop`, `GridLength`, `ImageSource`, `InlineCollection`, `Inline`, `KeySpline`, `Material`, `Matrix`, `PathFigureCollection`, `PathFigure`, `PathSegmentCollection`, `PathSegment`, `Path`, `PointCollection`, `Point`, `PropertyPath`, `Rect`, `RepeatBehavior`, `Setter`, `Size`, `StaticResource`, `TextAlignment`, `TextDecorationCollection`, `ThemeResourceExtension`, `Thickness`, `TimeSpan`, `Transform3D`,`TransformCollection`

Например:

```csharp
using Microsoft.VisualStudio.DesignTools.Extensibility.Features;
using Microsoft.VisualStudio.DesignTools.Extensibility.Model;

public class MyControlDefaultInitializer : DefaultInitializer
{
  public override void InitializeDefaults(ModelItem item)
  {
    item.Properties["Width"].SetValue(800d);
    base.InitializeDefaults(item);
  }
}
```

```vb
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Features
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Model

Public Class MyControlDefaultInitializer
    Inherits DefaultInitializer

    Public Overrides Sub InitializeDefaults(item As ModelItem)
        item.Properties!Width.SetValue(800.0)
        MyBase.InitializeDefaults(item)
    End Sub
End Class
```

Дополнительные примеры кода доступны в репозитории [XAML-Designer-Extensibility-Samples](https://github.com/microsoft/xaml-designer-extensibility-samples) .

## <a name="limited-support-for-designdll-extensions"></a>Ограниченная поддержка для расширений. Design. dll

Если обнаружено какое-либо расширение *десигнтулс. dll* для библиотеки элементов управления, оно сначала загружается, а обнаружение для расширения *. Design. dll* пропускается.

Если расширения. *десигнтулс. dll* отсутствуют, но обнаружено расширение *. Design. dll* , служба языка XAML пытается загрузить эту сборку для извлечения сведений таблицы атрибутов для поддержки базовых сценариев редактора и инспектора свойств. Этот механизм ограничен в области. Он не позволяет загружать расширения изоляции конструктора для выполнения поставщиков функций, но может обеспечивать базовую поддержку существующих библиотек элементов управления WPF.
