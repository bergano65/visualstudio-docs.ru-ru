---
title: Пошаговое руководство. Создание пользовательского обработчика директив
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
- walkthroughs [text templates], directive processor
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
dev_langs:
- CSharp
- VB
ms.openlocfilehash: e0ee905cf4ddaec6a05d5c0722b80c345489acd2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31979039"
---
# <a name="walkthrough-create-a-custom-directive-processor"></a>Пошаговое руководство: Создание пользовательского процессора директив

*Процессоры директив* работают путем добавления кода в *генерируемый класс преобразования*. При вызове метода *директивы* из *текстового шаблона*, остальной код, записанный в текстовый шаблон можно использовать предоставленную директивой функциональность.

Можно написать собственные пользовательские процессоры директив. Это позволяет настраивать текстовые шаблоны. Для создания пользовательского процессора директив создается класс, наследующий <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> либо <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

В данном пошаговом руководстве иллюстрируется выполнение следующих задач.

- Создание пользовательского процессора директив

- Регистрация процессора директив

- Тестирование процессора директив

## <a name="create-a-custom-directive-processor"></a>Создание пользовательского процессора директив

В данном пошаговом руководстве вы создадите пользовательский процессор директив. Вы добавите пользовательскую директиву, которая считывает XML-файл, сохраняет его в переменной <xref:System.Xml.XmlDocument> и предоставляет доступ к нему через свойство. В разделе "Тестирование процессора директив" вы используете это свойство в текстовом шаблоне для доступа к XML-файлу.

Вызов пользовательской директивы выглядит так:

`<#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<Your Path>DocFile.xml" #>`

Пользовательский процессор директив добавляет переменную и свойство к сгенерированному классу преобразования. Директива, которую вы пишете, использует классы <xref:System.CodeDom> для создания кода, который процессор добавляет в сгенерированный класс преобразования. <xref:System.CodeDom> Классы создания кода в Visual C# или Visual Basic, в зависимости от языка, заданного параметром `language` параметр `template` директивы. Язык процессора директив и язык текстового шаблона, осуществляющего доступ к этому процессору, не обязательно должен совпадать.

Создаваемый этой директивой код выглядит так:

```csharp
private System.Xml.XmlDocument document0Value;

public virtual System.Xml.XmlDocument Document0
{
  get
  {
    if ((this.document0Value == null))
    {
      this.document0Value = XmlReaderHelper.ReadXml(<FileNameParameterValue>);
    }
    return this.document0Value;
  }
}
```

```vb
Private document0Value As System.Xml.XmlDocument

Public Overridable ReadOnly Property Document0() As System.Xml.XmlDocument
    Get
        If (Me.document0Value Is Nothing) Then
            Me.document0Value = XmlReaderHelper.ReadXml(<FileNameParameterValue>)
        End If
        Return Me.document0Value
    End Get
End Property
```

### <a name="to-create-a-custom-directive-processor"></a>Создание пользовательского процессора директив

1. В среде Visual Studio создайте проект библиотеки классов C# или Visual Basic с именем CustomDP.

    > [!NOTE]
    > Если требуется установить процессор директив на более чем один компьютер, лучше использовать проект расширения Visual Studio (VSIX) и включать в расширение pkgdef-файл. Дополнительные сведения см. в разделе [развертывание пользовательского процессора директив](../modeling/deploying-a-custom-directive-processor.md).

2. Добавьте ссылки на следующие сборки:

    - **Microsoft.VisualStudio.TextTemplating.\*.0**

    - **Microsoft.VisualStudio.TextTemplating.Interfaces. \*.0**

