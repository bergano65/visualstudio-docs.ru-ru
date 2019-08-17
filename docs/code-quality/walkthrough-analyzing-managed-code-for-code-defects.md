---
title: Пошаговое руководство по анализу управляемого кода для дефектов кода | Документация Майкрософт
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
ms.openlocfilehash: 4a00fdb2a41a03554113f2ecb626185aab2c74d5
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547995"
---
# <a name="walkthrough-use-static-code-analysis-to-find-code-defects"></a>Пошаговое руководство. Использование статического анализа кода для поиска дефектов кода

В этом пошаговом руководстве вы проанализируете управляемый проект на предмет дефектов кода, используя прежний анализ кода.

В этой статье описывается процесс использования устаревшего анализа для анализа сборок управляемого кода .NET на соответствие рекомендациям по проектированию .NET.

## <a name="create-a-class-library"></a>Создание библиотеки классов

### <a name="to-create-a-class-library"></a>Создание библиотеки классов

1. В меню **Файл** последовательно выберите пункты **Создать** > **Проект**.

1. В диалоговом окне **Новый проект** разверните узел **установленный** > **C#визуальный**элемент, а затем выберите **Рабочий стол Windows**.

1. Выберите шаблон **Библиотека классов (.NET Framework)** .

1. В текстовом поле **имя** введите **кодеаналисисманажеддемо** и нажмите кнопку **ОК**.

1. После создания проекта откройте файл *Class1.CS* .

1. Замените существующий текст в Class1.cs следующим кодом:

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

### <a name="to-analyze-a-managed-project-for-code-defects"></a>Анализ управляемого проекта на предмет дефектов кода

1. Выберите проект Кодеаналисисманажеддемо в **Обозреватель решений**.

1. В меню **Проект** выберите пункт **Свойства**.

     Отобразится страница свойств Кодеаналисисманажеддемо.

1. Перейдите на вкладку **анализ кода** .

1. Убедитесь, что установлен флажок **Включить анализ кода при сборке** .

1. В раскрывающемся списке **выполнить этот набор правил** выберите параметр **Майкрософт все правила**.

1. В меню **файл** выберите команду **Сохранить выбранные элементы**, а затем закройте страницы свойств.

1. В меню **Сборка** выберите команду **построить кодеаналисисманажеддемо**.

    Предупреждения сборки проекта Кодеаналисисманажеддемо отображаются в окнах **Список ошибок** и **вывод** .

## <a name="correct-the-code-analysis-issues"></a>Устранение проблем с анализом кода

### <a name="to-correct-code-analysis-rule-violations"></a>Исправление нарушений правил анализа кода

1. В меню **вид** выберите **Список ошибок**.

    В зависимости от выбранного профиля разработчика может потребоваться указать **другие окна** в меню **вид** , а затем выбрать **Список ошибок**.

1. В **обозревателе решений** выберите **Показать все файлы**.

1. Разверните узел Свойства, а затем откройте файл *AssemblyInfo.CS* .

1. Чтобы исправить предупреждения, используйте следующие советы.

   [CA1014 Пометьте сборки с](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)помощью CLSCompliantAttribute: Microsoft. Design: "Demo" должен быть помечен атрибутом CLSCompliantAttribute, а его значение должно быть true.

   1. Добавьте код `using System;` в файл AssemblyInfo.cs.

   1. Затем добавьте код `[assembly: CLSCompliant(true)]` в конец файла AssemblyInfo.cs.

   [CA1032 Реализуйте стандартные конструкторы](../code-quality/ca1032-implement-standard-exception-constructors.md)исключений: Microsoft. Design: Добавьте в этот класс следующий конструктор: открытая демонстрация (строка)

   1. Добавьте конструктор `public demo (String s) : base(s) { }` в класс `demo`.

   [CA1032 Реализуйте стандартные конструкторы](../code-quality/ca1032-implement-standard-exception-constructors.md)исключений: Microsoft. Design: Добавьте в этот класс следующий конструктор: открытая демонстрация (строка, исключение)

   1. Добавьте конструктор `public demo (String s, Exception e) : base(s, e) { }` в класс `demo`.

   [CA1032 Реализуйте стандартные конструкторы](../code-quality/ca1032-implement-standard-exception-constructors.md)исключений: Microsoft. Design: Добавьте в этот класс следующий конструктор: защищенная демонстрация (SerializationInfo, StreamingContext).

   1. Добавьте код `using System.Runtime.Serialization;` в начало файла Class1.cs.

   1. Затем добавьте конструктор`protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

   [CA1032 Реализуйте стандартные конструкторы](../code-quality/ca1032-implement-standard-exception-constructors.md)исключений: Microsoft. Design: Добавьте в этот класс следующий конструктор: открытая демонстрация ().

   1. Добавьте конструктор `public demo () : base() { }` в класс **.** `demo`

   [CA1709 Идентификаторы должны иметь правильный](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)регистр: Microsoft. Naming: Исправьте регистр имени пространства имен "Тесткоде", изменив его на "Тесткоде".

   1. Измените регистр пространства имен `testCode` на. `TestCode`

   [CA1709 Идентификаторы должны иметь правильный](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)регистр: Microsoft. Naming: Исправьте регистр имени типа "Demo", изменив его на "Demo".

   1. Измените имя элемента на `Demo`.

   [CA1709 Идентификаторы должны иметь правильный](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)регистр: Microsoft. Naming: Исправьте регистр для имени элемента "Item", изменив его на "Item".

   1. Измените имя элемента на `Item`.

   [CA1710 Идентификаторы должны иметь правильные суффиксы](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft. Naming: Переименуйте "Тесткоде. Demo" в конец "Exception".

   1. Измените имя класса и его конструкторов на `DemoException`.

   [CA2210: Сборки должны иметь допустимые строгие имена](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): Подпишите "Кодеаналисисманажеддемо" с помощью ключа строгого имени.

   1. В меню **проект** выберите **Свойства кодеаналисисманажеддемо**.

      Отобразятся свойства проекта.

   1. Перейдите на вкладку **Подписывание** .

   1. Установите флажок **подписать сборку** .

   1. В списке **выберите имя строки файл ключа** выберите  **\<создать... >** .

      Откроется диалоговое окно **Создание ключа строгого имени** .

   1. В поле **имя файла ключа**введите тесткэй.

   1. Введите пароль и нажмите кнопку **ОК**.

   1. В меню **файл** выберите команду **Сохранить выбранные элементы**, а затем закройте страницы свойств.

   [CA2237. Пометьте типы ISerializable на](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)SerializableAttribute: Microsoft. Usage: Добавьте атрибут [Serializable] в тип "Demo", так как этот тип реализует интерфейс ISerializable.

   1. Добавьте атрибут в класс `demo`. `[Serializable ()]`

   После завершения изменений файл Class1.cs должен выглядеть следующим образом:

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

## <a name="exclude-code-analysis-warnings"></a>Исключить предупреждения анализа кода

1. Для каждого из оставшихся предупреждений выполните следующие действия.

    1. Выберите предупреждение в **Список ошибок**.

    1. В контекстном меню (контекстное меню) выберите **подавлять** > **в файле подавления**.

1. Перестройте проект.

     Проект строится без предупреждений или ошибок.

## <a name="see-also"></a>См. также

[Анализ кода для управляемого кода](../code-quality/code-analysis-for-managed-code-overview.md)