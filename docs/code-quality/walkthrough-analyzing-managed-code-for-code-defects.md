---
title: "Пошаговое руководство: Проверка управляемого кода на наличие дефектов кода | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code analysis, walkthroughs
- managed code, analyzing
- code analysis tool, walkthroughs
ms.assetid: 22b99f49-1924-4fb5-a421-c8b23e5d5cd4
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 6ea39704ea232fb304257b897087f0ae60d19c4f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>Пошаговое руководство. Проверка управляемого кода на наличие дефектов
В этом пошаговом руководстве анализ управляемого проекта на наличие дефектов кода с помощью средства анализа кода.  
  
 В этом пошаговом руководстве будет пошаговый процесс с помощью функций анализа кода для анализа вашей сборок управляемого кода .NET на соответствие рекомендациям по Microsoft .NET Framework.  
  
 В этом пошаговом руководстве вы:  
  
-   Анализа и исправления предупреждений о дефектах кода.  
  
## <a name="prerequisites"></a>Предварительные требования  
  
-   [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
  
## <a name="create-a-class-library"></a>Создание библиотеки классов  
  
#### <a name="to-create-a-class-library"></a>Для создания библиотеки классов  
  
1.  На **файл** меню [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], нажмите кнопку **New** и нажмите кнопку **проекта**.  
  
2.  В **новый проект** диалогового **типы проектов**, нажмите кнопку **Visual C#**.  
  
3.  В разделе **шаблоны**выберите **библиотеки классов**.  
  
4.  В **имя** введите **CodeAnalysisManagedDemo** и нажмите кнопку **ОК**.  
  
5.  После создания проекта, откройте файл Class1.cs.  
  
6.  Замените существующий текст в файле Class1.cs следующий код:  
  
     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`  
  
7.  Сохраните файл Class1.cs.  
  
## <a name="analyze-the-project"></a>Анализ проекта  
  
#### <a name="to-analyze-a-managed-project-for-code-defects"></a>Анализ управляемого проекта для дефекта кода  
  
1.  Выберите проект в CodeAnalysisManagedDemo **обозревателе решений**.  
  
2.  В меню **Проект** выберите пункт **Свойства**.  
  
     Откроется страница свойств CodeAnalysisManagedDemo.  
  
3.  Нажмите кнопку **CodeAnalysis**.  
  
4.  Убедитесь, что **включить анализ кода в построении (определяет константу CODE_ANALYSIS**) установлен.  
  
5.  Из **выполнить этот набор правил** раскрывающемся списке выберите **все правила Майкрософт**.  
  
6.  На **файл** меню, нажмите кнопку **сохранить выбранные элементы**, а затем закройте свойств проекта ManagedDemo.  
  
7.  На **построения** меню, нажмите кнопку **Построить ManagedDemo**.  
  
     Предупреждения построения проекта CodeAnalysisManagedDemo выводятся в **анализа кода** и **вывода** windows.  
  
     Если **анализа кода** окно не отображается, на **анализ** меню, выберите **Windows** и затем **выберите Анализ кода**.  
  
## <a name="correct-the-code-analysis-issues"></a>Исправьте проблемы анализа кода  
  
#### <a name="to-correct-code-analysis-rule-violations"></a>Для устранения нарушения правил анализа кода  
  
1.  На **представление** меню, нажмите кнопку **список ошибок**.  
  
     В зависимости от выбранного профиля разработчика, возможно, чтобы она указывала на **другие окна** на **представление** меню, а затем нажмите **список ошибок**.  
  
2.  В **обозревателе решений**, нажмите кнопку **Показать все файлы**.  
  
3.  Затем разверните узел свойства и откройте файл AssemblyInfo.cs.  
  
4.  Для устранения предупреждения используйте следующие параметры:  
  
-   [CA1014: Помечайте сборки атрибутом CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft.Design: «demo» должен быть помечен атрибутом CLSCompliantAttribute и его значение должно быть true.  
  
    -   Добавьте код `using``System;` файл AssemblyInfo.cs.  
  
         Добавьте следующий код `[assembly: CLSCompliant(true)]` файл AssemblyInfo.cs в конец.  
  
         Перестройте проект.  
  
-   [CA1032: Реализуйте стандартные конструкторы исключения](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: добавьте следующий конструктор этого класса: открытого demo(String)  
  
    -   Добавьте конструктор `public demo (String s) : base(s) { }` к классу `demo`.  
  
-   [CA1032: Реализуйте стандартные конструкторы исключения](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: добавьте следующий конструктор этого класса: демонстрация открытые (String, исключение)  
  
    -   Добавьте конструктор `public demo (String s, Exception e) : base(s, e) { }` к классу `demo`.  
  
-   [CA1032: Реализуйте стандартные конструкторы исключения](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: добавьте следующий конструктор этого класса: защищенные Демонстрация (SerializationInfo, StreamingContext)  
  
    -   Добавьте код `using System.Runtime.Serialization;` в начало файла Class1.cs.  
  
         Добавьте конструктор`protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`  
  
         Перестройте проект.  
  
-   [CA1032: Реализуйте стандартные конструкторы исключения](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: добавьте следующий конструктор этого класса: открытого demo()  
  
    -   Добавьте конструктор `public demo () : base() { }` к классу `demo` **.**  
  
         Перестройте проект.  
  
-   [CA1709: Идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: исправьте регистр имени пространства имен «testCode», изменив ее «TestCode».  
  
    -   Изменить регистр пространства имен `testCode` для `TestCode`.  
  
-   [CA1709: Идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: исправьте регистр имени типа «demo», изменив ее «Demo».  
  
    -   Измените имя члена `Demo`.  
  
-   [CA1709: Идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: исправьте регистр имени члена «item», изменив ее «Item».  
  
    -   Измените имя члена `Item`.  
  
-   [CA1710: Идентификаторы должны иметь правильные суффиксы](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft.Naming: переименование «testCode.demo» завершить «Исключения».  
  
    -   Измените имя класса и его конструкторов на `DemoException`.  
  
-   [CA2210: Сборки должны иметь допустимые строгие имена](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): подпись «ManagedDemo» с ключом строгого имени.  
  
    -   На **проекта** меню, нажмите кнопку **ManagedDemo свойства**.  
  
         Будут отображены свойства проекта.  
  
         Нажмите кнопку **подписи**.  
  
         Выберите **подписать сборку** флажок.  
  
         В **выберите файл ключа строгого имени** выберите  **\<создать... >**.  
  
         **Создание ключа строгого имени** откроется диалоговое окно.  
  
         В **имя файла ключа**, введите TestKey.  
  
         Введите пароль и нажмите кнопку **ОК**.  
  
         На **файл** меню, нажмите кнопку **сохранить выбранные элементы**, а затем закройте страницы свойств.  
  
         Перестройте проект.  
  
-   [CA2237: Пометьте типы ISerializable атрибутом SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage: добавить атрибут [Serializable] в тип «demo», что этот тип реализует интерфейс ISerializable.  
  
    -   Добавить `[Serializable ()]` к классу атрибут `demo`.  
  
         Перестройте проект.  
  
 После завершения изменения файл Class1.cs должен выглядеть следующим образом:  
  
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
  
## <a name="exclude-code-analysis-warnings"></a>Исключение предупреждений анализа кода  
  
#### <a name="to-exclude-code-defect-warnings"></a>Для исключения предупреждений о дефектах кода  
  
1.  Для каждого из оставшихся предупреждений выполните следующее:  
  
    1.  Выберите предупреждение в окне анализа кода.  
  
    2.  Выберите **действия**, выберите **подавить сообщение**, а затем выберите **в файле проекта для блокируемых**.  
  
     Дополнительные сведения см. в разделе [как: отключение предупреждений при помощи пункта меню](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)  
  
2.  Перестройте проект.  
  
     Сборка проекта выполняется без предупреждения или ошибки.