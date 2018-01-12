---
title: "Как: использование мастеров для шаблонов проекта | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8eef98d11f98e3db8216c69dcfacf478c676a837
ms.sourcegitcommit: 5f436413bbb1e8aa18231eb5af210e7595401aa6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="how-to-use-wizards-with-project-templates"></a>Практическое руководство. Использование мастеров для шаблонов проекта
Visual Studio предоставляет <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> интерфейс, который при реализации позволяет запускать пользовательский код, когда пользователь создает проект на основе шаблона.  
  
 Настройка шаблона проекта можно использовать для отображения пользовательского интерфейса, собирающий пользователем данные, чтобы настроить шаблон, добавьте дополнительные файлы в шаблон или любых других действий, разрешенных в проекте.  
  
 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> Методы интерфейса вызываются в различные моменты времени при проекта, запускающиеся сразу после того, как пользователь щелкает **ОК** на **новый проект** диалоговое окно. Каждый метод интерфейса называется точке, в которой он вызывается. Например, Visual Studio вызывает <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> , когда для создания проекта, сделав его удобное место для написания пользовательского кода для сбора входных данных пользователя.  
  
## <a name="creating-a-project-template-project-with-a-vsix-project"></a>Создание проекта шаблона проекта с помощью проекта VSIX  
 Приступить к созданию пользовательского шаблона с помощью проекта шаблона проекта., которая входит в пакет SDK для Visual Studio. В этой процедуре будет использоваться проекта шаблона проекта C#, но отсутствует проект шаблона проекта Visual Basic. Затем проект VSIX, КОТОРЫЙ добавляется в решение, содержащее проект шаблона проекта.  
  
1.  Создание проекта шаблона проекта C# (в Visual Studio **файл > Создать > проект > Visual C# > расширяемости > шаблон проекта C#**). Назовите его **MyProjectTemplate**.  
  
    > [!NOTE]
    >  Вы может появиться запрос на установку Visual Studio SDK. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