3. Замените код в **Class1** следующим кодом. Этот код определяет класс CustomDirectiveProcessor, наследующий класс <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> и реализующий необходимые методы.

    ```csharp
    using System;
    using System.CodeDom;
    using System.CodeDom.Compiler;
    using System.Collections.Generic;
    using System.Globalization;
    using System.IO;
    using System.Text;
    using System.Xml;
    using System.Xml.Serialization;
    using Microsoft.VisualStudio.TextTemplating;

    namespace CustomDP
    {
        public class CustomDirectiveProcessor : DirectiveProcessor
        {
            // This buffer stores the code that is added to the
            // generated transformation class after all the processing is done.
            // ---------------------------------------------------------------------
            private StringBuilder codeBuffer;

            // Using a Code Dom Provider creates code for the
            // generated transformation class in either Visual Basic or C#.
            // If you want your directive processor to support only one language, you
            // can hard code the code you add to the generated transformation class.
            // In that case, you do not need this field.
            // --------------------------------------------------------------------------
            private CodeDomProvider codeDomProvider;

            // This stores the full contents of the text template that is being processed.
            // --------------------------------------------------------------------------
            private String templateContents;

            // These are the errors that occur during processing. The engine passes
            // the errors to the host, and the host can decide how to display them,
            // for example the the host can display the errors in the UI
            // or write them to a file.
            // ---------------------------------------------------------------------
            private CompilerErrorCollection errorsValue;
            public new CompilerErrorCollection Errors
            {
                get { return errorsValue; }
            }

            // Each time this directive processor is called, it creates a new property.
            // We count how many times we are called, and append "n" to each new
            // property name. The property names are therefore unique.
            // -----------------------------------------------------------------------------
            private int directiveCount = 0;

            public override void Initialize(ITextTemplatingEngineHost host)
            {
                // We do not need to do any initialization work.
            }

            public override void StartProcessingRun(CodeDomProvider languageProvider, String templateContents, CompilerErrorCollection errors)
            {
                // The engine has passed us the language of the text template
                // we will use that language to generate code later.
                // ----------------------------------------------------------
                this.codeDomProvider = languageProvider;
                this.templateContents = templateContents;
                this.errorsValue = errors;

                this.codeBuffer = new StringBuilder();
            }

            // Before calling the ProcessDirective method for a directive, the
            // engine calls this function to see whether the directive is supported.
            // Notice that one directive processor might support many directives.
            // ---------------------------------------------------------------------
            public override bool IsDirectiveSupported(string directiveName)
            {
                if (string.Compare(directiveName, "CoolDirective", StringComparison.OrdinalIgnoreCase) == 0)
                {
                    return true;
                }
                if (string.Compare(directiveName, "SuperCoolDirective", StringComparison.OrdinalIgnoreCase) == 0)
                {
                    return true;
                }
                return false;
            }

            public override void ProcessDirective(string directiveName, IDictionary<string, string> arguments)
            {
                if (string.Compare(directiveName, "CoolDirective", StringComparison.OrdinalIgnoreCase) == 0)
                {
                    string fileName;

                    if (!arguments.TryGetValue("FileName", out fileName))
                    {
                        throw new DirectiveProcessorException("Required argument 'FileName' not specified.");
                    }

                    if (string.IsNullOrEmpty(fileName))
                    {
                        throw new DirectiveProcessorException("Argument 'FileName' is null or empty.");
                    }

                    // Now we add code to the generated transformation class.
                    // This directive supports either Visual Basic or C#, so we must use the
                    // System.CodeDom to create the code.
                    // If a directive supports only one language, you can hard code the code.
                    // --------------------------------------------------------------------------

                    CodeMemberField documentField = new CodeMemberField();

                    documentField.Name = "document" + directiveCount + "Value";
                    documentField.Type = new CodeTypeReference(typeof(XmlDocument));
                    documentField.Attributes = MemberAttributes.Private;

                    CodeMemberProperty documentProperty = new CodeMemberProperty();

                    documentProperty.Name = "Document" + directiveCount;
                    documentProperty.Type = new CodeTypeReference(typeof(XmlDocument));
                    documentProperty.Attributes = MemberAttributes.Public;
                    documentProperty.HasSet = false;
                    documentProperty.HasGet = true;

                    CodeExpression fieldName = new CodeFieldReferenceExpression(new CodeThisReferenceExpression(), documentField.Name);
                    CodeExpression booleanTest = new CodeBinaryOperatorExpression(fieldName, CodeBinaryOperatorType.IdentityEquality, new CodePrimitiveExpression(null));
                    CodeExpression rightSide = new CodeMethodInvokeExpression(new CodeTypeReferenceExpression("XmlReaderHelper"), "ReadXml", new CodePrimitiveExpression(fileName));
                    CodeStatement[] thenSteps = new CodeStatement[] { new CodeAssignStatement(fieldName, rightSide) };

                    CodeConditionStatement ifThen = new CodeConditionStatement(booleanTest, thenSteps);
                    documentProperty.GetStatements.Add(ifThen);

                    CodeStatement s = new CodeMethodReturnStatement(fieldName);
                    documentProperty.GetStatements.Add(s);

                    CodeGeneratorOptions options = new CodeGeneratorOptions();
                    options.BlankLinesBetweenMembers = true;
                    options.IndentString = "    ";
                    options.VerbatimOrder = true;
                    options.BracingStyle = "C";

                    using (StringWriter writer = new StringWriter(codeBuffer, CultureInfo.InvariantCulture))
                    {
                        codeDomProvider.GenerateCodeFromMember(documentField, writer, options);
                        codeDomProvider.GenerateCodeFromMember(documentProperty, writer, options);
                    }
                }

                // One directive processor can contain many directives.
                // If you want to support more directives, the code goes here...
                // -----------------------------------------------------------------
                if (string.Compare(directiveName, "supercooldirective", StringComparison.OrdinalIgnoreCase) == 0)
                {
                    // Code for SuperCoolDirective goes here...
                }

                // Track how many times the processor has been called.
                // -----------------------------------------------------------------
                directiveCount++;

            }

            public override void FinishProcessingRun()
            {
                this.codeDomProvider = null;

                // Important: do not do this:
                // The get methods below are called after this method
                // and the get methods can access this field.
                // -----------------------------------------------------------------
                // this.codeBuffer = null;
            }

            public override string GetPreInitializationCodeForProcessingRun()
            {
                // Use this method to add code to the start of the
                // Initialize() method of the generated transformation class.
                // We do not need any pre-initialization, so we will just return "".
                // -----------------------------------------------------------------
                // GetPreInitializationCodeForProcessingRun runs before the
                // Initialize() method of the base class.
                // -----------------------------------------------------------------
                return String.Empty;
            }

            public override string GetPostInitializationCodeForProcessingRun()
            {
                // Use this method to add code to the end of the
                // Initialize() method of the generated transformation class.
                // We do not need any post-initialization, so we will just return "".
                // ------------------------------------------------------------------
                // GetPostInitializationCodeForProcessingRun runs after the
                // Initialize() method of the base class.
                // -----------------------------------------------------------------
                return String.Empty;
            }

            public override string GetClassCodeForProcessingRun()
            {
                //Return the code to add to the generated transformation class.
                // -----------------------------------------------------------------
                return codeBuffer.ToString();
            }

            public override string[] GetReferencesForProcessingRun()
            {
                // This returns the references that we want to use when
                // compiling the generated transformation class.
                // -----------------------------------------------------------------
                // We need a reference to this assembly to be able to call
                // XmlReaderHelper.ReadXml from the generated transformation class.
                // -----------------------------------------------------------------
                return new string[]
                {
                    "System.Xml",
                    this.GetType().Assembly.Location
                };
            }

            public override string[] GetImportsForProcessingRun()
            {
                //This returns the imports or using statements that we want to
                //add to the generated transformation class.
                // -----------------------------------------------------------------
                //We need CustomDP to be able to call XmlReaderHelper.ReadXml
                //from the generated transformation class.
                // -----------------------------------------------------------------
                return new string[]
                {
                    "System.Xml",
                    "CustomDP"
                };
            }
        }

        // -------------------------------------------------------------------------
        // The code that we are adding to the generated transformation class
        // will call this method.
        // -------------------------------------------------------------------------
        public static class XmlReaderHelper
        {
            public static XmlDocument ReadXml(string fileName)
            {
                XmlDocument d = new XmlDocument();

                using (XmlTextReader reader = new XmlTextReader(fileName))
                {
                    try
                    {
                        d.Load(reader);
                    }
                    catch (System.Xml.XmlException e)
                    {
                        throw new DirectiveProcessorException("Unable to read the XML file.", e);
                    }
                }
                return d;
            }
        }
    }
    ```

    ```vb
    Imports System
    Imports System.CodeDom
    Imports System.CodeDom.Compiler
    Imports System.Collections.Generic
    Imports System.Globalization
    Imports System.IO
    Imports System.Text
    Imports System.Xml
    Imports System.Xml.Serialization
    Imports Microsoft.VisualStudio.TextTemplating

    Namespace CustomDP

        Public Class CustomDirectiveProcessor
        Inherits DirectiveProcessor

            ' This buffer stores the code that is added to the
            ' generated transformation class after all the processing is done.
            ' ---------------------------------------------------------------
            Private codeBuffer As StringBuilder

            ' Using a Code Dom Provider creates code for the
            ' generated transformation class in either Visual Basic or C#.
            ' If you want your directive processor to support only one language, you
            ' can hard code the code you add to the generated transformation class.
            ' In that case, you do not need this field.
            ' --------------------------------------------------------------------------
            Private codeDomProvider As CodeDomProvider

            ' This stores the full contents of the text template that is being processed.
            ' --------------------------------------------------------------------------
            Private templateContents As String

            ' These are the errors that occur during processing. The engine passes
            ' the errors to the host, and the host can decide how to display them,
            ' for example the the host can display the errors in the UI
            ' or write them to a file.
            ' ---------------------------------------------------------------------
            Private errorsValue As CompilerErrorCollection
            Public Shadows ReadOnly Property Errors() As CompilerErrorCollection
                Get
                    Return errorsValue
                End Get
            End Property

            ' Each time this directive processor is called, it creates a new property.
            ' We count how many times we are called, and append "n" to each new
            ' property name. The property names are therefore unique.
            ' --------------------------------------------------------------------------
            Private directiveCount As Integer = 0

            Public Overrides Sub Initialize(ByVal host As ITextTemplatingEngineHost)

                ' We do not need to do any initialization work.
            End Sub

            Public Overrides Sub StartProcessingRun(ByVal languageProvider As CodeDomProvider, ByVal templateContents As String, ByVal errors As CompilerErrorCollection)

                ' The engine has passed us the language of the text template
                ' we will use that language to generate code later.
                ' ----------------------------------------------------------
                Me.codeDomProvider = languageProvider
                Me.templateContents = templateContents
                Me.errorsValue = errors

                Me.codeBuffer = New StringBuilder()
            End Sub

            ' Before calling the ProcessDirective method for a directive, the
            ' engine calls this function to see whether the directive is supported.
            ' Notice that one directive processor might support many directives.
            ' ---------------------------------------------------------------------
            Public Overrides Function IsDirectiveSupported(ByVal directiveName As String) As Boolean

                If String.Compare(directiveName, "CoolDirective", StringComparison.OrdinalIgnoreCase) = 0 Then
                    Return True
                End If

                If String.Compare(directiveName, "SuperCoolDirective", StringComparison.OrdinalIgnoreCase) = 0 Then
                    Return True
                End If

                Return False
            End Function

            Public Overrides Sub ProcessDirective(ByVal directiveName As String, ByVal arguments As IDictionary(Of String, String))

                If String.Compare(directiveName, "CoolDirective", StringComparison.OrdinalIgnoreCase) = 0 Then

                    Dim fileName As String

                    If Not (arguments.TryGetValue("FileName", fileName)) Then
                        Throw New DirectiveProcessorException("Required argument 'FileName' not specified.")
                    End If

                    If String.IsNullOrEmpty(fileName) Then
                        Throw New DirectiveProcessorException("Argument 'FileName' is null or empty.")
                    End If

                    ' Now we add code to the generated transformation class.
                    ' This directive supports either Visual Basic or C#, so we must use the
                    ' System.CodeDom to create the code.
                    ' If a directive supports only one language, you can hard code the code.
                    ' --------------------------------------------------------------------------

                    Dim documentField As CodeMemberField = New CodeMemberField()

                    documentField.Name = "document" & directiveCount & "Value"
                    documentField.Type = New CodeTypeReference(GetType(XmlDocument))
                    documentField.Attributes = MemberAttributes.Private

                    Dim documentProperty As CodeMemberProperty = New CodeMemberProperty()

                    documentProperty.Name = "Document" & directiveCount
                    documentProperty.Type = New CodeTypeReference(GetType(XmlDocument))
                    documentProperty.Attributes = MemberAttributes.Public
                    documentProperty.HasSet = False
                    documentProperty.HasGet = True

                    Dim fieldName As CodeExpression = New CodeFieldReferenceExpression(New CodeThisReferenceExpression(), documentField.Name)
                    Dim booleanTest As CodeExpression = New CodeBinaryOperatorExpression(fieldName, CodeBinaryOperatorType.IdentityEquality, New CodePrimitiveExpression(Nothing))
                    Dim rightSide As CodeExpression = New CodeMethodInvokeExpression(New CodeTypeReferenceExpression("XmlReaderHelper"), "ReadXml", New CodePrimitiveExpression(fileName))
                    Dim thenSteps As CodeStatement() = New CodeStatement() {New CodeAssignStatement(fieldName, rightSide)}

                    Dim ifThen As CodeConditionStatement = New CodeConditionStatement(booleanTest, thenSteps)
                    documentProperty.GetStatements.Add(ifThen)

                    Dim s As CodeStatement = New CodeMethodReturnStatement(fieldName)
                    documentProperty.GetStatements.Add(s)

                    Dim options As CodeGeneratorOptions = New CodeGeneratorOptions()
                    options.BlankLinesBetweenMembers = True
                    options.IndentString = "    "
                    options.VerbatimOrder = True
                    options.BracingStyle = "VB"

                    Using writer As StringWriter = New StringWriter(codeBuffer, CultureInfo.InvariantCulture)

                        codeDomProvider.GenerateCodeFromMember(documentField, writer, options)
                        codeDomProvider.GenerateCodeFromMember(documentProperty, writer, options)
                    End Using

                End If

                ' One directive processor can contain many directives.
                ' If you want to support more directives, the code goes here...
                ' -----------------------------------------------------------------
                If String.Compare(directiveName, "supercooldirective", StringComparison.OrdinalIgnoreCase) = 0 Then

                    ' Code for SuperCoolDirective goes here.
                End If

                ' Track how many times the processor has been called.
                ' -----------------------------------------------------------------
                directiveCount += 1
            End Sub

            Public Overrides Sub FinishProcessingRun()

                Me.codeDomProvider = Nothing

                ' Important: do not do this:
                ' The get methods below are called after this method
                ' and the get methods can access this field.
                ' -----------------------------------------------------------------
                ' Me.codeBuffer = Nothing
            End Sub

            Public Overrides Function GetPreInitializationCodeForProcessingRun() As String

                ' Use this method to add code to the start of the
                ' Initialize() method of the generated transformation class.
                ' We do not need any pre-initialization, so we will just return "".
                ' -----------------------------------------------------------------
                ' GetPreInitializationCodeForProcessingRun runs before the
                ' Initialize() method of the base class.
                ' -----------------------------------------------------------------
                Return String.Empty
            End Function

            Public Overrides Function GetPostInitializationCodeForProcessingRun() As String

                ' Use this method to add code to the end of the
                ' Initialize() method of the generated transformation class.
                ' We do not need any post-initialization, so we will just return "".
                ' ------------------------------------------------------------------
                ' GetPostInitializationCodeForProcessingRun runs after the
                ' Initialize() method of the base class.
                ' -----------------------------------------------------------------
                Return String.Empty
            End Function

            Public Overrides Function GetClassCodeForProcessingRun() As String

                ' Return the code to add to the generated transformation class.
                ' -----------------------------------------------------------------
                Return codeBuffer.ToString()
            End Function

            Public Overrides Function GetReferencesForProcessingRun() As String()

                ' This returns the references that we want to use when
                ' compiling the generated transformation class.
                ' -----------------------------------------------------------------
                ' We need a reference to this assembly to be able to call
                ' XmlReaderHelper.ReadXml from the generated transformation class.
                ' -----------------------------------------------------------------
                Return New String() {"System.Xml", Me.GetType().Assembly.Location}
            End Function

            Public Overrides Function GetImportsForProcessingRun() As String()

                ' This returns the imports or using statements that we want to
                ' add to the generated transformation class.
                ' -----------------------------------------------------------------
                ' We need CustomDP to be able to call XmlReaderHelper.ReadXml
                ' from the generated transformation class.
                ' -----------------------------------------------------------------
                Return New String() {"System.Xml", "CustomDP"}
            End Function
        End Class

        ' --------------------------------------------------------------------------
        ' The code that we are adding to the generated transformation class
        ' will call this method.
        ' --------------------------------------------------------------------------
        Public Class XmlReaderHelper

            Public Shared Function ReadXml(ByVal fileName As String) As XmlDocument

                Dim d As XmlDocument = New XmlDocument()

                Using reader As XmlTextReader = New XmlTextReader(fileName)

                    Try
                        d.Load(reader)

                    Catch e As System.Xml.XmlException

                        Throw New DirectiveProcessorException("Unable to read the XML file.", e)
                    End Try
                End Using

                Return d
            End Function
        End Class

    End Namespace
    ```

