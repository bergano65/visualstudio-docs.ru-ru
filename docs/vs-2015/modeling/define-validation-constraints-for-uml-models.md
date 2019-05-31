---
title: Определение ограничений проверки для моделей UML | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, validation constraints
ms.assetid: 87b3b0da-122d-4121-9318-200c38ff49d0
caps.latest.revision: 49
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4107a5fb88392f9d02cca8f41b0f53d5844d9490
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63422714"
---
# <a name="define-validation-constraints-for-uml-models"></a>Определение ограничений проверки для моделей UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете определить ограничения проверки, чтобы узнать, соответствует ли модель заданному условию. Например, можно определить ограничение, чтобы убедиться в том, что пользователь не создает цикл отношений наследования. Ограничение вызывается, когда пользователь пытается открыть или сохранить модель, но также может вызываться вручную. Если происходит сбой ограничения, в окно ошибок добавляется заданное вами сообщение об ошибке. Вы можете упаковать эти ограничения в расширение Visual Studio Integration Extension ([VSIX](http://go.microsoft.com/fwlink/?LinkId=160780)) и распространить их другим пользователям Visual Studio.  
  
 Можно также определить ограничения, проверяющие модель на соответствие внешним ресурсам, таким как базы данных. Если вы хотите проверить код программы по схеме слоев, см. в разделе [Добавление пользовательской проверки архитектуры в схемы слоев](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).  
  
 Чтобы узнать, какие версии Visual Studio поддерживают модели UML, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="requirements"></a>Требования  
 См. раздел [Требования](../modeling/extend-uml-models-and-diagrams.md#Requirements).  
  
 Чтобы узнать, какие версии Visual Studio поддерживают эту функцию, см. раздел [Поддержка версий для инструментов моделирования и архитектуры](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="applying-validation-constraints"></a>Применение ограничений проверки  
 Ограничения проверки применяются в трех случаях: при сохранении модели, при открытии модели и при выборе пункта **Проверить модель UML** в меню **Архитектура** . В каждом случае применяются только те ограничения, которые были определены для этого варианта, хотя обычно каждое из ограничений применяется в нескольких случаях.  
  
 Ошибки проверки регистрируются в окне ошибок [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Кроме того, можно дважды щелкнуть ошибку для выбора элементов модели с такой ошибкой.  
  
 Дополнительные сведения о применении проверки см. в разделе [проверка модели UML](../modeling/validate-your-uml-model.md).  
  
## <a name="defining-a-validation-extension"></a>Определение расширения проверки  
 Чтобы создать расширение проверки для конструктора UML, необходимо создать класс, определяющий ограничения проверки, и внедрить этот класс в расширение Visual Studio Integration Extension (VSIX). VSIX выполняет роль контейнера, позволяющего установить ограничение. Существует два альтернативных способа определения ограничения проверки.  
  
- **Создание расширения проверки в его собственном расширении VSIX с помощью шаблона проекта.** Этот способ быстрее. Используйте его, если не хотите объединять ограничения проверки с другими типами расширения, такими как команды меню, пользовательские элементы панели элементов или обработчики жестов. В одном классе можно определить несколько ограничений.  
  
- **Создайте отдельный класс проверки и проекты VSIX.** Используйте этот метод, если нужно объединить несколько типов расширения в одном расширении VSIX. Например, если для команды меню требуется, чтобы модель соблюдала определенные ограничения, можно внедрить ее в то же расширение VSIX, что и метод проверки.  
  
#### <a name="to-create-a-validation-extension-in-its-own-vsix"></a>Создание ограничения проверки в его собственном расширении VSIX  
  
1. В области **Проекты моделирования** диалогового окна **Новый проект**выберите **Расширение проверки**.  
  
2. Откройте файл **.cs** в новом проекте и измените класс для реализации вашего ограничения проверки.  
  
    Более подробную информацию см. в разделе [Оценка ограничения проверки](#Implementing).  
  
   > [!IMPORTANT]
   > Убедитесь в том, что ваши файлы **.cs** содержат следующий оператор `using` :  
   >   
   >  `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`  
  
3. Можно добавлять дополнительные ограничения, определяя новые методы. Для идентификации метода в качестве метода проверки он должен быть помечен атрибутами таким же образом, как и исходный метод проверки.  
  
4. Проверьте ограничения, нажав клавишу F5. Более подробную информацию см. в разделе [Выполнение ограничения проверки](#Executing).  
  
5. Установите команду меню на другой компьютер, скопировав файл **bin\\\*\\\*.vsix** , созданный вашим проектом. Более подробную информацию см. в разделе [Установка и удаление расширения](#Installing).  
  
   При добавлении других файлов **.cs** обычно требуются следующие операторы `using` :  
  
```csharp  
using System.Collections.Generic;  
using System.ComponentModel.Composition;  
using System.Linq;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.Modeling.Validation;  
using Microsoft.VisualStudio.Uml.Classes;  
  
```  
  
 Ниже описана альтернативная процедура.  
  
#### <a name="to-create-a-separate-validation-constraint-in-a-class-library-project"></a>Создание отдельного ограничения проверки в проекте библиотеки классов  
  
1. Создайте проект библиотеки классов, добавив его в существующее решение VSIX или создав новое решение.  
  
    1. В меню **Файл** последовательно выберите пункты **Создать**и **Проект**.  
  
    2. В разделе **Установленные шаблоны**разверните узел **Visual C#** или **Visual Basic**и выберите в среднем столбце пункт **Библиотека классов**.  
  
2. Создайте проект VSIX, если ваше решение еще его не содержит.  
  
    1. В контекстном меню решения в **обозревателе решений**выберите пункт  **Добавить**, а затем **Новый проект**.  
  
    2. В разделе **Установленные шаблоны**разверните узел **Visual C#** или **Visual Basic**и выберите пункт **Расширение среды**. В среднем столбце выберите пункт **Проект VSIX**.  
  
3. Назначьте проект VSIX запускаемым проектом решения.  
  
    - В контекстном меню проекта VSIX в обозревателе решений выберите пункт **Назначить запускаемым проектом**.  
  
4. Последовательно выберите **source.extension.vsixmanifest**, **Содержимое**и добавьте проект библиотеки классов в качестве компонента MEF.  
  
    1. На вкладке **Метаданные** введите имя для VSIX.  
  
    2. На вкладке **Цели установки** задайте в качестве целевых объектов версии Visual Studio.  
  
    3. На вкладке **Активы** выберите **Создать**и укажите в диалоговом окне следующие значения:  
  
         **Тип** = **Компонент MEF**  
  
         **Источник** = **Проект в текущем решении**  
  
         **Проект** = *Ваш проект библиотеки классов*  
  
#### <a name="to-define-the-validation-class"></a>Определение класса проверки  
  
1. Эта процедура не требуется, если класс проверки создан со своим собственным расширением VSIX на основе шаблона проекта проверки.  
  
2. В проекте класса проверки добавьте ссылки на следующие сборки [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] :  
  
     `Microsoft.VisualStudio.Modeling.Sdk.[version]`  
  
     `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml`  
  
     `Microsoft.VisualStudio.Uml.Interfaces`  
  
     `System.ComponentModel.Composition`  
  
3. Добавьте файл в проект библиотеки классов с кодом, аналогичным приведенному ниже.  
  
    - Каждое ограничение проверки содержится внутри метода, помеченного определенным атрибутом. Метод принимает параметр типа элемента модели. При вызове проверки среда проверки применяет каждый метод проверки к каждому элементу модели, который соответствует этому типу параметра.  
  
    - Эти методы можно помещать в любые классы и пространства имен. В случае необходимости их можно изменить.  
  
    ```  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using System.Linq;  
    using Microsoft.VisualStudio.Modeling.Validation;  
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
    using Microsoft.VisualStudio.Uml.Classes;  
    // You might also need the other Microsoft.VisualStudio.Uml namespaces.  
  
    namespace Validation  
    {  
      public class MyValidationExtensions  
      {  
        // SAMPLE VALIDATION METHOD.  
        // All validation methods have the following attributes.  
        [Export(typeof(System.Action<ValidationContext, object>))]  
        [ValidationMethod(  
           ValidationCategories.Save  
         | ValidationCategories.Open  
         | ValidationCategories.Menu)]  
        public void ValidateClassNames  
          (ValidationContext context,   
           // This type determines what elements   
           // will be validated by this method:  
           IClass elementToValidate)  
        {  
          // A validation method should not change the model.  
  
          List<string> attributeNames = new List<string>();  
          foreach (IProperty attribute in elementToValidate.OwnedAttributes)  
          {  
            string name = attribute.Name;  
            if (!string.IsNullOrEmpty(name) && attributeNames.Contains(name))  
            {  
              context.LogError(  
                string.Format("Duplicate attribute name '{0}' in class {1}", name, elementToValidate.Name),  
                "001", elementToValidate);  
            }  
            attributeNames.Add(name);  
          }  
  
        }  
        // Add more validation methods for different element types.  
      }  
    }  
    ```  
  
## <a name="Executing"></a> Выполнение ограничения проверки  
 В целях тестирования запустите методы проверки в режиме отладки.  
  
#### <a name="to-test-the-validation-constraint"></a>Тестирование ограничения проверки  
  
1. Нажмите клавишу **F5**или выберите команду **Начать отладку** в меню **Отладка**.  
  
     Запустится экспериментальный экземпляр [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
     **Устранение неполадок**: Если новый [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] не запускается:  
  
    - При наличии нескольких проектов убедитесь в том, что для проекта VSIX задан параметр "Назначить запускаемым проектом".  
  
    - В обозревателе решений в контекстном меню запускаемого или единственного проекта выберите пункт **Свойства**. В редакторе свойств проекта перейдите на вкладку **Отладка** . Убедитесь в том, что строка в поле **Запуск внешней программы** является полным путем к [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]; обычно она имеет следующий вид:  
  
         `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`  
  
2. В экспериментальном экземпляре [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]откройте или создайте проект моделирования и откройте или создайте схему моделирования.  
  
3. Чтобы настроить тест для примера ограничения, приведенного в предыдущем разделе, выполните указанные ниже действия.  
  
    1. Откройте схему классов.  
  
    2. Создайте класс и добавьте два атрибута с тем же именем.  
  
4. Откройте контекстное меню в любом месте схемы и выберите пункт **Проверить**.  
  
5. Все ошибки в модели будут отражены в окне ошибок.  
  
6. Дважды щелкните отчет об ошибках. Если на экране отображаются элементы, упомянутые в отчете, они будут выделены.  
  
     **Устранение неполадок**: Если **Validate** команда не отображается в меню, убедитесь, что:  
  
    - Проект проверки указан в качестве компонента MEF на вкладке **Активы** в **source.extensions.manifest** проекта VSIX.  
  
    - К методам проверки добавлены правильные атрибуты `Export` и `ValidationMethod` .  
  
    - `ValidationCategories.Menu` включается в аргументе для `ValidationMethod` атрибут и соединен с другими значениями, с помощью логического или (&#124;).  
  
    - Параметры всех атрибутов `Import` и `Export` являются допустимыми.  
  
## <a name="Implementing"></a> Оценка ограничения  
 Метод проверки должен определить, имеет ли ограничение проверки, которое нужно применить, значение true или false. Если задано значение true, метод не должен выполнять никаких действий. Если задано значение false, метод должен сообщить об ошибке с помощью методов, предоставленных параметром `ValidationContext` .  
  
> [!NOTE]
> Методы проверки не должны изменять модель. Нельзя гарантировать определенное время или определенный порядок выполнения ограничений. Если необходимо передать сведения между последовательными выполнениями метода проверки в рамках прохода проверки, можно использовать контекстный кэш, описанный в разделе [Согласование нескольких проверок](#ContextCache).  
  
 Например, если вы хотите убедиться в том, что каждый тип (класс, интерфейс или перечислитель) имеет имя длиной не менее трех символов, можно использовать этот метод:  
  
```  
public void ValidateTypeName(ValidationContext context, IType type)  
{  
  if (!string.IsNullOrEmpty(type.Name) && type.Name.Length < 3)  
  {  
    context.LogError(  
      string.Format("Type name {0} is too short", type.Name),  
               "001", type);  
   }  
 }  
```  
  
 В разделе [Programming with the UML API](../modeling/programming-with-the-uml-api.md) приведены сведения о методах и типах, которые можно использовать для чтения модели и навигации по ней.  
  
### <a name="about-validation-constraint-methods"></a>Сведения о методах ограничения проверки  
 Каждое ограничение проверки определяется методом следующей формы:  
  
```  
[Export(typeof(System.Action<ValidationContext, object>))]  
 [ValidationMethod(ValidationCategories.Save   
  | ValidationCategories.Menu   
  | ValidationCategories.Open)]  
public void ValidateSomething  
  (ValidationContext context, IClassifier elementToValidate)  
{...}  
```  
  
 Каждый метод проверки имеет указанные ниже атрибуты и параметры.  
  
|||  
|-|-|  
|`[Export(typeof(System.Action <ValidationContext, object>))]`|Определяет метод как ограничение проверки с помощью Managed Extensibility Framework (MEF).|  
|`[ValidationMethod (ValidationCategories.Menu)]`|Указывает, когда будет выполнена проверка. Используйте побитовый оператор или (&#124;) Если нужно объединить несколько вариантов.<br /><br /> `Menu` = вызывается из меню проверки.<br /><br /> `Save` = вызывается при сохранении модели.<br /><br /> `Open` = вызывается при открытии модели. `Load` = вызывается при сохранении модели, но в случае конфликта пользователь предупреждается о том, что повторное открытие модели может быть невозможно. Также вызывается при загрузке до того, как будет выполнен анализ модели.|  
|`public void ValidateSomething`<br /><br /> `(ValidationContext context,`<br /><br /> `IElement element)`|Замените второй параметр `IElement` на тип элемента, к которому должно применяться ограничение. Метод ограничения будет вызываться для всех элементов в указанном типе.<br /><br /> Имя метода не имеет значения.|  
  
 Можно определить любое число методов проверки, используя различные типы в качестве второго параметра. При вызове проверки каждый метод проверки вызывается для каждого элемента модели, соответствующего типу параметра.  
  
### <a name="reporting-validation-errors"></a>Сообщение об ошибках проверки  
 Чтобы создать отчет об ошибках, используйте методы, предоставленные `ValidationContext`:  
  
 `context.LogError("error string", errorCode, elementsWithError);`  
  
- `"error string"` отображается в списке ошибок [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
- `errorCode` представляет собой строку, которая должна быть уникальным идентификатором ошибки.  
  
- `elementsWithError` определяет элементы в модели. При двойном щелчке по отчету об ошибках выбирается фигура, представляющая этот элемент.  
  
  `LogError(),` `LogWarning()` и `LogMessage()` помещают сообщения в разные разделы списка ошибок.  
  
## <a name="how-validation-methods-are-applied"></a>Применение методов проверки  
 Проверка применяется к каждому элементу в модели, включая отношения и части более крупных элементов, такие как атрибуты класса и параметры операции.  
  
 Каждый метод проверки применяется к каждому элементу, соответствующему типу в его втором параметре. Это означает, например, что при определении одного метода проверки с использованием второго параметра `IUseCase` и другого метода с использованием его супертипа `IElement`оба этих метода будут применяться к каждому варианту использования в модели.  
  
 Иерархию типов [типы элементов модели UML](../modeling/uml-model-element-types.md).  
  
 Кроме того, доступ к элементам можно получить по следующим отношениям. Например, если определить метод проверки на основе `IClass`, можно выполнить перебор принадлежащих ему свойств:  
  
```  
public void ValidateTypeName(ValidationContext context, IClass c)  
{  
   foreach (IProperty property in c.OwnedAttributes)  
   {  
       if (property.Name.Length < 3)  
       {  
            context.LogError(  
                 string.Format(  
                        "Property name {0} is too short",   
                        property.Name),   
                 "001", property);  
        }  
   }  
}  
```  
  
### <a name="creating-a-validation-method-on-the-model"></a>Создание метода проверки для модели  
 Если вы хотите убедиться в том, что на протяжении всего прохода проверки метод проверки вызывается только один раз, можно проверить `IModel`:  
  
```  
using Microsoft.VisualStudio.Uml.AuxiliaryConstructs; ...  
[Export(typeof(System.Action<ValidationContext, object>))]  
[ValidationMethod(ValidationCategories.Menu)]  
public void ValidateModel(ValidationContext context, IModel model)  
{  foreach (IElement element in model.OwnedElements)  
   { ...  
```  
  
### <a name="validating-shapes-and-diagrams"></a>Проверка фигур и схем  
 Методы проверки не вызываются для отображаемых элементов, таких как схемы и фигуры, так как основной задачей этих методов является проверка модели. Однако доступ к текущей схеме можно получить через контекст схемы.  
  
 В классе проверки объявите `DiagramContext` как импортированное свойство:  
  
```  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;   
...  
[Import]  
public IDiagramContext DiagramContext { get; set; }  
```  
  
 В методе проверки можно использовать `DiagramContext` для доступа к текущей схеме фокуса, если она существует:  
  
```  
[Export(typeof(System.Action<ValidationContext, object>))]  
[ValidationMethod(ValidationCategories.Menu)]  
public void ValidateModel(ValidationContext context, IModel model)  
{  
  IDiagram focusDiagram = DiagramContext.CurrentDiagram;  
  if (focusDiagram != null)  
  {  
    foreach (IShape<IUseCase> useCaseShape in  
              focusDiagram.GetChildShapes<IUseCase>())  
    { ...  
```  
  
 Для регистрации ошибки необходимо получить элемент модели, представляемый фигурой, так как нельзя передать фигуру в `LogError`:  
  
```  
IUseCase useCase = useCaseShape.Element;  
context.LogError(... , usecase);  
```  
  
### <a name="ContextCache"></a> Согласование нескольких проверок  
 При вызове проверки, например, пользователем из меню схемы, каждый метод проверки применяется к каждому элементу модели. Это означает, что в ходе одного вызова рабочей среды проверки один и тот же метод может быть применен много раз к различным элементам.  
  
 Это представляет проблему для проверок, обрабатывающих отношения между элементами. Например, можно создать проверку, которая начинается с варианта использования и перебирает отношения **include** , чтобы убедиться в отсутствии циклов. Но если метод применяется к каждому варианту использования в модели, обладающей множеством связей **include** , он с большой вероятностью будет многократно обрабатывать одни и те же области модели.  
  
 Чтобы избежать подобной ситуации, имеется кэш контекста, в котором сохраняются сведения во время прохода проверки. Его можно использовать для передачи сведений между различными выполнениями методов проверки. Например, можно хранить список элементов, которые уже были обработаны в рамках этого прохода проверки. Такой кэш создается в начале каждого прохода проверки и не может использоваться для передачи сведений между разными проходами проверки.  
  
|||  
|-|-|  
|`context.SetCacheValue<T> (name, value)`|Сохранение значения|  
|`context.TryGetCacheValue<T> (name, out value)`|Получение значения. Возвращает значение true в случае успешного выполнения.|  
|`context.GetValue<T>(name)`|Получение значения.|  
|`Context.GetValue<T>()`|Получение значения указанного типа.|  
  
## <a name="Installing"></a> Установка и удаление расширения  
 Расширение [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] можно установить как на своем компьютере, так и на других.  
  
#### <a name="to-install-an-extension"></a>Установка расширения  
  
1. На компьютере найдите файл **.vsix** , который был создан проектом VSIX.  
  
    1. В контекстном меню проекта VSIX в **обозревателе решений**выберите пункт **Открыть папку в проводнике Windows**.  
  
    2. Найдите файл **bin\\\*\\** _Ваш_проект_ **.vsix**  
  
2. Скопируйте файл **.vsix** на компьютер, где необходимо установить расширение. Это может быть как ваш собственный компьютер, так и любой другой.  
  
    - На конечном компьютере должен быть установлен один из выпусков [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] , заданный в **source.extension.vsixmanifest**.  
  
3. На целевом компьютере откройте файл **.vsix** .  
  
     Откроется**установщик расширений Visual Studio** , который устанавливает расширение.  
  
4. Запустите или перезапустите [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
#### <a name="to-uninstall-an-extension"></a>Удаление расширения  
  
1. В меню **Сервис** щелкните пункт **Расширения и обновления**.  
  
2. Разверните узел **Установленные расширения**.  
  
3. Выберите расширение и щелкните **Удалить**.  
  
   Иногда неисправное расширение не удается загрузить, в результате чего в окне ошибок создается отчет, который не отображается в диспетчере расширений. В этом случае расширение можно удалить, удалив файл из следующего расположения где *% LocalAppData %* обычно *DriveName*: \Users\\*имяпользователя*\AppData\Local:  
  
   *% LocalAppData %* **\Microsoft\VisualStudio\\\Extensions [версия]**  
  
## <a name="Example"></a> Пример  
 В этом примере выполняется поиск циклов в отношении зависимости между элементами.  
  
 Проверка проводится при сохранении и при выполнении команды меню проверки.  
  
```  
/// <summary>  
/// Verify that there are no loops in the dependency relationsips.  
/// In our project, no element should be a dependent of itself.  
/// </summary>  
/// <param name="context">Validation context for logs.</param>  
/// <param name="element">Element to start validation from.</param>  
[Export(typeof(System.Action<ValidationContext, object>))]  
[ValidationMethod(ValidationCategories.Menu   
     | ValidationCategories.Save | ValidationCategories.Open)]  
public void NoDependencyLoops(ValidationContext context, INamedElement element)  
{  
    // The validation framework will call this method  
    // for every element in the model. But when we follow  
    // the dependencies from one element, we will validate others.  
    // So we keep a list of the elements that we don't need to validate again.   
    // The list is kept in the context cache so that it is passed  
    // from one execution of this method to another.  
    List<INamedElement> alreadySeen = null;  
    if (!context.TryGetCacheValue("No dependency loops", out alreadySeen))  
    {  
       alreadySeen = new List<INamedElement>();  
       context.SetCacheValue("No dependency loops", alreadySeen);  
    }  
  
    NoDependencyLoops(context, element,   
                new INamedElement[0], alreadySeen);      
}  
  
/// <summary>  
/// Log an error if there is any loop in the dependency relationship.  
/// </summary>  
/// <param name="context">Validation context for logs.</param>  
/// <param name="element">The element to be validated.</param>  
/// <param name="dependants">Elements we've followed in this recursion.</param>  
/// <param name="alreadySeen">Elements that have already been validated.</param>  
/// <returns>true if no error was detected</returns>  
private bool NoDependencyLoops(ValidationContext context,   
    INamedElement element, INamedElement[] dependants,   
    List<INamedElement> alreadySeen)  
{  
    if (dependants.Contains(element))  
    {  
        context.LogError(string.Format("{0} should not depend on itself", element.Name),   
        "Fabrikam.UML.NoGenLoops", // unique code for this error  
        dependants.SkipWhile(e => e != element).ToArray());   
            // highlight elements that are in the loop  
        return false;  
    }  
    INamedElement[] dependantsPlusElement =   
        new INamedElement[dependants.Length + 1];  
    dependants.CopyTo(dependantsPlusElement, 0);  
    dependantsPlusElement[dependantsPlusElement.Length - 1] = element;  
  
    if (alreadySeen.Contains(element))  
    {  
        // We have already validated this when we started   
        // from another element during this validation run.  
        return true;  
    }  
    alreadySeen.Add(element);  
  
    foreach (INamedElement supplier in element.GetDependencySuppliers())  
    {  
        if (!NoDependencyLoops(context, supplier,  
             dependantsPlusElement, alreadySeen))  
        return false;  
    }  
    return true;  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Определение и Установка расширения моделирования](../modeling/define-and-install-a-modeling-extension.md)   
 [Программирование с UML API](../modeling/programming-with-the-uml-api.md)
