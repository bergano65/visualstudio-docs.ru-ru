---
title: Добавление свойства отслеживания в определение предметно-ориентированного языка | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- tracking properties [Domain-Specific Language Tools], walkthrough
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
ms.assetid: 4aa47777-de75-4897-a423-a3c4426b4125
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1e98a5902495528082a8328befe724c91f01a3d0
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2020
ms.locfileid: "75852402"
---
# <a name="adding-a-tracking-property-to-a-domain-specific-language-definition"></a>Добавление свойства отслеживания в определение доменного языка
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве показано, как добавить свойство отслеживания в модель предметной области.

 Свойство *домена отслеживания* — это свойство, которое может быть обновлено пользователем, но имеет значение по умолчанию, вычисляемое с использованием значений других свойств или элементов домена.

 Например, в Средства предметно-ориентированных языков (средства DSL) свойство "отображаемое имя" доменного класса имеет значение по умолчанию, вычисляемое с помощью имени доменного класса, но пользователь может изменить это значение во время разработки или сбросить его до вычисляемого значения.

 В этом пошаговом руководстве вы создадите доменный язык (DSL) с свойством отслеживания пространства имен, имеющим значение по умолчанию, основанное на свойстве пространства имен по умолчанию для модели. Дополнительные сведения о свойствах отслеживания см. в разделе [Определение свойств отслеживания](https://msdn.microsoft.com/0538b0e4-6221-4e7d-911a-b92cd622f0be).

- Средства DSL поддерживают дескрипторы свойств отслеживания. Однако конструктор DSL нельзя использовать для добавления свойства отслеживания в язык. Поэтому необходимо добавить пользовательский код для определения и реализации свойства отслеживания.

  Свойство отслеживания имеет два состояния: отслеживание и обновление пользователем. Свойства отслеживания имеют следующие характеристики.

- В состоянии отслеживания значение свойства отслеживания вычисляется, и значение обновляется по мере изменения других свойств модели.

- При изменении состояния пользователя значение свойства отслеживания оставляет значение, которое пользователь последним установил свойство.

- В окне **Свойства** команда **сброса** для свойства Отслеживание включается только в том случае, если свойство находится в состоянии Обновлено пользователем. Команда **Reset** устанавливает отслеживаемое состояние свойства.

- В окне **Свойства** , если свойство отслеживания находится в состоянии отслеживания, его значение отображается в обычном шрифте.

- В окне **Свойства** , когда свойство отслеживания находится в состоянии Обновлено пользователем, его значение отображается полужирным шрифтом.

## <a name="prerequisites"></a>Prerequisites
 Перед началом работы с этим пошаговым руководством необходимо сначала установить следующие компоненты:

|||
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](https://www.visualstudio.com/)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](https://docs.microsoft.com/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts)|
|[!INCLUDE[dsl](../includes/dsl-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185581](https://docs.microsoft.com/samples/browse/?redirectedfrom=MSDN-samples)|

## <a name="creating-the-dsl-project"></a>Создание проекта DSL
 Создайте проект для конкретного доменного языка.

#### <a name="to-create-the-project"></a>Создание проекта

1. Создайте проект Конструктор предметно-ориентированных языков. Присвойте обработчику события имя `TrackingPropertyDSL`.

2. В **мастере конструктор предметно-ориентированных языков**задайте следующие параметры.

    1. Выберите шаблон **минималлангуаже** .

    2. Используйте имя по умолчанию для предметно-ориентированного языка `TrackingPropertyDSL`.

    3. Задайте для расширения файлов модели значение `trackingPropertyDsl`.

    4. Используйте значок шаблона по умолчанию для файлов модели.

    5. Задайте имя продукта для `Product Name`.

    6. Задайте имя компании, `Company Name`.

    7. Используйте значение по умолчанию для корневого пространства имен проектов в решении `CompanyName.ProductName.TrackingPropertyDSL`.

    8. Разрешите мастеру создать файл ключа строгого имени для сборок.

    9. Просмотрите сведения о решении и нажмите кнопку **Готово** , чтобы создать проект определения DSL.

## <a name="customizing-the-default-dsl-definition"></a>Настройка определения DSL по умолчанию
 В этом разделе вы настроите определение DSL, чтобы оно содержало следующие элементы:

- Свойство отслеживания пространства имен для каждого элемента модели.

- Логическое свойство Иснамеспацетраккинг для каждого элемента модели. Это свойство будет указывать, находится ли свойство отслеживания в состоянии отслеживания или в обновленном состоянии пользователем.

- Свойство пространства имен по умолчанию для модели. Это свойство будет использоваться для вычисления значения по умолчанию для свойства отслеживания пространства имен.

- Вычисляемое свойство Кустомелементс для модели. Это свойство будет указывать долю элементов, имеющих пользовательское пространство имен.

#### <a name="to-add-the-domain-properties"></a>Добавление свойств домена

1. В конструкторе DSL щелкните правой кнопкой мыши класс домена **пространстве ExampleModel** , наведите указатель на пункт **Добавить**и выберите пункт **DomainProperty**.

    1. Назовите новое свойство `DefaultNamespace`.

    2. В окне **Свойства** нового свойства задайте **значение по умолчанию** `DefaultNamespace`и присвойте параметру **тип** **строковое**.

2. В доменный класс **пространстве ExampleModel** добавьте свойство домена с именем `CustomElements`.

     В окне **Свойства** нового свойства задайте для параметра **тип** значение **вычисляемое**.

3. В доменный класс **ексамплилемент** добавьте свойство домена с именем `Namespace`.

     В окне **Свойства** для нового **Свойства задайте для параметра значение значение** **false**и задайте для параметра **тип** значение **CustomStorage**.

4. В доменный класс **ексамплилемент** добавьте свойство домена с именем `IsNamespaceTracking`.

     В окне **Свойства** для нового свойства задайте для параметра вид значение **false**, в поле **по умолчанию** **—** `true`, а для параметра **тип** — **логическое**.

#### <a name="to-update-the-diagram-elements-and-dsl-details"></a>Обновление элементов схемы и сведений о DSL

1. В конструкторе DSL щелкните правой кнопкой мыши фигуру Geometry **ексамплешапе** , наведите указатель на пункт **Добавить**, а затем выберите **текст декоратор**.

    1. Назовите новый декоратор текста `NamespaceDecorator`.

    2. В окне **Свойства** декоратора текста задайте для параметра **Расположение** значение **InnerBottomLeft**.

2. В конструкторе DSL выберите строку, соединяющую класс **ексамплилемент** с фигурой **ексамплешапе** .

    1. В окне **сведения о DSL** перейдите на вкладку **карты декораторов** .

    2. В списке **декораторов** выберите **намеспацедекоратор**, установите его флажок, а затем в списке **отображаемое свойство** выберите **пространство имен**.

3. В **обозревателе DSL**разверните папку **классы доменов** , щелкните правой кнопкой мыши узел **Ексамплилемент** и выберите команду **Добавить новый дескриптор типа домена**.

    1. Разверните узел **ексамплилемент** и выберите узел **дескриптор настраиваемого типа (дескриптор типа домена)** .

    2. В окне **Свойства** для дескриптора типа домена присвойте параметру **Custom закодировано** **значение true**.

4. В **обозревателе DSL**выберите узел **поведение сериализации XML** .

    1. В окне **Свойства** установите для параметра **Пользовательская** отправка **значение true**.

## <a name="transforming-templates"></a>Преобразование шаблонов
 После определения доменных классов и свойств для DSL можно убедиться, что определение DSL может быть правильно преобразовано для повторного создания кода проекта.

#### <a name="to-transform-the-text-templates"></a>Преобразование текстовых шаблонов

1. На панели инструментов **Обозреватель решений** нажмите кнопку **преобразовать все шаблоны**.

2. Система повторно создает код для решения и сохраняет DslDefinition. DSL. Дополнительные сведения о XML-формате файлов определений см. [в файле DslDefinition. DSL](../modeling/the-dsldefinition-dsl-file.md).

## <a name="creating-files-for-custom-code"></a>Создание файлов для пользовательского кода
 При преобразовании всех шаблонов система создает исходный код, определяющий доменный язык в проектах DSL и DslPackage. Чтобы избежать конфликта с созданным текстом, напишите пользовательский код в файлах, которые отличаются от созданных файлов кода.

 Необходимо указать код для сохранения значения и состояния свойства отслеживания. Чтобы облегчить различение пользовательского кода от созданного кода и избежать конфликтов именования файлов, разместите файлы пользовательского кода в отдельной вложенной папке.

#### <a name="to-create-the-code-files"></a>Создание файлов кода

1. В **Обозреватель решений**щелкните правой кнопкой мыши проект **DSL** , наведите указатель на пункт **добавить**и выберите пункт **создать папку**. Назовите новую папку `CustomCode`.

2. Щелкните правой кнопкой мыши новую папку **значение CustomCode** , выберите команду **Добавить**, а затем пункт **новый элемент**.

3. Выберите шаблон **файл кода** , задайте **имя** для `NamespaceTrackingProperty.cs`и нажмите кнопку **ОК**.

     Файл NamespaceTrackingProperty.cs создается и открывается для редактирования.

4. В папке создайте следующие файлы кода: `ExampleModel.cs,``HelperClasses.cs`, `Serialization.cs`и `TypeDescriptor.cs`.

5. В проекте **DslPackage** также создайте папку `CustomCode` и добавьте в нее файл `Package.cs` Code.

## <a name="adding-helper-classes-to-support-tracking-properties"></a>Добавление вспомогательных классов для поддержки свойств отслеживания
 В файл HelperClasses.cs добавьте классы `TrackingHelper` и `CriticalException`, как показано ниже. Далее в этом пошаговом руководстве вы будете ссылаться на эти классы.

#### <a name="to-add-the-helper-classes"></a>Добавление вспомогательных классов

1. Добавьте следующий код в файл HelperClasses.cs.

    ```csharp
    using System;
    using System.Collections;
    using System.Diagnostics;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        internal static class TrackingHelper
        {
            /// <summary>Notify each model element in a collection that a tracked
            /// property has changed.</summary>
            /// <param name="store">The store for the model.</param>
            /// <param name="collection">The collection of model elements that
            /// contain the tracking property.</param>
            /// <param name="propertyId">The ID of the tracking property.</param>
            /// <param name="trackingPropertyId">The ID of the property that
            /// indicates whether the tracking property is tracking.</param>
            internal static void UpdateTrackingCollectionProperty(
                Store store,
                IEnumerable collection,
                Guid propertyId,
                Guid trackingPropertyId)
            {
                DomainPropertyInfo propInfo =
                    store.DomainDataDirectory.GetDomainProperty(propertyId);

                DomainPropertyInfo trackingPropInfo =
                    store.DomainDataDirectory.GetDomainProperty(trackingPropertyId);

                Debug.Assert(propInfo != null);
                Debug.Assert(trackingPropInfo != null);
                Debug.Assert(trackingPropInfo.PropertyType.Equals(typeof(bool)),
                    "Tracking property not specified as a boolean");

                foreach (ModelElement element in collection)
                {
                    // If the tracking property is currently tracking, then notify
                    // it that the tracked property has changed.
                    bool isTracking = (bool)trackingPropInfo.GetValue(element);
                    if (isTracking)
                    {
                        propInfo.NotifyValueChange(element);
                    }
                }
            }
        }

        /// <summary>Helper class to flag critical exceptions from ones that are
        /// safe to ignore.</summary>
        internal static class CriticalException
        {
            /// <summary>Gets whether an exception is critical and can not be
            /// ignored.</summary>
            /// <param name="ex">The exception to check.</param>
            /// <returns>True if the exception is critical.</returns>
            internal static bool IsCriticalException(Exception ex)
            {
                if (ex is NullReferenceException
                    || ex is StackOverflowException
                    || ex is OutOfMemoryException
                    || ex is System.Threading.ThreadAbortException)
                    return true;

                if (ex.InnerException != null)
                    return IsCriticalException(ex.InnerException);

                return false;
            }
        }
    }
    ```

## <a name="adding-custom-code-for-the-custom-type-descriptor"></a>Добавление пользовательского кода для пользовательского дескриптора типа
 Реализуйте метод `GetCustomProperties` для дескриптора типа `ExampleModel` доменного класса.

> [!NOTE]
> Код, создаваемый инструментами DSL для пользовательского дескриптора типа для `ExampleModel` вызывает `GetCustomProperties`; Однако средства DSL не создают код, реализующий метод.

 При определении этого метода создается дескриптор свойства отслеживания для свойства отслеживания пространства имен. Кроме того, предоставление атрибутов для свойства отслеживания позволяет окну **свойств** правильно отображать свойство.

#### <a name="to-modify-the-type-descriptor-for-the-examplemodel-domain-class"></a>Изменение дескриптора типа для доменного класса пространстве ExampleModel

1. Добавьте следующий код в файл TypeDescriptor.cs.

    ```csharp
    using System;
    using System.ComponentModel;
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Design;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // To the custom type descriptor for the ExampleElement domain class, add
        // the GetCustomProperties method.
        public partial class ExampleElementTypeDescriptor
        {
            /// <summary>Returns the property descriptors for the described
            /// ExampleElement domain class.</summary>
            /// <remarks>This method adds the tracking property descriptor.
            /// </remarks>
            private PropertyDescriptorCollection GetCustomProperties(
                Attribute[] attributes)
            {
                // Get the default property descriptors from the base class
                PropertyDescriptorCollection propertyDescriptors =
                    base.GetProperties(attributes);

                // Get a reference to the model element that is being described.
                ExampleElement source = this.ModelElement as ExampleElement;

                //Add the descriptor for the tracking property.
                if (source != null)
                {
                    DomainPropertyInfo domainProperty =
                        source.Store.DomainDataDirectory.GetDomainProperty(
                            ExampleElement.NamespaceDomainPropertyId);

                    DomainPropertyInfo trackingProperty =
                        source.Store.DomainDataDirectory.GetDomainProperty(
                            ExampleElement.IsNamespaceTrackingDomainPropertyId);

                    // Define attributes for the tracking property so that the
                    // Properties window displays the property correctly.
                    Attribute[] attr = new Attribute[] {
                        new DisplayNameAttribute("Element Namespace"),
                        new DescriptionAttribute("The namespace of the element."),
                        new CategoryAttribute("Tracking Properties"),
                    };

                    propertyDescriptors.Add(new TrackingPropertyDescriptor(
                        source, domainProperty, trackingProperty, attr));
                }

                // Return the property descriptors for this element
                return propertyDescriptors;
            }
        }
    }
    ```

## <a name="adding-custom-code-for-the-package"></a>Добавление пользовательского кода для пакета
 Созданный код определяет поставщик описания типа для доменного класса Ексамплилемент. Однако необходимо добавить код, чтобы указать DSL использовать поставщик описания типа.

#### <a name="to-update-the-dsl-package-to-use-your-custom-type-descriptor"></a>Обновление пакета DSL для использования пользовательского дескриптора типа

1. Добавьте следующий код в файл Package.cs.

    ```csharp
    using System.ComponentModel;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // Override the default Initialize method.
        internal sealed partial class TrackingPropertyDSLPackage
        {
            protected override void Initialize()
            {
                // Add the custom type descriptor for the ExampleElement type.
                TypeDescriptor.AddProvider(
                    new ExampleElementTypeDescriptionProvider(),
                    typeof(ExampleElement));

                base.Initialize();
            }
        }
    }
    ```

## <a name="adding-custom-code-for-the-model"></a>Добавление пользовательского кода для модели
 Реализуйте метод `GetCustomElementsValue` для класса `ExampleModel` домена.

> [!NOTE]
> Код, создаваемый инструментами DSL для `ExampleModel`, вызывает `GetCustomElementsValue`; Однако средства DSL не создают код, реализующий метод.

 Определение метода `GetCustomElementsValue` предоставляет логику для вычисляемого свойства Кустомелементс `ExampleModel`. Этот метод подсчитывает количество `ExampleElement` классов доменов, имеющих свойство отслеживания пространства имен с измененным пользователем значением, и возвращает строку, представляющую это количество как часть общего числа элементов в модели.

 Кроме того, добавьте метод `OnDefaultNamespaceChanged` для `ExampleModel`и переопределите метод `OnValueChanged` `DefaultNamespacePropertyHandler` вложенного класса `ExampleModel`, чтобы вызвать `OnDefaultNamespaceChanged`.

 Так как свойство свойство DefaultNamespace используется для вычисления свойства отслеживания пространства имен, `ExampleModel` должен уведомлять все `ExampleElement`ные классы домена о том, что значение свойство DefaultNamespace изменилось.

#### <a name="to-modify-the-property-handler-for-the-tracked-property"></a>Изменение обработчика свойства для свойства Tracked

1. Добавьте следующий код в файл ExampleModel.cs.

    ```csharp
    using System.Linq;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        public partial class ExampleModel
        {
            public string GetCustomElementsValue()
            {
                if (this.Elements.Count == 0) return "0/0";

                int number = this.Elements.Count(e => !e.IsNamespaceTracking);
                return string.Format("{0}/{1}", number, this.Elements.Count);
            }

            #region Value changed handler for the tracked property

            // When a tracked property changes, it needs to notify all of the properties
            // that track it.

            /// <summary>Called by the DefaultNamespace property value handler when the
            /// DefaultNamespace property changes.</summary>
            /// <param name="oldValue">The previous value of the property.</param>
            /// <param name="newValue">The new value of the property.</param>
            protected virtual void OnDefaultNamespaceChanged(
                string oldValue, string newValue)
            {
                // Use the helper class to notify all of the elements in the model
                // that the default namespace has changed.
                TrackingHelper.UpdateTrackingCollectionProperty(
                    this.Store,
                    this.Elements,
                    ExampleElement.NamespaceDomainPropertyId,
                    ExampleElement.IsNamespaceTrackingDomainPropertyId);
            }

            // Update the change handler for the DefaultNamespace property.
            internal sealed partial class DefaultNamespacePropertyHandler
            {
                /// <summary>Called when the DefaultNamespace property changes.</summary>
                /// <param name="element">The model element that has the property that
                /// changed.</param>
                /// <param name="oldValue">The previous value of the property.</param>
                /// <param name="newValue">The new value of the property.</param>
                protected override void OnValueChanged(
                    ExampleModel element, string oldValue, string newValue)
                {
                    base.OnValueChanged(element, oldValue, newValue);

                    if (!element.Store.InUndoRedoOrRollback)
                    {
                        element.OnDefaultNamespaceChanged(oldValue, newValue);
                    }
                }
            }

            #endregion
        }
    }
    ```

## <a name="adding-custom-code-for-the-tracking-property"></a>Добавление пользовательского кода для свойства отслеживания
 Добавьте `CalculateNamespace` метод в доменный класс `ExampleElement`.

 Определение этого метода обеспечивает логику для вычисляемого свойства Кустомелементс `ExampleModel`. Этот метод подсчитывает количество `ExampleElement` классов доменов, имеющих свойство отслеживания пространства имен, которое находится в состоянии "Обновлено пользователем", и возвращает строку, представляющую это количество как часть общего числа элементов в модели.

 Кроме того, добавьте хранилище для методов и, чтобы получить и задать свойство "пользовательское хранилище" для пространства имен `ExampleElement` доменного класса.

> [!NOTE]
> Код, создаваемый инструментами DSL для `ExampleModel`, вызывает методы get и Set; Однако средства DSL не создают код, реализующий методы.

#### <a name="to-add-the-method-for-the-custom-type-descriptor"></a>Добавление метода для пользовательского дескриптора типа

1. Добавьте следующий код в файл NamespaceTrackingProperty.cs.

    ```csharp
    using System;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // To the domain class that has the tracking property, add the caluclation
        // for when the property is tracking.
        public partial class ExampleElement
        {
            /// <summary>Calculates the actual value of the property when it is
            /// tracking.</summary>
            /// <returns>The value of the tracking property when it is
            /// tracking.</returns>
            /// <remarks>Making this method virtual allows child classes to modify
            /// the calculation. This method does not need to perform validation, as
            /// its caller handles validation prior to calling this method.
            /// <para>In this case, the tracking value depends on the default namespace
            /// property of the parent model.</para></remarks>
            protected virtual string CalculateNamespace()
            {
                return this.ExampleModel.DefaultNamespace;
            }

            #region Tracking property implementation

            // Implement the Namespace domain property of the ExampleElement domain class,
            // and update the IsNamespaceTracking domain property value handler.

            /// <summary>Storage for the Namespace property.</summary>
            private string namespaceStorage;

            /// <summary>Gets the value of the Namespace property.</summary>
            /// <returns>The value of the Namespace property.</returns>
            private string GetNamespaceValue()
            {
                // Only retrieve the tracked value if the store is not in the
                // middle of a serialization transaction.
                bool loading = this.Store.TransactionManager.InTransaction
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;

                if (!loading && this.IsNamespaceTracking)
                {
                    try
                    {
                        return this.CalculateNamespace();
                    }
                    catch (NullReferenceException)
                    {
                        return default(string);
                    }
                    catch (Exception e)
                    {
                        if (CriticalException.IsCriticalException(e))
                        {
                            throw;
                        }
                        else
                        {
                            return default(string);
                        }
                    }
                }

                return namespaceStorage;
            }

            /// <summary>Sets the value of the Namespace property.</summary>
            /// <param name="value">The new value for the property.</param>
            private void SetNamespaceValue(string value)
            {
                namespaceStorage = value;

                // Only update the state of the tracking property if the store is
                // not in the middle of a serialization transaction.
                bool loading = this.Store.TransactionManager.InTransaction
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;

                if (!this.Store.InUndoRedoOrRollback && !loading)
                {
                    this.IsNamespaceTracking = false;
                }
            }

            // Update the default behavior of the ExampleElement.IsNamespaceTracking
            // domain property value handler.
            internal sealed partial class IsNamespaceTrackingPropertyHandler
            {
                /// <summary>Called after the IsNamespaceTracking property changes.
                /// </summary>
                /// <param name="element">The model element that has the property
                /// that changed.</param>
                /// <param name="oldValue">The previous value of the property.
                /// </param>
                /// <param name="newValue">The new value of the property.</param>
                protected override void OnValueChanged(
                    ExampleElement element, Boolean oldValue, Boolean newValue)
                {
                    base.OnValueChanged(element, oldValue, newValue);
                    if (!element.Store.InUndoRedoOrRollback && newValue)
                    {
                        DomainPropertyInfo propInfo =
                            element.Store.DomainDataDirectory.GetDomainProperty(
                                ExampleElement.NamespaceDomainPropertyId);
                        propInfo.NotifyValueChange(element);
                    }
                }

                /// <summary>Performs the reset operation for the IsNamespaceTracking
                /// property for a model element.</summary>
                /// <param name="element">The model element that has the property
                /// to reset.</param>
                internal void ResetValue(ExampleElement element)
                {
                    object calculatedValue = null;

                    try
                    {
                        calculatedValue = element.CalculateNamespace();
                    }
                    catch (NullReferenceException)
                    {
                    }
                    catch (System.Exception e)
                    {
                        if (CriticalException.IsCriticalException(e))
                        {
                            throw;
                        }
                    }

                    if ((calculatedValue != null
                        && object.Equals(element.Namespace, calculatedValue)))
                    {
                        element.isNamespaceTrackingPropertyStorage = true;
                    }
                }

                /// <summary>Method to set IsNamespaceTracking to false so that this
                /// instance of this tracking property is not storage-based.
                /// </summary>
                /// <param name="element">The element on which to reset the property
                /// value.</param>
                internal void PreResetValue(ExampleElement element)
                {
                    // Force the IsNamespaceTracking property to false so that the value
                    // of the Namespace property is retrieved from storage.
                    element.isNamespaceTrackingPropertyStorage = false;
                }
            }

            #endregion
        }
    }
    ```

## <a name="adding-custom-code-to-support-serialization"></a>Добавление пользовательского кода для поддержки сериализации
 Добавьте код для поддержки пользовательского поведения после загрузки для сериализации XML.

> [!NOTE]
> Код, создаваемый инструментами DSL, вызывает методы `OnPostLoadModel` и `OnPostLoadModelAndDiagram`; Однако средства DSL не создают код, реализующий эти методы.

#### <a name="to-add-code-to-support-the-custom-post-load-behavior"></a>Добавление кода для поддержки пользовательского поведения после загрузки

1. Добавьте следующий код в файл Serialization.cs.

    ```csharp
    using System;
    using System.Diagnostics;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        #region Helper classes for maintaining state while the store is serializing.

        public abstract partial class TrackingPropertyDSLSerializationHelperBase
        {
            /// <summary>Reset the tracking state properties to their natural values
            /// based on comparing storage with calculation.</summary>
            /// <param name="store">The store that contains this model.</param>
            internal static void ResetTrackingProperties(Store store)
            {
                // Two passes required - one to set all elements to storage-based
                // then another to set some back to being tracking.
                foreach (ModelElement element in store.ElementDirectory.AllElements)
                {
                    ExampleElement myElementInstance = element as ExampleElement;
                    if (myElementInstance != null)
                    {
                        myElementInstance.PreResetIsTrackingProperties();
                        continue;
                    }
                }
                foreach (ModelElement element in store.ElementDirectory.AllElements)
                {
                    ExampleElement myElementInstance = element as ExampleElement;
                    if (myElementInstance != null)
                    {
                        myElementInstance.ResetIsTrackingProperties();
                        continue;
                    }
                }
            }
        }

        // Add the pre-reset and reset methods for the model element.
        public partial class ExampleElement
        {
            /// <summary>Calls the pre-reset method on the associated property value
            /// handler for each tracking property of this model element.</summary>
            internal virtual void PreResetIsTrackingProperties()
            {
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.PreResetValue(this);
            }

            /// <summary>Calls the reset method on the associated property value
            /// handler for each tracking property of this model element.</summary>
            internal virtual void ResetIsTrackingProperties()
            {
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.ResetValue(this);
            }
        }

        #endregion

        #region Custom serialization code

        // To the serialization helper for the TrackingPropertyDSL class, add post
        // load handlers to bind the tracking property to the serialization process.
        // These handlers manage the tracking states and property values when the
        // model is serialized and deserialized.
        public partial class TrackingPropertyDSLSerializationHelperBase
        {
            /// <summary>Customize model loading.</summary>
            /// <param name="serializationResult">The serialization result from the
            /// load operation.</param>
            /// <param name="partition">The partition in which the new
            /// instance was created.</param>
            /// <param name="fileName">The name of the file from which the
            /// instance was deserialized.</param>
            /// <param name="modelRoot">The root of the file that was loaded.
            /// </param>
            private void OnPostLoadModel(
                SerializationResult serializationResult,
                Partition partition,
                string fileName,
                ExampleModel modelRoot)
            {
            }

            /// <summary>Customize model and diagram loading.</summary>
            /// <param name="serializationResult">Stores serialization result from
            /// the load operation.</param>
            /// <param name="modelPartition">Partition in which the new
            /// instance will be created.</param>
            /// <param name="modelFileName">Name of the file from which the
            /// instance will be deserialized.</param>
            /// <param name="diagramPartition">Partition in which the new
            /// diagram instance will be created.</param>
            /// <param name="diagramFileName">Name of the file from which the
            /// diagram instance will be deserialized.</param>
            /// <param name="modelRoot">The root of the file that was loaded.</param>
            /// <param name="diagram">The diagram matching the modelRoot.</param>
            private void OnPostLoadModelAndDiagram(
                SerializationResult serializationResult,
                Partition modelPartition,
                string modelFileName,
                Partition diagramPartition,
                string diagramFileName,
                ExampleModel modelRoot,
                TrackingPropertyDSLDiagram diagram)
            {
                Debug.Assert(modelPartition != null);
                Debug.Assert(modelPartition.Store != null);

                // Tracking properties need to be set up according to whether the
                // serialization matches the calculated values.
                TrackingPropertyDSLSerializationHelperBase.ResetTrackingProperties(
                    modelPartition.Store);
            }
        }

        #endregion
    }
    ```

## <a name="testing-the-language"></a>Тестирование языка
 Следующим шагом является создание и запуск конструктора DSL в новом экземпляре [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], чтобы можно было убедиться, что свойство отслеживания работает правильно.

#### <a name="to-exercise-the-language"></a>Чтобы применить язык

1. В меню **Построить** выберите пункт **Перестроить решение**.

2. В меню **Отладка** щелкните **Начать отладку**.

     Экспериментальная сборка [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] открывает решение для **отладки** , которое содержит пустой тестовый файл.

3. В **Обозреватель решений**дважды щелкните файл Test. траккингпропертидсл, чтобы открыть его в конструкторе, а затем щелкните область конструктора.

     Обратите внимание, что в окне **Свойства** схемы свойство **Namespace по умолчанию** имеет значение **свойство DefaultNamespace**, а свойство **Custom Elements** — **0/0**.

4. Перетащите элемент **ексамплилемент** с **панели элементов** на поверхность схемы.

5. В окне **Свойства** для элемента выберите свойство **пространство имен элемента** и измените значение с **свойство DefaultNamespace** на **осернамеспаце**.

     Обратите внимание, что значение **пространства имен element** теперь отображается полужирным шрифтом.

6. В окне **Свойства** щелкните правой кнопкой мыши **элемент пространство имен**и выберите команду **сбросить**.

     Значение свойства меняется на **свойство DefaultNamespace**, а значение отображается в обычном шрифте.

     Щелкните правой кнопкой мыши **элемент пространство имен** еще раз. Команда **Reset** теперь отключена, так как свойство в настоящее время находится в состоянии отслеживания.

7. Перетащите еще один **ексамплилемент** из **области элементов** на поверхность схемы и измените **пространство имен элемента** на **осернамеспаце**.

8. Щелкните область конструктора.

     В окне **свойств** схемы значение **настраиваемые элементы** теперь равно **1/2**.

9. Измените **пространство имен по умолчанию** для схемы с **свойство DefaultNamespace** на **невнамеспаце**.

     **Пространство имен** первого элемента отслеживает свойство **пространства имен по умолчанию** , в то время как **пространство имен** второго элемента оставляет свое измененное пользователем значение **осернамеспаце**.

10. Сохраните решение, а затем закройте экспериментальную сборку.

## <a name="next-steps"></a>Дальнейшие действия
 Если планируется использовать несколько свойств отслеживания или реализовать свойства отслеживания более чем в одном DSL, можно создать текстовый шаблон для создания общего кода для поддержки каждого свойства отслеживания. Дополнительные сведения о текстовых шаблонах см. в разделе [Создание кода и текстовые шаблоны T4](../modeling/code-generation-and-t4-text-templates.md).

## <a name="see-also"></a>См. также раздел
 <xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor> <xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor>
 Инструкции по [определению доменного языка](../modeling/how-to-define-a-domain-specific-language.md) [Практическое руководство. Создание решения для](../modeling/how-to-create-a-domain-specific-language-solution.md) доменного языка — [Настройка определения предметно-](../misc/walkthrough-customizing-the-domain-specific-language-definition.md) ориентированного языка