4. Visual Basic, откройте **проекта** меню и выберите пункт **Свойства CustomDP**. На **приложения** вкладке **корневое пространство имен**, удалите значение по умолчанию `CustomDP`.

5. На **файл** меню, нажмите кнопку **сохранить все**.

6. В меню **Сборка** выберите **Собрать решение**.

### <a name="build-the-project"></a>Постройте проект.

Выполните построение проекта. В меню **Сборка** выберите **Собрать решение**.

## <a name="register-the-directive-processor"></a>Регистрация процессора директив

Прежде чем директиву можно вызывать из текстового шаблона в Visual Studio, необходимо добавить раздел реестра для процессора директив.

> [!NOTE]
> Если требуется установить процессор директив на более чем один компьютер, лучше определить Visual Studio Extension (VSIX), включающий *.pkgdef* файл и вашу сборку. Дополнительные сведения см. в разделе [развертывание пользовательского процессора директив](../modeling/deploying-a-custom-directive-processor.md).

Разделы для процессора директив имеются в реестре в следующих местах:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\*.0\TextTemplating\DirectiveProcessors
```

Местоположение реестра в 64-разрядных системах:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VisualStudio\*.0\TextTemplating\DirectiveProcessors
```

Сейчас вы добавите раздел для вашего пользовательского процессора директив в реестр в то же самое место.

