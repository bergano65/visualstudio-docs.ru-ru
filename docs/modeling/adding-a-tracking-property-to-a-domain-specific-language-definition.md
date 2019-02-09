---
title: Добавление свойства отслеживания в определение доменного языка
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tracking properties [Domain-Specific Language Tools], walkthrough
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 98e3c4aabd973a755f2289abfa809df556680070
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55944537"
---
# <a name="add-a-tracking-property-to-a-domain-specific-language-definition"></a>Добавление свойства отслеживания в определение предметно-ориентированного языка

В этом пошаговом руководстве демонстрируется добавление свойства отслеживания в доменную модель.

Объект *отслеживания домена* свойство является свойством, можно обновить пользователем, но содержит значение по умолчанию, которая рассчитывается, используя значения других свойств домена или элементов.

К примеру в средства доменного языка (DSL Tools), отображаемое имя свойства класса домена имеет значение по умолчанию, которая рассчитывается, используя имя доменного класса, но пользователь может изменить значение во время разработки или выполнить его сброс до вычисленное значение.

В этом пошаговом руководстве создается доменный язык (DSL), с пространством имен, отслеживания свойство, которое имеет значение по умолчанию, на основе пространства имен по умолчанию свойства модели. Дополнительные сведения об отслеживании свойств см. в разделе [определение свойства отслеживания](https://msdn.microsoft.com/0538b0e4-6221-4e7d-911a-b92cd622f0be).

- Поддержка средств DSL, отслеживания дескрипторов свойств. Однако конструктор DSL не может использоваться для добавления свойства отслеживания в язык. Таким образом необходимо добавить пользовательский код для определения и реализации свойства отслеживания.

  Свойства отслеживания имеет два состояния: отслеживание и обновленные пользователем. Свойства отслеживания имеют следующие особенности:

- В состоянии отслеживания, значение свойства отслеживания, и значение будет обновлено, как другие свойства в изменении модели.

- При работе в обновленный по пользовательской среды, значение свойства отслеживания сохраняет значение, к которому пользователь последнего свойства.

- В **свойства** окне **Сброс** команды для свойства отслеживания становится доступен только в том случае, когда свойство в обновленном с пользовательской среды. **Сброс** команда задает свойство отслеживания состояния для отслеживания.

- В **свойства** окне, если свойство отслеживания находится в состоянии отслеживания, его значение отображается в обычным шрифтом.

- В **свойства** окно, когда свойство отслеживания в обновленном по пользовательской среды, его значение отображается полужирным шрифтом.

## <a name="prerequisites"></a>Предварительные требования

Перед запуском этого пошагового руководства, необходимо сначала установить эти компоненты:


| | |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580) |
| [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] | [http://go.microsoft.com/fwlink/?LinkID=185581](http://go.microsoft.com/fwlink/?LinkID=185581) |

## <a name="create-the-project"></a>Создание проекта

1.  Создайте проект конструктора доменного языка. Присвойте обработчику события имя `TrackingPropertyDSL`.

2.  В **мастер конструктора предметно-ориентированного языка**, задать следующие параметры:

    1.  Выберите **MinimalLanguage** шаблона.

    2.  Используйте имя по умолчанию для доменного языка, `TrackingPropertyDSL`.

    3.  Установить расширение для файлов моделей для `trackingPropertyDsl`.

    4.  Используйте значок шаблона по умолчанию для файлов моделей.

    5.  Имя обновляемого продукта `Product Name`.

    6.  Задайте имя компании `Company Name`.

    7.  Используйте значение по умолчанию для корневого пространства имен для проектов в решении, `CompanyName.ProductName.TrackingPropertyDSL`.

    8.  Разрешите мастеру создать файл ключа строгого имени для сборки.

    9. Просмотрите сведения о решении и нажмите кнопку **Готово** Создание проекта определения DSL.

## <a name="customize-the-default-dsl-definition"></a>Настройка определения доменного языка по умолчанию
 В этом разделе вы Настройка определения DSL должен содержать следующие элементы:

-   Пространство имен, отслеживания свойство для каждого элемента модели.

-   IsNamespaceTracking логическое свойство, для каждого элемента модели. Это свойство будет указывать, является ли свойство отслеживания в состоянии отслеживания или в обновленном с пользовательской среды.

-   Свойство пространства имен по умолчанию для модели. Это свойство будет использоваться для вычисления значения по умолчанию пространства имен, свойство отслеживания.

-   CustomElements вычисляемого свойства для модели. Это свойство будет указывать долю элементов, имеющих пользовательского пространства имен.

### <a name="to-add-the-domain-properties"></a>Добавление свойств домена

1.  Щелкните правой кнопкой мыши в конструкторе DSL **ExampleModel** доменного класса, выберите пункт **добавить**, а затем нажмите кнопку **DomainProperty**.

    1.  Имя нового свойства `DefaultNamespace`.

    2.  В **свойства** окна для нового свойства, установить **значение по умолчанию** для `DefaultNamespace`и задайте **тип** для **строка**.

2.  Чтобы **ExampleModel** домена добавьте свойство домена с именем `CustomElements`.

     В **свойства** окна для нового свойства, установить **вид** для **Calculated**.

3.  Чтобы **ExampleElement** домена добавьте свойство домена с именем `Namespace`.

     В **свойства** окна для нового свойства, установить **возможность просмотра** для **False**и задайте **вид** для **CustomStorage** .

4.  Чтобы **ExampleElement** домена добавьте свойство домена с именем `IsNamespaceTracking`.

     В **свойства** окна для нового свойства, установить **возможность просмотра** для **False**, задайте **значение по умолчанию** для `true`и задайте **Тип** для **логическое**.

### <a name="to-update-the-diagram-elements-and-dsl-details"></a>Для обновления элементов схемы и сведения о DSL

1.  Щелкните правой кнопкой мыши в конструкторе DSL **ExampleShape** геометрической фигуры, выберите пункт **добавить**, а затем нажмите кнопку **текстовый декоратор**.

    1.  Назовите новый текстовый декоратор `NamespaceDecorator`.

    2.  В **свойства** задать окно для текстовый декоратор, **позиции** для **InnerBottomLeft**.

2.  В конструкторе доменного языка выберите линии, соединяющей **ExampleElement** класс **ExampleShape** фигуры.

    1.  В **подробные сведения о DSL** выберите **сопоставления декораторов** вкладки.

    2.  В **декораторы** выберите **NamespaceDecorator**, установите соответствующий флажок и затем на **отображаемое свойство** выберите **пространства имен**.

3.  В **обозреватель DSL**, разверните **доменных классов** папку, щелкните правой кнопкой мыши **ExampleElement** узел, а затем щелкните **добавить новый дескриптор доменного типа**.

    1.  Разверните **ExampleElement** узел и выберите **дескрипторе настраиваемого типа (дескриптор доменного типа)** узла.

    2.  В **свойства** задать окно для дескриптора типа домена **закодированных пользовательских** для **True**.

4.  В **обозреватель DSL**выберите **поведение сериализации Xml** узла.

    1.  В **свойства** окне **после загрузки пользовательского** для **True**.

## <a name="transform-templates"></a>Преобразование шаблонов

Теперь, когда вы определили доменных классов и свойств для доменного языка, вы можете проверить, что определение DSL могут быть преобразованы неправильно для повторного создания кода для проекта.

1.  На **обозревателе решений** панели инструментов нажмите кнопку **преобразовать все шаблоны**.

2.  Система заново генерирует код для решения и сохраняет DslDefinition.dsl. Сведения о XML-формат файлов определений, см. в разделе [файл DslDefinition.dsl](../modeling/the-dsldefinition-dsl-file.md).

## <a name="create-files-for-custom-code"></a>Создание файлов для пользовательского кода

При преобразовании всех шаблонов, система создает исходный код, определяющий вашего доменного языка в проектах Dsl и DslPackage. Таким образом, вы можете избежать конфликта с созданный текст, пользовательский код пишется в файлах, которые отличаются от созданных файлах кода.

Необходимо указать код для поддержания значение и состояние свойства отслеживания. Что позволяет отличить пользовательский код из созданного кода и избежать конфликтов имен файлов, размещайте файлы пользовательского кода в отдельной подпапке.

1.  В **обозревателе решений**, щелкните правой кнопкой мыши **DSL** проект, выберите пункт **добавить**, а затем нажмите кнопку **новую папку**. Назовите новую папку `CustomCode`.

2.  Щелкните правой кнопкой мыши новый **значение CustomCode** папку **добавить**, а затем нажмите кнопку **новый элемент**.

3.  Выберите **файл кода** шаблон, набора **имя** для `NamespaceTrackingProperty.cs`, а затем нажмите кнопку **ОК**.

     Файл NamespaceTrackingProperty.cs создается и открывается для редактирования.

4.  В папке, создайте следующие файлы кода: `ExampleModel.cs,``HelperClasses.cs`, `Serialization.cs`, и `TypeDescriptor.cs`.

5.  В **DslPackage** проекта, также создать `CustomCode` папки и добавьте в него `Package.cs` файл кода.

## <a name="add-helper-classes-to-support-tracking-properties"></a>Добавить вспомогательные классы для поддержки свойства отслеживания

Добавьте файл HelperClasses.cs `TrackingHelper` и `CriticalException` классов следующим образом. Вы будете ссылаться эти классы далее в этом пошаговом руководстве.

1.  Добавьте следующий код в файл HelperClasses.cs.

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

## <a name="add-custom-code-for-the-custom-type-descriptor"></a>Добавьте пользовательский код для настраиваемого дескриптора типа

Реализуйте `GetCustomProperties` метод для дескриптора типа для `ExampleModel` доменного класса.

> [!NOTE]
> Код, создаваемый средств доменного языка для настраиваемого дескриптора типа для `ExampleModel` вызовы `GetCustomProperties`, однако средства DSL не создают код, который реализует метод.

Определение этот метод создает отслеживания дескриптор свойства для пространства имен, свойство отслеживания. Кроме того, предоставление атрибутов для свойства отслеживания позволяет **свойства** окно для отображения свойства правильно.

### <a name="to-modify-the-type-descriptor-for-the-examplemodel-domain-class"></a>Чтобы изменить дескриптор типа для класса домена ExampleModel

1.  Добавьте следующий код в файл TypeDescriptor.cs.

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

Созданный код определяет поставщик описания типа для класса домена ExampleElement; Тем не менее необходимо добавить код, чтобы дать указание DSL, чтобы использовать этот поставщик описания типа.

1.  Добавьте следующий код в файле Package.cs.

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

## <a name="add-custom-code-for-the-model"></a>Добавление пользовательского кода для модели

Реализуйте `GetCustomElementsValue` метод `ExampleModel` доменного класса.

> [!NOTE]
> Код, создаваемый средств доменного языка для `ExampleModel` вызовы `GetCustomElementsValue`, однако средства DSL не создают код, который реализует метод.

Определение `GetCustomElementsValue` метод предоставляет логику для CustomElements вычисляемые свойства `ExampleModel`. Этот метод подсчитывает число `ExampleElement` доменных классов, пространство имен отслеживания свойство, которое имеет пользователь обновил значение и возвращает строку, представляющую это число как части общих элементов в модели.

Кроме того, добавьте `OnDefaultNamespaceChanged` метод `ExampleModel`и Переопределите `OnValueChanged` метод `DefaultNamespacePropertyHandler` вложенных классов из `ExampleModel` для вызова `OnDefaultNamespaceChanged`.

Так как свойство DefaultNamespace используется для вычисления пространства имен, свойство, отслеживания `ExampleModel` необходимо уведомить всех `ExampleElement` доменных классов, значение DefaultNamespace изменилось.

### <a name="to-modify-the-property-handler-for-the-tracked-property"></a>Чтобы изменить обработчик свойств отслеживаемые свойства

1.  Добавьте следующий код в файл ExampleModel.cs.

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

## <a name="add-custom-code-for-the-tracking-property"></a>Добавление пользовательского кода для свойства отслеживания

Добавить `CalculateNamespace` метод `ExampleElement` доменного класса.

Определение этого метода содержит логику для CustomElements вычисляемые свойства `ExampleModel`. Этот метод подсчитывает число `ExampleElement` доменных классов, пространство имен отслеживания свойство, которое находится в обновленный с пользовательской среды и возвращает строку, представляющую это число как части общих элементов в модели.

Кроме того, добавьте хранилище для и методы для получения и задания, свойство пространства имен пользовательского хранилища `ExampleElement` доменного класса.

> [!NOTE]
> Код, создаваемый средств доменного языка для `ExampleModel` вызовы get и настроить методы; Однако средства DSL не создают код, реализующий методы.

### <a name="to-add-the-method-for-the-custom-type-descriptor"></a>Добавление метода для настраиваемого дескриптора типа

1.  Добавьте следующий код в файл NamespaceTrackingProperty.cs.

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

## <a name="add-custom-code-to-support-serialization"></a>Добавление пользовательского кода для поддержки сериализации

Добавьте код для поддержки пользовательского поведения после загрузки XML-сериализации.

> [!NOTE]
> Код, что средства DSL создают вызовы `OnPostLoadModel` и `OnPostLoadModelAndDiagram` методов; Однако средства DSL не создают код, который реализует эти методы.

### <a name="to-add-code-to-support-the-custom-post-load-behavior"></a>Добавление кода для поддержки пользовательского поведения после загрузки

1.  Добавьте следующий код в файл Serialization.cs.

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

## <a name="test-the-language"></a>Тестирование языка

Следующий шаг — построение и запуск конструктора DSL в новый экземпляр класса [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] , можно проверить, правильно ли работает свойства отслеживания.

1. В меню **Построить** выберите пункт **Перестроить решение**.

2. В меню **Отладка** щелкните **Начать отладку**.

    Экспериментальная сборка [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] открывает **Отладка** решение, которое содержит пустой тестовый файл.

3. В **обозревателе решений**, дважды щелкните файл Test.trackingPropertyDsl, чтобы открыть его в конструкторе и затем щелкните область конструктора.

    Обратите внимание, что в **свойства** окно для схемы, **пространство имен по умолчанию** свойство **DefaultNamespace**и **настраиваемые элементы** свойство **0/0**.

4. Перетащите **ExampleElement** элемент из **элементов** на поверхность диаграммы.

5. В **свойства** окна для элемента, выберите **пространство имен элемента** свойство и измените значение с **DefaultNamespace** для  **OtherNamespace**.

    Обратите внимание, что значение **пространство имен элемента** отображается полужирным шрифтом.

6. В **свойства** окно, щелкните правой кнопкой мыши **пространство имен элемента**, а затем нажмите кнопку **сбросить**.

    Значение свойства изменяется на **DefaultNamespace**, и значение отображается в обычным шрифтом.

    Щелкните правой кнопкой мыши **пространство имен элемента** еще раз. **Сброс** команда теперь отключена, так как свойство в настоящее время находится в состоянии отслеживания.

7. Перетащите еще один **ExampleElement** из **элементов** поверхности диаграммы и изменение его **пространство имен элемента** для **OtherNamespace**.

8. Щелкните область конструктора.

    В **свойства** окно для схемы, значение **настраиваемые элементы** теперь **1/2**.

9. Изменение **пространство имен по умолчанию** схемы из **DefaultNamespace** для **NewNamespace**.

     **Пространства имен** первый элемент дорожек **пространство имен по умолчанию** свойство, тогда как **пространства имен** второй элемент сохраняет его пользователь обновил значение  **OtherNamespace**.

10. Сохраните решение, а затем закройте экспериментальную сборку.

## <a name="next-steps"></a>Следующие шаги

Если вы планируете использовать более одного отслеживания свойство или реализовать свойства отслеживания в нескольких доменных ЯЗЫКОВ, можно создать текстовый шаблон, чтобы создать общий код для поддержки каждого свойства отслеживания. Дополнительные сведения о текстовых шаблонах см. в разделе [создание кода и текстовые шаблоны T4](../modeling/code-generation-and-t4-text-templates.md).

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor>
- <xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor>
- [Определение доменного языка](../modeling/how-to-define-a-domain-specific-language.md)
- [Практическое руководство. Создайте решение доменного языка](../modeling/how-to-create-a-domain-specific-language-solution.md)
