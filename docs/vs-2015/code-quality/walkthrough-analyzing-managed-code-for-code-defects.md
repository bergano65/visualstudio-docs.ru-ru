---
title: Пошаговое руководство. Проверка управляемого кода на наличие дефектов кода | Документация Майкрософт
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 26d8412318efd2292fd0f5a0f0ef52fe36c7d06c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60116294"
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>Пошаговое руководство. Анализ управляемого кода на наличие дефектов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве вы анализировать управляемого проекта для дефектов кода с помощью средства анализа кода.  
  
 В этом пошаговом руководстве вы пошагово проанализируем процесс с помощью функций анализа кода для анализа вашей сборок управляемого кода .NET на соответствие рекомендациям по Microsoft .NET Framework.  
  
 В этом пошаговом руководстве вы:  
  
- Анализа и исправления предупреждений о дефектах кода.  
  
## <a name="prerequisites"></a>Предварительные требования  
  
- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
## <a name="create-a-class-library"></a>Создание библиотеки классов  
  
#### <a name="to-create-a-class-library"></a>Чтобы создать библиотеку классов  
  
1. На **файл** меню [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], нажмите кнопку **New** и нажмите кнопку **проекта**.  
  
2. В **новый проект** диалогового **типы проектов**, нажмите кнопку **Visual C#**.  
  
3. В разделе **шаблоны**выберите **библиотеки классов**.  
  
4. В **имя** текстовое поле, тип **CodeAnalysisManagedDemo** и нажмите кнопку **ОК**.  
  
5. После создания проекта откройте файл Class1.cs.  
  
6. Замените существующий текст в файл Class1.cs следующим кодом:  
  
     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`  
  
7. Сохраните файл Class1.cs.  
  
## <a name="analyze-the-project"></a>Анализ проекта  
  
#### <a name="to-analyze-a-managed-project-for-code-defects"></a>Анализ управляемого проекта для дефектов кода  
  
1. Выберите проект CodeAnalysisManagedDemo в **обозревателе решений**.  
  
2. В меню **Проект** выберите пункт **Свойства**.  
  
     Откроется страница свойств CodeAnalysisManagedDemo.  
  
3. Нажмите кнопку **CodeAnalysis**.  
  
4. Убедитесь, что **включить анализ кода в построении (определяет константу CODE_ANALYSIS**) установлен.  
  
5. Из **выполнить этот набор правил** стрелку раскрывающегося списка выберите **все правила Майкрософт**.  
  
6. На **файл** меню, щелкните **сохранить выбранные элементы**, а затем закройте свойств проекта ManagedDemo.  
  
7. На **построения** меню, щелкните **построения ManagedDemo**.  
  
     В выводятся предупреждения сборки проекта CodeAnalysisManagedDemo **анализа кода** и **вывода** windows.  
  
     Если **анализа кода** окно не отображается, на **анализ** меню, выберите **Windows** и затем **выберите анализа кода**.  
  
## <a name="correct-the-code-analysis-issues"></a>Исправьте проблемы анализа кода  
  
#### <a name="to-correct-code-analysis-rule-violations"></a>Для устранения нарушений правил анализа кода  
  
1. На **представление** меню, щелкните **список ошибок**.  
  
     В зависимости от выбранного профиля разработчика, возможно, чтобы они указывали **Other Windows** на **представление** меню, а затем щелкните **список ошибок**.  
  
2. В **обозревателе решений**, нажмите кнопку **Показать все файлы**.  
  
3. Разверните узел свойства затем откройте файл AssemblyInfo.cs.  
  
4. Используйте следующие параметры для устранения предупреждения.  
  
- [CA1014: Помечайте сборки атрибутом CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft.Design: «demo» должен быть помечен атрибутом CLSCompliantAttribute и его значение должно быть true.  
  
  - Добавьте код `using``System;` в файл AssemblyInfo.cs.  
  
       Далее добавьте код `[assembly: CLSCompliant(true)]` в конец файл AssemblyInfo.cs.  
  
       Перестройте проект.  
  
- [CA1032: Реализуйте стандартные конструкторы исключения](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Добавьте следующий конструктор этого класса: открытый demo(String)  
  
  - Добавьте конструктор `public demo (String s) : base(s) { }` к классу `demo`.  
  
- [CA1032: Реализуйте стандартные конструкторы исключения](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Добавьте следующий конструктор этого класса: открытый demo (String, исключений)  
  
  - Добавьте конструктор `public demo (String s, Exception e) : base(s, e) { }` к классу `demo`.  
  
- [CA1032: Реализуйте стандартные конструкторы исключения](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Добавьте следующий конструктор этого класса: защищенные demo (SerializationInfo, StreamingContext)  
  
  - Добавьте код `using System.Runtime.Serialization;` в начало файла Class1.cs.  
  
       Добавьте конструктор `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`  
  
       Перестройте проект.  
  
- [CA1032: Реализуйте стандартные конструкторы исключения](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Добавьте следующий конструктор этого класса: открытый demo()  
  
  - Добавьте конструктор `public demo () : base() { }` к классу `demo` **.**  
  
       Перестройте проект.  
  
- [CA1709: Идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Исправьте прописные или строчные буквы имени пространства имен «testCode», изменив ее на «TestCode».  
  
  - Регистр пространства имен `testCode` для `TestCode`.  
  
- [CA1709: Идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Исправьте прописные или строчные буквы имени типа «demo», изменив ее на «Demo».  
  
  - Измените имя элемента, на который `Demo`.  
  
- [CA1709: Идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Исправьте прописные или строчные буквы имени член «item», изменив ее на «Item».  
  
  - Измените имя элемента, на который `Item`.  
  
- [CA1710: Идентификаторы должны иметь правильные суффиксы](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft.Naming: Переименуйте «testCode.demo» конец «Исключение».  
  
  - Измените имя класса и его конструкторов для `DemoException`.  
  
- [CA2210: Сборки должны иметь допустимые строгие имена](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): Подпись «ManagedDemo» с ключом строгого имени.  
  
  - На **проекта** меню, щелкните **ManagedDemo свойства**.  
  
       Отображаются свойства проекта.  
  
       Нажмите кнопку **подписи**.  
  
       Выберите **подписать сборку** "флажок".  
  
       В **выберите файл ключа строгого имени** выберите  **\<создать... >**.  
  
       **Создание ключа строгого имени** откроется диалоговое окно.  
  
       В **имя файла ключа**, введите TestKey.  
  
       Введите пароль и нажмите кнопку **ОК**.  
  
       На **файл** меню, щелкните **сохранить выбранные элементы**, а затем закройте окно свойств.  
  
       Перестройте проект.  
  
- [CA2237. Пометьте типы ISerializable атрибутом SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage: Добавьте атрибут [Serializable] к типу «demo», так как этот тип реализует ISerializable.  
  
  - Добавить `[Serializable ()]` классу атрибут `demo`.  
  
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
  
1. Для каждой из оставшихся предупреждения сделайте следующее:  
  
   1. В окне «Анализ кода» выберите предупреждение.  
  
   2. Выберите **действия**, нажмите кнопку **подавить сообщение**, а затем выберите **в файле проекта для блокируемых предупреждений**.  
  
      Дополнительные сведения см. в разделе [Как Подавление предупреждений при помощи пункта меню](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)  
  
2. Перестройте проект.  
  
    Сборка проекта выполняется без предупреждения или ошибки.
