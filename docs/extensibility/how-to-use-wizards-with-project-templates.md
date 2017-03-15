---
title: "Практическое руководство. Использование мастеров для шаблонов проекта | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "интерфейс IWizard"
  - "шаблоны проектов [Visual Studio], мастера"
  - "шаблоны [Visual Studio], мастера"
  - "шаблоны Visual Studio, мастера"
  - "мастера [Visual Studio], шаблоны проектов"
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# Практическое руководство. Использование мастеров для шаблонов проекта
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio предоставляет интерфейс <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>, который позволяет запускать пользовательский код, когда пользователь создает проект из шаблона.  
  
 Настройка шаблона проекта может использоваться для:  
  
-   Отображения настраиваемых пользовательских интерфейсов, содержащих пользовательский ввод для параметризации шаблона.  
  
-   Добавления значений параметра для использования в шаблоне.  
  
-   Добавления дополнительных файлов в шаблон.  
  
-   Выполнения практически любых действий, разрешенных объектной моделью автоматизации проекта [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Методы интерфейса <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> вызываются в различные моменты времени при создании проекта, запускающиеся сразу после того, как пользователь щелкает **ОК** в диалоговом окне **Новый проект**.  Имя каждого метода интерфейса соответствует точке, откуда он вызывается.  Например, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] вызывает <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>, когда создает проект, создавая удобное место для написания пользовательского кода для сбора пользовательского ввода.  
  
 Большая часть кода, который написан для пользовательских мастеров, будет использовать объект <xref:EnvDTE.DTE>, который является основным объектом в модели автоматизации объектов [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] для настройки проекта.  Дополнительные сведения о модели автоматизации объектов содержатся в [Расширение среды Visual Studio](../Topic/Extending%20the%20Visual%20Studio%20Environment.md) и [Справочник по автоматизации и возможностям расширения среды](../Topic/Automation%20and%20Extensibility%20Reference.md).  
  
## Создание пользовательских мастеров шаблонов  
 В этом разделе показано, как создать пользовательский мастер, открывающий форму Windows Forms до создания проекта.  Форма позволяет пользователю добавить значение пользовательских параметров, которое будет затем добавлено к исходному коду во время создания проекта.  Ниже приведены основные этапы, каждый из которых подробно описан.  
  
#### Чтобы создать пользовательский мастер шаблонов  
  
1.  Создайте сборку, которая реализует интерфейс <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  
  
2.  Установите сборку в глобальный кэш сборок.  
  
3.  Создайте проект и используйте мастер **Экспорт шаблона** для создания шаблона из проекта.  
  
4.  Измените шаблон, добавляя элемент `WizardExtension` в файле .vstemplate, чтобы привязать шаблон к сборке, которая реализует <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  
  
5.  Создайте новый проект с помощью пользовательского мастера.  
  
## Реализация IWizard  
 Первым шагом в этом процессе является создание сборки, реализующей <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  Эта сборка использует метод <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> для отображения формы Windows Forms, которая позволяет пользователю добавлять значение пользовательского параметра, которое затем будет использоваться во время создания проекта.  
  