> [!CAUTION]
> Неправильное изменение реестра может серьезно повредить систему. Перед внесением изменений в реестр необходимо выполнить резервное копирование всех ценных данных на компьютере.

### <a name="to-add-a-registry-key-for-the-directive-processor"></a>Добавление раздела реестра для процессора директив

1. Запустите `regedit` команду с помощью меню «Пуск» или из командной строки.

2. Перейдите к нужному **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\\*.0\TextTemplating\DirectiveProcessors**и щелкните узел.

   На 64-разрядных систем с помощью **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VisualStudio\\\*.0\TextTemplating\DirectiveProcessors**

3. Добавьте новый раздел с именем CustomDirectiveProcessor.

    > [!NOTE]
    > Это имя, которое будет использоваться в поле Processor пользовательских директив. Это имя не обязательно должно соответствовать имени директивы, класса процессора директив или пространства имен процессора директив.

4. Добавьте новое строковое значение с именем Class и значением CustomDP.CustomDirectiveProcessor в качестве имени новой строки.

5. Добавьте новое строковое значение с именем CodeBase и значением, равным пути к файлу CustomDP.dll, созданному ранее в этом пошаговом руководстве.

     Например, путь может выглядеть `C:\UserFiles\CustomDP\bin\Debug\CustomDP.dll`.

     Ваш раздел реестра должен содержать следующие значения:

    |name|Тип|Данные|
    |----------|----------|----------|
    |(Значение по умолчанию)|REG_SZ|(значение не задано)|
    |Класс|REG_SZ|CustomDP.CustomDirectiveProcessor|
    |CodeBase|REG_SZ|**\<Путь к решению >** CustomDP\bin\Debug\CustomDP.dll|

     Если вы поместили сборку в глобальный кэш сборок, эти значения должны выглядеть так:

    |name|Тип|Данные|
    |----------|----------|----------|
    |(Значение по умолчанию)|REG_SZ|(значение не задано)|
    |Класс|REG_SZ|CustomDP.CustomDirectiveProcessor|
    |Assembly|REG_SZ|CustomDP.dll|

