---
title: Пошаговое руководство анализ управляемого кода на наличие дефектов кода | Документы Microsoft
ms.date: 01/29/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis [Visual Studio]
- managed code, analyzing
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 98d1bbd347870bd704a0d17d7ae559da00e9adb5
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>Пошаговое руководство: Анализ управляемого кода для кода ошибки

В этом пошаговом руководстве будет проанализирован управляемого проекта на наличие дефектов кода с помощью средства анализа кода.

В этом пошаговом руководстве этапы процесса с помощью анализа кода для анализа вашей сборок управляемого кода .NET на соответствие с рекомендации по разработке Microsoft .NET Framework.

## <a name="create-a-class-library"></a>Создание библиотеки классов

### <a name="to-create-a-class-library"></a>Для создания библиотеки классов

1. В меню **Файл** последовательно выберите пункты **Создать** > **Проект**.

1. В **новый проект** диалогового окна разверните **установленные** > **Visual C#** и нажмите кнопку **классического Windows**.

1. Выберите **библиотека классов (.NET Framework)** шаблона.

1. В **имя** введите **CodeAnalysisManagedDemo** и нажмите кнопку **ОК**.

1. После создания проекта откройте *Class1.cs* файла.

1. Замените существующий текст в файле Class1.cs следующий код:

   ```csharp
   using System;

   namespace testCode
   {
       public class demo : Exception
       {
           public static void Initialize(int size) { }
           protected static readonly int _item;
           public static int item { get { return _item; } }
       }
   }
   ```

1. Сохраните файл Class1.cs.

## <a name="analyze-the-project"></a>Анализ проекта

### <a name="to-analyze-a-managed-project-for-code-defects"></a>Анализ управляемого проекта для дефекта кода

1. Выберите проект в CodeAnalysisManagedDemo **обозревателе решений**.

1. В меню **Проект** выберите пункт **Свойства**.

     Откроется страница свойств CodeAnalysisManagedDemo.

1. Выберите **анализа кода** вкладки.

1. Убедитесь, что **включить анализ кода в построении** проверяется.

1. Из **выполнить этот набор правил** раскрывающемся списке выберите **все правила Майкрософт**.

1. На **файл** меню, нажмите кнопку **сохранить выбранные элементы**, а затем закройте страницы свойств.

1. На **построения** меню, нажмите кнопку **построения CodeAnalysisManagedDemo**.

    Предупреждения при построении проекта CodeAnalysisManagedDemo отображаются в **список ошибок** и **вывода** windows.

## <a name="correct-the-code-analysis-issues"></a>Исправьте проблемы анализа кода

### <a name="to-correct-code-analysis-rule-violations"></a>Для устранения нарушения правил анализа кода

1. На **представление** меню, выберите **список ошибок**.

    В зависимости от выбранного профиля разработчика, возможно, чтобы она указывала на **другие окна** на **представление** меню, а затем выберите **список ошибок**.

1. В **обозревателе решений**, выберите **Показать все файлы**.

1. Разверните узел свойства, а затем откройте *AssemblyInfo.cs* файла.

1. Следуйте приведенным ниже советам, чтобы устранить предупреждения:

   [CA1014: Помечайте сборки атрибутом CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft.Design: «demo» должен быть помечен атрибутом CLSCompliantAttribute и его значение должно быть true.

   1. Добавьте код `using System;` файл AssemblyInfo.cs.

   1. Добавьте следующий код `[assembly: CLSCompliant(true)]` файл AssemblyInfo.cs в конец.

   [CA1032: Реализуйте стандартные конструкторы исключения](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: добавьте следующий конструктор этого класса: открытого demo(String)

   1. Добавьте конструктор `public demo (String s) : base(s) { }` к классу `demo`.

   [CA1032: Реализуйте стандартные конструкторы исключения](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: добавьте следующий конструктор этого класса: демонстрация открытые (String, исключение)

   1. Добавьте конструктор `public demo (String s, Exception e) : base(s, e) { }` к классу `demo`.

   [CA1032: Реализуйте стандартные конструкторы исключения](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: добавьте следующий конструктор этого класса: защищенные Демонстрация (SerializationInfo, StreamingContext)

   1. Добавьте код `using System.Runtime.Serialization;` в начало файла Class1.cs.

   1. Добавьте конструктор `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

   [CA1032: Реализуйте стандартные конструкторы исключения](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: добавьте следующий конструктор этого класса: открытого demo()

   1. Добавьте конструктор `public demo () : base() { }` к классу `demo` **.**

   [CA1709: Идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: исправьте регистр имени пространства имен «testCode», изменив ее «TestCode».

   1. Изменить регистр пространства имен `testCode` для `TestCode`.

   [CA1709: Идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: исправьте регистр имени типа «demo», изменив ее «Demo».

   1. Измените имя члена `Demo`.

   [CA1709: Идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: исправьте регистр имени члена «item», изменив ее «Item».

   1. Измените имя члена `Item`.

   [CA1710: Идентификаторы должны иметь правильные суффиксы](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft.Naming: переименование «testCode.demo» завершить «Исключения».

   1. Измените имя класса и его конструкторов на `DemoException`.

   [CA2210: Сборки должны иметь допустимые строгие имена](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): подпись «CodeAnalysisManagedDemo» с ключом строгого имени.

   1. На **проекта** меню, выберите **CodeAnalysisManagedDemo свойства**.

      Будут отображены свойства проекта.

   1. Перейдите на вкладку **Подписывание** .

   1. Выберите **подписать сборку** флажок.

   1. В **выберите файл ключа строгого имени** выберите  **\<создать... >**.

      **Создание ключа строгого имени** откроется диалоговое окно.

   1. В **имя файла ключа**, введите TestKey.

   1. Введите пароль и нажмите кнопку **ОК**.

   1. На **файл** меню, выберите **сохранить выбранные элементы**, а затем закройте страницы свойств.

   [CA2237: Пометьте типы ISerializable атрибутом SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage: добавить атрибут [Serializable] в тип «demo», что этот тип реализует интерфейс ISerializable.

   1. Добавить `[Serializable ()]` к классу атрибут `demo`.

   После завершения изменения файл Class1.cs должен выглядеть следующим образом:

   ```csharp
   using System;
   using System.Runtime.Serialization;

   namespace TestCode
   {
       [Serializable()]
       public class DemoException : Exception
       {
           public DemoException () : base() { }
           public DemoException(String s) : base(s) { }
           public DemoException(String s, Exception e) : base(s, e) { }
           protected DemoException(SerializationInfo info, StreamingContext context) : base(info, context) { }

           public static void Initialize(int size) { }
           protected static readonly int _item;
           public static int Item { get { return _item; } }
       }
   }
   ```

1. Перестройте проект.

## <a name="exclude-code-analysis-warnings"></a>Исключение предупреждений анализа кода

### <a name="to-exclude-code-defect-warnings"></a>Для исключения предупреждений о дефектах кода

1. Для каждого из оставшихся предупреждений выполните следующее:

    1. Выберите предупреждение в **список ошибок**.

    1. Щелкните правой кнопкой мыши или команду контекстного меню, выберите **подавлять** > **в файле блокируемых предупреждений**.

1. Перестройте проект.

     Сборка проекта выполняется без предупреждения или ошибки.

## <a name="see-also"></a>См. также

[Анализ кода для управляемого кода](../code-quality/code-analysis-for-managed-code-overview.md)