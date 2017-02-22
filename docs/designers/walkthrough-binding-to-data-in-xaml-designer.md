---
title: "Пошаговое руководство. Привязка к данным в конструкторе XAML | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.XamlDesigner.DataBinding"
ms.assetid: 1a99aeae-c3ef-407d-ba79-b8055489a43d
caps.latest.revision: 20
caps.handback.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Пошаговое руководство. Привязка к данным в конструкторе XAML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В конструкторе XAML можно задать свойства привязки данных с помощью области рисования и в окне "Свойства".  В примере в этом пошаговом руководстве показано, как привязать данные к элементу управления.  В частности, здесь демонстрируется, как создать простой класс покупательской корзины со свойством типа [DependencyProperty](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.dependencyproperty.aspx) с именем `ItemCount`, и затем привязать свойство `ItemCount` к свойству **Text** элемента управления [TextBlock](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx).  
  
### Создание класса для использования в качестве источника данных  
  
1.  В меню **Файл** последовательно выберите пункты **Создать** и **Проект**.  
  
2.  В диалоговом окне **Новый проект** разверните узел **Visual C\#** или **Visual Basic**, разверните узел **Настольный компьютер Windows** и выберите шаблон **Приложение WPF**.  
  
3.  Укажите BindingTest в качестве имени проекта и нажмите кнопку **ОК**.  
  
4.  Откройте файл MainWindow.xaml.cs \(или MainWindow.xaml.vb\) и добавьте следующий код.  В C\# добавьте код в пространстве имен `BindingTest` \(перед последней закрывающей скобкой в файле\).  В Visual Basic просто добавьте новый класс.  
  
    ```c#  
    public class ShoppingCart : DependencyObject  
    {  
        public int ItemCount  
        {  
            get { return (int)GetValue(ItemCountProperty); }  
            set { SetValue(ItemCountProperty, value); }  
        }  
  
        public static readonly DependencyProperty ItemCountProperty =  
             DependencyProperty.Register("ItemCount", typeof(int),  
             typeof(ShoppingCart), new PropertyMetadata(0));  
    }  
  
    ```  
  
    ```vb  
    Public Class ShoppingCart  
        Inherits DependencyObject  
  
        Public Shared ReadOnly ItemCountProperty As DependencyProperty = DependencyProperty.Register(  
            "ItemCount", GetType(Integer), GetType(ShoppingCart), New PropertyMetadata(0))  
        Public Property ItemCount As Integer  
            Get  
                ItemCount = CType(GetValue(ItemCountProperty), Integer)  
            End Get  
            Set(value As Integer)  
                SetValue(ItemCountProperty, value)  
            End Set  
        End Property  
    End Class  
    ```  
  
     Этот код задает значение 0 как число элементов по умолчанию с помощью объекта [PropertyMetadata](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.propertymetadata.aspx).  
  
5.  В меню **Файл** выберите **Построение** и **Построить решение**.  
  
### Привязка свойства ItemCount к элементу управления TextBlock  
  
1.  В обозревателе решений откройте контекстное меню файла MainWindow.xaml и выберите **Конструктор представлений**.  
  
2.  В области элементов выберите элемент управления [Сетка](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx) и добавьте его на форму.  
  
3.  Выбрав `Grid`, в окне "Свойства" нажмите кнопку **Создать** рядом со свойством **DataContext**.  
  
4.  В диалоговом окне **Выбор объекта** убедитесь, что флажок **Показать все сборки** снят, выберите **ShoppingCart** в пространстве имен **BindingTest** и нажмите кнопку **ОК**.  
  
     На следующем рисунке показано диалоговое окно **Выбор объекта** с выбранным объектом **ShoppingCart**.  
  
     ![Диалоговое окно "Выбор объекта"](../designers/media/blendselectobject.PNG "BlendSelectObject")  
  
5.  В **области элементов** выберите элемент управления `TextBlock`, чтобы добавить его на форму.  
  
6.  После выбора элемента управления `TextBlock` в окне "Свойства" выберите метку свойства справа от свойства **Text**, а затем выберите **Создать привязку данных**.  \(Метка свойства выглядит как небольшой квадрат.\)  
  
7.  В диалоговом окне "Создание привязки данных" в поле **Путь** выберите свойство **ItemCount: \(int32\)** и нажмите кнопку **ОК**.  
  
     На следующем рисунке показано диалоговое окно **Создание привязки данных** с выбранным свойством **ItemCount**.  
  
     ![Диалоговое окно "Создание привязки данных"](../designers/media/xaml_create_data_binding.png "xaml\_create\_data\_binding")  
  
8.  Нажмите клавишу F5 для запуска приложения.  
  
     Элемент управления `TextBlock` должен показать значение по умолчанию 0 в виде текста.  
  
## См. также  
 [Создание пользовательского интерфейса с помощью конструктора XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)   
 [NIB: Add Value Converter dialog box](http://msdn.microsoft.com/ru-ru/c5f3d110-a541-4b55-8bca-928f77778af8)