6. Перезапустите Visual Studio.

## <a name="test-the-directive-processor"></a>Тестирование процессора директив

Чтобы протестировать процессор директив, нужно написать вызывающий его текстовый шаблон.

В этом примере текстовый шаблон вызывает директиву и передает ей имя XML-файла, содержащего документацию для файла класса. Текстовый шаблон использует <xref:System.Xml.XmlDocument> свойство, создаваемое директивой для перемещения по XML и вывода комментариев документации.

### <a name="to-create-an-xml-file-for-use-in-testing-the-directive-processor"></a>Создание XML-файла для использования при тестировании процессора директив

1. Создайте файл с именем *DocFile.xml* , используя любой текстовый редактор (например, Блокнот).

    > [!NOTE]
    > Этот файл можно создать в любом месте (например, *C:\Test\DocFile.xml*).

2. Добавьте следующий XML-файл:

    ```xml
    <?xml version="1.0"?>
    <doc>
        <assembly>
            <name>xmlsample</name>
        </assembly>
        <members>
            <member name="T:SomeClass">
                <summary>Class level summary documentation goes here.</summary>
                <remarks>Longer comments can be associated with a type or member through the remarks tag</remarks>
            </member>
            <member name="F:SomeClass.m_Name">
                <summary>Store for the name property</summary>
            </member>
            <member name="M:SomeClass.#ctor">
                <summary>The class constructor.</summary>
            </member>
            <member name="M:SomeClass.SomeMethod(System.String)">
                <summary>Description for SomeMethod.</summary>
                <param name="s">Parameter description for s goes here</param>
                <seealso cref="T:System.String">You can use the cref attribute on any tag to reference a type or member and the compiler will check that the reference exists.</seealso>
            </member>
            <member name="M:SomeClass.SomeOtherMethod">
                <summary>Some other method.</summary>
                <returns>Return results are described through the returns tag.</returns>
                <seealso cref="M:SomeClass.SomeMethod(System.String)">Notice the use of the cref attribute to reference a specific method</seealso>
            </member>
            <member name="M:SomeClass.Main(System.String[])">
                <summary>The entry point for the application.</summary>
                <param name="args">A list of command line arguments</param>
            </member>
            <member name="P:SomeClass.Name">
                <summary>Name property</summary>
                <value>A value tag is used to describe the property value</value>
            </member>
        </members>
    </doc>
    ```

