---
title: Практическое руководство. Использование мастеров для шаблонов проекта
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c4ff83c2d4d28b6393f7f6d03b01e35d9cc0aa4f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62911385"
---
# <a name="how-to-use-wizards-with-project-templates"></a>Практическое руководство. Использование мастеров для шаблонов проектов

Visual Studio предоставляет <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> интерфейс, который, при реализации, дают возможность запускать пользовательский код, когда пользователь создает проект на основе шаблона.

Настройка шаблона проекта можно использовать для отображения пользовательского интерфейса, собирает пользователем данные, чтобы настроить шаблон, добавьте дополнительные файлы в шаблоне, или любое другое действие, выполнение которых разрешено на проект.

<xref:Microsoft.VisualStudio.TemplateWizard.IWizard> Методов интерфейса будут вызываться в разные моменты времени проекта во время создания, запуска, как только пользователь щелкает **ОК** на **новый проект** диалоговое окно. Каждый метод интерфейса называется точке, в которой он вызывается. Например, Visual Studio вызывает <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> , когда для создания проекта, воплощение в удобное место для написания пользовательского кода для сбора входных данных пользователя.

## <a name="create-a-project-template-project-with-a-vsix-project"></a>Создание проекта шаблона проекта с помощью проекта VSIX

Приступить к созданию пользовательского шаблона с помощью проекта шаблона проекта, которое входит в состав пакета SDK для Visual Studio. В этой процедуре мы будем использовать C# проект шаблона, но также есть проект шаблона проекта Visual Basic. Затем можно добавить проект VSIX в решение, содержащее проект шаблона проекта.

1. Создание C# проекта шаблона проекта (в Visual Studio выберите **файл** > **New** > **проекта** и выполните поиск «шаблон проекта» ). Назовите его **MyProjectTemplate**.

   > [!NOTE]
   > Вы может появиться запрос на установку Visual Studio SDK. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

2. Добавление нового проекта VSIX в том же решении, что и проект шаблона проекта (в **обозревателе решений**, выберите узел решения, щелкните правой кнопкой мыши и выберите **добавить** > **новый проект**  и выполните поиск «vsix»). Назовите его **MyProjectWizard.**

3. Назначьте проект VSIX запускаемым проектом. В **обозревателе решений**, выберите узел проекта VSIX, щелкните правой кнопкой мыши и выберите **Назначить запускаемым проектом**.

4. Добавьте проект шаблона как ресурс проекта VSIX. В **обозревателе решений**, в узле проекта VSIX, найти *source.extension.vsixmanifest* файл. Дважды щелкните его, чтобы открыть редактор манифеста.

5. В редакторе манифеста выберите **активы** вкладка в левой части окна.

6. В **активы** выберите **New**. В **добавить новый актив** окно, введите в поле выберите **Microsoft.VisualStudio.ProjectTemplate**. В **источника** выберите **проект в текущем решении**. В **проекта** выберите **MyProjectTemplate**. Затем нажмите кнопку **ОК**.

7. Постройте решение и запустите отладку. Откроется второй экземпляр Visual Studio. (Это может занять несколько минут).

8. В второй экземпляр Visual Studio, попробуйте создать новый проект с помощью нового шаблона (**файл** > **New** > **проекта**, поиск « Мой проект»). Новый проект должен отобразиться определить класс с именем **Class1**. Вы создали настраиваемого шаблона проекта! Остановите отладку сейчас.

## <a name="create-a-custom-template-wizard"></a>Создать настраиваемый мастер шаблонов

Эта процедура показано, как создать пользовательский мастер, который открывает форму Windows, прежде чем создается проект. Форма позволяет пользователям добавлять значение пользовательского параметра, который добавляется к исходному коду во время создания проекта.

1. Настройка проекта VSIX, чтобы его можно создать сборку.

2. В **обозревателе решений**, выберите узел проекта VSIX. Ниже **обозревателе решений**, вы должны увидеть **свойства** окна. Если этого не сделать, выберите **представление** > **окно "Свойства"**, или нажмите клавишу **F4**. В **свойства** окно, выберите следующие поля для `true`:

   - **IncludeAssemblyInVSIXContainer**

   - **IncludeDebugSymbolsInVSIXContainer**

   - **IncludeDebugSymbolsInLocalVSIXDeployment**

