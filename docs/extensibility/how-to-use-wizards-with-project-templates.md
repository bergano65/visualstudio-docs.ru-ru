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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d2dc057dfa518bb52c6ba4d30cd0f3e0a822cfd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710536"
---
# <a name="how-to-use-wizards-with-project-templates"></a>Как: Использование мастеров с шаблонами проектов

Visual Studio <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> предоставляет интерфейс, который при реализации позволяет запускать пользовательский код, когда пользователь создает проект из шаблона.

Настройка шаблона проекта может использоваться для отображения пользовательского интерфейса, который собирает пользовательский вход для настройки шаблона, добавления дополнительных файлов в шаблон или любых других действий, разрешенных в проекте.

Методы <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> интерфейса называются в разное время во время создания проекта, начиная, как только пользователь нажимает **OK** на поле диалога **Нового проекта.** Каждый метод интерфейса назван для описания точки, в которой он называется. Например, Visual <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> Studio звонит сразу же, когда она начинает создавать проект, что делает его хорошим местом для записи пользовательского кода для сбора пользовательского ввода.

## <a name="create-a-project-template-project-with-a-vsix-project"></a>Создание шаблонного проекта с проектом VSIX

Вы начинаете создавать пользовательский шаблон с проектом шаблона проекта, который является частью Visual Studio SDK. В этой процедуре мы будем использовать проект шаблона проекта C', но есть также проект шаблона Visual Basic. Затем вы добавляете проект VSIX в решение, содержащее шаблон проекта проекта.

1. Создайте проект шаблона проекта C '(в Visual Studio, выберите **Файл** > **Новый** > **проект** и поиск «шаблона проекта»). Назовите его **MyProjectTemplate**.

   > [!NOTE]
   > Вас могут попросить установить Visual Studio SDK. Для получения дополнительной информации, см [Установка Визуальной студии SDK](../extensibility/installing-the-visual-studio-sdk.md).

2. Добавьте новый проект VSIX в то же решение, что и проект шаблона проекта (в **Solution Explorer**, выберите узло решения, нажмите правой кнопкой мыши, и выберите **Добавить** > **новый проект** и поиск "vsix"). Назовите его **MyProjectWizard.**

3. Закудь проект VSIX в качестве стартап-проекта. В **Solution Explorer**выберите узло проекта VSIX, щелкните правой кнопкой мыши и выберите Set в качестве запуска **проекта.**

4. Добавьте проект шаблона в качестве актива проекта VSIX. В **Solution Explorer**, под узлом проекта VSIX, найдите файл *source.extension.vsixmanifest.* Дважды щелкните его, чтобы открыть его в редакторе манифеста.

5. В редакторе манифеста выберите вкладку **«Активы»** на левой стороне окна.

6. Во вкладке **«Активы»** выберите **новый**. В окне **Добавить новые активы** для поля Type выберите **Microsoft.VisualStudio.ProjectTemplate**. В поле **Source** выберите **проект в текущем решении.** В поле **проекта** выберите **MyProjectTemplate**. После этого щелкните **OK**.

7. Постройте решение и запустите отладку. Откроется второй экземпляр Visual Studio. Это может занять несколько минут.

8. Во втором экземпляре Visual Studio попробуйте создать новый проект с новым шаблоном **(File** > **New** > **Project,** поиск "мипроект"). Новый проект должен отображаться с классом под названием **Class1**. Теперь вы создали пользовательский шаблон проекта! Прекратите отладку.

## <a name="create-a-custom-template-wizard"></a>Создание мастера пользовательского шаблона

Эта процедура показывает, как создать пользовательский мастер, который открывает форму Windows до создания проекта. Форма позволяет пользователям добавлять пользовательское значение параметра, которое добавляется к исходному коду во время создания проекта.

1. Настройка проекта VSIX, чтобы создать сборку.

2. В **Solution Explorer**выберите узло проекта VSIX. Ниже **Solution Explorer**, вы должны увидеть окно **Свойства.** Если вы этого не сделаете, выберите **окно View** > **Properties**или нажмите **F4.** В окне **Свойств** выберите `true`следующие поля:

   - **Включить сборку в контейнер VSIX**

   - **Включить символы отладки в контейнер VSIX**

   - **Включить символы отладки в локальное развертывание VSIX**