3. Сохраните и закройте файл.

### <a name="to-create-a-text-template-to-test-the-directive-processor"></a>Создание текстового шаблона для тестирования процессора директив

1. В среде Visual Studio создайте проект библиотеки классов C# или Visual Basic с именем TemplateTest.

2. Добавьте новый файл текстового шаблона с именем TestDP.tt.

3. Убедитесь, что **пользовательский инструмент** файла TestDP.tt свойству `TextTemplatingFileGenerator`.

4. Измените содержимое файла TestDP.tt следующим текстом.

    > [!NOTE]
    > Замените строку `<YOUR PATH>` с путем к *DocFile.xml* файла.

    Язык процессора директив и язык текстового шаблона не обязательно должны совпадать.

    ```csharp
    <#@ assembly name="System.Xml" #>
    <#@ template debug="true" #>
    <#@ output extension=".txt" #>

    <#  // This will call the custom directive processor. #>
    <#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFile.xml" #>

    <#  // Uncomment this line if you want to see the generated transformation class. #>
    <#  // System.Diagnostics.Debugger.Break(); #>

    <#  // This will use the results of the directive processor. #>
    <#  // The directive processor has read the XML and stored it in Document0. #>
    <#
        XmlNode node = Document0.DocumentElement.SelectSingleNode("members");

        foreach (XmlNode member in node.ChildNodes)
        {
            XmlNode name = member.Attributes.GetNamedItem("name");
            WriteLine("{0,7}:  {1}", "Name", name.Value);

            foreach (XmlNode comment in member.ChildNodes)
            {
                WriteLine("{0,7}:  {1}", comment.Name, comment.InnerText);
            }
            WriteLine("");
        }
    #>

    <# // You can call the directive processor again and pass it a different file. #>
    <# // @ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\<Your Second File>" #>

    <#  // To use the results of the second directive call, use Document1. #>
    <#
        // XmlNode node2 = Document1.DocumentElement.SelectSingleNode("members");

        // ...
    #>
    ```

    ```vb
    <#@ assembly name="System.Xml" #>
    <#@ template debug="true" language="vb" #>
    <#@ output extension=".txt" #>

    <#  ' This will call the custom directive processor. #>
    <#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFile.xml" #>

    <#  ' Uncomment this line if you want to see the generated transformation class. #>
    <#  ' System.Diagnostics.Debugger.Break() #>

    <#  ' This will use the results of the directive processor. #>
    <#  ' The directive processor has read the XML and stored it in Document0. #>
    <#
        Dim node as XmlNode = Document0.DocumentElement.SelectSingleNode("members")

        Dim member As XmlNode
        For Each member In node.ChildNodes

            Dim name As XmlNode = member.Attributes.GetNamedItem("name")
            WriteLine("{0,7}:  {1}", "Name", name.Value)

            Dim comment As XmlNode
            For Each comment In member.ChildNodes
                WriteLine("{0,7}:  {1}", comment.Name, comment.InnerText)
            Next

            WriteLine("")
        Next
    #>

    <# ' You can call the directive processor again and pass it a different file. #>
    <# ' @ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFileTwo.xml" #>

    <#  ' To use the results of the second directive call, use Document1. #>
    <#
        ' node = Document1.DocumentElement.SelectSingleNode("members")

        ' ...
    #>
    ```

    > [!NOTE]
    > В этом примере значением параметра `Processor` является `CustomDirectiveProcessor`. Значение параметра `Processor` должно соответствовать имени раздела реестра процессора.

