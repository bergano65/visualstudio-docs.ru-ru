---
title: "Пошаговое руководство. Проверка управляемого кода на наличие дефектов | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "анализ кода, пошаговые руководства"
  - "управляемый код, анализ"
  - "средство анализа кода, пошаговые руководства"
ms.assetid: 22b99f49-1924-4fb5-a421-c8b23e5d5cd4
caps.latest.revision: 45
caps.handback.revision: 45
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Пошаговое руководство. Проверка управляемого кода на наличие дефектов
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В этом пошаговом руководстве анализ управляемого проекта на наличие дефектов кода при помощи средства анализа кода.  
  
 В этом пошаговом руководстве приводится пошаговое описание процесса использования анализа кода для анализа вашего сборок управляемого кода .NET на соответствие с рекомендациями по разработке Microsoft .NET Framework.  
  
 В этом пошаговом руководстве вы:  
  
-   Анализ и исправление предупреждений о дефектах кода.  
  
## <a name="prerequisites"></a>Предварительные требования  
  
-   [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
  
## <a name="create-a-class-library"></a>Создание библиотеки классов  
  
#### <a name="to-create-a-class-library"></a>Создание библиотеки классов  
  
1.  На **файл** меню [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], нажмите кнопку **New** и нажмите кнопку **проекта**.  
  
2.  В **Новый проект** диалогового **типы проектов**, нажмите кнопку **Visual C#**.  
  
3.  В разделе **шаблоны**, выберите **библиотеки классов**.  
  
4.  В **имя** введите **CodeAnalysisManagedDemo** и нажмите кнопку **ОК**.  
  
5.  После создания проекта откройте файл Class1.cs.  
  
6.  Замените существующий текст в файле Class1.cs на следующий код:  
  
     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`  
  
7.  Сохраните файл Class1.cs.  
  
## <a name="analyze-the-project"></a>Анализ проекта  
  
#### <a name="to-analyze-a-managed-project-for-code-defects"></a>Для проверки управляемого проекта на наличие дефектов  
  
1.  Выберите проект в CodeAnalysisManagedDemo **обозревателе решений**.  
  
2.  На **проекта** меню, щелкните **Свойства**.  
  
     Откроется страница свойств CodeAnalysisManagedDemo.  
  
3.  Щелкните **CodeAnalysis**.  
  
4.  Убедитесь, что  **Включить анализ кода в построении (определяет константу CODE_ANALYSIS**) установлен.  
  
5.  Из **выполнить этот набор правил** раскрывающемся списке выберите **все правила Microsoft**.  
  
6.  На **файл** меню, щелкните **Сохранить выбранные элементы**, а затем закройте свойств проекта ManagedDemo.  
  
7.  На **построения** меню, щелкните **Построить ManagedDemo**.  
  
     Предупреждения построения проекта CodeAnalysisManagedDemo выводятся в **Анализ кода** и **вывода** windows.  
  
     Если **анализа кода** окне не отображаются, в **Анализ** меню, выберите **Windows** и затем **выберите Анализ кода**.  
  
## <a name="correct-the-code-analysis-issues"></a>Исправление проблем анализа кода  
  
#### <a name="to-correct-code-analysis-rule-violations"></a>Исправление нарушений правил анализа кода  
  
1.  На **представление** меню, щелкните **Список ошибок**.  
  
     В зависимости от выбранного профиля разработчика, может потребоваться пункты **Другие окна** на **представление** меню, а затем нажмите **Список ошибок**.  
  
2.  В **обозревателе**, нажмите кнопку **Показать все файлы**.  
  
3.  Затем разверните узел свойства и откройте файл AssemblyInfo.cs.  
  
4.  Для устранения предупреждения используйте следующие параметры:  
  
-   [CA1014: Помечайте сборки атрибутом CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft.Design: «demo» должны быть помечены CLSCompliantAttribute, а его значение должно быть true.  
  
    -   Добавьте код `using``System;` файл AssemblyInfo.cs.  
  
         Добавьте следующий код `[assembly: CLSCompliant(true)]` конец файл AssemblyInfo.cs.  
  
         Перестройте проект.  
  
-   [CA1032: Реализуйте стандартные конструкторы исключения](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: добавьте следующий конструктор в класс: открытые demo(String)  
  
    -   Добавьте конструктор `public demo (String s) : base(s) { }` класс `demo`.  
  
-   [CA1032: Реализуйте стандартные конструкторы исключения](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: добавьте следующий конструктор в класс: открытый Демонстрация (String, Exception)  
  
    -   Добавьте конструктор `public demo (String s, Exception e) : base(s, e) { }` класс `demo`.  
  
-   [CA1032: Реализуйте стандартные конструкторы исключения](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: добавьте следующий конструктор в класс: защищенные Демонстрация (SerializationInfo, StreamingContext)  
  
    -   Добавьте код `using System.Runtime.Serialization;` в начало файла Class1.cs.  
  
         Добавьте конструктор `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`  
  
         Перестройте проект.  
  
-   [CA1032: Реализуйте стандартные конструкторы исключения](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: добавьте следующий конструктор в класс: открытые demo()  
  
    -   Добавьте конструктор `public demo () : base() { }` класс `demo`**.**  
  
         Перестройте проект.  
  
-   [CA1709: Идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: исправьте регистр имен имя «testCode», измените его на «TestCode».  
  
    -   Измените регистр пространства имен `testCode` для `TestCode`.  
  
-   [CA1709: Идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: исправьте регистр имени типа «demo», измените его значение на «Demo».  
  
    -   Измените имя члена `Demo`.  
  
-   [CA1709: Идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: исправление регистр имени члена «item» изменив «Item».  
  
    -   Измените имя члена `Item`.  
  
-   [CA1710: Идентификаторы должны иметь правильные суффиксы](../Topic/CA1710:%20Identifiers%20should%20have%20correct%20suffix.md): Microsoft.Naming: Rename «testCode.demo» завершить «Исключения».  
  
    -   Измените имя класса и его конструкторов на `DemoException`.  
  
-   [CA2210: Сборки должны иметь допустимые строгие имена](../Topic/CA2210:%20Assemblies%20should%20have%20valid%20strong%20names.md): вход «ManagedDemo» с ключом строгого имени.  
  
    -   На **проекта** меню, щелкните **ManagedDemo свойства**.  
  
         Отобразятся свойства проекта.  
  
         Щелкните **подписи**.  
  
         Выберите **подписать сборку** флажок.  
  
         В **выберите файл ключей строгого имени** выберите **\< Создать >**.  
  
          **Создание ключа строгого имени** откроется диалоговое окно.  
  
         В **имя файла ключа**, введите TestKey.  
  
         Введите пароль и нажмите кнопку **ОК**.  
  
         На **файл** меню, щелкните **Сохранить выбранные элементы**, а затем закройте окно свойств.  
  
         Перестройте проект.  
  
-   [CA2237: Пометьте типы ISerializable атрибутом SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage: добавить атрибут [Serializable] в тип «demo», что этот тип реализует интерфейс ISerializable.  
  
    -   Добавить `[Serializable ()]` к классу атрибут `demo`.  
  
         Перестройте проект.  
  
 После внесения изменений файл Class1.cs должен выглядеть следующим образом:  
  
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
  
1.  Для каждой из оставшихся предупреждения выполните следующее:  
  
    1.  Выберите предупреждение в окне анализа кода.  
  
    2.  Выберите **действия**, выберите **подавить сообщение**, а затем выберите **в файле подавления проекта**.  
  
     Дополнительные сведения см. в разделе [Практическое руководство: отключение предупреждений при помощи пункта меню](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)  
  
2.  Перестройте проект.  
  
     Построение проекта выполняется без предупреждений и ошибок.