3. Добавьте сборку как ресурс проекта VSIX. Откройте *source.extension.vsixmanifest* файл и выберите **активы** вкладки. В **добавить новый актив** окне для **тип** выберите **Microsoft.VisualStudio.Assembly**, для **источника** выберите **A проект в текущем решении**, а также для **проекта** выберите **MyProjectWizard**.

4. Добавьте следующие ссылки в проект VSIX. (В **обозревателе решений**, в узле проекта VSIX, выберите **ссылки**, щелкните правой кнопкой мыши и выберите **добавить ссылку**.) В **добавить ссылку** диалоговое окно, в **Framework** вкладке, найти **System.Windows Forms** сборки и выберите его. Теперь выберите **расширения** вкладки. Найти **EnvDTE** сборки и выберите его. Также найти **Microsoft.VisualStudio.TemplateWizardInterface** сборки и выберите его. Нажмите кнопку **ОК**.

5. Добавьте класс для реализации мастера в проект VSIX. (В **обозревателе решений**, щелкните правой кнопкой мыши узел проекта VSIX и выберите **добавить**, затем **новый элемент**, затем **класс**.) Назовите класс **WizardImplementation**.

6. Замените код в *WizardImplementationClass.cs* файла следующим кодом:

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

    **UserInputForm** в этом коде будет реализована позже.

    `WizardImplementation` Класс содержит методы реализации для каждого члена <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>. В этом примере используется только <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> метод выполняет задачу. Все остальные методы не выполнять никаких действий или возвращать `true`.

    <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> Метод принимает четыре параметра:

   - <xref:System.Object> Параметр, который может быть приведен к корню <xref:EnvDTE._DTE> объекта, чтобы можно было настроить проект.

   - Объект <xref:System.Collections.Generic.Dictionary%602> параметр, который содержит коллекцию всех предварительно определенных параметров в шаблоне. Дополнительные сведения о параметраз шаблонов см. в разделе [параметров шаблона](../ide/template-parameters.md).

   - Объект <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind> параметр, содержащий сведения о том, какого рода шаблон используется.

   - <xref:System.Object> Массив, содержащий набор параметров передано мастера с помощью Visual Studio.

     В этом примере значение параметра из пользовательской формы ввода для <xref:System.Collections.Generic.Dictionary%602> параметра. Каждый экземпляр `$custommessage$` параметр в проекте будут заменены на текст, введенный пользователем. Добавьте следующие сборки в проект: **Система** и **System.Drawing**.

7. Теперь создайте **UserInputForm**. В *WizardImplementation.cs* добавьте следующий код в конце `WizardImplementation` класса.

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

    Форма ввода пользователя предоставляет простую форму для ввода пользовательских параметров. Форма содержит текстовое поле с именем `textBox1` и кнопки с именем `button1`. При нажатии кнопки, текст из текстового поля сохраняется в `customMessage` параметра.

## <a name="connect-the-wizard-to-the-custom-template"></a>Мастер подключений для пользовательского шаблона

Чтобы ваш пользовательский шаблон проекта для использования пользовательского мастера необходимо подписать сборку мастера и добавьте несколько строк в шаблон пользовательского проекта, чтобы позволить, он знает, где можно найти в мастер реализации при создании нового проекта.

1. Подпишите сборку. В **обозревателе решений**, выберите проект VSIX, щелкните правой кнопкой мыши и выберите **свойства проекта**.

2. В **свойства проекта** выберите **подписывание** вкладку в **подписывание** вкладке **подписать сборку**. В **выберите файл ключа строгого имени** выберите  **\<New >**. В **Создание ключа строгого имени** окно в **имя файла ключа** введите **key.snk**. Снимите флажок **защитить мой файл ключей паролем** поля.

3. В **обозревателе решений**, выберите проект VSIX и найти **свойства** окна.