5. На **файл** меню, выберите **сохранить все**.

### <a name="to-test-the-directive-processor"></a>Тестирование процессора директив

1. В **обозревателе решений**, щелкните файл TestDP.tt правой кнопкой мыши и выберите команду **запустить пользовательский инструмент**.

   Для пользователей Visual Basic TestDP.txt может не отображаться в **обозревателе решений** по умолчанию. Чтобы отобразить все файлы, назначенные проекту, откройте **проекта** меню и выберите пункт **Показать все файлы**.

2. В **обозревателе решений**, разверните узел TestDP.txt и дважды щелкните файл TestDP.txt, чтобы открыть его в редакторе.

    Отобразится сгенерированный текстовый вывод. Этот вывод должен выглядеть так:

    ```text
       Name:  T:SomeClass
    summary:  Class level summary documentation goes here.
    remarks:  Longer comments can be associated with a type or member through the remarks tag

       Name:  F:SomeClass.m_Name
    summary:  Store for the name property

       Name:  M:SomeClass.#ctor
    summary:  The class constructor.

       Name:  M:SomeClass.SomeMethod(System.String)
    summary:  Description for SomeMethod.
      param:  Parameter description for s goes here
    seealso:  You can use the cref attribute on any tag to reference a type or member and the compiler will check that the reference exists.

       Name:  M:SomeClass.SomeOtherMethod
    summary:  Some other method.
    returns:  Return results are described through the returns tag.
    seealso:  Notice the use of the cref attribute to reference a specific method

       Name:  M:SomeClass.Main(System.String[])
    summary:  The entry point for the application.
      param:  A list of command line arguments

       Name:  P:SomeClass.Name
    summary:  Name property
      value:  A value tag is used to describe the property value
    ```

