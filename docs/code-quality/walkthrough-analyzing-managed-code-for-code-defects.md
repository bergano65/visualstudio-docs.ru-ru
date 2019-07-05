---
title: Пошаговое руководство Проверка управляемого кода на наличие дефектов кода | Документация Майкрософт
ms.date: 01/29/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis [Visual Studio]
- managed code, analyzing
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3a2ce9b719f77377abf5b2bebd81b03a2606258b
ms.sourcegitcommit: fd5a5b057df3d733f5224c305096907989811f85
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2019
ms.locfileid: "67195294"
---
# <a name="walkthrough-use-static-code-analysis-to-find-code-defects"></a>Пошаговое руководство. Используйте статический анализ кода для поиска дефектов кода

В этом пошаговом руководстве будет анализировать управляемого проекта для дефектов кода с помощью средства анализа кода.

В этом пошаговом руководстве представлены шаги по с помощью функций анализа статического кода для анализа вашей сборок управляемого кода .NET на соответствие рекомендациям по .NET.

## <a name="create-a-class-library"></a>Создание библиотеки классов

### <a name="to-create-a-class-library"></a>Чтобы создать библиотеку классов

1. В меню **Файл** последовательно выберите пункты **Создать** > **Проект**.

1. В **новый проект** диалоговое окно последовательно раскройте элементы **установленные** > **Visual C#** , а затем выберите **Windows Desktop**.

1. Выберите **библиотека классов (.NET Framework)** шаблона.

1. В **имя** текстовое поле, тип **CodeAnalysisManagedDemo** и нажмите кнопку **ОК**.

1. После создания проекта, откройте *Class1.cs* файл.

1. Замените существующий текст в файл Class1.cs следующим кодом:

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

### <a name="to-analyze-a-managed-project-for-code-defects"></a>Анализ управляемого проекта для дефектов кода

1. Выберите проект CodeAnalysisManagedDemo в **обозревателе решений**.

1. В меню **Проект** выберите пункт **Свойства**.

     Откроется страница свойств CodeAnalysisManagedDemo.

1. Выберите **анализа кода** вкладки.

1. Убедитесь, что **включить анализ кода в построении** проверяется.

1. Из **выполнить этот набор правил** стрелку раскрывающегося списка выберите **все правила Майкрософт**.

1. На **файл** меню, щелкните **сохранить выбранные элементы**, а затем закройте страницы свойств.

1. На **построения** меню, щелкните **построения CodeAnalysisManagedDemo**.

    Предупреждения построения проекта CodeAnalysisManagedDemo отображаются в **список ошибок** и **вывода** windows.

## <a name="correct-the-code-analysis-issues"></a>Исправьте проблемы анализа кода

### <a name="to-correct-code-analysis-rule-violations"></a>Для устранения нарушений правил анализа кода

1. На **представление** меню, выберите **список ошибок**.

    В зависимости от выбранного профиля разработчика, возможно, чтобы они указывали **Other Windows** на **представление** меню, а затем выберите **список ошибок**.

1. В **обозревателе решений** выберите **Показать все файлы**.

1. Разверните узел свойства, а затем откройте *AssemblyInfo.cs* файл.

1. Следуйте приведенным ниже советам, чтобы устранить предупреждения:

   [CA1014: Помечайте сборки атрибутом CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft.Design: «demo» должен быть помечен атрибутом CLSCompliantAttribute и его значение должно быть true.

   1. Добавьте код `using System;` в файл AssemblyInfo.cs.

   1. Далее добавьте код `[assembly: CLSCompliant(true)]` в конец файл AssemblyInfo.cs.

   [CA1032: Реализуйте стандартные конструкторы исключения](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Добавьте следующий конструктор этого класса: открытый demo(String)

   1. Добавьте конструктор `public demo (String s) : base(s) { }` к классу `demo`.

   [CA1032: Реализуйте стандартные конструкторы исключения](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Добавьте следующий конструктор этого класса: открытый demo (String, исключений)

   1. Добавьте конструктор `public demo (String s, Exception e) : base(s, e) { }` к классу `demo`.

   [CA1032: Реализуйте стандартные конструкторы исключения](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Добавьте следующий конструктор этого класса: защищенные demo (SerializationInfo, StreamingContext)

   1. Добавьте код `using System.Runtime.Serialization;` в начало файла Class1.cs.

   1. Добавьте конструктор `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

   [CA1032: Реализуйте стандартные конструкторы исключения](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Добавьте следующий конструктор этого класса: открытый demo()

   1. Добавьте конструктор `public demo () : base() { }` к классу `demo` **.**

   [CA1709: Идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Исправьте прописные или строчные буквы имени пространства имен «testCode», изменив ее на «TestCode».

   1. Регистр пространства имен `testCode` для `TestCode`.

   [CA1709: Идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Исправьте прописные или строчные буквы имени типа «demo», изменив ее на «Demo».

   1. Измените имя элемента, на который `Demo`.

   [CA1709: Идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Исправьте прописные или строчные буквы имени член «item», изменив ее на «Item».

   1. Измените имя элемента, на который `Item`.

   [CA1710: Идентификаторы должны иметь правильные суффиксы](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft.Naming: Переименуйте «testCode.demo» конец «Исключение».

   1. Измените имя класса и его конструкторов для `DemoException`.

   [CA2210: Сборки должны иметь допустимые строгие имена](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): Подпись «CodeAnalysisManagedDemo» с ключом строгого имени.

   1. На **проекта** меню, выберите **CodeAnalysisManagedDemo свойства**.

      Отображаются свойства проекта.

   1. Перейдите на вкладку **Подписывание** .

   1. Выберите **подписать сборку** "флажок".

   1. В **выберите файл ключа строгого имени** выберите  **\<создать... >** .

      **Создание ключа строгого имени** откроется диалоговое окно.

   1. В **имя файла ключа**, введите TestKey.

   1. Введите пароль, а затем выберите **ОК**.

   1. На **файл** меню, выберите **сохранить выбранные элементы**, а затем закройте окно свойств.

   [CA2237. Пометьте типы ISerializable атрибутом SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage: Добавьте атрибут [Serializable] к типу «demo», так как этот тип реализует ISerializable.

   1. Добавить `[Serializable ()]` классу атрибут `demo`.

   После внесения изменений файл Class1.cs должен выглядеть следующим образом:

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

1. Для каждой из оставшихся предупреждения сделайте следующее:

    1. Выберите предупреждение в **список ошибок**.

    1. В контекстном меню (контекстного меню) выберите **подавлять** > **в файле блокируемых предупреждений**.

1. Перестройте проект.

     Сборка проекта выполняется без предупреждения или ошибки.

## <a name="see-also"></a>См. также

[Анализ кода для управляемого кода](../code-quality/code-analysis-for-managed-code-overview.md)