2.  Добавьте новый проект VSIX (**файл > Создать > проект > Visual C# > расширяемости > проект VSIX**) в том же решении, что проект шаблона проекта (в **обозревателе решений**выберите узел решения, щелкните правой кнопкой мыши и выберите **Добавить > Новый проект**). Назовите его **MyProjectWizard.**  
  
3.  Назначьте проект VSIX запускаемым проектом. В **обозревателе решений**, выберите узел проекта VSIX, щелкните правой кнопкой мыши и выберите **Назначить запускаемым проектом**.  
  
4.  Добавьте проект шаблона в качестве ресурса проекта VSIX. В **обозревателе решений**, в узле проекта VSIX, найти **source.extension.vsixmanifest** файла. Дважды щелкните его, чтобы открыть его в редакторе манифестов.  
  
5.  В редакторе манифестов выберите **активы** вкладка в левой части окна.  
  
6.  В **активы** выберите **New**. В **добавить новый актив** окна для поле «Тип» выберите **Microsoft.VisualStudio.ProjectTemplate**. В **источника** выберите **проект в текущем решении**. В **проекта** выберите **MyProjectTemplate**. Затем нажмите кнопку **ОК**.  
  
7.  Постройте решение и запустите отладку. Откроется второй экземпляр Visual Studio. (Это может занять несколько минут).  
  
8.  Во втором экземпляре Visual Studio попробуйте создать новый проект с помощью нового шаблона. (**Файл > Создать > проект > Visual C# > шаблон MyProject**). Класс с именем появится новый проект **Class1**. Вы создали пользовательский шаблон проекта. Остановите отладку сейчас.  
  
## <a name="creating-a-custom-template-wizard"></a>Создание настраиваемого шаблона  
 В этом разделе показано, как создать пользовательский мастер, который открывает форму Windows Forms до создания проекта. Форма дает пользователям возможность добавления пользовательского параметра, который добавляется к исходному коду во время создания проекта.  
  
1.  Настройте проект VSIX, чтобы его можно создать сборку.  
  
2.  В **обозревателе решений**, выберите узел проекта VSIX. Ниже в обозревателе решений появится **свойства** окна. Если этого не сделать, выберите **представление > «свойства»**, или нажмите клавишу **F4**. В окне «Свойства» выберите следующие поля, чтобы `true`:  
  
    -   **IncludeAssemblyInVSIXContainer**  
  
    -   **IncludeDebugSymbolsInVSIXContainer**  
  
    -   **IncludeDebugSymbolsInLocalVSIXDeployment**  
  
3.  Добавьте сборку в виде ресурса в проект VSIX. Откройте файл source.extension.vsixmanifest и выберите **активы** вкладки. В **добавить новый актив** окна для **тип** выберите **Microsoft.VisualStudio.Assembly**, для **источника** выберите **A проект в текущем решении**, а также для **проекта** выберите **MyProjectWizard**.  
  
4.  Добавьте следующие ссылки в проект VSIX. (В **обозреватель решений**, в разделе VSIX проекта выберите узел **ссылки**, щелкните правой кнопкой мыши и выберите **добавить ссылку**.) В **добавить ссылку** диалоговое окно, в **Framework** , найдите **System.Windows Forms** сборки и выберите его. Теперь выберите **расширения** найдите вкладку **EnvDTE** сборки и выберите его. Кроме того, найти **Microsoft.VisualStudio.TemplateWizardInterface** сборки и выберите его. Нажмите кнопку **ОК**.  
  
5.  Добавление класса для реализации мастера в проект VSIX. (В обозревателе решений щелкните правой кнопкой мыши узел проекта VSIX и выберите **добавить**, затем **новый элемент**, затем **класса**.) Имя класса **WizardImplementation**.  
  
6.  Замените код в **WizardImplementationClass.cs** файла следующим кодом:  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.TemplateWizard;  
    using System.Windows.Forms;  
    using EnvDTE;  
  
    namespace MyProjectWizard  
    {  
        public class WizardImplementation:IWizard  
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
  
                    customMessage = UserInputForm.CustomMessage;  
  
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
  
     **UserInputForm** ссылки в этом коде будет реализована более поздней версии.  
  
     `WizardImplementation` Класс содержит методы реализации для каждого члена <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>. В этом примере только <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> метод выполняет задачу. Все другие методы не выполняют никаких действий или возвращать `true`.  
  
     <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> Метод принимает четыре параметра:  
  
    -   <xref:System.Object> Параметр, который может быть приведен к корню <xref:EnvDTE._DTE> объекта, чтобы можно было настроить проект.  
  
    -   Объект <xref:System.Collections.Generic.Dictionary%602> параметр, который содержит коллекцию всех предварительно определенных параметров в шаблоне. Дополнительные сведения о параметрах шаблона см. в разделе [параметров шаблона](../ide/template-parameters.md).  
  
    -   Объект <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind> параметра, который содержит сведения о используется тип шаблона.  
  
    -   <xref:System.Object> Переданный массив, содержащий набор параметров мастера с Visual Studio.  
  
     В этом примере добавляется значение из пользовательской формы ввода для <xref:System.Collections.Generic.Dictionary%602> параметра. Каждый экземпляр `$custommessage$` параметр в проекте будут заменены на текст, введенный пользователем. Следующие сборки необходимо добавить в проект: **системы** и **System.Drawing**.
  
7.  Теперь создайте **UserInputForm**. В **WizardImplementation.cs** файл, добавьте следующий код в конце **WizardImplementation** класса.  
  
    ```csharp  
    public partial class UserInputForm : Form  
        {  
            private static string customMessage;  
            private TextBox textBox1;  
            private Button button1;  
  
            public UserInputForm()  
            {  
                this.Size = new System.Drawing.Size(155, 265);   
  
                button1 = new Button();  
                button1.Location = new System.Drawing.Point(90, 25);  
                button1.Size = new System.Drawing.Size(50, 25);  
                button1.Click += button1_Click;  
                this.Controls.Add(button1);  
  
                textBox1 = new TextBox();  
                textBox1.Location = new System.Drawing.Point(10, 25);  
                textBox1.Size = new System.Drawing.Size(70, 20);  
                this.Controls.Add(textBox1);  
            }  
            public static string CustomMessage  
            {  
                get  
                {  
                    return customMessage;  
                }  
                set  
                {  
                    customMessage = value;  
                }     
            }  
            private void button1_Click(object sender, EventArgs e)  
            {  
                customMessage = textBox1.Text;  
                this.Close();
            }  
        }  
    ```  
  
     Пользовательская форма ввода представляет собой простую форму для ввода пользовательских параметров. Форма содержит текстовое поле с именем `textBox1` и кнопку с именем `button1`. При нажатии кнопки текст из текстового поля сохраняется в `customMessage` параметра.  
  
## <a name="connect-the-wizard-to-the-custom-template"></a>Мастер соединиться пользовательского шаблона  
 Ваш пользовательский шаблон проекта для использования пользовательского мастера, необходимо подписать сборку мастера и добавьте некоторые строки в настраиваемом проекте шаблон позволяющее ему определить, где найти реализацию мастер при создании нового проекта.  
  
1.  Подпишите сборку. В **обозревателе решений**, выберите проект VSIX, щелкните правой кнопкой мыши и выберите **свойства проекта**.  
  
2.  В **свойства проекта** выберите **подписывание** вкладку в **подписывание** установите флажок **подписать сборку**. В **выберите файл ключей строгого имени** выберите  **\<Создать >**. В **Создание ключа строгого имени** окна в **имя файла ключа** введите **key.snk**. Снимите флажок **защитить мой файл ключей паролем** поля.  
  
3.  В **обозревателе решений**, выберите проект VSIX и найти **свойства** окна.  
  
4.  Задать **выходные данные в выходной каталог сборки копирования** на **true**. Это позволяет сборки копируются в выходную папку при перестроении решения. Он по-прежнему содержится в VSIX-файл. Необходимо просмотреть для выяснения его ключ подписи сборки.  
  
5.  Выполните повторную сборку решения.  
  
6.  Файл key.snk теперь можно найти в каталоге проекта MyProjectWizard (**\<расположение на диске > \MyProjectTemplate\MyProjectWizard\key.snk**). Скопируйте файл key.snk.  
  
7.  Перейдите в папку вывода и найти сборку (**\<расположение на диске > \MyProjectTemplate/MyProjectWizard\bin\Debug\MyProjectWizard.dll**). Вставьте здесь файл key.snk. (Это не крайней необходимости, однако он поможет упростить ниже).  
  
8.  Откройте окно командной строки и перейдите в каталог, в котором будет создана сборка.  
  
9. Найти **sn.exe** средством подписывания. Например в 64-разрядной операционной системе Windows 10, типичный путь будет следующая:  
  
     **Средства \Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.6.1 C:\Program (x86) файлов**  
  
     Если не удается найти средство, попробуйте запустить **где /R.  Sn.exe** в окне команд. Запишите путь.  
  
10. Извлечь открытый ключ из файла key.snk. В окне командной строки введите:  
  
     **\<расположение программы sn.exe > outfile.key key.snk \sn.exe -p.**  
  
     Не забудьте заключайте этот путь программы sn.exe в кавычки, при наличии пробелов в именах каталогов!  
  
11. Получение токена открытого ключа из outfile:  
  
     **\<расположение программы sn.exe > outfile.key \sn.exe -t.**  
  
     Не забывайте, кавычки. Должна появиться строка в выходных данных следующим образом  
  
     **Токен открытого ключа:<token>**  
  
     Запишите это значение.  
  
12. Добавьте ссылку на пользовательский мастер VSTEMPLATE-файлу шаблона проекта. В обозревателе решений найдите файл с именем MyProjectTemplate.vstemplate и откройте его. После окончания \<TemplateContent > добавьте следующий раздел:  
  
    ```xml  
    <WizardExtension>  
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>  
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>  
    </WizardExtension>  
    ```  
  
     Где **MyProjectWizard** имя сборки, и **маркера** токен, скопированный на предыдущем шаге.  
  
13. Сохраните все файлы в проекте и заново.  
  
## <a name="adding-the-custom-parameter-to-the-template"></a>Добавление пользовательского параметра в шаблон  
 В этом примере проект, используемый в качестве шаблона отображает сообщения, заданного в пользовательскую форму ввода пользовательского мастера.  
  
1.  В обозревателе решений, перейдите к **MyProjectTemplate** проект и откройте **Class1.cs**.  
  
2.  В `Main` метод приложения, добавьте следующую строку кода.  
  
    ```  
    Console.WriteLine("$custommessage$");  
    ```  
  
     Параметр `$custommessage$` заменяется текстом, введенным в пользовательскую форму ввода при создании проекта из шаблона.  
  
 Ниже приведен полный файл кода, прежде чем он был экспортирован в шаблон.  
  
```csharp  
using System;  
using System.Collections.Generic;  
$if$ ($targetframeworkversion$ >= 3.5)using System.Linq;  
$endif$using System.Text;  
  
namespace $safeprojectname$  
{  
    public class Class1  
    {  
          static void Main(string[] args)  
          {  
               Console.WriteLine("$custommessage$");  
          }  
    }  
}  
```  
  
## <a name="using-the-custom-wizard"></a>Использование пользовательского мастера  
 Теперь можно создать проект из шаблона и использовать пользовательский мастер.  
  
1.  Перестройте решение и запустить отладку. Откроется второй экземпляр Visual Studio.  
  
2.  Создайте новый проект MyProjectTemplate. (**Файл > Создать > проект > Visual C# > MyProjectTemplate**)  
  
3.  В **новый проект** диалоговое окно, найдите ваш шаблон, введите имя и нажмите кнопку **ОК**.  
  
     Откроется форма ввода пользовательского мастера.  
  
4.  Введите значение для пользовательского параметра и нажмите кнопку.  
  
     Форма ввода пользовательского мастера закроется, и проект создается из шаблона.  
  
5.  В **обозревателе решений**, щелкните правой кнопкой мыши файл исходного кода и нажмите кнопку **Просмотр кода**.  
  
     Обратите внимание, что `$custommessage$` был заменен текстом, введенным в форму ввода пользовательского мастера.  
  
## <a name="see-also"></a>См. также  

<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>   
[Настройка шаблонов](../ide/customizing-project-and-item-templates.md)  
[Элемент WizardExtension (шаблоны Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)  
[Пакеты NuGet в шаблонах Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