3. Добавьте сборку в качестве актива в проект VSIX. Откройте файл *source.extension.vsixmanifest* и выберите вкладку **Активы.** В окне **Добавить новые активы,** для **типа** выберите **Microsoft.VisualStudio.Assembly**, для **источника** выберите **проект в текущем решении,** и для **проекта** выберите **MyProjectWizard**.

4. Добавьте следующие ссылки на проект VSIX. (В **Solution Explorer**, под узлом проекта VSIX, выберите **Ссылки,** нажмите правой кнопкой мыши, и выберите **Добавить справку.)** В диалоге **Add Reference** во вкладке **Framework** найдите сборку **форм System.Windows** и выберите ее. Также найдите и выберите **сборки System** и **System.Drawing.** Теперь выберите вкладку **Расширения.** Найдите сборку **EnvDTE** и выберите ее. Также найдите сборку **Microsoft.VisualStudio.TemplateWizardInterface** и выберите ее. Нажмите кнопку **ОК**.

5. Добавьте класс для реализации мастера в проект VSIX. (В **Solution Explorer**, правой кнопкой мыши VSIX узла проекта и выберите **Добавить,** то **новый пункт**, то **класс**.) Назовите класс **WizardImplementation**.

6. Замените код в файле *WizardImplementationClass.cs* следующим кодом:

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

    **UserInputForm,** на который ссылается в этом коде, будет реализован позже.

    Класс `WizardImplementation` содержит реализации метода <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>для каждого участника . В этом примере <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> только метод выполняет задачу. Все остальные методы либо `true`ничего не делают, либо возвращаются.

    Метод <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> принимает четыре параметра:

   - Параметр, <xref:System.Object> который может быть <xref:EnvDTE._DTE> отлит на корневой объект, чтобы можно настроить проект.

   - Параметр, <xref:System.Collections.Generic.Dictionary%602> содержащий коллекцию всех заранее определенных параметров в шаблоне. Для получения дополнительной информации [Template parameters](../ide/template-parameters.md)о параметрах шаблона см.

   - Параметр, <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind> содержащий информацию о том, какой шаблон используется.

   - Массив, <xref:System.Object> содержащий набор параметров, переданных мастеру Visual Studio.

     Этот пример добавляет значение параметра из формы <xref:System.Collections.Generic.Dictionary%602> ввода пользователя к параметру. Каждый экземпляр `$custommessage$` параметра в проекте будет заменен текстом, введенным пользователем.

7. Теперь создайте **UserInPutForm**. В *WizardImplementation.cs* файле добавьте следующий код `WizardImplementation` после окончания класса.

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

    Пользователь входной формы обеспечивает простую форму для ввода пользовательского параметра. Форма содержит текстовое `textBox1` поле с `button1`именем и кнопку под названием . При нажатии кнопки текст из текстового ящика хранится в параметре. `customMessage`

## <a name="connect-the-wizard-to-the-custom-template"></a>Подключение мастера к пользовательскому шаблону

Для того, чтобы пользовательский шаблон проекта использовал пользовательский мастер, вам нужно подписать сборку мастера и добавить несколько строк в пользовательский шаблон проекта, чтобы он знал, где найти реализацию мастера при создании нового проекта.

1. Подпишите сборку. В **Solution Explorer**выберите проект VSIX, нажмите правой кнопкой мыши и выберите **свойства проекта.**

2. В окне **Свойств проекта** выберите вкладку **«Подпись»** во вкладке **«Подпись»,** проверьте **знак сборки.** В **поле файла «Выбрать сильное имя»** выберите ** \<New>. ** В окне **«Создайте сильное имя ключа»** в поле **имени файла Key** введите **key.snk.** Отключите файл Protect my key с помощью поля **паролей.**

3. В **Solution Explorer**выберите проект VSIX и найдите окно **Properties.**

