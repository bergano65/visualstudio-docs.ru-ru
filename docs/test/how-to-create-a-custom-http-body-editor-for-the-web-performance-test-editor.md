---
title: Создание пользовательского редактора текста HTTP для редактора веб-тестов производительности в Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, custom HTTP body editor
ms.assetid: a0b2d8ff-3e2a-487e-9172-90047174f336
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 187822c0217e6aca4f8828c82274520a35e8afe2
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/31/2018
ms.locfileid: "39380659"
---
# <a name="how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor"></a>Практическое руководство. Создание пользовательского редактора текста HTTP для редактора веб-тестов производительности

Чтобы изменить содержимое основного текста строки или двоичного основного текста запроса веб-служб, такого как запрос SOAP, REST, asmx, wcf, RIA или запрос веб-служб других типов, можно создать пользовательский редактор содержимого.

 Можно реализовать следующие типы редакторов.

-   **Редактор содержимого строк**. Этот редактор реализуется с помощью интерфейса <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>.

-   **Редактор двоичного содержимого**. Этот редактор реализуется с помощью интерфейса <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>.

Эти интерфейсы содержатся в пространстве имен <xref:Microsoft.VisualStudio.TestTools.WebTesting>.

## <a name="create-a-windows-control-library-project"></a>Создание проекта библиотеки элементов управления Windows

### <a name="create-a-user-control-by-using-a-windows-control-library-project"></a>Создание пользовательского элемента управления с использованием проекта библиотеки элементов управления Windows

1.  В меню **Файл** Visual Studio последовательно выберите пункты **Создать** и **Проект**.

     Откроется диалоговое окно **Новый проект**.

2.  В области **Установленные шаблоны** разверните узел **Visual Basic** или **Visual C#** в зависимости от используемого языка программирования и щелкните узел **Windows**.

    > [!NOTE]
    > В этом примере используется Visual C#.

3.  В списке шаблонов выберите пункт **Библиотека элементов управления Windows Forms**.

4.  В текстовом поле **Имя** введите имя, например `MessageEditors`, и нажмите кнопку **ОК**.

    > [!NOTE]
    > В этом примере используется имя MessageEditors.

     Проект добавляется в новое решение, и в конструкторе отображается объект <xref:System.Windows.Forms.UserControl> с именем *UserControl1.cs*.

5.  Перетащите объект <xref:System.Windows.Forms.RichTextBox> из категории **Стандартные элементы управления** области **Панель элементов** в область элемента управления UserControl1.

6.  Выберите глиф тега действия (![глиф смарт-тега](../test/media/vs_winformsmttagglyph.gif)) в правом верхнем углу элемента управления <xref:System.Windows.Forms.RichTextBox> и выберите команду **Закрепить в родительском контейнере**.

7.  В **обозревателе решений** щелкните правой кнопкой мыши проект библиотеки Windows Forms и выберите пункт **Свойства**.

8.  В окне **Свойства** перейдите на вкладку **Приложение**.

9. В раскрывающемся списке **Требуемая версия .NET Framework** выберите значение **.NET Framework 4**.

10. Откроется диалоговое окно **Изменение целевой рабочей среды**.

11. Выберите **Да**.

12. В **обозревателе решений** щелкните правой кнопкой мыши узел **Ссылки** и выберите команду **Добавить ссылку**.

13. Появится диалоговое окно **Добавление ссылки**.

14. Перейдите на вкладку **.NET**, прокрутите вниз, выберите пункт **Microsoft.VisualStudio.QualityTools.WebTestFramework** и нажмите кнопку **ОК**.

15. Если **конструктор представлений** еще не открыт, в **обозревателе решений** щелкните правой кнопкой мыши узел **UserControl1.cs** и выберите команду **Конструктор представлений**.

16. Щелкните правой кнопкой мыши в любом месте области конструктора и выберите команду **Просмотреть код**.

17. (Необязательно) Присвойте классу и конструктору из элемента управления UserControl1 значащее имя, например MessageEditorControl:

    > [!NOTE]
    > В этом примере используется имя MessageEditorControl.

    ```csharp
    namespace MessageEditors
    {
        public partial class MessageEditorControl : UserControl
        {
            public MessageEditorControl()
            {
                InitializeComponent();
            }
        }
    }
    ```

18. Добавьте следующие свойства для поддержки получения и задания текста в элементе управления RichTextBox1. Интерфейсом <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> используется свойство EditString, а интерфейсом <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> — свойство EditByteArray:

   ```csharp
   public String EditString
   {
       get
       {
           return this.richTextBox1.Text;
       }
       set
       {
           this.richTextBox1.Text = value;
       }
   }

   public byte[] EditByteArray
   {
       get
       {
           return System.Convert.FromBase64String(richTextBox1.Text);
       }
       set
       {
           richTextBox1.Text = System.Convert.ToBase64String(value, 0, value.Length);
       }
   }
   ```

## <a name="add-a-class-to-the-windows-control-library-project"></a>Добавление класса в проект библиотеки элементов управления Windows

Добавьте в проект класс. Этот класс будет использоваться для реализации интерфейсов <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> и <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>.