4. Задайте **выходных данных для выходного каталога сборки копирования** поле **true**. Благодаря этому сборки, в который копируется в выходной каталог при перестроении решения. Он по-прежнему содержится в `.vsix` файл. Необходимо просмотреть сборки, чтобы узнать его ключ подписи.

5. Выполните повторную сборку решения.

6. Файл key.snk теперь можно найти в каталоге проекта MyProjectWizard (*\<расположение на диске > \MyProjectTemplate\MyProjectWizard\key.snk*). Копировать *key.snk* файл.

7. Перейдите в выходной каталог и найти сборку (*\<расположение на диске > \MyProjectTemplate/MyProjectWizard\bin\Debug\MyProjectWizard.dll*). Вставить *key.snk* файл здесь. (Это не обязателен, но это сделает следующее более удобными.)

8. Откройте окно командной строки и перейдите в каталог, в котором будет создана сборка.

9. Найти *sn.exe* инструмент подписывания. Например в 64-разрядной операционной системе Windows 10, типичный путь будет иметь следующее:

     *C:\Program Files (x86)\Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.6.1 Tools*

     Если не удается найти средство, попробуйте запустить **где /R. sn.exe** в окне командной строки. Запомните или запишите путь.

10. Извлеките открытый ключ из *key.snk* файл. В окне командной строки введите

     **\<расположение sn.exe > outfile.key key.snk \sn.exe -p.**

     Не забудьте заключить путь *sn.exe* в кавычки, если есть пробелы в именах каталогов!

11. Получение токена открытого ключа из outfile:

     **\<расположение sn.exe > outfile.key \sn.exe -t.**

     Не забывайте кавычек. Вы должны увидеть строку в выходные данные следующего вида

     **Токен открытого ключа \<token >**

     Запомните или запишите это значение.

12. Добавление ссылки на пользовательские мастера для *.vstemplate* файл шаблона проекта. В **обозревателе решений**, найдите файл, именуемый *MyProjectTemplate.vstemplate*и откройте его. После окончания \<TemplateContent > разделе, добавьте следующий раздел:

    ```xml
    <WizardExtension>
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>
    </WizardExtension>
    ```

     Где **MyProjectWizard** имя сборки, и **маркера** является маркером, который вы скопировали на предыдущем шаге.

13. Сохраните все файлы в проекте и перестройте.

## <a name="add-the-custom-parameter-to-the-template"></a>Добавление пользовательского параметра в шаблон

В этом примере проект, используемый в качестве шаблона отображает сообщения, заданного в пользовательскую форму ввода пользовательского мастера.

1. В **обозревателе решений**, перейдите в меню **MyProjectTemplate** проект и откройте *Class1.cs*.

2. В `Main` методу приложения, добавьте следующую строку кода.

   ```csharp
   Console.WriteLine("$custommessage$");
   ```

    Параметр `$custommessage$` заменяется текстом, введенным в форму ввода пользователя, при создании проекта из шаблона.

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

## <a name="use-the-custom-wizard"></a>Использование пользовательского мастера

Теперь можно создать с помощью шаблона проекта и использовать пользовательский мастер.

1. Перестройте решение и начните отладку. Откроется второй экземпляр Visual Studio.

2. Создайте новый проект MyProjectTemplate. (**Файл** > **новый** > **проекта**).

3. В **новый проект** диалоговое окно, и выполните поиск «myproject» найти шаблон, введите имя и нажмите кнопку **ОК**.

     Откроется форма для ввода пользовательского мастера.

4. Введите значение для пользовательского параметра и нажмите кнопку.

     Форма для ввода пользовательского мастера закроется, и проект создается на основе шаблона.

5. В **обозревателе решений**, щелкните правой кнопкой мыши файл исходного кода и нажмите кнопку **Просмотр кода**.

     Обратите внимание, что `$custommessage$` был заменен текст, введенный в форму ввода пользовательского мастера.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>
- [Настройка шаблонов](../ide/customizing-project-and-item-templates.md)
- [Элемент WizardExtension (шаблоны Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [Пакеты NuGet в шаблонах Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)