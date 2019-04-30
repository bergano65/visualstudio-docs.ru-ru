---
title: Миграция расширяемость конструктора XAML
ms.date: 04/17/2019
ms.topic: conceptual
author: lutzroeder
ms.author: lutzr
manager: jillfra
monikerRange: vs-2019
ms.openlocfilehash: f83c40a67dc36301816b2384242d790a9f776044
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63447362"
---
# <a name="xaml-designer-extensibility-migration"></a>Миграция расширяемость конструктора XAML

Начиная с версии 16.1 в общедоступной предварительной версии 2019 г. Visual Studio, конструктор XAML поддерживает две различные архитектуры: архитектура конструктора изоляции и более новой архитектуры поверхности изоляции. Этот переход архитектура необходима для поддержки целевыми средами выполнения, который не может быть размещен в процессе .NET Framework. Перемещение в архитектуре поверхности изоляции вводятся принципиальные изменения в модель расширяемости сторонних. В этой статье перечислены изменения.

**Конструктора изоляции** используется в конструкторе WPF для проектов, предназначенных для .NET Framework и поддерживает *. design.dll* расширения. Пользовательский код, библиотеки элементов управления и сторонние расширения загружаются во внешнем процессе (*XDesProc.exe*) вместе с фактический код конструктора и панели конструктора.

**Область изоляции** используется конструктором универсальной платформы Windows. Он также используется в конструкторе WPF для проектов, предназначенных для .NET Core. Surface изолированно, библиотеки кода и управления единственным пользователем загружаются в отдельном процессе, пока конструктор и его панели загружаются в процесс Visual Studio (*DevEnv.exe*). Среды выполнения, используемый для выполнения кода и управления библиотеках пользователей отличается от используемого в .NET Framework для фактического конструктора и кода поддержки расширяемости сторонними.

![Архитектура расширения миграции](media/xaml-designer-extensibility-migration-architecture.png)

В результате такого перехода архитектура сторонние расширения больше не загружаются в одном процессе с библиотеками управления стороннего. Расширения больше не могут иметь прямых зависимостей от библиотек управления либо непосредственный доступ к объекты среды выполнения. Расширения, которые ранее были записаны для архитектуры конструктора изоляции с помощью *Microsoft.Windows.Extensibility.dll* API должны быть перенесены в новый подход для работы с архитектурой поверхности изоляции. На практике существующего расширения необходимо скомпилировать новые сборки API расширяемости. Типы доступа к элементу управления среды выполнения с помощью [typeof](/dotnet/csharp/language-reference/keywords/typeof) или экземпляров среды выполнения необходимо заменить или удалить, так как загрузка библиотеки элементов управления в другом процессе.

## <a name="new-extensibility-api-assemblies"></a>Новые сборки API расширяемости

Новые сборки API расширяемости похожи на существующие сборки API расширяемости, но выполните другую схему именования, чтобы различать их. Аналогичным образом имена пространств имен были изменены для отражения новых имен сборки.

| Конструктора изоляции сборки API            | Сборка поверхности изоляции API                       |
|:------------------------------------------ |:---------------------------------------------------- |
| Microsoft.Windows.Design.Extensibility.dll | Microsoft.VisualStudio.DesignTools.Extensibility.dll |
| Microsoft.Windows.Design.Interaction.dll   | Microsoft.VisualStudio.DesignTools.Interaction.dll   |

## <a name="new-file-extension-and-discovery"></a>Новое расширение файла и обнаружения

Вместо использования *. design.dll* расширение, новую поверхность extensions обнаруживаются с помощью файла *. designtools.dll* расширение файла. *. design.dll* и *. designtools.dll* расширения может находиться в одном *разработки* во вложенную папку.

Хотя библиотеки элементов управления сторонних компилируются для среды выполнения фактический целевой (.NET Core или UWP), *. designtools.dll* расширения всегда должны быть скомпилированы как сборки .NET Framework.

## <a name="decouple-attribute-tables-from-runtime-types"></a>Отделить таблиц атрибутов с типами среды выполнения

Модель расширяемости поверхности изоляции не допускает для расширений, чтобы он зависел от библиотеки фактического элемента управления, и таким образом, расширения не может ссылаться на типы из библиотеки элементов управления. Например *MyLibrary.designtools.dll* следует не зависят от *MyLibrary.dll*.

