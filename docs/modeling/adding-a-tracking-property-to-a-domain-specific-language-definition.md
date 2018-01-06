---
title: "Добавление свойства отслеживания в определение доменного языка | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tracking properties [Domain-Specific Language Tools], walkthrough
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
ms.assetid: 4aa47777-de75-4897-a423-a3c4426b4125
caps.latest.revision: "22"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 464557102bd6dcbbbda4032c0588c55baa954664
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="adding-a-tracking-property-to-a-domain-specific-language-definition"></a>Добавление свойства отслеживания в определение доменного языка
В этом пошаговом руководстве показано, как добавить свойство отслеживания в доменную модель.  
  
 Объект *отслеживания домена* свойство — это свойство может обновляться пользователем, но содержит значение по умолчанию, которое вычисляется на основе значений других свойств домена или элементов.  
  
 Например в средства доменного языка (Инструменты DSL), отображаемое имя свойства класса домена имеет значение по умолчанию, которое вычисляется с помощью имени класса домена, но пользователь можно изменить значение во время разработки или выполнить его сброс до вычисленное значение.  
  
 В этом пошаговом руководстве создается доменный язык (DSL), с пространством имен, отслеживания свойство, которое имеет значение по умолчанию на основе свойства по умолчанию пространство имен модели. Дополнительные сведения об отслеживании свойств см. в разделе [определение свойства отслеживания](http://msdn.microsoft.com/en-us/0538b0e4-6221-4e7d-911a-b92cd622f0be).  
  
-   Инструменты DSL поддержка отслеживания дескрипторов свойств. Однако конструктор DSL не может использоваться для добавления свойства отслеживания язык. Таким образом необходимо добавить пользовательский код для определения и реализации свойства отслеживания.  
  
 Свойство отслеживания имеет два состояния: отслеживание и обновленные пользователем. Свойства отслеживания имеют следующие особенности:  
  
-   В состоянии отслеживания, вычисляется значение свойства отслеживания, а значение обновляется как другие свойства в изменении модели.  
  
-   Если в обновленной по состоянию пользователя, значение свойства отслеживания сохраняет значение, для которого пользователь последнего свойства.  
  
-   В **свойства** окне **Сброс** команды для отслеживания свойства доступны только когда свойство в обновленной по пользовательской среды. **Сброс** команда присваивает свойству отслеживания состояния для отслеживания.  
  
-   В **свойства** откроется окно, когда свойство отслеживания находится в состоянии отслеживания, а его значение в обычный шрифт.  
  
-   В **свойства** окна, когда свойство трассировки в обновленной по состояния пользователей, его значение отображается жирным шрифтом.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Перед запуском данного пошагового руководства, необходимо сначала установить следующие компоненты:  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.Microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|  
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.Microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|  
|[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]|[http://go.Microsoft.com/fwlink/?LinkId=185581](http://go.microsoft.com/fwlink/?LinkID=185581)|  
  
## <a name="creating-the-dsl-project"></a>Создание проекта DSL  
 Создайте проект для вашего доменного языка.  
  
#### <a name="to-create-the-project"></a>Создание проекта  
  
1.  Создайте проект конструктора доменного языка. Присвойте обработчику события имя `TrackingPropertyDSL`.  
  
2.  В **мастера конструктора доменного языка**, задайте следующие параметры:  
  
    1.  Выберите **MinimalLanguage** шаблона.  
  
    2.  Используйте имя по умолчанию для доменного языка, `TrackingPropertyDSL`.  
  
    3.  Установка расширения для файлов модели `trackingPropertyDsl`.  
  
    4.  Используйте значок шаблона по умолчанию для файлов модели.  
  
    5.  Задайте имя продукта, чтобы `Product Name`.  
  
    6.  Задайте имя компании `Company Name`.  
  
    7.  Использовать значение по умолчанию для корневого пространства имен для проектов в решении, `CompanyName.ProductName.TrackingPropertyDSL`.  
  
    8.  Разрешите мастеру создать файл ключа строгого имени для сборки.  
  
    9. Просмотрите сведения о решении и нажмите кнопку **Готово** Создание проекта определения DSL.  
  
## <a name="customizing-the-default-dsl-definition"></a>Настройка определения DSL по умолчанию  
 В этом разделе настроить определение DSL, содержат следующие элементы:  
  
-   Пространство имен, отслеживания свойства для каждого элемента модели.  
  
-   IsNamespaceTracking логическое свойство для каждого элемента модели. Это свойство будет указывать, является ли свойство отслеживания в состоянии отслеживания или в обновленный с пользовательской среды.  
  
-   Свойство пространства имен по умолчанию для модели. Это свойство будет использоваться для вычисления значения по умолчанию пространства имен, свойство отслеживания.  
  
-   Свойство CustomElements вычисляется для модели. Это свойство будет указывать долю элементов, имеющих пользовательского пространства имен.  
  
#### <a name="to-add-the-domain-properties"></a>Для добавления свойств домена  
  
1.  Конструктор DSL, щелкните правой кнопкой мыши **ExampleModel** класса домена, выберите пункт **добавить**, а затем нажмите кнопку **свойство DomainProperty**.  
  
    1.  Имя нового свойства `DefaultNamespace`.  
  
    2.  В **свойства** окна для нового свойства установить **значение по умолчанию** для `DefaultNamespace`и задайте **тип** для **строка**.  
  
2.  Чтобы **ExampleModel** домена добавьте свойство домена с именем `CustomElements`.  
  
     В **свойства** окна для нового свойства установить **вид** для **вычисляемое**.  
  
3.  Чтобы **ExampleElement** домена добавьте свойство домена с именем `Namespace`.  
  
     В **свойства** окна для нового свойства установить **является отображаемым** для **False**и задайте **вид** для **CustomStorage** .  
  
4.  Чтобы **ExampleElement** домена добавьте свойство домена с именем `IsNamespaceTracking`.  
  
     В **свойства** окна для нового свойства установить **является отображаемым** для **False**, задайте **значение по умолчанию** для `true`и задайте **Тип** для **логическое**.  
  
#### <a name="to-update-the-diagram-elements-and-dsl-details"></a>Чтобы обновить диаграммы и сведений DSL  
  
1.  Конструктор DSL, щелкните правой кнопкой мыши **ExampleShape** геометрическая фигура, пункты **добавить**и нажмите кнопку **Decorator текст**.  
  
    1.  Назовите новый текст decorator `NamespaceDecorator`.  
  
    2.  В **свойства** окне для декоратора текста, задайте **позиции** для **InnerBottomLeft**.  
  
2.  В конструкторе DSL выберите линии, соединяющей **ExampleElement** класса **ExampleShape** фигуры.  
  
    1.  В **сведений DSL** выберите **Decorator Maps** вкладки.  
  
    2.  В **декораторов** выберите **NamespaceDecorator**, установите соответствующий флажок и затем на **отобразить свойство** выберите **имен**.  
  
3.  В **обозреватель DSL**, разверните **доменные классы** папку, щелкните правой кнопкой мыши **ExampleElement** , а затем щелкните **добавить новый домен дескриптор типа**.  
  
    1.  Разверните **ExampleElement** , а затем установите **пользовательский дескриптор типа (дескриптор типа домена)** узла.  
  
    2.  В **свойства** окна для дескриптора типа домена установить **закодированных пользовательских** для **True**.  
  
4.  В **обозреватель DSL**выберите **поведением при сериализации Xml** узла.  
  
    1.  В **свойства** задайте **настраиваемый Заключительная Загрузка** для **True**.  
  
## <a name="transforming-templates"></a>Преобразование шаблонов  
 Теперь, когда вы определили доменные классы и свойства для доменного языка, можно проверить, можно правильно преобразовать определения DSL повторное создание кода для проекта.  
  
#### <a name="to-transform-the-text-templates"></a>Для преобразования текстовых шаблонов  
  
1.  На **обозревателе решений** инструментов, нажмите кнопку **преобразовать все шаблоны**.  
  
2.  Система заново генерирует код для решения и сохраняет DslDefinition.dsl. Сведения о XML-формате файлов определений см. в разделе [DslDefinition.dsl файл](../modeling/the-dsldefinition-dsl-file.md).  
  
## <a name="creating-files-for-custom-code"></a>Создание файлов для пользовательского кода  
 При преобразовании все шаблоны, система создает исходный код, который определяет доменный язык Dsl и DslPackage проектов. Избежать конфликта с созданный текст, которое необходимо напишите пользовательский код в файлах, которые отличаются от созданных файлах кода.  
  
 Необходимо предоставить код для обслуживания значение и состояние свойства отслеживания. Что позволяет отличить пользовательский код из созданного кода и избежать конфликтов имен файлов, поместите файлы пользовательского кода в отдельной вложенной папки.  
  
#### <a name="to-create-the-code-files"></a>Для создания файлов кода  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши **DSL** проект, выберите пункт **добавить**, а затем нажмите кнопку **новую папку**. Имя новой папки `CustomCode`.  
  
2.  Щелкните правой кнопкой мыши новый **CustomCode** папку, выберите пункт **добавить**, а затем нажмите кнопку **новый элемент**.  
  
3.  Выберите **файл кода** шаблон, набора **имя** для `NamespaceTrackingProperty.cs`, а затем нажмите кнопку **ОК**.  
  
     Файл NamespaceTrackingProperty.cs создается и открывается для редактирования.  
  
4.  В папке, создайте следующие файлы кода: `ExampleModel.cs,``HelperClasses.cs`, `Serialization.cs`, и `TypeDescriptor.cs`.  
  
5.  В **DslPackage** проекта, также создать `CustomCode` папки и добавьте к нему `Package.cs` файл кода.  
  
## <a name="adding-helper-classes-to-support-tracking-properties"></a>Добавление вспомогательных классов для поддержки отслеживания свойства  
 Добавьте файл HelperClasses.cs `TrackingHelper` и `CriticalException` классы следующим образом. Эти классы далее в этом пошаговом руководстве будет ссылаться.  
  
#### <a name="to-add-the-helper-classes"></a>Добавление вспомогательных классов  
  
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
  
## <a name="adding-custom-code-for-the-custom-type-descriptor"></a>Добавление пользовательского кода для настраиваемого дескриптора типа  
 Реализуйте `GetCustomProperties` метод для дескриптора типа для `ExampleModel` класса домена.  
  
> [!NOTE]
>  Код, создаваемый DSL Tools для настраиваемого дескриптора типа для `ExampleModel` вызовы `GetCustomProperties`, однако DSL Tools не создают код, который реализует метод.  
  
 Определение этого метода создает отслеживания дескриптор свойства для отслеживания свойств пространства имен. Кроме того, позволяет указать атрибуты для свойства отслеживания **свойства** окно, чтобы правильно отобразить свойства.  
  
#### <a name="to-modify-the-type-descriptor-for-the-examplemodel-domain-class"></a>Чтобы изменить дескриптор типа для класса домена ExampleModel  
  
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
 Созданный код определяет поставщик описания типа для класса ExampleElement домена; Тем не менее необходимо добавить код, чтобы дать указание DSL используют этот поставщик описания типа.  
  
#### <a name="to-update-the-dsl-package-to-use-your-custom-type-descriptor"></a>Обновление пакета DSL использовать ваш пользовательский дескриптор типа  
  
1.  Добавьте следующий код в файл Package.cs.  
  
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
 Реализуйте `GetCustomElementsValue` метод `ExampleModel` класса домена.  
  
> [!NOTE]
>  Код, создаваемый DSL Tools для `ExampleModel` вызовы `GetCustomElementsValue`, однако DSL Tools не создают код, который реализует метод.  
  
 Определение `GetCustomElementsValue` метод предоставляет логику для CustomElements вычисляемые свойства `ExampleModel`. Этот метод подсчитывает количество `ExampleElement` домена классы, которые содержат пространства имен, отслеживания свойство, которое пользователь обновил значение и возвращает строку, представляющую это число как часть общих элементов в модели.  
  
 Кроме того, добавьте `OnDefaultNamespaceChanged` метод `ExampleModel`и Переопределите `OnValueChanged` метод `DefaultNamespacePropertyHandler` вложенных классов от `ExampleModel` для вызова `OnDefaultNamespaceChanged`.  
  
 Так как свойство DefaultNamespace используется для вычисления отслеживания свойство, пространство имен `ExampleModel` необходимо уведомить всех `ExampleElement` классы домена, значение DefaultNamespace изменилось.  
  
#### <a name="to-modify-the-property-handler-for-the-tracked-property"></a>Чтобы изменить свойство обработчик отслеживаемых свойств  
  
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
  
## <a name="adding-custom-code-for-the-tracking-property"></a>Добавление пользовательского кода для отслеживания свойства  
 Добавить `CalculateNamespace` метод `ExampleElement` класса домена.  
  
 Определение этого метода содержит логику для CustomElements вычисляемые свойства `ExampleModel`. Этот метод подсчитывает количество `ExampleElement` домена классы, которые имеют свойство, в обновленной отслеживания пространство имен по состоянию пользователя и возвращает строку, представляющую это число как часть общих элементов в модели.  
  
 Кроме того, добавьте хранилище для и методы для получения и задания свойства пространство имен пользовательского хранилища `ExampleElement` класса домена.  
  
> [!NOTE]
>  Код, создаваемый DSL Tools для `ExampleModel` вызовы get и set методов; Однако DSL Tools не создают код, который реализует методы.  
  
#### <a name="to-add-the-method-for-the-custom-type-descriptor"></a>Добавление метода для настраиваемого дескриптора типа  
  
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
  
## <a name="adding-custom-code-to-support-serialization"></a>Добавление пользовательского кода для поддержки сериализации  
 Добавьте код для поддержки пользовательского поведения после загрузки XML-сериализации.  
  
> [!NOTE]
>  Код, что инструменты DSL Создание вызовов `OnPostLoadModel` и `OnPostLoadModelAndDiagram` методов; Однако DSL Tools не создают код, который реализует эти методы.  
  
#### <a name="to-add-code-to-support-the-custom-post-load-behavior"></a>Добавление кода для поддержки настраиваемых поведений после загрузки  
  
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
  
## <a name="testing-the-language"></a>Тестирование языка  
 Следующий шаг — построение и запуск конструктор DSL в новый экземпляр [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] , чтобы проверить, работоспособность свойство отслеживания.  
  
#### <a name="to-exercise-the-language"></a>Для использования языка  
  
1.  На **построения** меню, нажмите кнопку **Перестроить решение**.  
  
2.  В меню **Отладка** щелкните **Начать отладку**.  
  
     Экспериментальная сборка [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] открывает **Отладка** решение, содержащее файл пустой тест.  
  
3.  В **обозревателе решений**, дважды щелкните файл Test.trackingPropertyDsl, чтобы открыть его в конструкторе и затем щелкните область конструктора.  
  
     Обратите внимание, что в **свойства** окна для диаграммы, **пространство имен по умолчанию** свойство **DefaultNamespace**и **пользовательские элементы** свойство **0/0**.  
  
4.  Перетащите **ExampleElement** элемент из **элементов** на поверхность схемы.  
  
5.  В **свойства** окно для элемента, выберите **пространство имен элемента** свойство и измените значение с **DefaultNamespace** для  **OtherNamespace**.  
  
     Обратите внимание, что значение **пространство имен элемента** отображается полужирным шрифтом.  
  
6.  В **свойства** окно, щелкните правой кнопкой мыши **пространство имен элемента**, а затем нажмите кнопку **Сброс**.  
  
     Значение свойства изменяется на **DefaultNamespace**, и значение отображается в обычный шрифт.  
  
     Щелкните правой кнопкой мыши **пространство имен элемента** еще раз. **Сброс** команда запрещена, так как свойство в настоящее время находится в состоянии отслеживания.  
  
7.  Перетащите еще одно **ExampleElement** из **элементов** для конструирования и изменения его **пространство имен элемента** для **OtherNamespace**.  
  
8.  Щелкните область конструктора.  
  
     В **свойства** окно диаграммы, значение **пользовательские элементы** теперь **1/2**.  
  
9. Изменение **пространство имен по умолчанию** диаграммы из **DefaultNamespace** для **NewNamespace**.  
  
     **Пространства имен** первый элемент дорожек **пространство имен по умолчанию** свойство, в то время как **пространства имен** второго элемента сохраняет его пользователь обновил значение  **OtherNamespace**.  
  
10. Сохраните решение, а затем закройте экспериментальную сборку.  
  
## <a name="next-steps"></a>Следующие шаги  
 Если вы планируете использовать более одного отслеживания свойство или реализовать свойства отслеживания в нескольких DSL, можно создать текстовый шаблон для создания общий код для поддержки каждого свойства отслеживания. Дополнительные сведения о текстовых шаблонах см. в разделе [создание кода и текстовые шаблоны T4](../modeling/code-generation-and-t4-text-templates.md).  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor>   
 <xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor>   
 [Способ определения доменного языка](../modeling/how-to-define-a-domain-specific-language.md)   
 [Практическое руководство. Создание решения на доменном языке](../modeling/how-to-create-a-domain-specific-language-solution.md)   
