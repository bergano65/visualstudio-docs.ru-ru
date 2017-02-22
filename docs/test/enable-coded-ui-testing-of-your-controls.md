---
title: "Включение закодированных тестов пользовательского интерфейса для элементов управления | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5ef1188f-89dc-413d-801d-0efdaf9b0427
caps.latest.revision: 22
caps.handback.revision: 22
ms.author: "mlearned"
manager: "douge"
---
# Включение закодированных тестов пользовательского интерфейса для элементов управления
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Элемент управления проще тестировать при реализации поддержки закодированных тестов пользовательского интерфейса.  Можно последовательно добавлять повышение уровней поддержки.  Можно начать с поддержки проверки записи и воспроизведения и свойства.  Это можно использовать, чтобы разрешить закодированным тестам пользовательского интерфейса распознавать пользовательские свойства элемента управления, а также давать пользовательским классом возможность получить доступ к этим свойствам из сгенерированного кода.  Также можно помочь построителю закодированных тестов пользовательского интерфейса захватывать действия тем способом, что ближе к цели записываемого действия.  
  
 **Содержание раздела**  
  
1.  [Поддержка записи, воспроизведения и проверки свойства путем реализации специальных возможностей](../test/enable-coded-ui-testing-of-your-controls.md#recordandplayback)  
  
2.  [Поддержка проверки пользовательского свойства путем реализации поставщика свойства](../test/enable-coded-ui-testing-of-your-controls.md#customproprties)  
  
3.  [Поддержка создания кода путем реализации класса для доступа к пользовательским свойствам](../test/enable-coded-ui-testing-of-your-controls.md#codegeneration)  
  
4.  [Поддержка действий, учитывающих намерение, путем реализации фильтра действий](../test/enable-coded-ui-testing-of-your-controls.md#intentawareactions)  
  
 ![CUIT&#95;Full](../test/media/cuit_full.png "CUIT\_Full")  
  
##  <a name="recordandplayback"></a> Поддержка записи, воспроизведения и проверки свойства путем реализации специальных возможностей  
 Построитель закодированных тестов пользовательского интерфейса собирает сведения об элементах управления, которые он обнаруживает во время записи и затем генерирует код для переигровки этого сеанса.  Если элемент управления не поддерживает специальных возможностей, построитель закодированных тестов пользовательского интерфейса захватывает действия \(например, щелчки мышью\) с помощью координат экрана.  Если тест будет воспроизведён, созданный код выводит эти щелчки мышью в тех же экранных координатах.  Если во время воспроизведения теста элемент управления отображается в другом месте на экране, созданный код не сможет выполнить это действие на элементе управления.  Это может привести к сбоям, если тест воспроизводится в различных конфигурациях экрана, в разных средах, или после внесения изменений в макет пользовательского интерфейса.  
  
 ![CUIT&#95;RecordNoSupport](../test/media/cuit_recordnosupport.png "CUIT\_RecordNoSupport")  
  
 Однако при реализации специальных возможностей построитель закодированных тестов пользовательского интерфейса будет использовать это, чтобы получить сведения об элементе управления, когда он записывает тест и создает код.  Затем, при выполнении теста, созданный код переиграет эти события для элемента управления, даже если он где\-либо еще в интерфейсе пользователя.  Авторы теста смогут также создать утверждения с помощью основных свойств элемента управления.  
  
 ![CUIT&#95;Record](../test/media/cuit_record.png "CUIT\_Record")  
  
### Поддержка записи, воспроизведения, проверки свойств и навигации для элемента управления Windows Forms  
 Реализуйте специальные возможности для элемента управления, как описано в следующей процедуре и подробно пояснено в разделе <xref:System.Windows.Forms.AccessibleObject>.  
  
 ![CUIT&#95;Accessible](../test/media/cuit_accessible.png "CUIT\_Accessible")  
  
1.  Реализуйте класс, производный от <xref:System.Windows.Forms.Control.ControlAccessibleObject>, и переопределите свойство <xref:System.Windows.Forms.Control.AccessibilityObject%2A> для возврата объекта класса.  
  
    ```c#  
    public partial class ChartControl : UserControl  
    {  
        // Overridden to return the custom AccessibleObject for the control.  
        protected override AccessibleObject CreateAccessibilityInstance()  
        {  
            return new ChartControlAccessibleObject(this);  
        }  
  
        // Inner class ChartControlAccessibleObject represents accessible information  
        // associated with the ChartControl and is used when recording tests.  
        public class ChartControlAccessibleObject : ControlAccessibleObject  
        {  
            ChartControl myControl;  
            public ChartControlAccessibleObject(ChartControl ctrl)  
                : base(ctrl)  
            {  
                myControl = ctrl;  
            }  
        }  
    }  
    ```  
  
2.  Переопределите свойства и методы <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.GetChild%2A> <xref:System.Windows.Forms.AccessibleObject.GetChildCount%2A> объекта специальных возможностей.  
  
3.  Реализуйте другой объект специальных возможностей для дочернего элемента управления и переопределите свойство <xref:System.Windows.Forms.Control.AccessibilityObject%2A> дочернего элемента управления для получения этого объекта специальных возможностей.  
  
4.  Переопределите свойства и методы <xref:System.Windows.Forms.AccessibleObject.Bounds%2A>, <xref:System.Windows.Forms.AccessibleObject.Name%2A>, <xref:System.Windows.Forms.AccessibleObject.Parent%2A>, <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.Navigate%2A>, <xref:System.Windows.Forms.AccessibleObject.Select%2A> объекта специальных возможностей дочернего элемента управления.  
  
> [!NOTE]
>  Этот раздел начинается примером специальных возможностей в <xref:System.Windows.Forms.AccessibleObject> в этой процедуре, и затем основывает на нем остальные процедуры.  Если требуется создать рабочую версию образца специальных возможностей, создайте консольное приложение, а затем замените код в файле Program.cs на пример кода.  Необходимо добавить ссылки на Accessibility, System.Drawing и System.Windows.Forms.  Необходимо изменить **Внедрить типы взаимодействия** для Accessibility в значение False, чтобы исключить предупреждение построения.  Можно изменить тип выходных данных проекта из Консольного приложения в Windows\-приложение, чтобы окно консоли не отображалось при запуске приложения.  
  
##  <a name="customproprties"></a> Поддержка проверки пользовательского свойства путем реализации поставщика свойства  
 После реализации базовой поддержки проверки записи и воспроизведения и свойства можно сделать пользовательские свойства элемента управления доступными закодированным тестам пользовательского интерфейса путем реализации подключаемого модуля <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>.  Например, в следующей процедуре создается поставщик свойства, позволяющий закодированным тестам пользовательского интерфейса получать доступ к свойству Состояния дочерних элементов управления CurveLegend элементом управления "Диаграмма".  
  
 ![CUIT&#95;CustomProps](../test/media/cuit_customprops.png "CUIT\_CustomProps")  
  
### Поддержка проверки пользовательского свойства  
 ![CUIT&#95;Props](../test/media/cuit_props.png "CUIT\_Props")  
  
1.  Переопределите свойство <xref:System.Windows.Forms.AccessibleObject.Description%2A> объекта специальных возможностей легенды кривой, чтобы передать форматируемое значение свойства в описание строки, отделенной точкой с запятой \(;\) от основного описания \(или друг от друга, если реализуются несколько свойств\).  
  
    ```c#  
    public class CurveLegendAccessibleObject : AccessibleObject  
    {  
        // add the state property value to the description  
        public override string Description  
        {  
            get  
            {  
                // Add “;” and the state value to the end  
                // of the curve legend’s description  
                return "CurveLegend; " + State.ToString();  
            }  
        }  
    }  
    ```  
  
2.  Создайте пакета расширения тестов пользовательского интерфейса для пользовательского элемента управления, создав проект библиотеки классов, и добавьте ссылки на Accessibility, Microsoft.VisualStudio.TestTools.UITesting, Microsoft.VisualStudio.TestTools.UITest.Common и Microsoft.VisualStudio.TestTools.Extension.  Измените **Внедрить типы взаимодействия** для Accessibility в значение False.  
  
3.  Добавьте класс поставщика свойства, который является производным от <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>.  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using Accessibility;  
    using Microsoft.VisualStudio.TestTools.UITesting;  
    using Microsoft.VisualStudio.TestTools.UITest.Extension;  
    using Microsoft.VisualStudio.TestTools.UITesting.WinControls;  
    using Microsoft.VisualStudio.TestTools.UITest.Common;  
  
    namespace ChartControlExtensionPackage  
    {  
        public class ChartControlPropertyProvider : UITestPropertyProvider  
        {  
        }  
    }  
    ```  
  
4.  Реализуйте поставщик свойства, установив имена свойств и дескрипторы свойств в <xref:System.Collections.Generic.Dictionary%602>.  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
5.  Переопределите <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A?displayProperty=fullName>, чтобы указать, что сборка обеспечивает поддержку отдельного элемента управления для элемента управления и его дочерних элементов.  
  
<CodeContentPlaceHolder>4</CodeContentPlaceHolder>  
6.  Переопределите оставшиеся абстрактные методы <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider?displayProperty=fullName>.  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
7.  Добавьте класс пакета расширения, который является производным от <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
8.  Задайте атрибут `UITestExtensionPackage` для сборки.  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
9. В классе пакета расширения переопределение <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A?displayProperty=fullName>, чтобы возвратить класс поставщика свойства, когда будет запрошен поставщик свойства.  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
10. Переопределите оставшиеся абстрактные методы и свойства <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
11. Выполните построение двоичных файлов и скопируйте их в **%ProgramFiles%\\Common\\Microsoft Shared\\VSTT\\10.0\\UITestExtensionPackages**.  
  
> [!NOTE]
>  Этот пакет расширения будет применяться к любому элементу управления типа «Текст».  При тестировании нескольких элементов управления одного типа необходимо тестировать их поодиночке и во время записи тестов указывать, какие пакеты расширения развертывать.  
  
##  <a name="codegeneration"></a> Поддержка создания кода путем реализации класса для доступа к пользовательским свойствам  
 Когда построитель закодированных тестов пользовательского интерфейса создает код из записи сеанса, он использует класс <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> для получения доступа к элементам управления.  
  
<CodeContentPlaceHolder>10</CodeContentPlaceHolder>  
 При реализации поставщика свойства для предоставления доступа к пользовательским свойствам элемента управления можно добавить специализированный класс, используемый для доступа к этим свойствам, что упростит создаваемый код.  
  
<CodeContentPlaceHolder>11</CodeContentPlaceHolder>  
### Добавление специализированного класса для доступа к элементу управления  
 ![CUIT&#95;CodeGen](../test/media/cuit_codegen.png "CUIT\_CodeGen")  
  
1.  Реализуйте класс, производный от <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinControl>, и добавьте тип элемента управления к коллекции свойств поиска в конструкторе.  
  
<CodeContentPlaceHolder>12</CodeContentPlaceHolder>  
2.  Реализуйте пользовательские свойства элемента управления как свойства класса.  
  
<CodeContentPlaceHolder>13</CodeContentPlaceHolder>  
3.  Переопределите метод <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetSpecializedClass%2A?displayProperty=fullName> поставщика свойства для возврата типа нового класса для дочерних элементов управления легенды кривой.  
  
<CodeContentPlaceHolder>14</CodeContentPlaceHolder>  
4.  Переопределите метод <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetPropertyNamesClassType%2A> поставщика свойства, чтобы возвратить тип метода PropertyNames новых классов.  
  
<CodeContentPlaceHolder>15</CodeContentPlaceHolder>  
##  <a name="intentawareactions"></a> Поддержка действий, учитывающих намерение, путем реализации фильтра действий  
 В то время, как Visual Studio записывает тест, записываются все события мыши и клавиатуры.  Однако в некоторых случаях цель действия можно потерять в серии событий мыши и клавиатуры.  Например, если элемент управления поддерживает автозаполнение, то один и тот же набор событий мыши и клавиатуры может возникать в разных значениях во время воспроизведения теста в другой среде.  Можно добавить подключаемый модуль фильтра действий, который заменяет события клавиатуры и мыши на одно действие.  Таким образом, можно заменить ряд событий мыши и клавиатуры для выделения значения на одно действием, которое задает значение.  Это защитит закодированные тесты пользовательского интерфейса от различий в автозаполнении между одной и другой средами.  
  
### Поддержка действий, учитывающих намерение  
 ![CUIT&#95;Actions](../test/media/cuit_actions.png "CUIT\_Actions")  
  
1.  Реализуйте класс фильтра действий, который является производным от <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>, переопределив свойства <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> и <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A>.  
  
<CodeContentPlaceHolder>16</CodeContentPlaceHolder>  
2.  Переопределите метод <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ProcessRule%2A>.  Ниже приведен пример замены действия двойного щелчка на действие с одним щелчком.  
  
<CodeContentPlaceHolder>17</CodeContentPlaceHolder>  
3.  Добавьте фильтр действий в метод <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> данного пакета расширения.  
  
<CodeContentPlaceHolder>18</CodeContentPlaceHolder>  
4.  Выполните построение двоичных файлов и скопируйте их в %ProgramFiles%\\Common Files\\Microsoft Shared\\VSTT\\10.0\\UITestExtensionPackages.  
  
> [!NOTE]
>  Фильтр действий не зависит от реализации специальных возможностей или от поставщика свойства.  
  
## Отладка поставщика свойств или фильтра действий  
 Поставщик свойств и фильтр действий реализованы в пакете расширения, который загружается и выполняется построителем закодированных тестов пользовательского интерфейса в процессе, независимо от приложения.  
  
#### Отладка поставщика свойств или фильтра действий  
  
1.  Выполнит построение отладочной версии пакета расширения, скопируйте dll\-файлы и pdb\-файлы в %ProgramFiles%\\Common Files\\Microsoft Shared\\VSTT\\10.0\\UITestExtensionPackages.  
  
2.  Запустите приложение \(не в отладчике\).  
  
3.  Запустите построитель закодированного теста пользовательского интерфейса  
  
     `codedUITestBuilder.exe  /standalone`  
  
4.  Присоедините отладчик к процессу codedUITestBuilder.  
  
5.  Задайте точки останова в коде.  
  
6.  В построителе закодированных тестов пользовательского интерфейса создайте утверждения для работы поставщика свойства и запишите действия для использования фильтров действий.  
  
## Внешние ресурсы  
  
### Руководство  
 [Книга "Шаблоны и приемы. Тестирование при непрерывной поставке с использованием Visual Studio 2012", глава 2, "Модульное тестирование: тестирование изнутри"](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
## См. также  
 <xref:System.Windows.Forms.AccessibleObject>   
 [Использование модели автоматизации пользовательского интерфейса для тестирования кода](../test/use-ui-automation-to-test-your-code.md)