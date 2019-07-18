---
title: Встраивание схемы в форму Windows
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9b2ed12175e986178d43ffe5e3da8b85e2ab22e5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62994583"
---
# <a name="embed-a-diagram-in-a-windows-form"></a>Внедрение схемы в Windows-форму

На схеме DSL можно внедрить в элемент управления Windows, который отображается в окне Visual Studio.

## <a name="embed-a-dsl-diagram-in-a-windows-control"></a>Внедрение схемы DSL в элементе управления Windows

1. Добавьте новый **пользовательский элемент управления** файл в проект DslPackage.

2. Добавьте элемент управления Panel в пользовательский элемент управления. В этой области будет содержать схему DSL.

     Добавьте другие элементы управления, которые необходимы.

     Задайте свойства привязки элементов управления.

3. В обозревателе решений щелкните правой кнопкой мыши файл пользовательского элемента управления и нажмите кнопку **Просмотр кода**. Добавьте в код этого конструктора и переменной:

    ```csharp
    internal UserControl1(MyDSLDocView docView, Control content)
      : this()
    {
      panel1.Controls.Add(content);
      this.docView = docView;
    }
    private MyDSLDocView docView;
    ```

4. Добавьте новый файл в проект DslPackage со следующим содержимым:

    ```csharp
    using System.Windows.Forms;
    namespace Company.MyDSL
    {
      partial class MyDSLDocView
      {
        private UserControl1 container;
        public override IWin32Window Window
        {
          get
          {
            if (container == null)
            {
              // Put our own form inside the DSL window:
              container = new UserControl1(this,
                (Control)base.Window);
            }
            return container;
    } } } }
    ```

5. Чтобы проверить DSL, нажмите клавиши **F5** и откройте файл образца модели. Внутри элемента управления отображается схема. Панели элементов и другие компоненты работают нормально.

## <a name="update-the-form-using-store-events"></a>Обновить форму с помощью событий хранилища

1. В конструкторе форм добавьте **ListBox** с именем `listBox1`. Откроется список элементов в модели. Он синхронизирован с модели с помощью *хранения событий*. Дополнительные сведения см. в разделе [обработчики распространения изменений за пределами модели событий](../modeling/event-handlers-propagate-changes-outside-the-model.md).

2. В файле пользовательского кода переопределите дополнительные методы в класс DocView:

    ```csharp
    partial class MyDSLDocView
    {
     /// <summary>
     /// Register store event listeners.
     /// This method is called when the model and diagram
     /// have completed loading.
     /// </summary>
     protected override bool LoadView()
      {
        bool result = base.LoadView();
        Store store = this.DocData.Store;
        EventManagerDirectory emd = store.EventManagerDirectory;
        DomainClassInfo componentClass = store.DomainDataDirectory.FindDomainClass(typeof(ExampleElement));
        emd.ElementAdded.Add(componentClass, new EventHandler<ElementAddedEventArgs>(AddElement));
        emd.ElementDeleted.Add(componentClass, new EventHandler<ElementDeletedEventArgs>(RemoveElement));

        // Do the initial parts list:
        container.SetUpFormFromModel();
        return result;
      }
     /// <summary>
     /// Listener method called on creation of each instance of
     /// the ExampleElement class or its subclasses.
     /// </summary>
     private void AddElement(object sender, ElementAddedEventArgs e)
     {
       container.Add(e.ModelElement as ExampleElement);
     }
     /// <summary>
     /// Listener method called after deletion of each instance of
     /// the ExampleElement class or its subclasses.
     /// </summary>
     private void RemoveElement(object sender, ElementDeletedEventArgs e)
     {
       container.Remove(e.ModelElement as ExampleElement);
     }
    ```

3. В коде программной части пользовательского элемента управления вставьте методы для прослушивания элементов добавляются и удаляются:

    ```csharp
    public partial class UserControl1 : UserControl { ...

    private ExampleModel modelRoot;

    internal void Add(ExampleElement e) { UpdatePartsList(); }
    internal void Remove(ExampleElement e) { UpdatePartsList(); }

    internal void SetUpFormFromModel()
    {
      modelRoot = this.docView.CurrentDiagram.ModelElement as ExampleModel;
      UpdatePartsList();
    }

    private void UpdatePartsList()
    {
      StringBuilder builder = new StringBuilder();
      listBox1.Items.Clear();
      foreach (ExampleElement c in modelRoot.Elements)
      {
        listBox1.Items.Add(c.Name);
      }
    }
    ```

4. Чтобы проверить DSL, нажмите клавиши **F5** и в экспериментальном экземпляре Visual Studio, откройте пример файла модели.

     Обратите внимание на то, что отображается список элементов в модели, и его правильности после любой добавления или удаления, а после отмены и повтора.

## <a name="see-also"></a>См. также

- [Перемещение по модели и обновление модели в коде программы](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Написание кода для настройки доменного языка](../modeling/writing-code-to-customise-a-domain-specific-language.md)
