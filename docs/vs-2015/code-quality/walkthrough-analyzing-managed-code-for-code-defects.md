---
title: Пошаговое руководство. анализ управляемого кода для дефектов кода | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, walkthroughs
- managed code, analyzing
- code analysis tool, walkthroughs
ms.assetid: 22b99f49-1924-4fb5-a421-c8b23e5d5cd4
caps.latest.revision: 47
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9478394162051fc08c33047cf1ac24275aff75e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72609323"
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>Пошаговое руководство. Проверка управляемого кода на наличие дефектов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве вы проанализируете управляемый проект на предмет дефектов кода с помощью средства анализа кода.

 В этом пошаговом руководстве описывается процесс использования анализа кода для анализа сборок управляемого кода .NET в отношении соответствия рекомендациям по проектированию Microsoft .NET Framework.

 В этом пошаговом руководстве описаны следующие операции:

- Анализ и исправление предупреждений о дефектах кода.

## <a name="prerequisites"></a>Предварительные требования

- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].

## <a name="create-a-class-library"></a>Создание библиотеки классов

#### <a name="to-create-a-class-library"></a>Создание библиотеки классов

1. В меню **файл** в выберите [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] команду **создать** , а затем выберите **проект**.

2. В диалоговом окне **Новый проект** в разделе **типы проектов**выберите **Visual C#**.

3. В разделе **Шаблоны** выберите пункт **Библиотека классов**.

4. В текстовом поле **имя** введите **кодеаналисисманажеддемо** и нажмите кнопку **ОК**.

5. После создания проекта откройте файл Class1.cs.

6. Замените существующий текст в Class1.cs следующим кодом:

     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`

7. Сохраните файл Class1.cs.

## <a name="analyze-the-project"></a>Анализ проекта

#### <a name="to-analyze-a-managed-project-for-code-defects"></a>Анализ управляемого проекта на предмет дефектов кода

1. Выберите проект Кодеаналисисманажеддемо в **Обозреватель решений**.

2. В меню **Проект** выберите **Свойства**.

     Отобразится страница свойств Кодеаналисисманажеддемо.

3. Щелкните **CodeAnalysis**.

4. Убедитесь, что установлен флажок  **Включить анализ кода для сборки (определяется CODE_ANALYSIS константа**).

5. В раскрывающемся списке **выполнить этот набор правил** выберите параметр **Майкрософт все правила**.

6. В меню **файл** выберите команду **Сохранить выбранные элементы**, а затем закройте страницы свойств манажеддемо.

7. В меню **Сборка** выберите команду **построить манажеддемо**.

     Предупреждения о сборке проекта Кодеаналисисманажеддемо отображаются в окнах " **анализ кода** " и " **вывод** ".

     Если окно **анализ кода** не отображается, в меню **анализ** выберите пункт **окна** , а затем **выберите анализ кода**.

## <a name="correct-the-code-analysis-issues"></a>Устранение проблем с анализом кода

#### <a name="to-correct-code-analysis-rule-violations"></a>Исправление нарушений правил анализа кода

1. В меню **Вид** выберите пункт **Список ошибок**.

     В зависимости от выбранного профиля разработчика может потребоваться указать **другие окна** в меню **вид** , а затем выбрать пункт **Список ошибок**.

2. В **Обозреватель решений**щелкните " **отобразить все файлы**".

3. Затем разверните узел Свойства и откройте файл AssemblyInfo.cs.

4. Для исправления предупреждений используйте следующую команду:

- [CA1014: Пометьте сборки атрибутом CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft. Design: "Demo" должен быть помечен атрибутом CLSCompliantAttribute, а его значение должно быть true.

  - Добавьте код `using``System;` в файл AssemblyInfo.cs.

       Затем добавьте код `[assembly: CLSCompliant(true)]` в конец файла AssemblyInfo.cs.

       Выполните повторную сборку проекта.

- [CA1032: реализуйте стандартные конструкторы исключений](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: Добавьте следующий конструктор к этому классу: открытая демонстрация (строка)

  - Добавьте конструктор `public demo (String s) : base(s) { }` в класс `demo` .

- [CA1032: реализуйте стандартные конструкторы исключений](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: Добавьте следующий конструктор к этому классу: открытая демонстрация (строка, исключение)

  - Добавьте конструктор `public demo (String s, Exception e) : base(s, e) { }` в класс `demo` .

- [CA1032: реализуйте стандартные конструкторы исключений](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: Добавьте следующий конструктор в этот класс: protected Demo (SerializationInfo, StreamingContext)

  - Добавьте код `using System.Runtime.Serialization;` в начало файла Class1.cs.

       Затем добавьте конструктор `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

       Выполните повторную сборку проекта.

- [CA1032: реализуйте стандартные конструкторы исключений](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: Добавьте следующий конструктор к этому классу: открытая демонстрация ()

  - Добавьте конструктор `public demo () : base() { }` в класс `demo` **.**

       Выполните повторную сборку проекта.

- [CA1709: идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. Naming: Исправьте регистр имени пространства имен "тесткоде", изменив его на "тесткоде".

  - Измените регистр пространства имен `testCode` на `TestCode` .

- [CA1709: идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. Naming: Исправьте регистр имени типа "Demo", изменив его на "Demo".

  - Измените имя элемента на `Demo` .

- [CA1709: идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. Naming: исправить регистр имени элемента "Item", изменив его на "Item".

  - Измените имя элемента на `Item` .

- [CA1710: идентификаторы должны иметь правильный суффикс](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft. Naming: Rename "тесткоде. Demo", заканчивающийся на "Exception".

  - Измените имя класса и его конструкторов на `DemoException` .

- [CA2210: сборки должны иметь допустимые строгие имена](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): знак "манажеддемо" с ключом строгого имени.

  - В меню **проект** выберите пункт **Свойства манажеддемо**.

       Отобразятся свойства проекта.

       Щелкните **Подписывание**.

       Установите флажок **подписать сборку** .

       В списке **выберите имя строки файл ключа** выберите **\<New…>** .

       Откроется диалоговое окно **Создание ключа строгого имени**.

       В поле **имя файла ключа**введите тесткэй.

       Введите пароль и нажмите кнопку **ОК**.

       В меню **файл** выберите команду **Сохранить выбранные элементы**, а затем закройте страницы свойств.

       Выполните повторную сборку проекта.

- [CA2237: Пометьте типы ISerializable с SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft. Usage: добавьте атрибут [Serializable] в тип "Demo", так как этот тип реализует интерфейс ISerializable.

  - Добавьте `[Serializable ()]` атрибут в класс `demo` .

       Выполните повторную сборку проекта.

  После завершения изменений файл Class1.cs должен выглядеть следующим образом:

```
//CodeAnalysisManagedDemo
//Class1.cs
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

## <a name="exclude-code-analysis-warnings"></a>Исключить предупреждения анализа кода

#### <a name="to-exclude-code-defect-warnings"></a>Исключение предупреждений о дефектах кода

1. Для каждого из оставшихся предупреждений выполните следующие действия.

   1. В окне анализ кода выберите предупреждение.

   2. Выберите **действия**, затем **подавить сообщение**, а затем выберите **в списке файл подавления проекта**.

      Дополнительные сведения см. в разделе [как отключить предупреждения с помощью пункта меню.](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)

2. Выполните повторную сборку проекта.

    Проект строится без предупреждений или ошибок.