**Обзор кода данной процедуры**

Для объекта <xref:System.Windows.Forms.UserControl> с именем MessageEditorControl, который был создан в предыдущей процедуре, создается экземпляр с именем messageEditorControl:

```csharp
private MessageEditorControl messageEditorControl
```

 Экземпляр messageEditorControl размещается в диалоговом окне подключаемого модуля, которое создается методом <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.CreateEditor*>. Кроме того, элемент управления <xref:System.Windows.Forms.RichTextBox> экземпляра messageEditorControl заполняется содержимым в интерфейсе <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>. Однако создание подключаемого модуля возможно, только если метод <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*> возвращает значение `true`. В случае данного редактора метод <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*> возвращает значение `true`, если свойство <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> интерфейса <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> содержит значение "xml".

 После того как пользователь завершит изменение основного текста строки и нажмет кнопку **ОК** в диалоговом окне подключаемого модуля, вызывается метод <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.GetNewValue*> для получения измененного текста в виде строки и обновления **текста строки** запроса в редакторе веб-тестов производительности.

### <a name="to-create-a-class-and-implement-the-istringhttpbodyeditorplugin-interface-code"></a>Создание класса и реализация кода интерфейса IStringHttpBodyEditorPlugin

1.  В **обозревателе решений** щелкните правой кнопкой мыши проект библиотеки элементов управления Windows Forms и выберите команду **Добавить новый элемент**.

2.  Откроется диалоговое окно **Добавление нового элемента**.

3.  Выберите **Класс**.

4.  В текстовом поле **Имя** введите значащее имя класса, например `MessageEditorPlugins`.

5.  Выберите **Добавить**.

     В проект добавляется класс Class1, который отображается в редакторе кода.