4. Установите выход Copy Build Output на поле **каталога вывода** на **достоверное.** Это позволяет скопировать сборку в каталог вывода при восстановлении решения. Он по-прежнему `.vsix` содержится в файле. Вам нужно увидеть сборку, чтобы узнать ее ключ подписания.

5. Повторно создайте решение.

6. Теперь вы можете найти файл key.snk в каталоге проекта MyProjectWizard*\<(ваше местоположение диска> »MyProjectTemplate»MyProjectWizard.key.snk*). Копируйте файл *key.snk.*

7. Перейдите в каталог вывода и найдите сборку*\<(месторасположение диска>»MyProjectTemplate/MyProjectWizard-bin-MyProjectWizard.dll*). Вставьте файл *key.snk* здесь. (Это не является абсолютно необходимым, но это сделает следующие шаги проще.)

8. Откройте окно команды и измените в каталог, в котором была создана сборка.

9. Найдите инструмент для подписания *sn.exe.* Например, на 64-битной операционной системе Windows 10 типичный путь будет следующим:

     *C:-Программные файлы (x86)»Microsoft SDKs-Windows-v10.0A-bin-NETFX 4.6.1 Инструменты*

     Если вы не можете найти инструмент, попробуйте **запустить, где /R . sn.exe** в окне команды. Сделать к сведению путь.

10. Извлеките открытый ключ из файла *key.snk.* В окне команды введите

     **\<расположение sn.exe>'sn.exe-p key.snk outfile.key.**

     Не забудьте окружить путь *sn.exe* с кавычками, если есть пробелы в каталоге имена!

11. Получите общедоступный маркер ключа из файла:

     **\<расположение sn.exe>'sn.exe -t outfile.key.**

     Опять же, не забывайте, кавычки. Вы должны увидеть строку в выходе, как это

     **Токен «Открытый ключ» является \<токеном>**

     Сделать к сведению это значение.

12. Добавьте ссылку на пользовательский мастер в файл *шаблона проекта .vstemplate.* В **Solution Explorer**, найти файл под названием *MyProjectTemplate.vstemplate*, и открыть его. После окончания раздела \<TemplateContent> добавьте следующий раздел:

    ```xml
    <WizardExtension>
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>
    </WizardExtension>
    ```

     Где **MyProjectWizard** — это название сборки, а **токен** — это токен, который вы скопировали на предыдущем этапе.

13. Сохраните все файлы в проекте и перестроить.

## <a name="add-the-custom-parameter-to-the-template"></a>Добавьте пользовательский параметр в шаблон

В этом примере проект, используемый в качестве шаблона, отображает сообщение, указанное в форме ввода пользовательом пользовательского мастера.

1. В **Solution Explorer**перейдите к проекту **MyProjectTemplate** и откройте *Class1.cs.*

2. В `Main` методе приложения добавьте следующую строку кода.

   ```csharp
   Console.WriteLine("$custommessage$");
   ```

    Параметр `$custommessage$` заменяется текстом, введенным в форму ввода пользователя при создании проекта из шаблона.

Вот полный файл кода, прежде чем он был экспортирован в шаблон.

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

## <a name="use-the-custom-wizard"></a>Используйте пользовательский мастер

Теперь вы можете создать проект из шаблона и использовать пользовательский мастер.

1. Перестроить решение и начать отладку. Откроется второй экземпляр Visual Studio.

2. Создайте новый проект MyProjectTemplate. (**Файл** > **Новый** > **проект**).

3. В диалоговом окне **нового проекта** ищите "myproject", чтобы найти шаблон, введите имя и **нажмите OK.**

     Открывается форма ввода пользователя мастера.

4. Введите значение для пользовательского параметра и нажмите кнопку.

     Форма ввода пользователя мастера закрывается, и из шаблона создается проект.

5. В **Solution Explorer**, правой кнопкой мыши исходного кода файла и нажмите **Просмотреть код**.

     Обратите `$custommessage$` внимание, что был заменен текстом, введенным в форму ввода пользователя мастера.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>
- [Настройка шаблонов](../ide/customizing-project-and-item-templates.md)
- [Элемент WizardExtension (шаблоны Визуальной студии)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [Пакеты NuGet в шаблонах Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
