---
title: Встраивание схемы в форму Windows | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fa6cd040-7c88-4329-b9c3-2a80b312610f
caps.latest.revision: 3
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 04ecf5bd7bfc91e03f48e624d208a5b4f29b10b7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49292530"
---
# <a name="embedding-a-diagram-in-a-windows-form"></a>Встраивание схемы в форму Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

На схеме DSL можно внедрить в элемент управления Windows, который отображается в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] окна.  
  
## <a name="embedding-a-diagram"></a>Встраивание схемы  
  
#### <a name="to-embed-a-dsl-diagram-in-a-windows-control"></a>Чтобы внедрить схему DSL в элементе управления Windows  
  
1.  Добавьте новый **пользовательский элемент управления** файл в проект DslPackage.  
  
2.  Добавьте элемент управления Panel в пользовательский элемент управления. В этой области будет содержать схему DSL.  
  
     Добавьте другие элементы управления, которые необходимы.  
  
     Задайте свойства привязки элементов управления.  
  
3.  В обозревателе решений щелкните правой кнопкой мыши файл пользовательского элемента управления и нажмите кнопку **Просмотр кода**. Добавьте в код этого конструктора и переменной:  
  
    ```csharp  
  
    internal UserControl1(MyDSLDocView docView, Control content)  
      : this()  
    {  
      panel1.Controls.Add(content);  
      this.docView = docView;  
    }  
    private MyDSLDSLDocView docView;  
  
    ```  
  
4.  Добавьте новый файл в проект DslPackage со следующим содержимым:  
  
    ```  
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
  
5.  Чтобы проверить DSL, нажмите клавишу F5 и откройте файл образца модели. Внутри элемента управления отображается схема. Панели элементов и другие компоненты работают нормально.  
  
#### <a name="updating-the-form-using-store-events"></a>Обновления формы с помощью событий Store  
  
1.  В конструкторе форм добавьте **ListBox** с именем `listBox1`. Откроется список элементов в модели. Он будет храниться в synchronism с модели с помощью *хранения событий*. Дополнительные сведения см. в разделе [обработчики распространения изменений за пределами модели событий](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
2.  В файле пользовательского кода переопределите дополнительные методы в класс DocView:  
  
    ```  
  
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
  
3.  В коде программной части пользовательского элемента управления вставьте методы для прослушивания элементов добавляются и удаляются:  
  
    ```  
  
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
  
4.  Чтобы проверить DSL, нажмите клавишу F5 и в экспериментальном экземпляре [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], откройте пример файла модели.  
  
     Обратите внимание на то, что отображается список элементов в модели, и его правильности после любой добавления или удаления, а после отмены и повтора.  
  
## <a name="see-also"></a>См. также  
 [Переход и обновление модели в программном коде](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Написание кода для настройки доменного языка](../modeling/writing-code-to-customise-a-domain-specific-language.md)

