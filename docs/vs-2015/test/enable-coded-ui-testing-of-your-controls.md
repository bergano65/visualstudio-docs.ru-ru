---
title: Включение закодированных тестов пользовательского интерфейса для элементов управления | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 5ef1188f-89dc-413d-801d-0efdaf9b0427
caps.latest.revision: 24
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9d6162f26bbfcf3f3bce8f2a3db649fbf1b63a52
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63416522"
---
# <a name="enable-coded-ui-testing-of-your-controls"></a>Включение закодированных тестов пользовательского интерфейса для элементов управления
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Элемент управления проще тестировать при реализации поддержки среды обработки закодированных тестов пользовательского интерфейса. Вы можете последовательно добавлять повышение уровней поддержки. Начать можно с поддержки проверки записи, воспроизведения и свойств. Это можно использовать, чтобы разрешить построителю закодированных тестов пользовательского интерфейса распознавать пользовательские свойства элемента управления, а также давать пользовательским классам возможность получить доступ к этим свойствам из созданного кода. Вы также можете помочь построителю закодированных тестов пользовательского интерфейса захватывать действия способом, который в большей степени соответствует цели записываемого действия.  
  
 **Содержание раздела**  
  
1. [Поддержка записи, воспроизведения и проверки свойства путем реализации специальных возможностей](../test/enable-coded-ui-testing-of-your-controls.md#recordandplayback)  
  
2. [Поддержка проверки пользовательского свойства путем реализации поставщика свойства](../test/enable-coded-ui-testing-of-your-controls.md#customproprties)  
  
3. [Поддержка создания кода путем реализации класса для доступа к пользовательским свойствам](../test/enable-coded-ui-testing-of-your-controls.md#codegeneration)  
  
4. [Поддержка действий, учитывающих намерение, путем реализации фильтра действий](../test/enable-coded-ui-testing-of-your-controls.md#intentawareactions)  
  
   ![CUIT&#95;Full](../test/media/cuit-full.png "CUIT_Full")  
  
## <a name="recordandplayback"></a> Поддержка записи, воспроизведения и проверки свойства путем реализации специальных возможностей  
 Построитель закодированных тестов пользовательского интерфейса собирает сведения об элементах управления, которые он обнаруживает во время записи, а затем создает код для повторения этого сеанса. Если элемент управления не поддерживает специальные возможности, построитель закодированных тестов пользовательского интерфейса захватывает действия (например, щелчки мышью) с помощью координат экрана. Созданный код выводит эти щелчки мышью в тех же экранных координатах при воспроизведении теста. Если во время воспроизведения теста элемент управления отображается в другом месте на экране, созданный код не сможет выполнить это действие на элементе управления. Это может привести к сбоям, если тест воспроизводится при различных конфигурациях экрана, в разных средах или после внесения изменений в макет пользовательского интерфейса.  
  
 ![CUIT&#95;RecordNoSupport](../test/media/cuit-recordnosupport.png "CUIT_RecordNoSupport")  
  
 Однако при реализации специальных возможностей построитель закодированных тестов пользовательского интерфейса будет использовать их для того, чтобы получить сведения об элементе управления во время записи теста и создания кода. Затем, при выполнении теста, созданный код повторит эти события для элемента управления, даже если он находится где-либо еще в интерфейсе пользователя. Авторы теста могут также создавать утверждения благодаря использованию основных свойств элемента управления.  
  
 ![CUIT&#95;Record](../test/media/cuit-record.png "CUIT_Record")  
  
### <a name="to-support-record-and-playback-property-validation-and-navigation-for-a-windows-forms-control"></a>Поддержка записи, воспроизведения, проверки свойств и навигации для элемента управления Windows Forms  
 Реализуйте специальные возможности для элемента управления согласно описанной ниже процедуре. Подробные пояснения см. в разделе <xref:System.Windows.Forms.AccessibleObject>.  
  
 ![CUIT&#95;Accessible](../test/media/cuit-accessible.png "CUIT_Accessible")  
  
1. Реализуйте производный от <xref:System.Windows.Forms.Control.ControlAccessibleObject> класс и переопределите свойство <xref:System.Windows.Forms.Control.AccessibilityObject%2A> для возврата объекта класса.  
  
    ```csharp  
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
  
2. Переопределите свойства, методы и <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.GetChild%2A><xref:System.Windows.Forms.AccessibleObject.GetChildCount%2A> объекта специальных возможностей.  
  
3. Реализуйте другой объект специальных возможностей для дочернего элемента управления и переопределите свойство дочернего элемента управления <xref:System.Windows.Forms.Control.AccessibilityObject%2A> для получения этого объекта специальных возможностей.  
  
4. Переопределите свойства, методы и <xref:System.Windows.Forms.AccessibleObject.Bounds%2A>, <xref:System.Windows.Forms.AccessibleObject.Name%2A>, <xref:System.Windows.Forms.AccessibleObject.Parent%2A>, <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.Navigate%2A>, <xref:System.Windows.Forms.AccessibleObject.Select%2A> объекта специальных возможностей дочернего элемента управления.  
  
> [!NOTE]
> Этот раздел начинается с примера специальных возможностей в <xref:System.Windows.Forms.AccessibleObject> в этой процедуре, а затем берется в основу остальных процедур. Если вам требуется создать рабочую версию образца специальных возможностей, создайте консольное приложение, а затем замените код в файле Program.cs на пример кода. Необходимо добавить ссылки на Accessibility, System.Drawing и System.Windows.Forms. Вы должны изменить значение **Внедрить типы взаимодействия** для объекта специальных возможностей на **False**, чтобы исключить предупреждение сборки. Можно изменить тип выходных данных проекта с **консольного приложения** на **приложение Windows**, чтобы окно консоли не отображалось при запуске приложения.  
  
## <a name="customproprties"></a> Поддержка проверки пользовательского свойства путем реализации поставщика свойства  
 После реализации базовой поддержки проверки записи, воспроизведения и свойств вы можете сделать пользовательские свойства элемента управления доступными закодированным тестам пользовательского интерфейса путем реализации подключаемого модуля <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>. Например, в следующей процедуре создается поставщик свойства, позволяющий закодированным тестам пользовательского интерфейса получать доступ к свойству состояния дочерних элементов управления CurveLegend элемента управления диаграммы.  
  
 ![CUIT&#95;CustomProps](../test/media/cuit-customprops.png "CUIT_CustomProps")  
  
### <a name="to-support-custom-property-validation"></a>Поддержка проверки пользовательского свойства  
 ![CUIT&#95;Props](../test/media/cuit-props.png "CUIT_Props")  
  
1. Переопределите свойство <xref:System.Windows.Forms.AccessibleObject.Description%2A> объекта специальных возможностей легенды кривой, чтобы передать форматируемые значения свойств в строку описания, отделенную точкой с запятой (;) от основного описания (или друг от друга, если реализуются несколько свойств).  
  
    ```csharp  
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
  
2. Создайте пакет расширений тестов пользовательского интерфейса для пользовательского элемента управления, создав проект библиотеки классов, и добавьте ссылки на Accessibility, Microsoft.VisualStudio.TestTools.UITesting, Microsoft.VisualStudio.TestTools.UITest.Common и Microsoft.VisualStudio.TestTools.Extension. Измените значение **Внедрить типы взаимодействия** для объекта специальных возможностей на **False**.  
  
3. Добавьте класс поставщика свойства, который является производным от <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>.  
  
    ```csharp  
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
  
4. Реализуйте поставщик свойства, установив имена свойств и дескрипторы свойств в <xref:System.Collections.Generic.Dictionary%602>.  
  
    ```csharp  
    // Define a map of property descriptors for CurveLegend  
    private static Dictionary<string, UITestPropertyDescriptor> curveLegendPropertiesMap = null;  
    private static Dictionary<string, UITestPropertyDescriptor> CurveLegendPropertiesMap  
    {  
        get  
        {  
            if (curveLegendPropertiesMap == null)  
            {  
                UITestPropertyAttributes read =  
                    UITestPropertyAttributes.Readable |  
                    UITestPropertyAttributes.DoNotGenerateProperties;  
                curveLegendPropertiesMap =  
                    new Dictionary<string, UITestPropertyDescriptor>  
                        (StringComparer.OrdinalIgnoreCase);  
                curveLegendPropertiesMap.Add("State",  
                    new UITestPropertyDescriptor(typeof(string), read));  
            }  
            return curveLegendPropertiesMap;  
        }  
    }  
  
    // return the property descriptor  
    public override UITestPropertyDescriptor GetPropertyDescriptor(UITestControl uiTestControl, string propertyName)  
    {  
        return CurveLegendPropertiesMap[propertyName];  
    }  
  
    // return the property names  
    public override ICollection<string> GetPropertyNames(UITestControl uiTestControl)  
    {  
        if (uiTestControl.ControlType.NameEquals("Chart") || uiTestControl.ControlType.NameEquals("Text"))  
        {  
            // the keys of the property map are the collection of property names  
            return CurveLegendPropertiesMap.Keys;  
        }  
  
        // this is not my control  
        throw new NotSupportedException();  
    }  
  
    // Get the property value by parsing the accessible description  
    public override object GetPropertyValue(UITestControl uiTestControl, string propertyName)  
    {  
        if (String.Equals(propertyName, "State", StringComparison.OrdinalIgnoreCase))  
        {  
            object[] native = uiTestControl.NativeElement as object[];  
            IAccessible acc = native[0] as IAccessible;  
  
            string[] descriptionTokens = acc.accDescription.Split(new char[] { ';' });  
            return descriptionTokens[1];  
        }  
  
        // this is not my control  
        throw new NotSupportedException();  
    }  
    ```  
  
5. Переопределите <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A?displayProperty=fullName>, чтобы указать, что сборка обеспечивает поддержку отдельного элемента управления для элемента управления и его дочерних элементов.  
  
    ```csharp  
    public override int GetControlSupportLevel(UITestControl uiTestControl)  
    {  
        // For MSAA, check the control type  
        if (string.Equals(uiTestControl.TechnologyName, "MSAA",  
            StringComparison.OrdinalIgnoreCase) &&  
            (uiTestControl.ControlType == "Chart"||uiTestControl.ControlType == "Text"))  
        {  
            return (int)ControlSupport.ControlSpecificSupport;  
        }  
  
        // This is not my control, so return NoSupport  
        return (int)ControlSupport.NoSupport;  
    }  
    ```  
  
6. Переопределите оставшиеся абстрактные методы <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider?displayProperty=fullName>.  
  
    ```csharp  
    public override string[] GetPredefinedSearchProperties(Type specializedClass)  
    {  
        throw new NotImplementedException();  
    }  
  
    public override Type GetSpecializedClass(UITestControl uiTestControl)  
    {  
        throw new NotImplementedException();  
    }  
  
    public override Type GetPropertyNamesClassType(UITestControl uiTestControl)  
    {  
        throw new NotImplementedException();  
    }  
  
    public override void SetPropertyValue(UITestControl uiTestControl, string propertyName, object value)  
    {  
        throw new NotImplementedException();  
    }  
  
    public override string GetPropertyForAction(UITestControl uiTestControl, UITestAction action)  
    {  
        throw new NotImplementedException();  
    }  
  
    public override string[] GetPropertyForControlState(UITestControl uiTestControl, ControlStates uiState, out bool[] stateValues)  
    {  
        throw new NotImplementedException();  
    }  
  
    ```  
  
7. Добавьте класс пакета расширений, который является производным от <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.  
  
    ```csharp  
    using System;  
    using Microsoft.VisualStudio.TestTools.UITesting;  
    using Microsoft.VisualStudio.TestTools.UITest.Extension;  
    using Microsoft.VisualStudio.TestTools.UITest.Common;  
  
    namespace ChartControlExtensionPackage  
    {  
        internal class ChartControlExtensionPackage : UITestExtensionPackage  
        {  
        }  
    }  
    ```  
  
8. Задайте атрибут `UITestExtensionPackage` для сборки.  
  
    ```csharp  
    [assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(  
                    "ChartControlExtensionPackage",  
                    typeof(ChartControlExtensionPackage.ChartControlExtensionPackage))]  
    namespace ChartControlExtensionPackage  
    {  
       …  
    ```  
  
9. В классе пакета расширений переопределите <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A?displayProperty=fullName>, чтобы возвратить класс поставщика свойства, когда будет запрошен поставщик свойства.  
  
    ```csharp  
    internal class ChartControlExtensionPackage : UITestExtensionPackage  
    {  
        public override object GetService(Type serviceType)  
        {  
            if (serviceType == typeof(UITestPropertyProvider))  
            {  
                if (propertyProvider == null)  
                {  
                    propertyProvider = new ChartControlPropertyProvider();  
                }  
                return propertyProvider;  
            }  
            return null;  
        }  
  
        private UITestPropertyProvider propertyProvider = null;  
    }  
    ```  
  
10. Переопределите оставшиеся абстрактные методы и свойства <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.  
  
    ```csharp  
  
    public override void Dispose() { }  
  
    public override string PackageDescription  
    {  
        get { return "Supports coded UI testing of ChartControl"; }  
    }  
  
    public override string PackageName  
    {  
        get { return "ChartControl Test Extension"; }  
    }  
  
    public override string PackageVendor  
    {  
        get { return "Microsoft (sample)"; }  
    }  
  
    public override Version PackageVersion  
    {  
        get { return new Version(1, 0); }  
    }  
  
    public override Version VSVersion  
    {  
        get { return new Version(10, 0); }  
    }  
    ```  
  
11. Выполните сборку двоичных файлов и скопируйте их в каталог **%ProgramFiles%\Common\Microsoft Shared\VSTT\10.0\UITestExtensionPackages**.  
  
> [!NOTE]
> Этот пакет расширений будет применяться к любому элементу управления типа "Текст". Если вы тестируете несколько элементов управления одного типа, то необходимо тестировать их поодиночке, указывая во время записи тестов, какие пакеты расширений развертывать.  
  
## <a name="codegeneration"></a> Поддержка создания кода путем реализации класса для доступа к пользовательским свойствам  
 Когда построитель закодированных тестов пользовательского интерфейса создает код из записи сеанса, он использует класс <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> для получения доступа к элементам управления.  
  
```csharp  
  
      UITestControl uIAText = this.UIItemWindow.UIChartControlWindow.UIAText;  
Assert.AreEqual(this.AssertMethod3ExpectedValues.UIATextState, uIAText.GetProperty("State").ToString());  
```  
  
 При реализации поставщика свойства для предоставления доступа к пользовательским свойствам элемента управления можно добавить специализированный класс, используемый для доступа к этим свойствам, что упростит создаваемый код.  
  
```csharp  
  
      ControlLegend uIAText = this.UIItemWindow.UIChartControlWindow.UIAText;  
Assert.AreEqual(this.AssertMethod3ExpectedValues.UIATextState, uIAText.State);  
```  
  
### <a name="to-add-a-specialized-class-to-access-your-control"></a>Добавление специализированного класса для доступа к элементу управления  
 ![CUIT&#95;CodeGen](../test/media/cuit-codegen.png "CUIT_CodeGen")  
  
1. Реализуйте класс, производный от <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinControl>, и добавьте тип элемента управления к коллекции свойств поиска в конструкторе.  
  
    ```csharp  
    public class CurveLegend:WinControl   
    {  
       public CurveLegend(UITestControl c) : base(c)   
       {  
          // The curve legend control is a “text” type of control  
          SearchProperties.Add(  
             UITestControl.PropertyNames.ControlType, "Text");  
       }  
    }  
    ```  
  
2. Реализуйте пользовательские свойства элемента управления как свойства класса.  
  
    ```csharp  
    public virtual string State  
    {  
        get  
        {  
            return (string)GetProperty("State");  
        }  
    }  
    ```  
  
3. Переопределите метод <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetSpecializedClass%2A?displayProperty=fullName> поставщика свойства для возврата типа нового класса для дочерних элементов управления легенды кривой.  
  
    ```csharp  
    public override Type GetSpecializedClass(UITestControl uiTestControl)   
    {   
       if (uiTestControl.ControlType.NameEquals("Text"))   
       {   
          // This is text type of control. For my control,  
          // that means it’s a curve legend control.  
          return typeof(CurveLegend);   
       }   
  
       // this is not a curve legend control  
       return null;  
    }  
    ```  
  
4. Переопределите метод <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetPropertyNamesClassType%2A> поставщика свойства, чтобы возвратить тип метода PropertyNames новых классов.  
  
    ```csharp  
    public override Type GetPropertyNamesClassType(UITestControl uiTestControl)  
    {  
        if (uiTestControl.ControlType.NameEquals("Text"))  
        {  
          // This is text type of control. For my control,  
          // that means it’s a curve legend control.  
            return typeof(CurveLegend.PropertyNames);  
        }  
  
        // this is not a curve legend control  
        return null;  
    }  
    ```  
  
## <a name="intentawareactions"></a> Поддержка действий, учитывающих намерение, путем реализации фильтра действий  
 В то время, как Visual Studio записывает тест, записываются все события мыши и клавиатуры. Однако в некоторых случаях цель действия может быть потеряна в ряде событий мыши и клавиатуры. Например, если элемент управления поддерживает автозаполнение, то один и тот же набор событий мыши и клавиатуры может возникать в разных значениях во время воспроизведения теста в другой среде. Вы можете добавить подключаемый модуль фильтра действий, который заменяет ряд событий клавиатуры и мыши на одно действие. Таким образом, можно заменить ряд событий мыши и клавиатуры для выделения значения на одно действие, которое задает значение. Это защитит закодированные тесты пользовательского интерфейса от различий в автозаполнении в различных средах.  
  
### <a name="to-support-intent-aware-actions"></a>Поддержка действий, учитывающих намерение  
 ![CUIT&#95;Actions](../test/media/cuit-actions.png "CUIT_Actions")  
  
1. Реализуйте класс фильтра действий, который является производным от <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>, переопределив свойства <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> и <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A>.  
  
    ```csharp  
    internal class MyActionFilter : UITestActionFilter  
    {  
       // If the user actions we are aggregating exceeds the time allowed,  
       // this filter is not applied. (The timeout is configured when the  
       // test is run.)  
       public override bool ApplyTimeout  
       {  
          get { return true; }  
       }  
  
       // Gets the category of this filter. Categories of filters  
       // are applied in priority order.  
       public override UITestActionFilterCategory Category  
       {  
          get { return UITestActionFilterCategory.PostSimpleToCompoundActionConversion; }  
       }  
  
       public override bool Enabled  
       {  
          get { return true; }  
       }  
  
       public override UITestActionFilterType FilterType  
       {  
          // This action filter operates on a single action  
          get { return UITestActionFilterType.Unary; }  
       }  
  
       // Gets the name of the group to which this filter belongs.  
       // A group can be enabled/disabled using configuration file.  
       public override string Group  
       {  
          get { return "ChartControlActionFilters"; }  
       }  
  
       // Gets the name of this filter.  
       public override string Name  
       {  
          get { return "Convert Double-Click to Single-Click"; }  
       }  
    ```  
  
2. Переопределите метод <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ProcessRule%2A>. Ниже приведен пример замены действия двойного щелчка на действие одним щелчком.  
  
    ```csharp  
    public override bool ProcessRule(IUITestActionStack actionStack)  
    {  
        if (actionStack.Count > 0)  
        {  
            MouseAction lastAction = actionStack.Peek() as MouseAction;  
            if (lastAction != null)  
            {  
                if (lastAction.UIElement.ControlTypeName.Equals(  
                     ControlType.Text.ToString(),  
                     StringComparison.OrdinalIgnoreCase))  
                {  
                    if(lastAction.ActionType == MouseActionType.DoubleClick)  
                    {  
                        // Convert to single click  
                        lastAction.ActionType = MouseActionType.Click;  
                    }  
                }  
            }  
        }  
        // Do not stop aggregation  
        return false;  
    }  
    ```  
  
3. Добавьте фильтр действий в метод <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> данного пакета расширений.  
  
    ```csharp  
    public override object GetService(Type serviceType)   
    {   
       if (serviceType == typeof(UITestPropertyProvider))   
       {   
          if (propertyProvider == null)  
          {  
             propertyProvider = new PropertyProvider();  
          }   
          return propertyProvider;  
       }   
       else if (serviceType == typeof(UITestActionFilter))   
       {   
          if (actionFilter == null)  
          {  
             actionFilter = new RadGridViewActionFilter();  
          }  
          return actionFilter;   
       }   
       return null;  
    }  
    ```  
  
4. Выполните сборку двоичных файлов и скопируйте их в каталог %ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages.  
  
> [!NOTE]
> Фильтр действий не зависит от реализации специальных возможностей или от поставщика свойств.  
  
## <a name="debug-your-property-provider-or-action-filter"></a>Отладка поставщика свойств или фильтра действий  
 Поставщик свойств и фильтр действий реализованы в пакете расширений, который загружается и выполняется построителем закодированных тестов пользовательского интерфейса в процессе, независимым от приложения.  
  
#### <a name="to-debug-your-property-provider-or-action-filter"></a>Отладка поставщика свойств или фильтра действий  
  
1. Выполните сборку отладочной версии пакета расширений и скопируйте DLL-файлы и PDB-файлы в каталог %ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages.  
  
2. Запустите приложение (не в отладчике).  
  
3. Запустите построитель закодированного теста пользовательского интерфейса.  
  
     `codedUITestBuilder.exe  /standalone`  
  
4. Присоедините отладчик к процессу codedUITestBuilder.  
  
5. Задайте точки останова в коде.  
  
6. В построителе закодированных тестов пользовательского интерфейса создайте утверждения для работы поставщика свойств и запишите действия для использования фильтров действий.  
  
## <a name="external-resources"></a>Внешние ресурсы  
  
### <a name="guidance"></a>Руководство  
 [Тестирование непрерывной доставки с Visual Studio 2012 — Глава 2: Модульное тестирование: Внутреннее тестирование](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
## <a name="see-also"></a>См. также  
 <xref:System.Windows.Forms.AccessibleObject>   
 [Использование модели автоматизации пользовательского интерфейса для тестирования кода](../test/use-ui-automation-to-test-your-code.md)