6.  В редакторе кода добавьте следующий оператор using:

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    ```

7.  Напишите или скопируйте следующий код, чтобы создать экземпляр класса XmlMessageEditor из интерфейса <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> и реализовать требуемые методы:

    ```csharp
    /// <summary>
    /// Editor for generic text based hierarchical messages such as XML and JSON.
    /// </summary>
    public class XmlMessageEditor : IStringHttpBodyEditorPlugin
    {
        public XmlMessageEditor()
        {
        }

        /// <summary>
        /// Determine if this plugin supports the content type.
        /// </summary>
        /// <param name="contentType">The content type to test.</param>
        /// <returns>Returns true if the plugin supports the specified content type.</returns>
        public bool SupportsContentType(string contentType)
        {
            return contentType.ToLower().Contains("xml");
        }

        /// <summary>
        /// Create a UserControl to edit the specified bytes.
        /// This control will be hosted in the
        /// plugin dialog which provides OK and Cancel buttons.
        /// </summary>
        /// <param name="contentType">The content type of the BinaryHttpBody.</param>
        /// <param name="initialValue">The bytes to edit.  The bytes are the payload of a BinaryHttpBody.</param>
        /// <returns>A UserControl capable of displaying and editing the byte array value of the specified content type.</returns>
        public object CreateEditor(string contentType, string initialValue)
        {
            messageEditorControl = new MessageEditorControl();
            messageEditorControl.EditString = initialValue;
            return this.messageEditorControl;
        }

        /// <summary>
        /// Gets the edited bytes after the OK button is clicked on the plugin dialog.
        /// </summary>
        public string GetNewValue()
        {
            return messageEditorControl.EditString;
        }

        private MessageEditorControl messageEditorControl;
    }
    ```

## <a name="add-a-ibinaryhttpbodyeditorplugin-to-the-class"></a>Добавление интерфейса IBinaryHttpBodyEditorPlugin в класс

Реализовать интерфейс <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>.

**Обзор кода данной процедуры**

Реализация кода интерфейса <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> аналогична реализации интерфейса <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>, рассмотренной в предыдущей процедуре. Однако в двоичной версии используется массив байтов для обработки двоичных данных, а не строки.

Для объекта <xref:System.Windows.Forms.UserControl> с именем MessageEditorControl, который был создан в первой процедуре, создается экземпляр с именем messageEditorControl:

```csharp
private MessageEditorControl messageEditorControl
```

Экземпляр messageEditorControl размещается в диалоговом окне подключаемого модуля, которое создается методом <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.CreateEditor*>. Кроме того, элемент управления <xref:System.Windows.Forms.RichTextBox> экземпляра messageEditorControl заполняется содержимым в интерфейсе <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>. Однако создание подключаемого модуля возможно, только если метод <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*> возвращает значение `true`. В случае данного редактора метод <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*> возвращает значение `true`, если свойство <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> интерфейса <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> содержит значение "msbin1".

После того как пользователь завершит изменение основного текста строки и нажмет кнопку **ОК** в диалоговом окне подключаемого модуля, вызывается метод <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.GetNewValue*> для получения измененного текста в виде строки и обновления свойства **BinaryHttpBody.Data** запроса в редакторе веб-тестов производительности.

### <a name="to-add-the-ibinaryhttpbodyeditorplugin-to-the-class"></a>Добавление интерфейса IBinaryHttpBodyEditorPlugin в класс

-   Напишите или скопируйте следующий код внутри класса XmlMessageEditor, добавленного в предыдущей процедуре, чтобы создать экземпляр класса Msbin1MessageEditor из интерфейса <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> и реализовать требуемые методы:

    ```csharp
    /// <summary>
        /// Editor for MSBin1 content type (WCF messages)
        /// </summary>
        public class Msbin1MessageEditor : IBinaryHttpBodyEditorPlugin
        {
            /// <summary>
            ///
            /// </summary>
            public Msbin1MessageEditor()
            {
            }

            /// <summary>
            /// Determine if this plugin supports a content type.
            /// </summary>
            /// <param name="contentType">The content type to test.</param>
            /// <returns>Returns true if the plugin supports the specified content type.</returns>
            public bool SupportsContentType(string contentType)
            {
                return contentType.ToLower().Contains("msbin1");
            }

            /// <summary>
            /// Create a UserControl to edit the specified bytes.  This control will be hosted in the
            /// plugin dialog which provides OK and Cancel buttons.
            /// </summary>
            /// <param name="contentType">The content type of the BinaryHttpBody.</param>
            /// <param name="initialValue">The bytes to edit.  The bytes are the payload of a BinaryHttpBody.</param>
            /// <returns>A UserControl capable of displaying and editing the byte array value of the specified content type.</returns>
            public object CreateEditor(string contentType, byte[] initialValue)
            {
                messageEditorControl = new MessageEditorControl();
                messageEditorControl.EditByteArray = initialValue;
                return messageEditorControl;
            }

            /// <summary>
            /// Gets the edited bytes after the OK button is clicked on the plugin dialog.
            /// </summary>
            public byte[] GetNewValue()
            {
                return messageEditorControl.EditByteArray;
            }

            private MessageEditorControl messageEditorControl;
            private object originalMessage;
        }
    ```

## <a name="build-and-deploy-the-plug-ins"></a>Сборка и развертывание подключаемых модулей

### <a name="to-build-and-deploy-the-resulting-dll-for-the-istringhttpbodyeditorplugin-and-ibinaryhttpbodyeditorplugin"></a>Построение и развертывание результирующей библиотеки DLL для интерфейсов IStringHttpBodyEditorPlugin и IBinaryHttpBodyEditorPlugin

1.  В меню **Сборка** выберите пункт **Сборка \<имя проекта библиотеки элементов управления Windows Form>**.

2.  Закройте все экземпляры Visual Studio.

    > [!NOTE]
    > Закрытие Visual Studio гарантирует, что файл *DLL* не будет заблокирован, когда вы попытаетесь его скопировать.

3.  Скопируйте итоговый файл *DLL* (например, *MessageEditors.dll*) из папки *bin\debug* соответствующего проекта в папку *%ProgramFiles%\Microsoft Visual Studio\2017\\<edition>\Common7\IDE\PrivateAssemblies\WebTestPlugins*.

4.  Запустите Visual Studio.

     Теперь файл *DLL* регистрируется в Visual Studio.

## <a name="verify-the-plug-ins-using-a-web-performance-test"></a>Проверка подключаемых модулей с помощью веб-теста производительности

### <a name="to-test-your-plug-ins"></a>Тестирование подключаемых модулей

1.  Создайте тестовый проект.

2.  Создайте веб-тест производительности и введите в браузере URL-адрес для веб-службы.

3.  По завершении записи в редакторе веб-тестов производительности разверните запрос веб-службы и выберите узел **Текст строки** или **Двоичный основной текст**.

4.  В окне "Свойства" выберите пункт "Текст строки" или "Двоичный основной текст" и нажмите кнопку с многоточием **(…)**.

     Откроется диалоговое окно **Изменение данных основного текста HTTP**.

5.  Теперь можно изменить данные и нажать кнопку **ОК**. При этом вызывается метод GetNewValue для обновления содержимого в интерфейсе <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>.

## <a name="compile-the-code"></a>Компиляция кода

Убедитесь, что требуемая версия платформы .NET Framework в проекте библиотеки элементов управления Windows — .NET Framework 4.5. По умолчанию проекты библиотеки элементов управления Windows используют клиентскую платформу .NET Framework 4.5, которая не позволит включить ссылку на Microsoft.VisualStudio.QualityTools.WebTestFramework.

Дополнительные сведения см. в статье [Страница "Приложение" в конструкторе проектов (C#)](../ide/reference/application-page-project-designer-csharp.md).

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.RichTextBox>
- [Создание пользовательского кода и подключаемых модулей для нагрузочных тестов](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Практическое руководство. Создание подключаемого модуля уровня запроса](../test/how-to-create-a-request-level-plug-in.md)
- [Кодирование пользовательского правила извлечения для веб-теста производительности](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Кодирование пользовательского правила проверки для веб-теста производительности](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Практическое руководство. Создание подключаемого модуля нагрузочных тестов](../test/how-to-create-a-load-test-plug-in.md)
- [Создание и запуск закодированного веб-теста производительности](../test/generate-and-run-a-coded-web-performance-test.md)
- [Практическое руководство. Создание надстройки Visual Studio для средства просмотра результатов веб-тестов производительности](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)