Такие зависимости были наиболее распространенных при регистрации метаданных для типов с помощью таблиц атрибутов. Типы код расширения, который ссылается на библиотеки элементов управления напрямую через [typeof](/dotnet/csharp/language-reference/keywords/typeof) подставляется в новых интерфейсов API с помощью имен строковых типов:

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
      AttributeTableBuilder builder = new AttributeTableBuilder();
      builder.AddCustomAttributes("MyLibrary.MyControl", new DescriptionAttribute(Strings.MyControlDescription);
      builder.AddCustomAttributes("MyLibrary.MyControl", new FeatureAttribute(typeof(MyControlDefaultInitializer));
      return builder.CreateTable();
    }
  }
}
```

## <a name="feature-providers-and-model-api"></a>Поставщики функций и API модели

Поставщики функций реализуются в сборках, расширение и загруженных в процесс Visual Studio. `FeatureAttribute` продолжат ссылаться на типы поставщика функцию напрямую с помощью [typeof](/dotnet/csharp/language-reference/keywords/typeof).

Так как поставщики функций теперь загружаются в процесс, отличается от библиотеки времени исполнения кода и управления, они больше не может получить доступ непосредственно к объекты среды выполнения. Вместо этого все взаимодействия необходимо преобразовать для использования соответствующие API на основе моделей. API модели была обновлена, а доступ к <xref:System.Type> или <xref:System.Object> либо более недоступны или были заменены `TypeIdentifier` и `TypeDefinition`.

`TypeIdentifier` Представляет строку без определения типа имя сборки. Объект `TypeIdenfifier` можно привести к `TypeDefinition` для запроса дополнительных сведений о типе. `TypeDefinition` экземпляры не может кэшироваться в коде расширения.

```csharp
TypeDefinition type = ModelFactory.ResolveType(
    item.Context, new TypeIdentifier("MyLibrary.MyControl"));
TypeDefinition buttonType = ModelFactory.ResolveType(
    item.Context, new TypeIdentifier("System.Windows.Controls.Button"));
if (type != null && buttonType != type.IsSubclassOf(buttonType))
{
}
```

API-интерфейсы, удаленное из набора API расширяемости поверхности изоляции:

* `ModelFactory.CreateItem(EditingContext context, object item)`
* `ViewItem.PlatformObject`
* `ModelProperty.DefaultValue`

Интерфейсы API, использующие `TypeIdentifier` вместо <xref:System.Type>:

* `ModelFactory.CreateItem(EditingContext context, Type itemType, params object[] arguments)`
* `ModelFactory.CreateItem(EditingContext context, Type itemType, CreateOptions options, params object[] arguments)`
* `ModelFactory.CreateStaticMemberItem(EditingContext context, Type type, string memberName)`
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

Интерфейсы API, использующие `TypeIdentifier` вместо <xref:System.Type> и больше не поддерживает аргументы конструктора:

* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, params object[] arguments)`
* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, CreateOptions options, params object[] arguments)`

Интерфейсы API, использующие `TypeDefinition` вместо <xref:System.Type>:

* `ModelFactory.ResolveType(EditingContext context, TypeIdentifier typeIdentifier)`
* `ValueTranslationService.GetProperties(Type itemType)`
* `ValueTranslationService.HasValueTranslation(Type itemType, PropertyIdentifier identifier)`
* `ValueTranslationService.TranslatePropertyValue(Type itemType, ModelItem item, PropertyIdentifier identifier, object value)`
* `ModelService.Find(ModelItem startingItem, Type type)`
* `ModelService.Find(ModelItem startingItem, Predicate<Type> match)`
* `ModelItem.ItemType`
* `ModelProperty.AttachedOwnerType`
* "ModelProperty.PropertyType
* `FeatureManager.CreateFeatureProviders(Type featureProviderType, Type type)`
* `FeatureManager.CreateFeatureProviders(Type featureProviderType, Type type, Predicate<Type> match)`
* `FeatureManager.InitializeFeatures(Type type)`
* `FeatureManager.GetCustomAttributes(Type type, Type attributeType)`
* `AdapterService.GetAdapter<TAdapterType>(Type itemType)`
* `AdapterService.GetAdapter(Type adapterType, Type itemType)`

Интерфейсы API, использующие `ModelItem` вместо <xref:System.Object>:

* `ModelItemCollection.Insert(int index, object value)`
* `ModelItemCollection.Remove(object value)`
* `ModelItemDictionary.Add(object key, object value)`
* `ModelItemDictionary.ContainsKey(object key)`
* `ModelItemDictionary.Remove(object key)`
* `ModelItemDictionary.TryGetValue(object key, out ModelItem value)`

Известные типы-примитивы, такие как `int`, `string`, или `Thickness` может передаваться в API модели как экземпляры .NET Framework и будет преобразован в соответствующий объект в целевом процессе среда выполнения. Пример:

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

## <a name="limited-support-for-designdll-extensions"></a>Ограниченная поддержка. design.dll расширений

При наличии *. designtools.dll* расширение было обнаружено для библиотеки элементов управления, он загружается первый и обнаружения *. design.dll* расширения пропускается.

Если не *. designtools.dll* расширения присутствуют, но *. design.dll* расширение обнаружено, языковая служба XAML пытается загрузить эту сборку можно извлечь сведения таблицы атрибутов для поддержки простой редактор и сценариев инспектора свойств. Этот механизм ограничен областью. Он не допускает загрузку конструктора изоляции расширений для выполнения поставщиков функций, но может предоставить базовую поддержку для существующей библиотеки элементов управления WPF.
