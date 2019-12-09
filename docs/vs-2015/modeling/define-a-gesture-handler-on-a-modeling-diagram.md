---
title: Определение обработчика жестов на схеме моделирования | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, double-click
- UML - extending, drag and drop
ms.assetid: e5e1d70a-3539-4321-a3b1-89e86e4d6430
caps.latest.revision: 36
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bf749d1073faf4cf22febafce716af36b47c6484
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299303"
---
# <a name="define-a-gesture-handler-on-a-modeling-diagram"></a>Определение обработчика жестов на схеме моделирования
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В Visual Studio можно определить команды, которые выполняются, когда пользователь дважды щелкает элементы на схеме UML или перетаскивает элементы на эту схему. Вы можете упаковать эти расширения в расширение Visual Studio Integration Extension ([VSIX](https://go.microsoft.com/fwlink/?LinkId=160780)) и предоставить их другим пользователям Visual Studio.

 Так как это поведение уже является встроенным для типа схемы и типа элемента, который нужно перетащить, его расширение и перезапись могут быть невозможны.

## <a name="requirements"></a>Требования
 См. раздел [Требования](../modeling/extend-uml-models-and-diagrams.md#Requirements).

 Чтобы узнать, какие версии Visual Studio поддерживают эту функцию, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="creating-a-gesture-handler"></a>Создание обработчика жестов
 Чтобы определить обработчик жестов для конструктора UML, необходимо создать класс, определяющий поведение обработчика жестов, и внедрить этот класс в расширение Visual Studio Integration Extension (VSIX). VSIX выполняет роль контейнера, позволяющего установить обработчик. Определить обработчик жестов можно одним из двух способов:

- **Создайте обработчик жестов в своем собственном расширении VSIX с помощью шаблона проекта.** Этот способ быстрее. Используйте его, если не хотите объединять обработчик с другими типами расширений, такими как расширения проверки, пользовательские элементы панели элементов или команды меню.

- **Создание отдельного обработчика жестов и проектов VSIX.** Используйте этот метод, если нужно объединить несколько типов расширения в одном расширении VSIX. Например, если для обработчика жестов требуется, чтобы модель соблюдала определенные ограничения, можно внедрить его в то же расширение VSIX, что и метод проверки.

#### <a name="to-create-a-gesture-handler-in-its-own-vsix"></a>Создание обработчика жестов в отдельном расширении VSIX

1. В области **Проекты моделирования** диалогового окна **Новый проект**выберите **Расширение обработчика жестов**.

2. Откройте файл **.cs** в новом проекте и внесите в класс `GestureExtension` изменения, реализующие обработчик жестов.

    Более подробную информацию см. в разделе [Реализация обработчика жестов](#Implementing).

3. Проверьте обработчик жестов, нажав клавишу F5. Более подробную информацию см. в разделе [Выполнение обработчика жестов](#Executing).

4. Установите обработчик жестов на другом компьютере, скопировав файл **bin\\\*\\\*. VSIX** , созданный проектом. Более подробную информацию см. в разделе [Установка и удаление расширения](#Installing).

   Ниже описана альтернативная процедура.

#### <a name="to-create-a-separate-class-library-dll-project-for-the-gesture-handler"></a>Создание отдельного проекта библиотеки классов (DLL) для обработчика жестов

1. Создайте проект библиотеки классов либо в новом решении [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , либо в уже существующем.

   1. В меню **Файл** последовательно выберите пункты **Создать**и **Проект**.

   2. В разделе **Установленные шаблоны**разверните узел **Visual C#** или **Visual Basic**и выберите в среднем столбце пункт **Библиотека классов**.

2. Добавьте в проект указанные ниже ссылки.

    `Microsoft.VisualStudio.Modeling.Sdk.[version]`

    `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]`

    `Microsoft.VisualStudio.ArchitectureTools.Extensibility`

    `Microsoft.VisualStudio.Uml.Interfaces`

    `System.ComponentModel.Composition`

    `System.Windows.Forms`

    `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer` — требуется только при расширении схем слоев. Дополнительные сведения см. в разделе [расширение схем слоев](../modeling/extend-layer-diagrams.md).

3. Добавьте файл класса в проект и вставьте в него указанный ниже код.

   > [!NOTE]
   > Измените пространство имен и имя класса в соответствии с вашими предпочтениями.

   ```
   using System.ComponentModel.Composition;
   using System.Linq;
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Modeling.Diagrams;
   using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
   using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
   using Microsoft.VisualStudio.Uml.AuxiliaryConstructs;
   using Microsoft.VisualStudio.Modeling;
   using Microsoft.VisualStudio.Uml.Classes;
   // ADD other UML namespaces if required

   namespace MyGestureHandler // CHANGE
   {
     // DELETE any of these attributes if the handler
     // should not work with some types of diagram.
     [ClassDesignerExtension]
     [ActivityDesignerExtension]
     [ComponentDesignerExtension]
     [SequenceDesignerExtension]
     [UseCaseDesignerExtension]
     // [LayerDesignerExtension]

     // Gesture handlers must export IGestureExtension:
     [Export(typeof(IGestureExtension))]
     // CHANGE class name
     public class MyGesture1 : IGestureExtension
     {
       [Import]
       public IDiagramContext DiagramContext { get; set; }

       /// <summary>
       /// Called when the user double-clicks on the diagram
       /// </summary>
       /// <param name="targetElement"></param>
       /// <param name="diagramPointEventArgs"></param>
       public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)
       {
         // CHANGE THIS CODE FOR YOUR APPLICATION.

         // Get the target shape, if any. Null if the target is the diagram.
         IShape targetIShape = targetElement.CreateIShape();

         // Do something...
       }

       /// <summary>
       /// Called repeatedly when the user drags from anywhere on the screen.
       /// Return value should indicate whether a drop here is allowed.
       /// </summary>
       /// <param name="targetMergeElement">References the element to be dropped on.</param>
       /// <param name="diagramDragEventArgs">References the element to be dropped.</param>
       /// <returns></returns>
       public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)
       {
         // CHANGE THIS CODE FOR YOUR APPLICATION.

         // Get the target element, if any. Null if the target is the diagram.
         IShape targetIShape = targetMergeElement.CreateIShape();

         // This example allows drag of any UML elements.
         return GetModelElementsFromDragEvent(diagramDragEventArgs).Count() > 0;
       }

       /// <summary>
       /// Execute the action to be performed on the drop.
       /// </summary>
       /// <param name="targetDropElement"></param>
       /// <param name="diagramDragEventArgs"></param>
       public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
       {
         // CHANGE THIS CODE FOR YOUR APPLICATION.
       }

       /// <summary>
       /// Retrieves UML IElements from drag arguments.
       /// Works for drags from UML diagrams.
       /// </summary>
       private IEnumerable<IElement> GetModelElementsFromDragEvent
               (DiagramDragEventArgs dragEvent)
       {
         //ElementGroupPrototype is the container for
         //dragged and copied elements and toolbox items.
         ElementGroupPrototype prototype =
            dragEvent.Data.
            GetData(typeof(ElementGroupPrototype))
                 as ElementGroupPrototype;
         // Locate the originals in the implementation store.
         IElementDirectory implementationDirectory =
            dragEvent.DiagramClientView.Diagram.Store.ElementDirectory;

         return prototype.ProtoElements.Select(
           prototypeElement =>
           {
             ModelElement element = implementationDirectory
               .FindElement(prototypeElement.ElementId);
             ShapeElement shapeElement = element as ShapeElement;
             if (shapeElement != null)
             {
               // Dragged from a diagram.
               return shapeElement.ModelElement as IElement;
             }
             else
             {
               // Dragged from UML Model Explorer.
               return element as IElement;
             }
           });
       }

     }
   }

   ```

    Более подробную информацию о том, что следует помещать в методы, см. в разделе [Реализация обработчика жестов](#Implementing).

   Команду меню необходимо добавить в проект VSIX, который выступает контейнером для установки команды. При необходимости в проект VSIX можно добавить и другие компоненты.

#### <a name="to-add-a-separate-gesture-handler-to-a-vsix-project"></a>Добавление отдельного обработчика жестов в проект VSIX

1. Эта процедура не требуется, если обработчик жестов создан со своим собственным расширением VSIX.

2. Создайте проект VSIX, если ваше решение еще его не содержит.

    1. В контекстном меню решения в **обозревателе решений**выберите пункт **Добавить**, а затем **Новый проект**.

    2. В разделе **Установленные шаблоны**разверните узел **Visual C#** или **Visual Basic**и выберите пункт **Расширение среды**. В среднем столбце выберите пункт **Проект VSIX**.

3. Назначьте проект VSIX запускаемым проектом решения.

    - В контекстном меню проекта VSIX в обозревателе решений выберите пункт **Назначить запускаемым проектом**.

4. В **source.extension.vsixmanifest**добавьте проект библиотеки классов обработчика жестов в качестве компонента MEF.

    1. На вкладке **Метаданные** введите имя для VSIX.

    2. На вкладке **Цели установки** задайте в качестве целевых объектов версии Visual Studio.

    3. На вкладке **Активы** выберите **Создать**и укажите в диалоговом окне следующие значения:

         **Тип** = **Компонент MEF**

         **Источник** = **Проект в текущем решении**

         **Проект** = *Ваш проект библиотеки классов*

## <a name="Executing"></a>Исполнение обработчика жестов
 В целях проверки запустите обработчик жестов в режиме отладки.

#### <a name="to-test-the-gesture-handler"></a>Проверка обработчика жестов

1. Нажмите клавишу **F5**или выберите в меню **Отладка** пункт **Начать отладку**.

    Запустится экспериментальный экземпляр [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

    **Устранение неполадок**. Если новый экземпляр [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] не запускается:

   - При наличии нескольких проектов убедитесь в том, что для проекта VSIX задан параметр "Назначить запускаемым проектом".

   - В обозревателе решений в контекстном меню запускаемого или единственного проекта выберите пункт "Свойства". В редакторе свойств проекта перейдите на вкладку **Отладка** . Убедитесь, что строка в поле **Запуск внешней программы** является полным путем к [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], обычно:

        `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`

2. В экспериментальном экземпляре [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]откройте или создайте проект моделирования и откройте или создайте схему моделирования. Используйте схему, которая относится к одному из типов, перечисленных в атрибутах вашего класса обработчика жестов.

3. Дважды щелкните в любом месте схемы. Будет вызван обработчик двойного щелчка.

4. Перетащите элемент из обозревателя UML на схему. Будет вызван обработчик перетаскивания.

   **Устранение неполадок**. Если обработчик жестов не работает, убедитесь в следующем:

- Проект обработчика жестов указан в качестве компонента MEF на вкладке **Активы** в **source.extensions.manifest** проекта VSIX.

- Параметры всех атрибутов `Import` и `Export` являются допустимыми.

- Метод `CanDragDrop` не возвращает значение `false`.

- Тип используемой схемы модели (схема UML классов, последовательностей и т. д.) указан в качестве одного из атрибутов класса обработчика жестов — [ClassDesignerExtension], [SequenceDesignerExtension] и т. д.

- Для данного типа целевого и перетаскиваемого элемента не предусмотрено встроенной функциональности.

## <a name="Implementing"></a>Реализация обработчика жестов

### <a name="the-gesture-handler-methods"></a>Методы обработчика жестов
 Класс обработчика жестов реализует и экспортирует тип <xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement.IGestureExtension>. Ниже перечислены методы, которые необходимо определить.

|||
|-|-|
|`bool CanDragDrop (ShapeElement target, DiagramDragEventArgs dragEvent)`|Чтобы разрешить перетаскивание исходного элемента, на который ссылается `true` , на данный целевой объект, этот метод должен возвращать значение `dragEvent` .<br /><br /> Этот метод не должен вносить изменения в модель. Метод должен работать быстро, так как используется для определения состояния указателя по мере того, как пользователь перемещает мышь.|
|`void OnDragDrop (ShapeElement target, DiagramDragEventArgs dragEvent)`|Обновите модель на основе исходного объекта, на который ссылается `dragEvent`, и целевого объекта.<br /><br /> Метод вызывается, когда пользователь отпускает кнопку мыши после перетаскивания.|
|`void OnDoubleClick (ShapeElement target, DiagramPointEventArgs pointEvent)`|`target` — это фигура, которую дважды щелкнул пользователь.|

 Можно создать обработчики, способные принимать не только UML, но и другие элементы, такие как файлы, узлы в представлении классов .NET и т. д. Пользователь может перетащить любые из этих элементов на схему UML при условии, что создан метод `OnDragDrop` , который может декодировать сериализованную форму этих элементов. Методы декодирования различаются в зависимости от типа элемента.

 Ниже представлены параметры этих методов.

- `ShapeElement target`. Фигура или схема, на которую пользователь перетащил объекты.

    `ShapeElement`. Класс реализации, лежащий в основе инструментов моделирования UML. Чтобы снизить риск приведения модели и схем UML в несогласованное состояние, рекомендуется не использовать методы этого класса напрямую. Вместо этого заключите элемент в `IShape`, а затем используйте методы, описанные в разделе [Отображение UML-модели на схемах](../modeling/display-a-uml-model-on-diagrams.md).

  - Получение оболочки `IShape`:

      ```
      IShape targetIShape = target.CreateIShape(target);
      ```

  - Получение элемента модели, который является целевым объектом операции перетаскивания или двойного щелчка:

      ```
      IElement target = targetIShape.Element;
      ```

      Его можно привести к более конкретному типу элемента.

  - Получение хранилища моделей UML, которое содержит модель UML:

      ```
      IModelStore modelStore =
        targetIShape.Element.GetModelStore(); 
      ```

  - Получение доступа к основному приложению и поставщику услуг:

      ```
      target.Store.GetService(typeof(EnvDTE.DTE)) as EnvDTE.DTE
      ```

- `DiagramDragEventArgs eventArgs`. Этот параметр содержит исходный объект операции перетаскивания в сериализованной форме.

    ```
    System.Windows.Forms.IDataObject data = eventArgs.Data;
    ```

     На схему можно перетаскивать элементы разных видов из разных частей [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]или с рабочего стола Windows. В `IDataObject`разные типы элементов кодируются по-разному. Инструкции по извлечению элементов см. в документации по соответствующему типу объекта.

     Если исходный объект является элементом UML, который перетаскивается из обозревателя моделей UML или из другой схемы UML, см. статью [Получение элементов модели UML из IDataObject](../modeling/get-uml-model-elements-from-idataobject.md).

### <a name="writing-the-code-of-the-methods"></a>Написание кода методов
 Более подробную информацию о создании кода для чтения и обновления модели см. в разделе [Programming with the UML API](../modeling/programming-with-the-uml-api.md).

 Сведения о доступе к сведениям о модели в операции перетаскивания см. в разделе [Получение элементов модели UML из IDataObject](../modeling/get-uml-model-elements-from-idataobject.md).

 Если вы работаете со схемой последовательностей, см. также раздел [изменение схем последовательностей UML с помощью API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).

 Помимо параметров методов, вы можете также объявить импортированное свойство в собственном классе, который предоставляет доступ к текущей схеме и модели.

```
[Import] public IDiagramContext DiagramContext { get; set; }
```

 Объявление `IDiagramContext` позволяет создавать код в методах, осуществляющих доступ к схеме, текущему выделению и модели:

```
IDiagram diagram = this.DiagramContext.CurrentDiagram;
foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>)
{ IElement element = shape.Element; ... }
IModelStore modelStore = diagram.ModelStore;
IModel model = modelStore.Root;
foreach (IDiagram diagram in modelStore.Diagrams) {...}
foreach (IElement element in modelStore.AllInstances<IUseCase>) {...}
```

 Дополнительные сведения см. [в разделе Навигация по модели UML](../modeling/navigate-the-uml-model.md).

## <a name="Installing"></a>Установка и удаление расширения
 Расширение [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] можно установить как на своем компьютере, так и на других.

#### <a name="to-install-an-extension"></a>Установка расширения

1. На компьютере найдите файл **.vsix** , который был создан проектом VSIX.

    1. В контекстном меню проекта VSIX в **обозревателе решений**выберите пункт **Открыть папку в проводнике Windows**.

    2. Откройте файл **bin\\\*\\** _йоурпрожект_ **. VSIX**

2. Скопируйте файл **.vsix** на компьютер, где необходимо установить расширение. Это может быть как ваш собственный компьютер, так и любой другой.

     На конечном компьютере должен быть установлен один из выпусков [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] , заданный в **source.extension.vsixmanifest**.

3. На целевом компьютере откройте файл **.vsix** .

     Откроется**установщик расширений Visual Studio** , который устанавливает расширение.

4. Запустите или перезапустите [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

#### <a name="to-uninstall-an-extension"></a>Удаление расширения

1. В меню **Сервис** щелкните пункт **Расширения и обновления**.

2. Разверните узел **Установленные расширения**.

3. Выберите расширение и щелкните **Удалить**.

   Иногда неисправное расширение не удается загрузить, в результате чего в окне ошибок создается отчет, который не отображается в диспетчере расширений. В этом случае расширение можно удалить, удалив файл из следующей папки:

   *% LocalAppData%* **\локал\микрософт\висуалстудио\\[версия] \екстенсионс**

## <a name="DragExample"></a> Пример
 В приведенном ниже примере показано создание линий жизни на схеме последовательностей с использованием частей и портов компонента, перетащенных со схемы компонентов.

 Чтобы проверить этот сценарий, нажмите клавишу F5. Откроется экспериментальный экземпляр Visual Studio. Откройте модель UML и создайте компонент на схеме компонентов в этом экземпляре. Добавьте в этот компонент несколько интерфейсов и внутренних частей компонента. Выберите интерфейсы и части. Затем перетащите интерфейсы и части на схему последовательностей. (Перетащите с диаграммы компонентов на вкладку схемы последовательностей, а затем на схему последовательностей.) Для каждого интерфейса и части будет отображаться линия жизни.

 Дополнительные сведения о связывании взаимодействий с схемами последовательностей см. [в разделе изменение схем последовательностей UML с помощью API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).

```
using System.Collections.Generic;
using System.ComponentModel.Composition;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Uml.AuxiliaryConstructs;
using Microsoft.VisualStudio.Uml.Classes;
using Microsoft.VisualStudio.Uml.Interactions;
using Microsoft.VisualStudio.Uml.CompositeStructures;
using Microsoft.VisualStudio.Uml.Components;

/// <summary>
/// Creates lifelines from component ports and parts.
/// </summary>
[Export(typeof(IGestureExtension))]
[SequenceDesignerExtension]
public class CreateLifelinesFromComponentParts : IGestureExtension
{
  [Import]
  public IDiagramContext Context { get; set; }

  /// <summary>
  /// Called by the modeling framework when
  /// the user drops something on a target.
  /// </summary>
  /// <param name="target">The target shape or diagram </param>
  /// <param name="dragEvent">The item being dragged</param>
  public void OnDragDrop(ShapeElement target,
           DiagramDragEventArgs dragEvent)
  {
    ISequenceDiagram diagram = Context.CurrentDiagram
            as ISequenceDiagram;
    IInteraction interaction = diagram.Interaction;
    if (interaction == null)
    {
      // Sequence diagram is empty: create an interaction.
      interaction = diagram.ModelStore.Root.CreateInteraction();
      interaction.Name = Context.CurrentDiagram.Name;
      diagram.Bind(interaction);
    }
    foreach (IConnectableElement connectable in
       GetConnectablesFromDrag(dragEvent))
    {
      ILifeline lifeline = interaction.CreateLifeline();
      lifeline.Represents = connectable;
      lifeline.Name = connectable.Name;
    }
  }

  /// <summary>
  /// Called by the modeling framework to determine whether
  /// the user can drop something on a target.
  /// Must not change anything.
  /// </summary>
  /// <param name="target">The target shape or diagram</param>
  /// <param name="dragEvent">The item being dragged</param>
  /// <returns>true if this item can be dropped on this target</returns>
  public bool CanDragDrop(ShapeElement target,
           DiagramDragEventArgs dragEvent)
  {
    IEnumerable<IConnectableElement> connectables = GetConnectablesFromDrag(dragEvent);
    return connectables.Count() > 0;
  }

  ///<summary>
  /// Get dragged parts and ports of an IComponent.
  ///</summary>
  private IEnumerable<IConnectableElement>
    GetConnectablesFromDrag(DiagramDragEventArgs dragEvent)
  {
    foreach (IElement element in
      GetModelElementsFromDragEvent(dragEvent))
    {
      IConnectableElement part = element as IConnectableElement;
      if (part != null)
      {
        yield return part;
      }
    }
  }

  /// <summary>
  /// Retrieves UML IElements from drag arguments.
  /// Works for drags from UML diagrams.
  /// </summary>
  private IEnumerable<IElement> GetModelElementsFromDragEvent
          (DiagramDragEventArgs dragEvent)
  {
    //ElementGroupPrototype is the container for
    //dragged and copied elements and toolbox items.
    ElementGroupPrototype prototype =
       dragEvent.Data.
       GetData(typeof(ElementGroupPrototype))
            as ElementGroupPrototype;
    // Locate the originals in the implementation store.
    IElementDirectory implementationDirectory =
       dragEvent.DiagramClientView.Diagram.Store.ElementDirectory;

    return prototype.ProtoElements.Select(
      prototypeElement =>
      {
        ModelElement element = implementationDirectory
          .FindElement(prototypeElement.ElementId);
        ShapeElement shapeElement = element as ShapeElement;
        if (shapeElement != null)
        {
          // Dragged from a diagram.
          return shapeElement.ModelElement as IElement;
        }
        else
        {
          // Dragged from UML Model Explorer.
          return element as IElement;
        }
      });
  }

  public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)
  {
  }
}

```

 Код `GetModelElementsFromDragEvent()` описан в разделе [Получение элементов модели UML из IDataObject](../modeling/get-uml-model-elements-from-idataobject.md).

## <a name="see-also"></a>См. также
 [Определение и установка расширения моделирования расширение](../modeling/define-and-install-a-modeling-extension.md) [моделей и схем UML](../modeling/extend-uml-models-and-diagrams.md) [Определение команды меню на схеме моделирования](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [Определение ограничений проверки для программирования UML-моделей](../modeling/define-validation-constraints-for-uml-models.md) [с помощью API UML](../modeling/programming-with-the-uml-api.md)
