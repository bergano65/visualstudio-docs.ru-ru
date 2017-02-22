---
title: "Задание уникального свойства автоматизации элементов управления для Магазина Windows при тестировании | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9bdd74ff-2534-4fc7-a5c3-a77bf7843037
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "mlearned"
manager: "douge"
---
# Задание уникального свойства автоматизации элементов управления для Магазина Windows при тестировании
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Чтобы выполнять закодированные тесты пользовательского интерфейса для приложения для Магазина Windows на базе XAML, необходимо обладать уникальным свойством автоматизации, идентифицирующим каждый элемент управления.  
  
 В зависимости от типа элемента управления XAML в приложении можно присвоить ему уникальное свойство автоматизации.  В этом разделе описывается, как присвоить уникальное свойство автоматизации в следующих случаях:  
  
-   [Статическое определение элементов управления на языке XAML](#UniquePropertyWindowsStoreControlsStaticXAML)  
  
-   [Присвоение уникальных свойств автоматизации с помощью Visual Studio или Expression Blend](#UniquePropertyWindowsStoreControlsExpressionBlend)  
  
-   [Использование шаблона данных](#UniquePropertyWindowsStoreControlsDataTemplate)  
  
-   [Использование шаблона элемента управления](#UniquePropertyWindowsStoreControlsControlTemplate)  
  
-   [Динамические элементы управления](#UniquePropertyWindowsStoreControlsDynamicControls)  
  
## Способы присвоения уникального свойства автоматизации  
  
###  <a name="UniquePropertyWindowsStoreControlsStaticXAML"></a> Статическое определение XAML  
 Чтобы указать уникальное свойство автоматизации для элемента управления, определенного в XAML\-файле, можно явно или неявно задать свойства AutomationProperties.AutomationId или AutomationProperties.Name, как это показано в следующих примерах.  Если задать одно из этих значений, элементу управления будет присвоено уникальное свойство автоматизации, которое может использоваться для идентификации элемента управления при создании закодированных тестов пользовательского интерфейса или при записи действий.  
  
 **Неявное задание свойства**  
  
 В XAML элемента управления с помощью свойства Name задайте свойству AutomationProperties.AutomationId значение ButtonX.  
  
```xaml  
<Button Name="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />  
  
```  
  
 В XAML элемента управления с помощью свойства Content задайте свойству AutomationProperties.Name значение ButtonY.  
  
```xaml  
<Button Content="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />  
  
```  
  
 **Явное задание свойства**  
  
 В XAML элемента управления явно задайте свойству AutomationProperties.AutomationId значение ButtonX.  
  
```xaml  
<Button AutomationProperties.AutomationId=“ButtonX” Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />  
  
```  
  
 В XAML элемента управления явно задайте свойству AutomationProperties.Name значение ButtonY.  
  
```  
<Button AutomationProperties.Name="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />  
```  
  
###  <a name="UniquePropertyWindowsStoreControlsExpressionBlend"></a> Присвоение уникальных свойств автоматизации с помощью Visual Studio или Expression Blend  
 Кроме того, для присвоения уникальных имен интерактивным элементам \(например кнопкам, спискам, полям со списком и текстовым полям\) можно использовать Visual Studio или Expression Blend версии 3 или более поздней версии.  С его помощью можно задать свойству AutomationProperties.Name элемента управления уникальное значение.  
  
 **Visual Studio:** В меню **Средства** укажите пункт **Параметры** и затем пункт **Текстовый редактор**, затем **XAML** и наконец **Разное**.  
  
 Выделите флажок **Автоматически именовать интерактивные элементы при создании** , и нажмите кнопку **OK**.  
  
 ![Прочие параметры XAML](../test/media/cuit_windowsstoreapp_b.png "CUIT\_WindowsStoreApp\_B")  
  
 **Blend для Visual Studio:** Ниже описаны способы, как это сделать с помощью приложения Blend для Visual Studio.  
  
> [!NOTE]
>  Этот способ можно использовать только для элементов управления, созданных статически с помощью XAML.  
  
 **Присвоение уникального имени существующим элементам управления**  
  
 В меню **Сервис** выберите пункт **Присвоение имени интерактивным элементам**, как показано на следующем рисунке.  
  
 ![Выбор присвоения имен интерактивных элементов в меню "Сервис"](../test/media/cuit_windowsstoreproperty_blend_1.png "CUIT\_WindowsStoreProperty\_Blend\_1")  
  
 **Автоматическое присвоение уникального имени создаваемым элементам управления**  
  
 В меню **Сервис** выберите пункт **Параметры** и нажмите **Проект**.  Выделите флажок **Автоматически именовать интерактивные элементы при создании** , и нажмите кнопку **OK**, как показано ниже:  
  
 ![Задание проекта для имен интерактивных элементов](../test/media/cuit_windowsstoreproeprty_blend_2.png "CUIT\_WindowsStoreProeprty\_Blend\_2")  
  
###  <a name="UniquePropertyWindowsStoreControlsDataTemplate"></a> Использование шаблона данных  
 Можно воспользоваться следующим кодом XAML, чтобы определить простой шаблон с помощью свойства ItemTemplate и привязать значения в списке к переменным.  
  
```xaml  
  
<ListBox Name="listBox1" ItemsSource="{Binding Source={StaticResource employees}}">  
   <ListBox.ItemTemplate>  
      <DataTemplate>  
         <StackPanel Orientation="Horizontal">  
            <TextBlock Text="{Binding EmployeeName}" />  
            <TextBlock Text="{Binding EmployeeID}" />  
         </StackPanel>  
      </DataTemplate>  
   </ListBox.ItemTemplate>  
</ListBox>  
```  
  
 Кроме того, можно воспользоваться следующим кодом XAML, где шаблон с свойством ItemContainerStyle используется для привязки значений к переменным.  
  
```xaml  
  
      <ListBox Name="listBox1" ItemsSource="{Binding Source={StaticResource employees}}">  
            <ListBox.ItemContainerStyle>  
                <Style TargetType="ListBoxItem">  
                    <Setter Property="Template">  
                        <Setter.Value>  
                            <ControlTemplate TargetType="ListBoxItem">  
                                <Grid>  
                                    <Button Content="{Binding EmployeeName}" AutomationProperties.AutomationId="{Binding EmployeeID}"/>  
                                </Grid>  
                            </ControlTemplate>  
                        </Setter.Value>  
                    </Setter>  
                </Style>  
            </ListBox.ItemContainerStyle>           
        </ListBox>  
  
```  
  
 В обоих примерах необходимо переопределить метод ToString\(\) элемента ItemSource, как показано в следующем примере кода.  Этот код проверяет, задано и уникально ли значение свойства AutomationProperties.Name, поскольку с помощью привязки нельзя задать уникальное свойство автоматизации для каждого элемента списка с привязкой к данным.  В этом случае достаточно задать уникальное значение для свойства AutomationProperties.Name.  
  
> [!NOTE]
>  Кроме того, при таком подходе с помощью привязки можно присвоить внутреннему содержимому элемента списка значение строки из класса Employee.  Как показано в примере, элементу управления "Кнопка" внутри каждого элемента списка присваивается уникальный идентификатор автоматизации, соответствующий идентификатору Employee.  
  
```  
  
Employee[] employees = new Employee[]   
{  
   new Employee("john", "4384"),  
   new Employee("margaret", "7556"),  
   new Employee("richard", "8688"),  
   new Employee("george", "1293")  
};  
  
listBox1.ItemsSource = employees;  
  
public override string ToString()  
{  
    return EmployeeName + EmployeeID; // Unique Identification to be set as the AutomationProperties.Name  
}  
  
```  
  
###  <a name="UniquePropertyWindowsStoreControlsControlTemplate"></a> Использование шаблона элемента управления  
 Шаблон элемента управления позволяет присваивать уникальное свойство автоматизации каждому экземпляру определенного типа, когда он определяется в коде.  Необходимо создать шаблон так, чтобы свойство AutomationProperty привязывалось к уникальному идентификатору в экземпляре элемента управления.  Следующий код XAML демонстрирует один из способов создания привязки с помощью шаблона элемента управления.  
  
```xaml  
  
<Style x:Key="MyButton" TargetType="Button">  
<Setter Property="Template">  
   <Setter.Value>  
<ControlTemplate TargetType="Button">  
   <Grid>  
      <CheckBox HorizontalAlignment="Left" AutomationProperties.AutomationId="{TemplateBinding Content}"></CheckBox>  
      <Button Width="90" HorizontalAlignment="Right" Content="{TemplateBinding Content}" AutomationProperties.AutomationId="{TemplateBinding Content}"></Button>  
   </Grid>  
</ControlTemplate>  
   </Setter.Value>  
</Setter>  
</Style>  
  
```  
  
 Если с помощью шаблона элемента управления определяются два экземпляра кнопки, идентификатору автоматизации присваивается уникальная строка содержимого элементов управления в шаблоне, как это показано в следующем коде XAML.  
  
```xaml  
  
<Button Content=”Button1” Style="{StaticResource MyButton}" Width="140"/>  
<Button Content=”Button2” Style="{StaticResource MyButton}" Width="140"/>  
```  
  
###  <a name="UniquePropertyWindowsStoreControlsDynamicControls"></a> Динамические элементы управления  
 Если элементы управления не были созданы статически или с помощью шаблонов в XAML\-файлах, а создаются динамически из кода, для них необходимо задать свойство Content или Name.  Тогда каждый динамический элемент управления будет иметь уникальное свойство автоматизации.  Например, если есть флажок, который должен отображаться при выборе элемента списка, эти свойства можно задать так, как показано ниже:  
  
```c#  
  
private void CreateCheckBox(string txt, StackPanel panel)  
   {  
      CheckBox cb = new CheckBox();  
      cb.Content = txt; // Sets the AutomationProperties.Name  
      cb.Height = 50;  
      cb.Width = 100;  
      cb.Name = "DynamicCheckBoxAid"+ txt; // Sets the AutomationProperties.AutomationId  
      panel.Children.Add(cb);  
    }  
  
```  
  
## См. также  
 [Тестирование приложений Магазина Windows 8.1 с помощью закодированных тестов пользовательского интерфейса](../test/test-windows-store-8-1-apps-with-coded-ui-tests.md)