> [!NOTE]
>  В этом примере [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] используется для реализации <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>, хотя также возможно использование [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
#### Чтобы реализовать IWizard  
  
1.  Создайте новый проект библиотеки классов.  
  
2.  Создайте класс, реализующий интерфейс <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  См. код ниже для [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] примера полностью реализованного интерфейса <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  
  
 Этот пример содержит два файла кода: `IWizardImplementation` – класс, реализующий интерфейс <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>, и `UserInputForm` – форма Windows Forms для пользовательского ввода.  
  
### Класс IWizardImplementation  
 Класс `IWizardImplementation` содержит методы реализации для каждого члена <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  В этом примере только метод <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> выполняет задачу.  Все другие методы ничего не совершают или возвращают `true`.  
  
 Метод <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> принимает четыре параметра:  
  
-   Параметр <xref:System.Object>, который может быть приведен к корневому объекту <xref:EnvDTE._DTE>, чтобы позволять настраивать проект.  
  
-   Параметр <xref:System.Collections.Generic.Dictionary%602>, содержащий коллекцию всех предварительно определенных параметров в шаблоне.  Дополнительные сведения о параметрах шаблона содержатся в разделе [Параметры шаблона](../ide/template-parameters.md).  
  
-   Параметр <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind>, содержащий сведения о том, какого рода шаблон уже используется.  
  
-   Массив <xref:System.Object>, содержащий набор параметров, передающихся мастеру [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 В этом примере добавляется значение из пользовательской формы ввода для параметра <xref:System.Collections.Generic.Dictionary%602>.  Каждый экземпляр параметра `$custommessage$` в проекте будет заменен текстом, введенным пользователем.  Необходимо добавить следующие сборки в проект.  
  
1.  EnvDTE.dll  
  
2.  Microsoft.VisualStudio.TemplateWizardInterface.dll  
  
3.  System.Windows.Forms.dll  
  
> [!IMPORTANT]
>  UserInputForm, используемый в этом примере определяется в следующем разделе.  
  
```c#  
using System;  
using System.Collections.Generic;  
using Microsoft.VisualStudio.TemplateWizard;  
using System.Windows.Forms;  
using EnvDTE;  
  
namespace CustomWizard  
{  
    public class IWizardImplementation:IWizard  
    {  
        private UserInputForm inputForm;  
        private string customMessage;  
  
        // This method is called before opening any item that   
        // has the OpenInEditor attribute.  
        public void BeforeOpeningFile(ProjectItem projectItem)  
        {  
        }  
  
        public void ProjectFinishedGenerating(Project project)  
        {  
        }  
  
        // This method is only called for item templates,  
        // not for project templates.  
        public void ProjectItemFinishedGenerating(ProjectItem   
            projectItem)  
        {  
        }  
  
        // This method is called after the project is created.  
        public void RunFinished()  
        {  
        }  
  
        public void RunStarted(object automationObject,  
            Dictionary<string, string> replacementsDictionary,  
            WizardRunKind runKind, object[] customParams)  
        {  
            try  
            {  
                // Display a form to the user. The form collects   
                // input for the custom message.  
                inputForm = new UserInputForm();  
                inputForm.ShowDialog();  
  
                customMessage = inputForm.get_CustomMessage();  
  
                // Add custom parameters.  
                replacementsDictionary.Add("$custommessage$",   
                    customMessage);  
            }  
            catch (Exception ex)  
            {  
                MessageBox.Show(ex.ToString());  
            }  
        }  
  
        // This method is only called for item templates,  
        // not for project templates.  
        public bool ShouldAddProjectItem(string filePath)  
        {  
            return true;  
        }          
    }  
}  
```  
  
### Пользовательская форма ввода  
 Пользовательская форма ввода представляет собой простую форму для ввода пользовательских параметров.  Форма содержит текстовое поле с именем `textBox1` и кнопку с именем `button1`.  При нажатии кнопки текст из текстового поля сохраняется в параметре `customMessage`.  
  
##### Чтобы добавить форму Windows Forms в решение  
  
1.  Добавьте следующий код в файл, который содержит реализацию мастера.  
  
```c#  
public partial class UserInputForm : Form  
{  
    private string customMessage;  
    private TextBox textBox1;  
  
    public UserInputForm()  
    {   
        textBox1 = new TextBox();  
        this.Controls.Add(textBox1);  
    }  
  
    public string get_CustomMessage()  
    {  
        return customMessage;  
    }  
  
    private void textBox1_TextChanged(object sender, EventArgs e)  
    {  
        customMessage = textBox1.Text;  
        this.Dispose();  
    }  
}  
```  
  
## Установка сборки в глобальный кэш сборок  
 Сборка, которая реализует <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>, должна быть подписана строгим именем и установлена в глобальный кэш сборок.  
  
#### Чтобы установить сборку в глобальный кэш сборок  
  
1.  Подпишите сборку строгим именем.  Дополнительные сведения см. в разделе [Практическое руководство. Подписание сборки строгим именем](../Topic/How%20to:%20Sign%20an%20Assembly%20with%20a%20Strong%20Name.md) или [How to: Sign an Assembly \(Visual Studio\)](http://msdn.microsoft.com/ru-ru/f468a7d3-234c-4353-924d-8e0ae5896564).  
  
2.  Установите сборку со строгим именем в глобальный кэш сборок.  Для получения дополнительной информации см. [Практическое руководство. Установка сборки в глобальный кэш сборок](../Topic/How%20to:%20Install%20an%20Assembly%20into%20the%20Global%20Assembly%20Cache.md).  
  
## Создание проекта для использования в качестве шаблона  
 В этом примере проект, используемый в качестве шаблона является консольным приложением, отображающим сообщение, указанным в пользовательской форме ввода пользовательского мастера.  
  
#### Чтобы создать пример проекта  
  
1.  Создайте новое консольное приложение [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
2.  В методе `Main` приложения добавьте следующую строку кода.  
  
    ```  
    Console.WriteLine("$custommessage$");  
    ```  
  
     Параметр `$custommessage$` заменяется текстом, введенным в пользовательскую форму ввода при создании проекта на основе шаблона.  
  
3.  В меню **Файл** выберите команду **Экспорт шаблона**.  
  
4.  В мастере **Экспорт шаблона** нажмите кнопку **Шаблон проекта**, выберите нужный проект и нажмите **Далее**.  
  
5.  В мастере **Экспорт шаблона** введите описательную информацию о шаблоне, установите флажок **Автоматически импортировать шаблон в Visual Studio** и нажмите кнопку **Готово**.  
  
     Шаблон теперь отображается в диалоговом окне **Новый проект**, но не использует пользовательский мастер.  
  
 В следующем примере приведен полный файл кода, прежде чем он был экспортирован в шаблон.  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
namespace TemplateProject  
{  
    class WriteMessage  
    {  
        static void Main(string[] args)  
        {  
            Console.WriteLine("$custommessage$");  
        }  
    }  
}  
```  
  
## Изменение шаблона  
 Теперь, когда шаблон создан и отображается в диалоговом окне **Новый проект**, необходимо изменить его таким образом, чтобы он использовал сборку, созданную на предыдущем шаге.  
  
#### Чтобы добавить пользовательский мастер в шаблон  
  
1.  Найдите файл с расширением ZIP, содержащий шаблон.  
  
    1.  В меню **Сервис** выберите пункт **Параметры**.  
  
    2.  Нажмите кнопку **Проекты и решения**.  
  
    3.  Проверьте текстовое поле **Расположение пользовательских шаблонов проектов Visual Studio**.  
  
     По умолчанию это папка мои \\Templates\\ProjectTemplates *Version* приложение Documents\\Visual.  
  
2.  Извлеките ZIP\-файл.  
  
3.  Откройте файл .vstemplate в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  После элемента `TemplateContent` добавьте элемент [Элемент WizardExtension \(шаблоны Visual Studio\)](../extensibility/wizardextension-element-visual-studio-templates.md), указав строгое имя сборки пользовательского мастера.  Дополнительные сведения для отыскания строгого имени сборки содержатся в разделе [Практическое руководство. Просмотр содержимого глобального кэша сборок](../Topic/How%20to:%20View%20the%20Contents%20of%20the%20Global%20Assembly%20Cache.md) [Практическое руководство. Создание ссылки на сборку со строгим именем](../Topic/How%20to:%20Reference%20a%20Strong-Named%20Assembly.md).  
  
     В следующем примере создается элемент `WizardExtension`.  
  
    ```  
    <WizardExtension>  
        <Assembly>CustomWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=fa3902f409bb6a3b</Assembly>  
        <FullClassName>CustomWizard.IWizardImplementation</FullClassName>  
    </WizardExtension>  
    ```  
  
## Использование пользовательского мастера  
 Теперь можно создать проект из шаблона и использовать пользовательский мастер.  
  
#### Чтобы использовать пользовательский мастер  
  
1.  В меню **Файл** выберите команду **Создать проект**.  
  
2.  В диалоговом окне **Новый проект** найдите ваш шаблон, введите имя и нажмите кнопку **ОК**.  
  
     Откроется форма ввода пользовательского мастера.  
  
3.  Введите значение для пользовательского параметра и нажмите кнопку.  
  
     Форма ввода пользовательского мастера закроется, и проект создастся с помощью шаблона.  
  
4.  В **обозревателе решений** щелкните правой кнопкой мыши файл исходного кода и нажмите кнопку **Просмотреть код**.  
  
     Обратите внимание на то, что `$custommessage$` был заменен текстом, введенным в форму ввода пользовательского мастера.  
  
## См. также  
 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>   
 [Настройка шаблонов](../ide/customizing-project-and-item-templates.md)   
 [Элемент WizardExtension \(шаблоны Visual Studio\)](../extensibility/wizardextension-element-visual-studio-templates.md)