## <a name="add-html-to-generated-text"></a>Добавление HTML в генерируемый текст

После тестирования пользовательского процессора директив вам может потребоваться добавить в генерируемый текст некоторый HTML-код.

### <a name="to-add-html-to-the-generated-text"></a>Добавление HTML в генерируемый текст

1. Замените код в *TestDP.tt* со следующими. Код HTML будет выделен. Убедитесь, что для замены строки `YOUR PATH` с путем к *DocFile.xml* файла.

    > [!NOTE]
    > Дополнительные открывающий \<# и закрывающий #> теги отделяют код оператора от тегов HTML.

    ```csharp
    <#@ assembly name="System.Xml" #>
    <#@ template debug="true" #>
    <#@ output extension=".htm" #>

    <#  // This will call the custom directive processor #>
    <#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFile.xml" #>

    <#  // Uncomment this line if you want to see the generated transformation class #>
    <#  // System.Diagnostics.Debugger.Break(); #>

    <html><body>

    <#  // This will use the results of the directive processor #>.
    <#  // The directive processor has read the XML and stored it in Document0#>.
    <#
        XmlNode node = Document0.DocumentElement.SelectSingleNode("members");

        foreach (XmlNode member in node.ChildNodes)
        {
    #>
    <h3>
    <#
            XmlNode name = member.Attributes.GetNamedItem("name");
            WriteLine("{0,7}:  {1}", "Name", name.Value);
    #>
    </h3>
    <#
            foreach (XmlNode comment in member.ChildNodes)
            {
                WriteLine("{0,7}:  {1}", comment.Name, comment.InnerText);
    #>
    <br/>
    <#
            }
        }
    #>
    </body></html>
    ```

    ```vb
    <#@ assembly name="System.Xml" #>
    <#@ template debug="true" language="vb" #>
    <#@ output extension=".htm" #>

    <#  ' This will call the custom directive processor #>
    <#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFile.xml" #>

    <#  ' Uncomment this line if you want to see the generated transformation class #>
    <#  ' System.Diagnostics.Debugger.Break() #>

    <html><body>

    <#  ' This will use the results of the directive processor #>.
    <#  ' The directive processor has read the XML and stored it in Document0#>.
    <#
        Dim node as XmlNode = Document0.DocumentElement.SelectSingleNode("members")

        Dim member As XmlNode
        For Each member In node.ChildNodes
    #>
    <h3>
    <#
            Dim name As XmlNode = member.Attributes.GetNamedItem("name")
            WriteLine("{0,7}:  {1}", "Name", name.Value)
    #>
    </h3>
    <#
            Dim comment As XmlNode
            For Each comment In member.ChildNodes
                WriteLine("{0,7}:  {1}", comment.Name, comment.InnerText)
    #>
    <br/>
    <#
            Next
        Next
    #>
    </body></html>
    ```

2. На **файл** меню, нажмите кнопку **Сохранить TestDP.txt**.

3. Чтобы просмотреть вывод в браузере, в **обозревателе решений**, щелкните файл TestDP.htm правой кнопкой мыши и выберите **просмотреть в браузере**.

   Выходными данными должен быть таким же, как исходный текст, отличаясь только наличием применением формата HTML. Имя каждого элемента будет выделен полужирным шрифтом.
